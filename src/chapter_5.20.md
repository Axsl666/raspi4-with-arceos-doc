# 代码结构导读
在使用rust编程时，我们并不总是遵循OOP（面向对象）的编程思想，转而我们更注重数据的流向，也就是说：我们更关注数据是怎么来的，怎么被处理的，在处理完成后，是怎么被传递到下一步的？

我们从入口开始：

## 入口
首先，目前在开发阶段，我们暂时选择不让系统在开机时自动进行驱动的初始化，转而由我们手动触发，因此，我们首先修改[命令行界面](../../../apps/cli/)

首先，修改cli crate的[Cargo.toml](../../../apps/cli/Cargo.toml)

```toml
#...
[dependencies]
# axfs_vfs = { path = "../../../crates/axfs_vfs", optional = true }
# axfs_ramfs = { path = "../../../crates/axfs_ramfs", optional = true }
# crate_interface = { path = "../../../crates/crate_interface", optional = true }
# axstd = { path = "../../../ulib/axstd", features = ["alloc", "fs"], optional = true }
axstd = { path = "../../ulib/axstd", optional = true }
axfeat = { path = "../../api/axfeat", features = [
  "phytium-pi", # +
  "usb-host", # +
  "multitask", # +
] }
driver_usb = { path = "../../crates/driver_usb", features = ["phytium-xhci"] } # +
xhci = "0.9" # +
#...
```

在添加了driver_usb这个crate后，我们就可以在代码中直接调用[驱动中的函数](../../../apps/cli/src/cmd.rs)

```rust
//...
const CMD_TABLE: &[(&str, CmdHandler)] = &[
    ("exit", do_exit),
    ("help", do_help),
    ("uname", do_uname),
    ("ldr", do_ldr),
    ("str", do_str),
    ("test_xhci", test_xhci), // +
    ("enum_device", enum_device),// +
];

fn test_xhci(_args: &str) { // +
    driver_usb::try_init()  // +
}                           // +

//...
fn do_ldr(args: &str) { //顺便优化一下do_ldr，来让我们读内存更方便一些
    println!("ldr");
    if args.is_empty() {
        println!("try: ldr ffff0000400fe000 4");
    }

    fn ldr_one(addr: &str, offset: &str) -> io::Result<()> {
        // println!("addr = {}", addr);

        if let (Ok(parsed_addr), Ok(parsed_offset)) = (
            u64::from_str_radix(addr, 16),
            u64::from_str_radix(offset, 10),
        ) {
            for i in 0..parsed_offset {
                let address: *const u64 = (parsed_addr + i * 8) as *const u64; // 强制转换为合适的指针类型
                if address.is_aligned() {
                    let value: u64;
                    // println!("Parsed address: {:p}", address); // 打印地址时使用 %p 格式化符号

                    unsafe {
                        value = *address;
                    }

                    let le_bytes = value.to_le_bytes();

                    // println!("Value at address {}: 0x{:X}", addr, value); // 使用输入的地址打印值
                    // println!("value at address{} = 0x{:X}: ", addr, value);
                    for (j, chunk) in le_bytes.chunks(4).enumerate() {
                        let mut chunk_value: u32 = 0;
                        for (i, byte) in chunk.iter().enumerate() {
                            chunk_value |= (*byte as u32) << (i * 8);
                        }
                        println!(
                            "offset: 0x{:02x}: {:032b}",
                            i as usize * 8 + j * 4,
                            chunk_value
                        );
                    }
                } else {
                    println!("addr not aligned!");
                }
            }
        } else {
            println!("Failed to parse address.");
        }
        return Ok(());
    }

    // for addr in args.split_whitespace() {
    //     if let Err(e) = ldr_one(addr) {
    //         println!("ldr {} {}", addr, e);
    //     }
    // }
    let mut split_ascii_whitespace = args.split_ascii_whitespace();
    let base_addr = split_ascii_whitespace.next();
    let byte_counts = split_ascii_whitespace.next().unwrap_or("1");
    ldr_one(base_addr.unwrap(), byte_counts);
}
//...
```

接下来，让我们直接转到[driver_usb crate](../../../crates/driver_usb/),看看驱动到底是怎么运作的。

```zsh
[4.0K]  ./
├── [4.0K]  guide/
│   ├── [6.1K]  code_structure1.md
│   └── [7.0K]  quickstart_usb.md
├── [4.0K]  question/
│   ├── [ 39K]  minicom_output.log
│   ├── [ 23K]  question_5_29.md
│   └── [352K]  scan_from_31000000.png
├── [4.0K]  src/
│   ├── [4.0K]  host/
│   │   ├── [4.0K]  structures/
│   │   │   ├── [4.0K]  todos/
│   │   │   │   ├── [ 834]  TODO.md
│   │   │   │   └── [ 13M]  xhci_root_port_init_graph.svg
│   │   │   ├── [4.0K]  usb/
│   │   │   │   ├── [3.7K]  mod.rs
│   │   │   │   ├── [ 10K]  usb_audio.rs
│   │   │   │   ├── [ 854]  usb_device.rs
│   │   │   │   └── [   0]  usb_request.rs
│   │   │   ├── [3.1K]  command_ring.rs
│   │   │   ├── [2.3K]  context.rs
│   │   │   ├── [4.0K]  descriptor.rs
│   │   │   ├── [2.4K]  event_ring.rs
│   │   │   ├── [1.3K]  extended_capabilities.rs
│   │   │   ├── [4.2K]  mod.rs
│   │   │   ├── [1.1K]  registers.rs
│   │   │   ├── [2.3K]  root_port.rs
│   │   │   ├── [2.4K]  scratchpad.rs
│   │   │   ├── [4.2K]  transfer_ring.rs
│   │   │   ├── [9.4K]  xhci_command_manager.rs
│   │   │   ├── [6.2K]  xhci_event_manager.rs
│   │   │   ├── [4.5K]  xhci_roothub.rs
│   │   │   ├── [3.1K]  xhci_slot_manager.rs
│   │   │   └── [ 18K]  xhci_usb_device.rs
│   │   ├── [4.0K]  xhci/
│   │   │   ├── [4.0K]  vl805/
│   │   │   │   ├── [5.8K]  mailbox.rs
│   │   │   │   └── [3.0K]  mod.rs
│   │   │   └── [5.0K]  mod.rs
│   │   └── [ 304]  mod.rs
│   ├── [ 10K]  .build.rs
│   ├── [2.7K]  device_types.rs
│   ├── [2.0K]  dma.rs
│   └── [ 992]  lib.rs
├── [ 24K]  Cargo.lock
└── [1.7K]  Cargo.toml
```

首先可以关注[lib.rs](../src/lib.rs),在这里，我们参考飞腾派官方提供的信息，选择第一个XHCI控制器，其地址为0x31a0_8000,在这里我们加上了虚拟地址的前缀：0xffff_0000,但是由于arceos在映射mmio区域时，采取的是1：1映射，因此这个地址仍然指向0x31a0_8000，同时事实上我们也可以直接访问0x31a0_8000来访问控制器。
```rust
//...
pub fn try_init() {
    init(0xffff_0000_31a0_8000 as usize) //just hard code it! refer phytium pi embedded sdk
}
//...
```
* 什么是mmio?
* 答：操作系统课上老师会告诉你虚拟内存的概念，现代的计算机系统，为了上层应用的方便，都会将硬件/数据/指令，统一编址进同一片内存空间中，而开发人员能见到的就是这片空间，在这片内存空间中，映射至硬件的内存区域，就被称为MMIO区域(Memory IO)，通过MMIO区域，我们可以直接访问硬件的寄存器。
  
## 深入
接下来，让我们往里细看，看看这个函数中具体做了什么，追根溯源，最终可以追踪到[xhci](../src/host/xhci/mod.rs)这个module
```rust
pub(crate) fn init(mmio_base: usize) {
    unsafe {
        registers::init(mmio_base); //在这里，我们首先读取了xhci的寄存器，并将它们抽象为方便我们操作的数据结构
        extended_capabilities::init(mmio_base);//extended_capabilities寄存器比较特殊，他记载了xhci控制器所支持的额外可选特性
    };

    debug!("resetting xhci controller");
    debug!(
        "before reset:{:?},pagesize: {}",
        registers::handle(|r| r.operational.usbsts.read_volatile()),
        registers::handle(|r| r.operational.pagesize.read_volatile().get())
    );
    reset_xhci_controller(); //在这里，我们遵循xhci规范4.2,进行控制器的重置与暂停运行
    debug!(
        "pagesize: {}",
        registers::handle(|r| r.operational.pagesize.read_volatile().get())
    );

// -----------------0 重置完成后，我们继续遵循4.2，进行各部分有关数据结构的初始化
    xhci_slot_manager::new(); //初始化槽位管理器，xhci_slot_manager这个module中包含了dcbaa的数据结构，并且在new的时候会将其注册进xhci控制器的对应寄存器中
    scratchpad::new(); //初始化scratchpad-这部分是交给xhci控制器进行其内部用途的空间，对于我们来说是个黑盒，只需要知道我们根据规范，得分配出特定大小的连续内存空间即可
    xhci_command_manager::new(); //command_manager-其内部持有CommandRing,同时包含了一些封装好的工具函数，用于发送事件
    xhci_event_manager::new(); //event_manager-其内部持有EventRing，同时包含了各个事件处理函数的入口，换句话来说，这里是处理控制器接收到的事件的地方
    xhci_roothub::new(); //root_hub-在前面的quickstart中，我们有提到，root_hub是整个usb系统的设备树的根节点，事实上root_hub是集成在控制器中的，我们在这里对其进行初始化
//------------------0

    // axhal::irq::register_handler(ARM_IRQ_PCIE_HOST_INTA, interrupt_handler); //中断系统损坏，待修复
    // axhal::irq::register_handler(ARM_IRQ_PCIE_HOST_INTA + 1, interrupt_handler);//就目前来说，我们不使用中断，而是使用轮询eventring来检查有没有新事件

    debug!(
        "before start:{:?}",
        registers::handle(|r| r.operational.usbsts.read_volatile())
    );
    registers::handle(|r| {
        r.operational.usbcmd.update_volatile(|r| {
            r.set_run_stop();  //至此，控制器的数据结构部分分配完毕，我们在这里设置控制器运行
        });

        while r.operational.usbsts.read_volatile().hc_halted() {} //并且等待控制器开机完成，一般等待100ms,在这里我们直接用while循环等待其标志位置0
    });

//-------------------------1仅仅是一些调试信息的输出
    debug!(
        "init completed!, coltroller state:{:?}",
        registers::handle(|r| r.operational.usbsts.read_volatile())
    );

    let number_of_ports =
        registers::handle(|r| r.capability.hcsparams1.read_volatile().number_of_ports() as usize);

    for i in 0..number_of_ports {
        debug!(
            "port{i} : {}",
            registers::handle(|r| r
                .port_register_set
                .read_volatile_at(i)
                .portsc
                .current_connect_status())
        )
    }
//------------------------1

    debug!("initializing roothub");
    ROOT_HUB.get().unwrap().lock().initialize(); //这里就是设备枚举的地方
}
```
那么，设备枚举之前的代码没有什么可以细说的地方，大家自行查看即可，需要注意的是，各个数据结构的分配需要遵循[xhci规范](https://www.intel.com/content/dam/www/public/us/en/documents/technical-specifications/extensible-host-controler-interface-usb-xhci.pdf)的第六章-Table 6.1中所描述的关于内存对齐的要求，这部分我们还没做[细致的检查](../question/question_5_29.md)(参考当前所面临的问题的描述/猜想)，请同学们进行一一核对，以确定代码的正确性

## 达成成就-我们需要再深入点

接下来让我们直接看看[设备枚举的过程](../src/host/structures/xhci_roothub.rs)吧
```rust
// 定义静态变量ROOT_HUB，用于存储根集线器的实例--我们之后要把所有的此类单例模式改写，因为有些计算机系统中有多个xhci控制器，目前重构进度位于phytium_pi_dev分支，任务处于暂停状态，目前不用关心
pub(crate) static ROOT_HUB: OnceCell<Spinlock<Roothub>> = OnceCell::uninit();

pub struct Roothub {
    ports: usize,
    root_ports: PageBox<[Arc<MaybeUninit<Spinlock<RootPort>>>]>, //pagebox分配 无 cache的空间
}

impl Roothub {
    pub fn initialize(&mut self) {
        //todo delay?
        debug!("initializing root ports");
        self.root_ports
            .iter_mut()
            .map(|a| unsafe { a.clone().assume_init() })
            .for_each(|arc| {
                debug!("initializing port {}", arc.lock().root_port_id);
                arc.lock().initialize(); //在这里，我们对每个port进行初始化
            });

        // debug!("configuring root ports"); //configure-目前无需关心，这是个空方法
        // self.root_ports
        //     .iter_mut()
        //     .map(|a| unsafe { a.clone().assume_init() })
        //     .for_each(|arc| {
        //         arc.lock().configure();
        //     });
    }
}
```

于是，我们转而去查看[RootPort::initialize方法](../src/host/structures/root_port.rs)
```rust
//...
    pub fn initialize(&mut self) { //从这里开始，我们就要转而查看规范文档4.3章所描写的关于设备初始化的部分了
        if !self.connected() { //首先检查这个port上有没有插usb设备
            error!("port {} not connected", self.root_port_id);
            return;
        }
        debug!("port {} connected, continue", self.root_port_id);

        //由于uboot已经探测过设备，因此设备的device context可能已被更改，因此我们需要进行port复位-其实哪怕是在使用其他软件引导的情况下，我们也得这么做，因为你不知道系统启动前发生了什么
        reset_port(self.root_port_id);
        dump_port_status(self.root_port_id);

        let get_speed = self.get_speed(); //从port的寄存器上获取设备速度-这里的速度是硬件通过检查端点上的电压来确定的，是不可靠的。仅仅只是在初期启动时作过渡作用
        if get_speed == USBSpeed::USBSpeedUnknown {
            error!("unknown speed, index:{}", self.root_port_id);
        }
        debug!("port speed: {:?}", get_speed);

        debug!("initializing device: {:?}", get_speed);

        if let Ok(mut device) = XHCIUSBDevice::new(self.root_port_id as u8) { //在这一切之后，创建设备---但是真的应该在这里才开始创建嘛？我们是不是应该从一开始就分配好所有端口上设备的内存区域呢？
            debug!("writing ...");
            self.device_inited = true;
            unsafe { self.device.write(device) };
            debug!("writing complete");
        }

        unsafe { self.device.assume_init_mut().initialize() }; //开始设备的初始化
        debug!("initialize complete");
    }
//...
```

## 达成成就-结束了？
让我们看看[这个设备的initialize方法](../src/host/structures/xhci_usb_device.rs)是个怎么回事？
```rust
//... 从这里开始，就是正在施工的部分了
//我是指，我们正在折腾的部分，你已经跟上了项目最新的进度
    pub fn initialize(&mut self) {
        debug!("initialize/enum this device! port={}", self.port_id);

        // self.address_device(true);
        self.enable_slot(); //向设备申请slot
        self.slot_ctx_init();       ///配置设备的Input Context
        self.config_endpoint_0();   ///
        // self.check_input();
        self.assign_device();//配置设备的Output Context,并将其分配到dcbaa
        self.address_device(false); //address_device-问题就出现在这里，EventRing始终在返回ParamaterError,查阅规范得知，这说明控制器（或usb设备）收到了他不认识的TRB，当然也有可能是其他相关原因，让我们开始排查！接下来在讨论组里讨论吧！
        self.dump_ep0();
        dump_port_status(self.port_id as usize);
        // only available after address device
        // let get_descriptor = self.get_descriptor(); //damn, just assume speed is same lowest!
        // debug!("get desc: {:?}", get_descriptor);
        // dump_port_status(self.port_id as usize);
        // // self.check_endpoint();
        // // sleep(Duration::from_millis(2));

        // self.set_endpoint_speed(get_descriptor.max_packet_size()); //just let it be lowest speed!
        // self.evaluate_context_enable_ep0();
    }
//...
```


## **更新版：**

## 前情提要

在之前的代码结构导读中，我们介绍了位于分支"phytium_pi_port"上的代码。目前，随着 xhci 部分的结束，我们已经将代码重构并迁移到了"phytium_pi_dev"分支，最新的驱动架构能够应对更多复杂情况，但结构也发生了大的变化，因此，我们重新做一遍代码导读。

## 文件结构

```log
.
├── Cargo.lock
├── Cargo.toml
├── guide
│   ├── code_file_structure.log
│   ├── code_structure.md
│   └── quickstart_usb.md
└── src
    ├── addr.rs
    ├── ax
    │   └── mod.rs
    ├── device_types.rs
    ├── dma.rs
    ├── err.rs
    ├── host
    │   ├── device.rs
    │   ├── mod.rs
    │   └── xhci
    │       ├── context.rs
    │       ├── event.rs
    │       ├── mod.rs
    │       ├── registers.rs
    │       └── ring.rs
    └── lib.rs
6 directories, 18 files
```

## 入口

目前，我们暂时抛弃了原来的 cli 手动启动，而是将 usb 模块的引导做成了一个[app](../../../apps/usb/src/main.rs)：

```rust

#[derive(Clone)]
struct OsDepImp;

impl OsDep for OsDepImp { //我们优化了驱动的架构，将其重构为系统无关的库，因此我们需要引入对各个操作系统进行适配的抽象层，也就是说，我们将驱动需要操作系统做的事情抽象了出来，形成了这个trait："OsDep"
    type DMA = GlobalNoCacheAllocator;

    const PAGE_SIZE: usize = axalloc::PAGE_SIZE;
    fn dma_alloc(&self) -> Self::DMA { //就目前来说，我们仅仅只需要操作系统负责分配出No Cache的内存区域（DMA)即可。
        axalloc::global_no_cache_allocator()
    }
}

#[cfg_attr(feature = "axstd", no_mangle)]
fn main() {
    let phytium_cfg_id_0 = (0xffff_0000_31a0_8000, 48, 0);

    let config = USBHostConfig::new(
        phytium_cfg_id_0.0,
        phytium_cfg_id_0.1,
        phytium_cfg_id_0.2,
        OsDepImp {},
    );

    let usb = USBHost::new::<Xhci<_>>(config).unwrap();

    usb.poll();
}
```

让我们看看[USBHostConfig](../src/host/mod.rs)里有什么：

```rust
#[derive(Clone)]
pub struct USBHostConfig<O>
where O: OsDep
{
    pub(crate) base_addr: VirtAddr,
    pub(crate) irq_num: u32,      //中断系统相关：中断号。
    pub(crate) irq_priority: u32, //中断系统相关：中断优先级。注：目前中断系统尚未适配
    pub(crate) os: O //集成了操作系统相关操作的trait对象
}
```

接下来，是与我们曾经的代码逻辑相似的 USBHost(XHCI)初始化流程,也就是[USBHost::new](../src/host/xhci/mod.rs)方法,这部分所做事情与移植之前相差不大，请读者自行比对理解。

## 深入

让我们来看看最新的进展，在 USBHost 创建之后，就会被调用 poll 方法，这个方法的作用是进行设备的枚举：

```rust
    fn probe(&self) -> Result {
        let mut port_id_list = Vec::new();
        {
            let mut g = self.regs.lock();
            let regs = &mut g.regs;
            let port_len = regs.port_register_set.len();
            for i in 0..port_len {
                let portsc = &regs.port_register_set.read_volatile_at(i).portsc;
                info!(
                    "{TAG} Port {}: Enabled: {}, Connected: {}, Speed {}, Power {}",
                    i,
                    portsc.port_enabled_disabled(),
                    portsc.current_connect_status(),
                    portsc.port_speed(),
                    portsc.port_power()
                );

                if !portsc.port_enabled_disabled() {
                    continue;
                }

                port_id_list.push(i); //寻找所有连接上了设备的port
            }
        }
        for port_id in port_id_list {
            let slot = self.device_slot_assignment(port_id); //首先，是为设备分配slot
            self.address_device(slot, port_id);              //在这里，我们配置对应slot的上下文(context)，并请求xhci为设备设置地址
            self.set_ep0_packet_size(slot);                  //通过控制传输，获取准确的endpoint 0传输数据包大小
            self.setup_fetch_all_dev_desc(slot);             //在以上的配置完成后，获取设备的全部描述符。
        }

        self.dev_ctx
            .lock()
            .attached_set
            .iter_mut()
            .for_each(|dev| {}); //TODO: 为设备选择制定的配置，而后开始传输。目前我们先做一个HID设备（鼠标/键盘）
        Ok(())
    }
```

## 任务分解 1-设备描述符

设备描述符是设备所包含的描述信息，在这里，我们一次性获取所有的描述符信息，并在需要的时候获取对应条目的描述符

设备描述符有许多种类，不同的种类描述了不同的信息，比如 device 就可能会包含设备的厂家/设备的类型等信息，[参考](../src/host/usb/descriptors/mod.rs):

```rust
#[derive(FromPrimitive, ToPrimitive, Copy, Clone, Debug)]
#[allow(non_camel_case_types)]
pub(crate) enum Type {
    //USB 1.1: 9.4 Standard Device Requests, Table 9-5. Descriptor Types
    Device = 1,
    Configuration = 2,
    String = 3,
    Interface = 4,
    Endpoint = 5,
    // USB 2.0: 9.4 Standard Device Requests, Table 9-5. Descriptor Types
    DeviceQualifier = 6,
    OtherSpeedConfiguration = 7,
    InterfacePower1 = 8,
    Hid = 0x21,
    HIDReport = 0x22,
    HIDPhysical = 0x23,
    // USB 3.0+: 9.4 Standard Device Requests, Table 9-5. Descriptor Types
    OTG = 0x09,
    Debug = 0x0a,
    InterfaceAssociation = 0x0b,
    Bos = 0x0f,
    DeviceCapability = 0x10,
    SuperSpeedEndpointCompanion = 0x30,
    SuperSpeedPlusIsochEndpointCompanion = 0x31,
}
```

这些类型，每一个都对应了不同的 Descriptor，每个 Descriptor 又有不同的数据结构，好在我们目前暂时不用全部实现，只实现需要的部分即可。我们所需要关心的代码位于这里,

```rust
impl Descriptor {
    pub(crate) fn from_slice(raw: &[u8]) -> Result<Self, Error> {
        assert_eq!(raw.len(), raw[0].into());
        match FromPrimitive::from_u8(raw[1]) {
            Some(t) => {
                let raw: *const [u8] = raw;
                match t {
                    // SAFETY: This operation is safe because the length of `raw` is equivalent to the
                    // one of the descriptor.
                    //todo 任务1：我们所需要的就是在这里补充描述符的创建,在setup_fetch_all_dev_desc方法中，这个方法会被调用多次以反序列化设备传输过来的描述符
                    Type::Device => Ok(Self::Device(unsafe { ptr::read(raw.cast()) })),
                    Type::Configuration => {
                        Ok(Self::Configuration(unsafe { ptr::read(raw.cast()) }))
                    }
                    Type::String => Ok(Self::Str),
                    Type::Interface => Ok(Self::Interface(unsafe { ptr::read(raw.cast()) })),
                    Type::Endpoint => Ok(Self::Endpoint(unsafe { ptr::read(raw.cast()) })),
                    Type::Hid => Ok(Self::Hid),
                    other => unimplemented!("please implement descriptor type:{:?}", other),
                }
            }
            None => Err(Error::UnrecognizedType(raw[1])),
        }
    }
}
```

额外的参考资料:

- [USB 中文网-关于设备描述符的部分](https://www.usbzh.com/article/detail-104.html)
- USB3.2 spec 文档：在资料附件中

## 任务分解 2：设备配置选择

在获取到了描述符后，我们要从设备提供的几种配置中选择一种来设置端点（endpoint），参考：[redox 的代码](https://github.com/redox-os/drivers/blob/master/xhcid/src/xhci/scheme.rs#L595)

这部分在我们的代码中应当位于[根据设备描述符查找驱动](../src/host/xhci/xhci_device.rs)时

## 任务分解 3-HID 驱动编写-键盘

先写一个键盘驱动，参考 [redox 代码](https://github.com/redox-os/drivers/tree/master/usbhidd)
