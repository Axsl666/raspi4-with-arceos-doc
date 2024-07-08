# USB最新进展

可以读取到描述符：
```shell
arceos# test_xhci
[ 47.250961 0:2 driver_usb::host::xhci:49] resetting xhci controller
[ 47.255722 0:2 driver_usb::host::xhci:50] before reset:UsbStatusRegister { hc_halted: false, host_system_error: false, event_interrupt: false, port_change_detect: true, save_state_status: false, restore_state_status: false, save_restore_error: false, controller_not_ready: false, host_controller_error: false },pagesize: 1
[ 47.285321 0:2 driver_usb::host::xhci:136] stop
[ 47.291050 0:2 driver_usb::host::xhci:141] wait until halt
[ 47.297733 0:2 driver_usb::host::xhci:143] halted
[ 47.303635 0:2 driver_usb::host::xhci:145] HCRST!
[ 47.309539 0:2 driver_usb::host::xhci:154] get bios ownership
[ 47.316483 0:2 driver_usb::host::xhci:168] taked xhci ownershop
[ 47.323600 0:2 driver_usb::host::xhci:56] pagesize: 1
[ 47.329850 0:2 driver_usb::host::structures::xhci_roothub:86] number of ports:2
[ 47.338355 0:2 driver_usb::host::structures::xhci_roothub:91] allocating port 0
[ 47.346864 0:2 driver_usb::host::structures:100] ----dumped port state: PortStatusAndControlRegister { current_connect_status: false, port_enabled_disabled: false, over_current_active: false, port_reset: false, port_link_state: 5, port_power: true, port_speed: 0, port_indicator_control: Off, port_link_state_write_strobe: false, connect_status_change: false, port_enabled_disabled_change: false, warm_port_reset_change: false, over_current_change: false, port_reset_change: false, port_link_state_change: false, port_config_error_change: false, cold_attach_status: false, wake_on_connect_enable: false, wake_on_disconnect_enable: false, wake_on_over_current_enable: false, device_removable: false, warm_port_reset: false }
[ 47.411268 0:2 driver_usb::host::structures::xhci_roothub:98] assert:0 == 0
[ 47.419426 0:2 driver_usb::host::structures::xhci_roothub:91] allocating port 1
[ 47.427934 0:2 driver_usb::host::structures:100] ----dumped port state: PortStatusAndControlRegister { current_connect_status: true, port_enabled_disabled: true, over_current_active: false, port_reset: false, port_link_state: 0, port_power: true, port_speed: 4, port_indicator_control: Off, port_link_state_write_strobe: false, connect_status_change: false, port_enabled_disabled_change: false, warm_port_reset_change: false, over_current_change: false, port_reset_change: true, port_link_state_change: false, port_config_error_change: false, cold_attach_status: false, wake_on_connect_enable: false, wake_on_disconnect_enable: false, wake_on_over_current_enable: false, device_removable: false, warm_port_reset: false }
[ 47.492078 0:2 driver_usb::host::structures::xhci_roothub:98] assert:1 == 1
[ 47.500237 0:2 driver_usb::host::structures::xhci_roothub:102] ended
[ 47.507790 0:2 driver_usb::host::structures::xhci_roothub:112] initialized!
[ 47.515949 0:2 driver_usb::host::structures::xhci_slot_manager:63] max slot: 16
[ 47.524457 0:2 driver_usb::host::structures::xhci_slot_manager:87] addr of dcbaa: 90196040
[ 47.533917 0:2 driver_usb::host::structures::xhci_slot_manager:96] initialized!
[ 47.542425 0:2 driver_usb::host::structures::xhci_slot_manager:24] assign device: VA:0x90197000 to dcbaa 0
[ 47.553274 0:2 driver_usb::host::structures::scratchpad:79] initialized!
[ 47.561207 0:2 driver_usb::host::structures::xhci_command_manager:271] initialized!
[ 47.570024 0:2 driver_usb::host::structures::xhci_event_manager:43] initilizating!
[ 47.578825 0:2 driver_usb::host::structures::event_ring:33] created! event ring, check alignment of 4k: VA:0x9019a000
[ 47.590597 0:2 driver_usb::host::structures::xhci_event_manager:56] test
[ 47.598500 0:2 driver_usb::host::structures::xhci_event_manager:96] initialized!
[ 47.607088 0:2 driver_usb::host::xhci:70] before start:UsbStatusRegister { hc_halted: true, host_system_error: false, event_interrupt: false, port_change_detect: true, save_state_status: false, restore_state_status: false, save_restore_error: false, controller_not_ready: false, host_controller_error: false }
[ 47.635560 0:2 driver_usb::host::xhci:82] init completed!, coltroller state:UsbStatusRegister { hc_halted: false, host_system_error: false, event_interrupt: false, port_change_detect: true, save_state_status: false, restore_state_status: false, save_restore_error: false, controller_not_ready: false, host_controller_error: false }
[ 47.665941 0:2 driver_usb::host::xhci:91] port0 : false
[ 47.672363 0:2 driver_usb::host::xhci:91] port1 : true
[ 47.678698 0:2 driver_usb::host::xhci:101] initializing roothub
[ 47.685816 0:2 driver_usb::host::structures::xhci_roothub:40] initializing root ports
[ 47.694843 0:2 driver_usb::host::structures::xhci_roothub:45] initializing port 0
[ 47.703525 0:2 driver_usb::host::structures::root_port:26] port 0 not connected
[ 47.712029 0:2 driver_usb::host::structures::xhci_roothub:45] initializing port 1
[ 47.720711 0:2 driver_usb::host::structures::root_port:29] port 1 connected, continue
[ 47.729737 0:2 driver_usb::host::structures:112] reseting port 1
[ 47.736943 0:2 driver_usb::host::structures:114] before reset Port 1, status: PortStatusAndControlRegister { current_connect_status: true, port_enabled_disabled: true, over_current_active: false, port_reset: false, port_link_state: 0, port_power: true, port_speed: 4, port_indicator_control: Off, port_link_state_write_strobe: false, connect_status_change: false, port_enabled_disabled_change: false, warm_port_reset_change: false, over_current_change: false, port_reset_change: true, port_link_state_change: false, port_config_error_change: false, cold_attach_status: false, wake_on_connect_enable: false, wake_on_disconnect_enable: false, wake_on_over_current_enable: false, device_removable: false, warm_port_reset: false }
[ 47.801619 0:2 driver_usb::host::structures:140] Port 1 reset ok, status: PortStatusAndControlRegister { current_connect_status: true, port_enabled_disabled: true, over_current_active: false, port_reset: false, port_link_state: 0, port_power: true, port_speed: 4, port_indicator_control: Off, port_link_state_write_strobe: false, connect_status_change: false, port_enabled_disabled_change: false, warm_port_reset_change: false, over_current_change: false, port_reset_change: true, port_link_state_change: false, port_config_error_change: false, cold_attach_status: false, wake_on_connect_enable: false, wake_on_disconnect_enable: false, wake_on_over_current_enable: false, device_removable: false, warm_port_reset: false }
[ 47.865927 0:2 driver_usb::host::structures:100] ----dumped port state: PortStatusAndControlRegister { current_connect_status: true, port_enabled_disabled: true, over_current_active: false, port_reset: false, port_link_state: 0, port_power: true, port_speed: 4, port_indicator_control: Off, port_link_state_write_strobe: false, connect_status_change: false, port_enabled_disabled_change: false, warm_port_reset_change: false, over_current_change: false, port_reset_change: true, port_link_state_change: false, port_config_error_change: false, cold_attach_status: false, wake_on_connect_enable: false, wake_on_disconnect_enable: false, wake_on_over_current_enable: false, device_removable: false, warm_port_reset: false }
[ 47.930073 0:2 driver_usb::host::structures::root_port:39] port speed: USBSpeedSuper
[ 47.939011 0:2 driver_usb::host::structures::root_port:41] initializing device: USBSpeedSuper
[ 47.948733 0:2 driver_usb::host::structures::xhci_usb_device:63] new device! port:1
[ 47.957656 0:2 driver_usb::host::structures::root_port:44] writing ...
[ 47.965312 0:2 driver_usb::host::structures::root_port:47] writing complete
[ 47.973471 0:2 driver_usb::host::structures::xhci_usb_device:83] initialize/enum this device! port=1
[ 47.983801 0:2 driver_usb::host::structures::xhci_command_manager:147] do command EnableSlot(EnableSlot { slot_type: 0, cycle_bit: true }) !
[ 47.997601 0:2 driver_usb::host::structures::xhci_command_manager:151] enque trb, assert addr 16B aligned! 90198000
[ 48.009234 0:2 driver_usb::host::structures::xhci_command_manager:167] waiting for interrupt handler complete!
[ 48.020432 0:2 driver_usb::host::structures::xhci_event_manager:106] event handler has a trb:PortStatusChange(PortStatusChange { completion_code: Ok(Success), port_id: 2, cycle_bit: true })
[ 48.038484 0:2 driver_usb::host::structures::xhci_event_manager:135] step into port status change.

[ 48.048813 0:2 driver_usb::host::structures::xhci_roothub:65] port 1 changed!
[ 48.057147 0:2 driver_usb::host::structures:100] ----dumped port state: PortStatusAndControlRegister { current_connect_status: true, port_enabled_disabled: true, over_current_active: false, port_reset: false, port_link_state: 0, port_power: true, port_speed: 4, port_indicator_control: Off, port_link_state_write_strobe: false, connect_status_change: false, port_enabled_disabled_change: false, warm_port_reset_change: false, over_current_change: false, port_reset_change: true, port_link_state_change: false, port_config_error_change: false, cold_attach_status: false, wake_on_connect_enable: false, wake_on_disconnect_enable: false, wake_on_over_current_enable: false, device_removable: false, warm_port_reset: false }
[ 48.121293 0:2 driver_usb::host::structures::xhci_event_manager:106] event handler has a trb:PortStatusChange(PortStatusChange { completion_code: Ok(Success), port_id: 2, cycle_bit: true })
[ 48.139345 0:2 driver_usb::host::structures::xhci_event_manager:135] step into port status change.

[ 48.149675 0:2 driver_usb::host::structures::xhci_roothub:65] port 1 changed!
[ 48.158009 0:2 driver_usb::host::structures:100] ----dumped port state: PortStatusAndControlRegister { current_connect_status: true, port_enabled_disabled: true, over_current_active: false, port_reset: false, port_link_state: 0, port_power: true, port_speed: 4, port_indicator_control: Off, port_link_state_write_strobe: false, connect_status_change: false, port_enabled_disabled_change: false, warm_port_reset_change: false, over_current_change: false, port_reset_change: true, port_link_state_change: false, port_config_error_change: false, cold_attach_status: false, wake_on_connect_enable: false, wake_on_disconnect_enable: false, wake_on_over_current_enable: false, device_removable: false, warm_port_reset: false }
[ 48.222154 0:2 driver_usb::host::structures::xhci_event_manager:106] event handler has a trb:CommandCompletion(CommandCompletion { completion_code: Ok(Success), command_trb_pointer: 2417590272, command_completion_parameter: 0, vf_id: 0, slot_id: 1, cycle_bit: true })
[ 48.246978 0:2 driver_usb::host::structures::xhci_command_manager:230] handleing command complete:CommandCompletion { completion_code: Ok(Success), command_trb_pointer: 2417590272, command_completion_parameter: 0, vf_id: 0, slot_id: 1, cycle_bit: true }
[ 48.270589 0:2 driver_usb::host::structures::xhci_command_manager:182] t o t a l success!
[ 48.279962 0:2 driver_usb::host::structures::xhci_usb_device:145] enable slot success! CommandCompletion { completion_code: Ok(Success), command_trb_pointer: 2417590272, command_completion_parameter: 0, vf_id: 0, slot_id: 1, cycle_bit: true }
[ 48.302616 0:2 driver_usb::host::structures::xhci_usb_device:200] init input ctx
[ 48.311210 0:2 driver_usb::host::structures::xhci_usb_device:266] endpoint 0 state: Disabled, slot state: DisabledEnabled
[ 48.323362 0:2 driver_usb::host::structures::xhci_usb_device:208] root port id: 1
[ 48.332043 0:2 driver_usb::host::structures::xhci_usb_device:241] begin config endpoint 0 and assign dev!
[ 48.342807 0:2 driver_usb::host::structures::xhci_usb_device:244] config ep0
[ 48.351051 0:2 driver_usb::host::structures::xhci_usb_device:266] endpoint 0 state: Disabled, slot state: DisabledEnabled
[ 48.363203 0:2 driver_usb::host::structures::xhci_usb_device:252] address of transfer ring: 9019d000
[ 48.373533 0:2 driver_usb::host::structures::xhci_usb_device:275] assigning device into dcbaa, slot number= 1,output addr: VA:0x901a1000
[ 48.386986 0:2 driver_usb::host::structures::xhci_slot_manager:24] assign device: VA:0x901a1000 to dcbaa 1
[ 48.397837 0:2 driver_usb::host::structures::xhci_usb_device:289] addressing device
[ 48.406690 0:2 driver_usb::host::structures::xhci_usb_device:291] address to input VA:0x9019f000, check 64 alignment!
[ 48.418495 0:2 driver_usb::host::structures::xhci_command_manager:105] addressing device!
[ 48.427869 0:2 driver_usb::host::structures::xhci_command_manager:147] do command AddressDevice(AddressDevice { input_context_pointer: 2417618944, block_set_address_request: false, slot_id: 1, cycle_bit: true }) !
[ 48.448006 0:2 driver_usb::host::structures::xhci_command_manager:151] enque trb, assert addr 16B aligned! 90198010
[ 48.459638 0:2 driver_usb::host::structures::xhci_command_manager:167] waiting for interrupt handler complete!
[ 48.470836 0:2 driver_usb::host::structures::xhci_event_manager:106] event handler has a trb:CommandCompletion(CommandCompletion { completion_code: Ok(Success), command_trb_pointer: 2417590288, command_completion_parameter: 0, vf_id: 0, slot_id: 1, cycle_bit: true })
[ 48.495659 0:2 driver_usb::host::structures::xhci_command_manager:230] handleing command complete:CommandCompletion { completion_code: Ok(Success), command_trb_pointer: 2417590288, command_completion_parameter: 0, vf_id: 0, slot_id: 1, cycle_bit: true }
[ 48.519270 0:2 driver_usb::host::structures::xhci_command_manager:182] t o t a l success!
[ 48.528644 0:2 driver_usb::host::structures::xhci_usb_device:300] addressed device at slot id 1
[ 48.538539 0:2 driver_usb::host::structures::xhci_usb_device:301] command result CommandCompletion { completion_code: Ok(Success), command_trb_pointer: 2417590288, command_completion_parameter: 0, vf_id: 0, slot_id: 1, cycle_bit: true }
[ 48.560673 0:2 driver_usb::host::structures::xhci_usb_device:306] assert ep0 running!
[ 48.569700 0:2 driver_usb::host::structures::xhci_usb_device:266] endpoint 0 state: Disabled, slot state: DisabledEnabled

------------------------------------------------------------------------------------------------------------
[ 48.581852 0:2 driver_usb::host::structures::xhci_usb_device:368] get descriptor! //获取描述符
[ 48.590532 0:2 driver_usb::host::structures::xhci_usb_device:266] endpoint 0 state: Disabled, slot state: DisabledEnabled
[ 48.602685 0:2 driver_usb::host::structures::xhci_usb_device:376] doorbell id: 1
[ 48.611279 0:2 driver_usb::host::structures::transfer_ring:137] enque_index: 1
[ 48.619697 0:2 driver_usb::host::structures::transfer_ring:137] enque_index: 2
[ 48.628117 0:2 driver_usb::host::structures::transfer_ring:137] enque_index: 3
[ 48.636536 0:2 driver_usb::host::structures::xhci_usb_device:350] doorbell ing
[ 48.644957 0:2 driver_usb::host::structures::xhci_usb_device:357] waiting for event
[ 48.653810 0:2 driver_usb::host::structures::xhci_event_manager:106] event handler has a trb:TransferEvent(TransferEvent { completion_code: Ok(Success), trb_pointer: 2417610784, trb_transfer_length: 0, event_data: false, endpoint_id: 1, slot_id: 1, cycle_bit: true })
[ 48.678634 0:2 driver_usb::host::structures::xhci_event_manager:109] event = TransferEvent { completion_code: Ok(Success), trb_pointer: 2417610784, trb_transfer_length: 0, event_data: false, endpoint_id: 1, slot_id: 1, cycle_bit: true }
[ 48.700768 0:2 driver_usb::host::structures::xhci_event_manager:110] step into transfer event

[ 48.710663 0:2 driver_usb::host::structures::xhci_slot_manager:45] transfer event! param: Success,TransferEvent { completion_code: Ok(Success), trb_pointer: 2417610784, trb_transfer_length: 0, event_data: false, endpoint_id: 1, slot_id: 1, cycle_bit: true }
[ 48.734620 0:2 driver_usb::host::structures::xhci_slot_manager:48] transfer event succeed!
[ 48.744081 0:2 driver_usb::host::structures::xhci_usb_device:360] interrupt handler complete! result = Ok([2417610784, 0, 16777216, 16875521])
[ 48.758056 0:2 driver_usb::host::structures::xhci_usb_device:404] getted! buffer:Device { len: 18, descriptor_type: 1, cd_usb: 800, class: 0, subclass: 0, protocol: 0, max_packet_size0: 9, vendor: 0, product_id: 0, device: 0, manufacture: 0, product: 0, serial_number: 0, num_configurations: 0 }
[ 48.785311 0:2 driver_usb::host::structures::xhci_usb_device:406] return!
[ 48.793298 0:2 driver_usb::host::structures::xhci_usb_device:91] get max packet size: 512
[ 48.802671 0:2 driver_usb::host::structures::xhci_usb_device:418] eval ctx and enable ep0!
[ 48.812133 0:2 driver_usb::host::structures::xhci_command_manager:147] do command EvaluateContext(EvaluateContext { input_context_pointer: 2417618944, slot_id: 1, cycle_bit: true }) !
[ 48.829666 0:2 driver_usb::host::structures::xhci_command_manager:151] enque trb, assert addr 16B aligned! 90198020
[ 48.841298 0:2 driver_usb::host::structures::xhci_command_manager:167] waiting for interrupt handler complete!
[ 48.852496 0:2 driver_usb::host::structures::xhci_event_manager:106] event handler has a trb:CommandCompletion(CommandCompletion { completion_code: Ok(Success), command_trb_pointer: 2417590304, command_completion_parameter: 0, vf_id: 0, slot_id: 1, cycle_bit: true })
[ 48.877319 0:2 driver_usb::host::structures::xhci_command_manager:230] handleing command complete:CommandCompletion { completion_code: Ok(Success), command_trb_pointer: 2417590304, command_completion_parameter: 0, vf_id: 0, slot_id: 1, cycle_bit: true }
[ 48.900930 0:2 driver_usb::host::structures::xhci_command_manager:182] t o t a l success!
[ 48.910303 0:2 driver_usb::host::structures::xhci_usb_device:427] success! complete code: CommandCompletion { completion_code: Ok(Success), command_trb_pointer: 2417590304, command_completion_parameter: 0, vf_id: 0, slot_id: 1, cycle_bit: true }
[ 48.933238 0:2 driver_usb::host::structures::transfer_ring:137] enque_index: 4
[ 48.941639 0:2 driver_usb::host::structures::transfer_ring:137] enque_index: 5
[ 48.950058 0:2 driver_usb::host::structures::transfer_ring:137] enque_index: 6
[ 48.958477 0:2 driver_usb::host::structures::xhci_usb_device:350] doorbell ing
[ 48.966897 0:2 driver_usb::host::structures::xhci_usb_device:357] waiting for event
[ 48.975752 0:2 driver_usb::host::structures::xhci_event_manager:106] event handler has a trb:TransferEvent(TransferEvent { completion_code: Ok(Success), trb_pointer: 2417610832, trb_transfer_length: 0, event_data: false, endpoint_id: 1, slot_id: 1, cycle_bit: true })
[ 49.000575 0:2 driver_usb::host::structures::xhci_event_manager:109] event = TransferEvent { completion_code: Ok(Success), trb_pointer: 2417610832, trb_transfer_length: 0, event_data: false, endpoint_id: 1, slot_id: 1, cycle_bit: true }
[ 49.022709 0:2 driver_usb::host::structures::xhci_event_manager:110] step into transfer event

[ 49.032604 0:2 driver_usb::host::structures::xhci_slot_manager:45] transfer event! param: Success,TransferEvent { completion_code: Ok(Success), trb_pointer: 2417610832, trb_transfer_length: 0, event_data: false, endpoint_id: 1, slot_id: 1, cycle_bit: true }
[ 49.056561 0:2 driver_usb::host::structures::xhci_slot_manager:48] transfer event succeed!
[ 49.066022 0:2 driver_usb::host::structures::xhci_usb_device:360] interrupt handler complete! result = Ok([2417610832, 0, 16777216, 16875521])
[ 49.079997 0:2 driver_usb::host::structures::xhci_usb_device:159] fetched!

------------------------------------------------------------------------------------------------------------
[ 49.088074 0:2 driver_usb::host::structures::xhci_usb_device:161] dev descriptors: [Device(Device { len: 18, descriptor_type: 1, cd_usb: 800, class: 0, subclass: 0, protocol: 0, max_packet_size0: 9, vendor: 2385, product_id: 5734, device: 1, manufacture: 1, product: 2, serial_number: 3, num_configurations: 1 })] //设备描述符
[ 49.116887 0:2 driver_usb::host::structures::root_port:51] initialize complete
[ 49.125325 0:2 driver_usb::host::structures::transfer_ring:137] enque_index: 7
[ 49.133727 0:2 driver_usb::host::structures::transfer_ring:137] enque_index: 8
[ 49.142147 0:2 driver_usb::host::structures::transfer_ring:137] enque_index: 9
[ 49.150566 0:2 driver_usb::host::structures::xhci_usb_device:350] doorbell ing
[ 49.158986 0:2 driver_usb::host::structures::xhci_usb_device:357] waiting for event
[ 49.167840 0:2 driver_usb::host::structures::xhci_event_manager:106] event handler has a trb:TransferEvent(TransferEvent { completion_code: Ok(Success), trb_pointer: 2417610880, trb_transfer_length: 0, event_data: false, endpoint_id: 1, slot_id: 1, cycle_bit: true })
[ 49.192663 0:2 driver_usb::host::structures::xhci_event_manager:109] event = TransferEvent { completion_code: Ok(Success), trb_pointer: 2417610880, trb_transfer_length: 0, event_data: false, endpoint_id: 1, slot_id: 1, cycle_bit: true }
[ 49.214797 0:2 driver_usb::host::structures::xhci_event_manager:110] step into transfer event

[ 49.224693 0:2 driver_usb::host::structures::xhci_slot_manager:45] transfer event! param: Success,TransferEvent { completion_code: Ok(Success), trb_pointer: 2417610880, trb_transfer_length: 0, event_data: false, endpoint_id: 1, slot_id: 1, cycle_bit: true }
[ 49.248649 0:2 driver_usb::host::structures::xhci_slot_manager:48] transfer event succeed!
[ 49.258111 0:2 driver_usb::host::structures::xhci_usb_device:360] interrupt handler complete! result = Ok([2417610880, 0, 16777216, 16875521])
[ 49.272086 0:2 driver_usb::host::structures::xhci_usb_device:172] fetched!
[ 49.280164 0:2 driver_usb::host::structures::descriptor:188] Unrecognized USB descriptor: UnrecognizedType(48)
[ 49.291358 0:2 driver_usb::host::structures::descriptor:188] Unrecognized USB descriptor: UnrecognizedType(48)

------------------------------------------------------------------------------------------------------------
[ 49.302554 0:2 driver_usb::host::structures::xhci_usb_device:174] config descriptors: [Configuration(Configuration { length: 9, ty: 2, total_length: 44, num_interfaces: 1, config_val: 1, config_string: 0, attributes: 128, max_power: 37 }), Interface(Interface { len: 9, descriptor_type: 4, interface_number: 0, alternate_setting: 0, num_endpoints: 2, interface_class: 8, interface_subclass: 6, interface_protocol: 80, interface: 0 }), Endpoint(Endpoint { len: 7, descriptor_type: 5, endpoint_address: 129, attributes: 2, max_packet_size: 1024, interval: 0 }), Endpoint(Endpoint { len: 7, descriptor_type: 5, endpoint_address: 2, attributes: 2, max_packet_size: 1024, interval: 0 })] //配置描述符、接口描述符、端点描述符
[ 49.363478 0:2 driver_usb::host::structures::xhci_command_manager:147] do command ConfigureEndpoint(ConfigureEndpoint { input_context_pointer: 2417618944, deconfigure: false, slot_id: 1, cycle_bit: true }) !
[ 49.383016 0:2 driver_usb::host::structures::xhci_command_manager:151] enque trb, assert addr 16B aligned! 90198030
[ 49.394648 0:2 driver_usb::host::structures::xhci_command_manager:167] waiting for interrupt handler complete!
[ 49.405845 0:2 driver_usb::host::structures::xhci_event_manager:106] event handler has a trb:CommandCompletion(CommandCompletion { completion_code: Ok(Success), command_trb_pointer: 2417590320, command_completion_parameter: 0, vf_id: 0, slot_id: 1, cycle_bit: true })
[ 49.430669 0:2 driver_usb::host::structures::xhci_command_manager:230] handleing command complete:CommandCompletion { completion_code: Ok(Success), command_trb_pointer: 2417590320, command_completion_parameter: 0, vf_id: 0, slot_id: 1, cycle_bit: true }
[ 49.454280 0:2 driver_usb::host::structures::xhci_command_manager:182] t o t a l success!
[ 49.463654 0:2 driver_usb::host::structures::xhci_usb_device:114] configure endpoint complete
[ 49.473375 0:2 driver_usb::host::structures::root_port:54] configure complete
arceos# 
```



### 设备描述符（Device Descriptor）已经成功获取，字段的解释如下：

1. **len: 18**
   - 描述符的长度为18字节
2. **descriptor_type: 1**
   - 描述符类型为1，表示这是设备描述符
3. **cd_usb: 800**
   - USB协议版本，0x800表示USB 2.0版本
4. **class: 0**
   - 设备类代码，0表示设备由其接口描述符指定设备类
5. **subclass: 0**
   - 设备子类代码，0表示无特定子类
6. **protocol: 0**
   - 设备协议代码，0表示无特定协议
7. **max_packet_size0: 9**
   - 端点0的最大包大小为9字节
8. **vendor: 2385**
   - 供应商ID，2385
9. **product_id: 5734**
   - 产品ID，5734
10. **device: 1**
    - 设备版本号
11. **manufacture: 1**
    - 制造商字符串描述符的索引
12. **product: 2**
    - 产品字符串描述符的索引
13. **serial_number: 3**
    - 序列号字符串描述符的索引
14. **num_configurations: 1**
    - 设备支持的配置数，表示该设备有1个配置

### 配置描述符 (Configuration Descriptor)

1. **length: 9**
   * 描述符长度为9字节

2. **ty: 2**
   * 描述符类型为2，表示这是一个配置描述符

3. **total_length: 44**
   * 该配置所包含的所有描述符的总长度为44字节

4. **num_interfaces: 1**
   * 该配置包含1个接口

5. **config_val: 1**
   * 该配置的值为1，用于设置该配置

6. **config_string: 0**
   * 配置字符串描述符的索引，值为0表示没有字符串描述符

7. **attributes: 128**
   * 配置的属性，128表示总线供电

8. **max_power: 37**
   * 设备所需的最大功率

### 接口描述符 (Interface Descriptor)：

1. **len: 9**
   * 描述符长度为9字节

2. **descriptor_type: 4**
   * 描述符类型为4，表示这是一个接口描述符

3. **interface_number: 0**
   * 接口编号为0

4. **alternate_setting: 0**
   * 备用设置编号为0

5. **num_endpoints: 2**
   * 该接口有2个端点（不包括端点0）

6. **interface_class: 8**
   * 接口类代码为8，表示该接口属于大容量存储类

7. **interface_subclass: 6**
   * 接口子类代码为6，表示SCSI传输命令集

8. **interface_protocol: 80**
   * 接口协议代码为80，表示Bulk-Only传输

9. **interface: 0**
   * 接口字符串描述符的索引，值为0表示没有字符串描述符

### 端点描述符 (Endpoint Descriptor)：

1. **第一个端点描述符**
   - len: 7
     - 描述符长度为7字节
   - descriptor_type: 5
     - 描述符类型为5，表示这是一个端点描述符
   - endpoint_address: 129
     - 端点地址为129（0x81），表示这是一个IN方向的端点，端点号为1
   - attributes: 2
     - 端点属性为2，表示这是一个批量传输端点
   - max_packet_size: 1024
     - 端点的最大包大小为1024字节
   - interval: 0
     - 轮询间隔为0，表示不适用于批量传输端点
2. **第二个端点描述符**
   - len: 7
     - 描述符长度为7字节
   - descriptor_type: 5
     - 描述符类型为5，表示这是一个端点描述符
   - endpoint_address: 2
     - 端点地址为2，表示这是一个OUT方向的端点，端点号为2
   - attributes: 
     - 端点属性为2，表示这是一个批量传输端点
   - max_packet_size: 1024
     - 端点的最大包大小为1024字节
   - interval: 0
     - 轮询间隔为0，表示不适用于批量传输端点
    


根据描述符配置端点，进行通信：
```shell
ccc[ 53.770504 0 axruntime:138] Logging is enabled.
[ 53.776233 0 axruntime:139] Primary CPU 512 started, dtb = 0x1.
[ 53.783350 0 axruntime:141] Found physcial memory regions:
c[ 53.790122 0 axruntime:144]   [PA:0x90100000, PA:0x90126000) .text (READ | EXECUTE | RESERVED)
[ 53.799929 0 axruntime:144]   [PA:0x90126000, PA:0x9012d000) .rodata (READ | RESERVED)
[ 53.809043 0 axruntime:144]   [PA:0x9012d000, PA:0x90131000) .data .tdata .tbss .percpu (READ | WRITE | RESERVED)
[ 53.820500 0 axruntime:144]   [PA:0x90131000, PA:0x90171000) boot stack (READ | WRITE | RESERVED)
[ 53.830569 0 axruntime:144]   [PA:0x90171000, PA:0x90197000) .bss (READ | WRITE | RESERVED)
[ 53.840117 0 axruntime:144]   [PA:0x0, PA:0x1000) spintable (READ | WRITE | RESERVED)
[ 53.849144 0 axruntime:144]   [PA:0x90197000, PA:0x90897000) nocache memory (READ | WRITE | DEVICE)
[ 53.859387 0 axruntime:144]   [PA:0x90897000, PA:0xff900000) free memory (READ | WRITE | FREE)
[ 53.869195 0 axruntime:144]   [PA:0x2800c000, PA:0x2800d000) mmio (READ | WRITE | DEVICE | RESERVED)
[ 53.879524 0 axruntime:144]   [PA:0x2800d000, PA:0x2800e000) mmio (READ | WRITE | DEVICE | RESERVED)
[ 53.889854 0 axruntime:144]   [PA:0x2800e000, PA:0x2800f000) mmio (READ | WRITE | DEVICE | RESERVED)
[ 53.900183 0 axruntime:144]   [PA:0x2800f000, PA:0x28010000) mmio (READ | WRITE | DEVICE | RESERVED)
[ 53.910512 0 axruntime:144]   [PA:0x30000000, PA:0x38000000) mmio (READ | WRITE | DEVICE | RESERVED)
[ 53.920841 0 axruntime:144]   [PA:0x40000000, PA:0x80000000) mmio (READ | WRITE | DEVICE | RESERVED)
[ 53.931170 0 axruntime:144]   [PA:0x1000000000, PA:0x3000000000) mmio (READ | WRITE | DEVICE | RESERVED)
[ 53.941847 0 axruntime:223] Initialize global memory allocator...
[ 53.949138 0 axruntime:224]   use TLSF allocator.
[ 53.955042 0 axalloc:284] initialize global allocator at: free-[0xffff000090897000, 0xffff0000ff900000)
[ 53.965952 0 axruntime:158] Initialize kernel page table...
[ 53.972494 0 axruntime:258] Initialize global no cache memory allocator...
[ 53.980474 0 axalloc:300] initialize global allocator at: nocache-[0x90197000,0x90897000)
[ 53.989850 0 axruntime:165] Initialize platform devices...
[ 53.996531 0 axhal::platform::aarch64_common::gic:51] Initialize GICv2...
[ 54.004518 0 axtask::api:66] Initialize scheduling...
[ 54.010771 0 axtask::task:146] new task: Task(1, "idle")
[ 54.017280 0 axtask::task:146] new task: Task(3, "gc")
[ 54.023617 0 axalloc:126] expand heap memory: [0xffff0000908a9000, 0xffff0000908e9000)
[ 54.032734 0 axalloc:126] expand heap memory: [0xffff0000908e9000, 0xffff000090969000)
[ 54.041844 0 axtask::api:72]   use Round-robin scheduler.
[ 54.048437 0 axdriver:158] Initialize device drivers...
[ 54.054861 0 axdriver:159]   device model: static
[ 54.060763 0 driver_pci::phytium:18] PCIe link start @0xFFFF000040000000...
[ 54.068922 0 driver_pci::phytium:19] theroticly, since uboot had already initialized it, we need't to operate it any more!
[ 54.081161 0 axdriver::bus::pci:14] probing in pci.rs!
[ 54.087498 0 driver_pci::root_complex:96] into next!
[ 54.093661 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 54.100604 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 54.107548 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 54.114492 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 54.121436 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 54.128380 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 54.135324 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 54.142268 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 54.149212 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 54.156156 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 54.163100 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 54.170044 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 54.176988 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 54.183932 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 54.190876 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 54.197820 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 54.204764 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 54.211708 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 54.218652 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 54.225596 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 54.232540 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 54.239484 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 54.246428 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 54.253372 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 54.260316 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 54.267260 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 54.274204 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 54.281148 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 54.288092 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 54.295036 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 54.301980 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 54.308924 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 54.315868 0 driver_pci::root_complex:116] none!
[ 54.321684 0 axdriver:190] number of usb host controller: 0
[ 54.328454 0 axruntime:191] Initialize interrupt handlers...
[ 54.335312 0 axruntime:201] Primary CPU 512 init OK.
[ 54.341475 0:2 driver_usb::host::xhci:79] [XHCI] Base addr: VA:0xffff000031a08000
[ 54.350157 0:2 driver_usb::host::xhci:90] [XHCI] Max_slots: 16, max_ports: 2, max_irqs: 1, page size: 1
[ 54.361463 0:2 driver_usb::dma:125] allocated data:0x901b8880
[ 54.367723 0:2 driver_usb::dma:125] allocated data:0x901b9900
[ 54.374667 0:2 driver_usb::host::xhci:141] [XHCI] Reset begin
[ 54.381576 0:2 driver_usb::host::xhci:142] [XHCI] Stop
[ 54.387913 0:2 driver_usb::host::xhci:150] [XHCI] Until halt
[ 54.394770 0:2 driver_usb::host::xhci:152] [XHCI] Halted
[ 54.401279 0:2 driver_usb::host::xhci:157] [XHCI] Wait for ready...
[ 54.408744 0:2 driver_usb::host::xhci:159] [XHCI] Ready
[ 54.415169 0:2 driver_usb::host::xhci:167] [XHCI] Reset HC
[ 54.421852 0:2 driver_usb::host::xhci:181] [XHCI] XCHI reset ok
[ 54.428969 0:2 driver_usb::host::xhci:187] [XHCI] Setting enabled slots to 16.
[ 54.437389 0:2 driver_usb::host::xhci:197] [XHCI] Writing DCBAAP: 90198000
[ 54.445461 0:2 driver_usb::host::xhci:208] [XHCI] Writing CRCR: 901B8880
[ 54.453360 0:2 driver_usb::host::xhci:252] [XHCI] Disable interrupts
[ 54.460912 0:2 driver_usb::host::xhci:262] [XHCI] Writing ERSTZ
[ 54.468029 0:2 driver_usb::host::xhci:266] [XHCI] Writing ERDP: 901B9900
[ 54.475928 0:2 driver_usb::host::xhci:273] [XHCI] Writing ERSTBA: 901B98C0
[ 54.484001 0:2 driver_usb::host::xhci:284] [XHCI] Enabling primary interrupter.
[ 54.492507 0:2 driver_usb::host::xhci:500] [XHCI] Scratch buf count: 0
[ 54.500232 0:2 driver_usb::host::xhci:234] [XHCI] Start run
[ 54.507003 0:2 driver_usb::host::xhci:241] [XHCI] Is running
[ 54.513859 0:2 driver_usb::host::xhci:483] [XHCI] Test command ring
[ 54.521325 0:2 driver_usb::host::xhci::ring:46] enqueue trb into 0
[ 54.528702 0:2 driver_usb::host::xhci::ring:59] next index
[ 54.535385 0:2 driver_usb::host::xhci::ring:49] enqueued,next index: 0
[ 54.543110 0:2 driver_usb::host::xhci:308] [XHCI] Post cmd Noop(Noop { cycle_bit: true }) @FFFF0000901704C4
[ 54.554048 0:2 driver_usb::host::xhci:320] [XHCI] Wait result
[ 54.560991 0:2 driver_usb::host::xhci::ring:59] next index
[ 54.567677 0:2 driver_usb::host::xhci:337] event: PortStatusChange(PortStatusChange { completion_code: Ok(Success), port_id: 1, cycle_bit: true })
[ 54.581997 0:2 driver_usb::host::xhci::ring:59] next index
[ 54.588681 0:2 driver_usb::host::xhci:329] [XHCI] Cmd @901B8880 got result, cycle true
[ 54.597795 0:2 driver_usb::host::xhci::ring:46] enqueue trb into 1
[ 54.605172 0:2 driver_usb::host::xhci::ring:59] next index
[ 54.611856 0:2 driver_usb::host::xhci::ring:49] enqueued,next index: 1
[ 54.619581 0:2 driver_usb::host::xhci:308] [XHCI] Post cmd Noop(Noop { cycle_bit: true }) @FFFF0000901704C4
[ 54.630519 0:2 driver_usb::host::xhci:320] [XHCI] Wait result
[ 54.637462 0:2 driver_usb::host::xhci::ring:59] next index
[ 54.644146 0:2 driver_usb::host::xhci:329] [XHCI] Cmd @901B8890 got result, cycle true
[ 54.653260 0:2 driver_usb::host::xhci::ring:46] enqueue trb into 2
[ 54.660638 0:2 driver_usb::host::xhci::ring:59] next index
[ 54.667321 0:2 driver_usb::host::xhci::ring:49] enqueued,next index: 2
[ 54.675046 0:2 driver_usb::host::xhci:308] [XHCI] Post cmd Noop(Noop { cycle_bit: true }) @FFFF0000901704C4
[ 54.685984 0:2 driver_usb::host::xhci:320] [XHCI] Wait result
[ 54.692927 0:2 driver_usb::host::xhci::ring:59] next index
[ 54.699611 0:2 driver_usb::host::xhci:329] [XHCI] Cmd @901B88A0 got result, cycle true
[ 54.708725 0:2 driver_usb::host::xhci:487] [XHCI] Command ring ok
[ 54.716016 0:2 driver_usb::host::xhci:543] [XHCI] Port 0 start reset
[ 54.781410 0:2 driver_usb::host::xhci:556] [XHCI] Port 0 reset ok
[ 54.785829 0:2 driver_usb::host::xhci:543] [XHCI] Port 1 start reset
[ 54.793387 0:2 driver_usb::host::xhci:556] [XHCI] Port 1 reset ok
[ 54.800672 0:2 driver_usb::host::xhci:115] [XHCI] Init success
[ 54.807706 0:2 driver_usb::host::xhci:568] [XHCI] Port 0: Enabled: true, Connected: true, Speed 1, Power true
[ 54.818816 0:2 driver_usb::host::xhci:568] [XHCI] Port 1: Enabled: false, Connected: false, Speed 0, Power true
[ 54.830098 0:2 driver_usb::host::xhci:880] [XHCI] CMD: enable slot
[ 54.837475 0:2 driver_usb::host::xhci::ring:46] enqueue trb into 3
[ 54.844853 0:2 driver_usb::host::xhci::ring:59] next index
[ 54.851537 0:2 driver_usb::host::xhci::ring:49] enqueued,next index: 3
[ 54.859262 0:2 driver_usb::host::xhci:308] [XHCI] Post cmd EnableSlot(EnableSlot { slot_type: 0, cycle_bit: true }) @FFFF00009017039C
[ 54.872456 0:2 driver_usb::host::xhci:320] [XHCI] Wait result
[ 54.879400 0:2 driver_usb::host::xhci::ring:59] next index
[ 54.886084 0:2 driver_usb::host::xhci:337] event: PortStatusChange(PortStatusChange { completion_code: Ok(Success), port_id: 1, cycle_bit: true })
[ 54.900405 0:2 driver_usb::host::xhci::ring:59] next index
[ 54.907090 0:2 driver_usb::host::xhci:329] [XHCI] Cmd @901B88B0 got result, cycle true
[ 54.916203 0:2 driver_usb::host::xhci:885] [XHCI] Result: CommandCompletion { completion_code: Ok(Success), command_trb_pointer: 2417723568, command_completion_parameter: 0, vf_id: 0, slot_id: 1, cycle_bit: true }, slot id: 1
[ 54.937382 0:2 driver_usb::host::xhci:888] new slot!
[ 54.943546 0:2 driver_usb::dma:125] allocated data:0x901ba940
[ 54.950491 0:2 driver_usb::dma:125] allocated data:0x901baa80
[ 54.957435 0:2 driver_usb::dma:125] allocated data:0x901babc0
[ 54.964379 0:2 driver_usb::dma:125] allocated data:0x901bad00
[ 54.971323 0:2 driver_usb::dma:125] allocated data:0x901bae40
[ 54.978267 0:2 driver_usb::dma:125] allocated data:0x901baf80
[ 54.985211 0:2 driver_usb::dma:125] allocated data:0x901bb0c0
[ 54.992156 0:2 driver_usb::dma:125] allocated data:0x901bb200
[ 54.999099 0:2 driver_usb::dma:125] allocated data:0x901bb340
[ 55.006043 0:2 driver_usb::dma:125] allocated data:0x901bb480
[ 55.012987 0:2 driver_usb::dma:125] allocated data:0x901bb5c0
[ 55.019931 0:2 driver_usb::dma:125] allocated data:0x901bb700
[ 55.026875 0:2 driver_usb::dma:125] allocated data:0x901bb840
[ 55.033819 0:2 driver_usb::dma:125] allocated data:0x901bb980
[ 55.040763 0:2 driver_usb::dma:125] allocated data:0x901bbac0
[ 55.047708 0:2 driver_usb::dma:125] allocated data:0x901bbc00
[ 55.054651 0:2 driver_usb::host::xhci::context:76] new rings!
[ 55.061593 0:2 driver_usb::host::xhci::context:87] new desc container
[ 55.069233 0:2 driver_usb::host::xhci::context:93] insert complete!
[ 55.076697 0:2 driver_usb::host::xhci:586] assign complete!
[ 55.083474 0:2 driver_usb::host::xhci:844] [XHCI] CMD: address device
[ 55.091105 0:2 driver_usb::host::xhci::ring:46] enqueue trb into 4
[ 55.098483 0:2 driver_usb::host::xhci::ring:59] next index
[ 55.105167 0:2 driver_usb::host::xhci::ring:49] enqueued,next index: 4
[ 55.112892 0:2 driver_usb::host::xhci:308] [XHCI] Post cmd AddressDevice(AddressDevice { input_context_pointer: 2417606656, block_set_address_request: false, slot_id: 1, cycle_bit: true }) @FFFF00009017032C
[ 55.132422 0:2 driver_usb::host::xhci:320] [XHCI] Wait result
[ 55.139366 0:2 driver_usb::host::xhci::ring:59] next index
[ 55.146050 0:2 driver_usb::host::xhci:329] [XHCI] Cmd @901B88C0 got result, cycle true
[ 55.155164 0:2 driver_usb::host::xhci:853] [XHCI] Result: CommandCompletion { completion_code: Ok(Success), command_trb_pointer: 2417723584, command_completion_parameter: 0, vf_id: 0, slot_id: 1, cycle_bit: true }
[ 55.175301 0:2 driver_usb::host::xhci:588] address complete!
[ 55.182160 0:2 driver_usb::host::xhci:746] [XHCI] CMD: get endpoint0 packet size
[ 55.190753 0:2 driver_usb::host::xhci::ring:46] enqueue trb into 0
[ 55.198129 0:2 driver_usb::host::xhci::ring:59] next index
[ 55.204813 0:2 driver_usb::host::xhci::ring:49] enqueued,next index: 0
[ 55.212538 0:2 driver_usb::host::xhci::ring:46] enqueue trb into 1
[ 55.219916 0:2 driver_usb::host::xhci::ring:59] next index
[ 55.226600 0:2 driver_usb::host::xhci::ring:49] enqueued,next index: 1
[ 55.234325 0:2 driver_usb::host::xhci::ring:46] enqueue trb into 2
[ 55.241703 0:2 driver_usb::host::xhci::ring:59] next index
[ 55.248386 0:2 driver_usb::host::xhci::ring:49] enqueued,next index: 2
[ 55.256112 0:2 driver_usb::host::xhci:442] [XHCI] Post control transfer!
[ 55.264011 0:2 driver_usb::host::xhci:456] [XHCI] Wait result
[ 55.270956 0:2 driver_usb::host::xhci:462] received temp!:TransferEvent(TransferEvent { completion_code: Ok(Success), trb_pointer: 2417731936, trb_transfer_length: 0, event_data: false, endpoint_id: 1, slot_id: 1, cycle_bit: true })
[ 55.292741 0:2 driver_usb::host::xhci::ring:59] next index
[ 55.299426 0:2 driver_usb::host::xhci:467] [XHCI] Transfer @901BA960 got result, cycle true
[ 55.308974 0:2 driver_usb::host::xhci:753] [XHCI] Result: TransferEvent { completion_code: Ok(Success), trb_pointer: 2417731936, trb_transfer_length: 0, event_data: false, endpoint_id: 1, slot_id: 1, cycle_bit: true }
[ 55.329458 0:2 driver_usb::host::xhci:767] [XHCI] CMD: evaluating context for set endpoint0 packet size
[ 55.340047 0:2 driver_usb::host::xhci::ring:46] enqueue trb into 5
[ 55.347425 0:2 driver_usb::host::xhci::ring:59] next index
[ 55.354109 0:2 driver_usb::host::xhci::ring:49] enqueued,next index: 5
[ 55.361834 0:2 driver_usb::host::xhci:308] [XHCI] Post cmd EvaluateContext(EvaluateContext { input_context_pointer: 2417606656, slot_id: 1, cycle_bit: true }) @FFFF00009017032C
[ 55.378761 0:2 driver_usb::host::xhci:320] [XHCI] Wait result
[ 55.385704 0:2 driver_usb::host::xhci::ring:59] next index
[ 55.392388 0:2 driver_usb::host::xhci:329] [XHCI] Cmd @901B88D0 got result, cycle true
[ 55.401502 0:2 driver_usb::host::xhci:773] [XHCI] Result: CommandCompletion { completion_code: Ok(Success), command_trb_pointer: 2417723600, command_completion_parameter: 0, vf_id: 0, slot_id: 1, cycle_bit: true }
[ 55.421641 0:2 driver_usb::host::xhci:590] packet size complete!
[ 55.428846 0:2 driver_usb::dma:125] allocated data:0x901bd000
[ 55.436063 0:2 driver_usb::host::xhci:716] [XHCI] Transfer Control: Fetching all configs
[ 55.445077 0:2 driver_usb::host::xhci::ring:46] enqueue trb into 3
[ 55.452453 0:2 driver_usb::host::xhci::ring:59] next index
[ 55.459137 0:2 driver_usb::host::xhci::ring:49] enqueued,next index: 3
[ 55.466862 0:2 driver_usb::host::xhci::ring:46] enqueue trb into 4
[ 55.474240 0:2 driver_usb::host::xhci::ring:59] next index
[ 55.480924 0:2 driver_usb::host::xhci::ring:49] enqueued,next index: 4
[ 55.488649 0:2 driver_usb::host::xhci::ring:46] enqueue trb into 5
[ 55.496027 0:2 driver_usb::host::xhci::ring:59] next index
[ 55.502710 0:2 driver_usb::host::xhci::ring:49] enqueued,next index: 5
[ 55.510436 0:2 driver_usb::host::xhci:442] [XHCI] Post control transfer!
[ 55.518335 0:2 driver_usb::host::xhci:456] [XHCI] Wait result
[ 55.525279 0:2 driver_usb::host::xhci:462] received temp!:TransferEvent(TransferEvent { completion_code: Ok(Success), trb_pointer: 2417731984, trb_transfer_length: 0, event_data: false, endpoint_id: 1, slot_id: 1, cycle_bit: true })
[ 55.547065 0:2 driver_usb::host::xhci::ring:59] next index
[ 55.553750 0:2 driver_usb::host::xhci:467] [XHCI] Transfer @901BA990 got result, cycle true
[ 55.563297 0:2 driver_usb::host::xhci:725] [XHCI] Result: TransferEvent { completion_code: Ok(Success), trb_pointer: 2417731984, trb_transfer_length: 0, event_data: false, endpoint_id: 1, slot_id: 1, cycle_bit: true }
[ 55.583787 0:2 driver_usb::dma:125] allocated data:0x901bd000
[ 55.591001 0:2 driver_usb::host::xhci:688] [XHCI] Transfer Control: Fetching all configs
[ 55.600014 0:2 driver_usb::host::xhci::ring:46] enqueue trb into 6
[ 55.607391 0:2 driver_usb::host::xhci::ring:59] next index
[ 55.614075 0:2 driver_usb::host::xhci::ring:49] enqueued,next index: 6
[ 55.621800 0:2 driver_usb::host::xhci::ring:46] enqueue trb into 7
[ 55.629178 0:2 driver_usb::host::xhci::ring:59] next index
[ 55.635862 0:2 driver_usb::host::xhci::ring:49] enqueued,next index: 7
[ 55.643587 0:2 driver_usb::host::xhci::ring:46] enqueue trb into 8
[ 55.650965 0:2 driver_usb::host::xhci::ring:59] next index
[ 55.657648 0:2 driver_usb::host::xhci::ring:49] enqueued,next index: 8
[ 55.665374 0:2 driver_usb::host::xhci:442] [XHCI] Post control transfer!
[ 55.673273 0:2 driver_usb::host::xhci:456] [XHCI] Wait result
[ 55.680217 0:2 driver_usb::host::xhci:462] received temp!:TransferEvent(TransferEvent { completion_code: Ok(Success), trb_pointer: 2417732032, trb_transfer_length: 0, event_data: false, endpoint_id: 1, slot_id: 1, cycle_bit: true })
[ 55.702003 0:2 driver_usb::host::xhci::ring:59] next index
[ 55.708688 0:2 driver_usb::host::xhci:467] [XHCI] Transfer @901BA9C0 got result, cycle true
[ 55.718235 0:2 driver_usb::host::xhci:697] [XHCI] Result: TransferEvent { completion_code: Ok(Success), trb_pointer: 2417732032, trb_transfer_length: 0, event_data: false, endpoint_id: 1, slot_id: 1, cycle_bit: true }
[ 55.738735 0:2 driver_usb::host::xhci:669] fetched descriptors:[Device(Device { len: 18, descriptor_type: 1, cd_usb: 272, class: 0, subclass: 0, protocol: 0, max_packet_size0: 8, vendor: 9354, product_id: 33639, device: 256, manufacture: 1, product: 2, serial_number: 0, num_configurations: 1 }), Configuration(Configuration { length: 9, ty: 2, total_length: 59, num_interfaces: 2, config_val: 1, config_string: 0, attributes: 160, max_power: 25 }), Interface(Interface { len: 9, descriptor_type: 4, interface_number: 0, alternate_setting: 0, num_endpoints: 1, interface_class: 3, interface_subclass: 1, interface_protocol: 2, interface: 0 }), Hid(Hid { len: 9, descriptor_type: 33, hid_bcd: 273, country_code: 33, num_descriptions: 1, report_descriptor_type: 34, report_descriptor_len: 142 }), Endpoint(Endpoint { len: 7, descriptor_type: 5, endpoint_address: 130, attributes: 3, max_packet_size: 8, interval: 4, ssc: None }), Interface(Interface { len: 9, descriptor_type: 4, interface_number: 1, alternate_setting: 0, num_endpoints: 1, interface_class: 3, interface_subclass: 1, interface_protocol: 1, interface: 0 }), Hid(Hid { len: 9, descriptor_type: 33, hid_bcd: 273, country_code: 33, num_descriptions: 1, report_descriptor_type: 34, report_descriptor_len: 59 }), Endpoint(Endpoint { len: 7, descriptor_type: 5, endpoint_address: 129, attributes: 3, max_packet_size: 8, interval: 10, ssc: None })]
[ 55.862323 0:2 driver_usb::host::xhci:592] fetch all complete!
[ 55.869355 0:2 driver_usb::host::xhci:598] set cfg!
[ 55.875433 0:2 driver_usb::host::xhci::xhci_device:84] found last entry: 0x82
[ 55.883767 0:2 driver_usb::host::xhci::xhci_device:185] set a interrupt endpoint! addr:5
[ 55.893051 0:2 driver_usb::host::xhci::xhci_device:185] set a interrupt endpoint! addr:3
[ 55.902338 0:2 driver_usb::host::xhci::xhci_device:109] [XHCI DEVICE] CMD: configure endpoint
[ 55.912060 0:2 driver_usb::host::xhci::ring:46] enqueue trb into 6
[ 55.919437 0:2 driver_usb::host::xhci::ring:59] next index
[ 55.926121 0:2 driver_usb::host::xhci::ring:49] enqueued,next index: 6
[ 55.933846 0:2 driver_usb::host::xhci:308] [XHCI] Post cmd ConfigureEndpoint(ConfigureEndpoint { input_context_pointer: 2417606656, deconfigure: false, slot_id: 1, cycle_bit: true }) @FFFF0000901704C4
[ 55.952856 0:2 driver_usb::host::xhci:320] [XHCI] Wait result
[ 55.959799 0:2 driver_usb::host::xhci::ring:59] next index
[ 55.966483 0:2 driver_usb::host::xhci:329] [XHCI] Cmd @901B88E0 got result, cycle true
[ 55.975597 0:2 driver_usb::host::xhci::xhci_device:119] [XHCI DEVICE] CMD: result:Ok(CommandCompletion { completion_code: Ok(Success), command_trb_pointer: 2417723616, command_completion_parameter: 0, vf_id: 0, slot_id: 1, cycle_bit: true })
[ 55.998166 0:2 driver_usb::host::xhci::xhci_device:58] try creating!
[ 56.005717 0:2 driver_usb::host::usb::drivers::driver_usb_hid:61] creating!
[ 56.013878 0:2 driver_usb::host::usb::drivers::driver_usb_hid:65] desc_device: [Device { len: 18, descriptor_type: 1, cd_usb: 272, class: 0, subclass: 0, protocol: 0, max_packet_size0: 8, vendor: 9354, product_id: 33639, device: 256, manufacture: 1, product: 2, serial_number: 0, num_configurations: 1 }]
[ 56.041914 0:2 driver_usb::host::usb::drivers::driver_usb_hid:89] interface csp:3,1,2
[ 56.050943 0:2 driver_usb::host::usb::drivers::driver_usb_hid:125] [USB-HID DRIVER]: post idle request to control endpoint
[ 56.063179 0:2 driver_usb::host::xhci::ring:46] enqueue trb into 9
[ 56.070556 0:2 driver_usb::host::xhci::ring:59] next index
[ 56.077240 0:2 driver_usb::host::xhci::ring:49] enqueued,next index: 9
[ 56.084965 0:2 driver_usb::host::xhci::ring:46] enqueue trb into 10
[ 56.092430 0:2 driver_usb::host::xhci::ring:59] next index
[ 56.099113 0:2 driver_usb::host::xhci::ring:49] enqueued,next index: 10
[ 56.106925 0:2 driver_usb::host::xhci:442] [XHCI] Post control transfer!
[ 56.114824 0:2 driver_usb::host::xhci:456] [XHCI] Wait result
[ 56.121769 0:2 driver_usb::host::xhci:462] received temp!:TransferEvent(TransferEvent { completion_code: Ok(Success), trb_pointer: 2417732064, trb_transfer_length: 0, event_data: false, endpoint_id: 1, slot_id: 1, cycle_bit: true })
[ 56.143555 0:2 driver_usb::host::xhci::ring:59] next index
[ 56.150240 0:2 driver_usb::host::xhci:467] [XHCI] Transfer @901BA9E0 got result, cycle true
[ 56.159787 0:2 driver_usb::host::usb::drivers::driver_usb_hid:134] [USB-HID DRIVER]: result: Ok(TransferEvent { completion_code: Ok(Success), trb_pointer: 2417732064, trb_transfer_length: 0, event_data: false, endpoint_id: 1, slot_id: 1, cycle_bit: true })
[ 56.683657 0:2 driver_usb::dma:125] allocated data:0x901bc180
[ 56.687738 0:2 driver_usb::host::usb::drivers::driver_usb_hid:156] [USB-HID DRIVER]: post report request
[ 56.698407 0:2 driver_usb::host::xhci::ring:46] enqueue trb into 11
[ 56.705870 0:2 driver_usb::host::xhci::ring:59] next index
[ 56.712554 0:2 driver_usb::host::xhci::ring:49] enqueued,next index: 11
[ 56.720366 0:2 driver_usb::host::xhci::ring:46] enqueue trb into 12
[ 56.727831 0:2 driver_usb::host::xhci::ring:59] next index
[ 56.734514 0:2 driver_usb::host::xhci::ring:49] enqueued,next index: 12
[ 56.742326 0:2 driver_usb::host::xhci::ring:46] enqueue trb into 13
[ 56.749791 0:2 driver_usb::host::xhci::ring:59] next index
[ 56.756475 0:2 driver_usb::host::xhci::ring:49] enqueued,next index: 13
[ 56.764287 0:2 driver_usb::host::xhci:388] [XHCI] Post control transfer!
[ 56.772186 0:2 driver_usb::host::xhci:398] [XHCI] Wait result
[ 56.779129 0:2 driver_usb::host::xhci:456] [XHCI] Wait result
[ 56.786074 0:2 driver_usb::host::xhci:462] received temp!:TransferEvent(TransferEvent { completion_code: Ok(Success), trb_pointer: 2417732112, trb_transfer_length: 0, event_data: false, endpoint_id: 1, slot_id: 1, cycle_bit: true })
[ 56.807860 0:2 driver_usb::host::xhci::ring:59] next index
[ 56.814544 0:2 driver_usb::host::xhci:467] [XHCI] Transfer @901BAA10 got result, cycle true
[ 56.824093 0:2 driver_usb::host::usb::drivers::driver_usb_hid:167] [USB-HID DRIVER]: result: TransferEvent { completion_code: Ok(Success), trb_pointer: 2417732112, trb_transfer_length: 0, event_data: false, endpoint_id: 1, slot_id: 1, cycle_bit: true }
[ 56.847620 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] 05 01 09 02 
[ 56.856124 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] a1 01 85 01 
[ 56.864630 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] 09 01 a1 00 
[ 56.873136 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] 05 09 19 01 
[ 56.881643 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] 29 05 15 00 
[ 56.890149 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] 25 01 95 05 
[ 56.898655 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] 75 01 81 02 
[ 56.907162 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] 95 01 75 03 
[ 56.915668 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] 81 01 05 01 
[ 56.924175 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] 09 30 09 31 
[ 56.932681 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] 15 81 25 7f 
[ 56.941187 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] 75 08 95 02 
[ 56.949694 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] 81 06 09 38 
[ 56.958200 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] 15 81 25 7f 
[ 56.966707 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] 75 08 95 01 
[ 56.975213 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] 81 06 c0 c0 
[ 56.983719 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] 05 0c 09 01 
[ 56.992226 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] a1 01 85 03 
[ 57.000732 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] 75 10 95 02 
[ 57.009239 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] 15 01 26 8c 
[ 57.017745 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] 02 19 01 2a 
[ 57.026252 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] 8c 02 81 00 
[ 57.034758 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] c0 05 01 09 
[ 57.043264 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] 80 a1 01 85 
[ 57.051771 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] 04 75 02 95 
[ 57.060277 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] 01 15 01 25 
[ 57.068783 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] 03 09 82 09 
[ 57.077290 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] 81 09 83 81 
[ 57.085796 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] 60 75 06 81 
[ 57.094303 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] 03 c0 05 01 
[ 57.102809 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] 09 00 a1 01 
[ 57.111316 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] 85 05 06 00 
[ 57.119822 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] ff 09 01 15 
[ 57.128328 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] 81 25 7f 75 
[ 57.136835 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] 08 95 07 b1 
[ 57.145340 0:2 driver_usb::host::usb::drivers::driver_usb_hid:254] 02 c0 
[ 57.653328 0:2 driver_usb::dma:125] allocated data:0x901bc160
[ 57.657400 0:2 driver_usb::host::usb::drivers::driver_usb_hid:185] [USB-HID DRIVER]: post IN Transfer report request
[ 57.669119 0:2 driver_usb::host::xhci::ring:46] enqueue trb into 0
[ 57.676496 0:2 driver_usb::host::xhci::ring:59] next index
[ 57.683180 0:2 driver_usb::host::xhci::ring:49] enqueued,next index: 0
[ 57.690906 0:2 driver_usb::host::usb::drivers::driver_usb_hid:222] [USB-HID DRIVER] Post control transfer!
[ 57.701755 0:2 driver_usb::host::xhci:456] [XHCI] Wait result
[ 57.708699 0:2 driver_usb::host::xhci:462] received temp!:TransferEvent(TransferEvent { completion_code: Ok(EndpointNotEnabledError), trb_pointer: 0, trb_transfer_length: 0, event_data: false, endpoint_id: 3, slot_id: 1, cycle_bit: true })
[ 57.731093 0:2 driver_usb::host::xhci::ring:59] next index
[ 57.737777 0:2 driver_usb::host::xhci:467] [XHCI] Transfer @0 got result, cycle true
[ 57.751718 0:2 driver_usb::host::usb::drivers::driver_usb_hid:236] [USB-HID DRIVER]: result: Ok(TransferEvent { completion_code: Ok(EndpointNotEnabledError), trb_pointer: 0, trb_transfer_length: 0, event_data: false, endpoint_id: 3, slot_id: 1, cycle_bit: true })
[ 57.773327 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] 00 00 00 00 
[ 58.281835 0:2 driver_usb::dma:125] allocated data:0x901bc160
[ 58.285907 0:2 driver_usb::host::usb::drivers::driver_usb_hid:185] [USB-HID DRIVER]: post IN Transfer report request
[ 58.297626 0:2 driver_usb::host::xhci::ring:46] enqueue trb into 1
[ 58.305003 0:2 driver_usb::host::xhci::ring:59] next index
[ 58.311686 0:2 driver_usb::host::xhci::ring:49] enqueued,next index: 1
[ 58.319412 0:2 driver_usb::host::usb::drivers::driver_usb_hid:222] [USB-HID DRIVER] Post control transfer!
[ 58.330262 0:2 driver_usb::host::xhci:456] [XHCI] Wait result
[ 58.337206 0:2 driver_usb::host::xhci:462] received temp!:TransferEvent(TransferEvent { completion_code: Ok(EndpointNotEnabledError), trb_pointer: 0, trb_transfer_length: 0, event_data: false, endpoint_id: 3, slot_id: 1, cycle_bit: true })
[ 58.359600 0:2 driver_usb::host::xhci::ring:59] next index
[ 58.366285 0:2 driver_usb::host::xhci:467] [XHCI] Transfer @0 got result, cycle true
[ 58.380224 0:2 driver_usb::host::usb::drivers::driver_usb_hid:236] [USB-HID DRIVER]: result: Ok(TransferEvent { completion_code: Ok(EndpointNotEnabledError), trb_pointer: 0, trb_transfer_length: 0, event_data: false, endpoint_id: 3, slot_id: 1, cycle_bit: true })
[ 58.401833 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] 00 00 00 00 
[ 58.910339 0:2 driver_usb::dma:125] allocated data:0x901bc160
[ 58.914411 0:2 driver_usb::host::usb::drivers::driver_usb_hid:185] [USB-HID DRIVER]: post IN Transfer report request
[ 58.926130 0:2 driver_usb::host::xhci::ring:46] enqueue trb into 2
[ 58.933507 0:2 driver_usb::host::xhci::ring:59] next index
[ 58.940191 0:2 driver_usb::host::xhci::ring:49] enqueued,next index: 2
[ 58.947916 0:2 driver_usb::host::usb::drivers::driver_usb_hid:222] [USB-HID DRIVER] Post control transfer!
[ 58.958766 0:2 driver_usb::host::xhci:456] [XHCI] Wait result
[ 58.965710 0:2 driver_usb::host::xhci:462] received temp!:TransferEvent(TransferEvent { completion_code: Ok(EndpointNotEnabledError), trb_pointer: 0, trb_transfer_length: 0, event_data: false, endpoint_id: 3, slot_id: 1, cycle_bit: true })
[ 58.988104 0:2 driver_usb::host::xhci::ring:59] next index
[ 58.994789 0:2 driver_usb::host::xhci:467] [XHCI] Transfer @0 got result, cycle true
[ 59.008728 0:2 driver_usb::host::usb::drivers::driver_usb_hid:236] [USB-HID DRIVER]: result: Ok(TransferEvent { completion_code: Ok(EndpointNotEnabledError), trb_pointer: 0, trb_transfer_length: 0, event_data: false, endpoint_id: 3, slot_id: 1, cycle_bit: true })
[ 59.030337 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] 00 00 00 00 
[ 59.538843 0:2 driver_usb::dma:125] allocated data:0x901bc160
[ 59.542915 0:2 driver_usb::host::usb::drivers::driver_usb_hid:185] [USB-HID DRIVER]: post IN Transfer report request
[ 59.554634 0:2 driver_usb::host::xhci::ring:46] enqueue trb into 3
[ 59.562011 0:2 driver_usb::host::xhci::ring:59] next index
[ 59.568695 0:2 driver_usb::host::xhci::ring:49] enqueued,next index: 3
[ 59.576420 0:2 driver_usb::host::usb::drivers::driver_usb_hid:222] [USB-HID DRIVER] Post control transfer!
[ 59.587270 0:2 driver_usb::host::xhci:456] [XHCI] Wait result
[ 59.594214 0:2 driver_usb::host::xhci:462] received temp!:TransferEvent(TransferEvent { completion_code: Ok(EndpointNotEnabledError), trb_pointer: 0, trb_transfer_length: 0, event_data: false, endpoint_id: 3, slot_id: 1, cycle_bit: true })
[ 59.616608 0:2 driver_usb::host::xhci::ring:59] next index
[ 59.623293 0:2 driver_usb::host::xhci:467] [XHCI] Transfer @0 got result, cycle true
[ 59.637233 0:2 driver_usb::host::usb::drivers::driver_usb_hid:236] [USB-HID DRIVER]: result: Ok(TransferEvent { completion_code: Ok(EndpointNotEnabledError), trb_pointer: 0, trb_transfer_length: 0, event_data: false, endpoint_id: 3, slot_id: 1, cycle_bit: true })
[ 59.658841 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] 00 00 00 00 
[ 60.167347 0:2 driver_usb::dma:125] allocated data:0x901bc160
[ 60.171419 0:2 driver_usb::host::usb::drivers::driver_usb_hid:185] [USB-HID DRIVER]: post IN Transfer report request
[ 60.183138 0:2 driver_usb::host::xhci::ring:46] enqueue trb into 4
[ 60.190515 0:2 driver_usb::host::xhci::ring:59] next index
[ 60.197199 0:2 driver_usb::host::xhci::ring:49] enqueued,next index: 4
[ 60.204924 0:2 driver_usb::host::usb::drivers::driver_usb_hid:222] [USB-HID DRIVER] Post control transfer!
[ 60.215775 0:2 driver_usb::host::xhci:456] [XHCI] Wait result
[ 60.222719 0:2 driver_usb::host::xhci:462] received temp!:TransferEvent(TransferEvent { completion_code: Ok(EndpointNotEnabledError), trb_pointer: 0, trb_transfer_length: 0, event_data: false, endpoint_id: 3, slot_id: 1, cycle_bit: true })
[ 60.245113 0:2 driver_usb::host::xhci::ring:59] next index
[ 60.251797 0:2 driver_usb::host::xhci:467] [XHCI] Transfer @0 got result, cycle true
[ 60.265737 0:2 driver_usb::host::usb::drivers::driver_usb_hid:236] [USB-HID DRIVER]: result: Ok(TransferEvent { completion_code: Ok(EndpointNotEnabledError), trb_pointer: 0, trb_transfer_length: 0, event_data: false, endpoint_id: 3, slot_id: 1, cycle_bit: true })
[ 60.287345 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] 00 00 00 00 
[ 60.795851 0:2 driver_usb::dma:125] allocated data:0x901bc160
[ 60.799924 0:2 driver_usb::host::usb::drivers::driver_usb_hid:185] [USB-HID DRIVER]: post IN Transfer report request
[ 60.811642 0:2 driver_usb::host::xhci::ring:46] enqueue trb into 5
[ 60.819019 0:2 driver_usb::host::xhci::ring:59] next index
[ 60.825703 0:2 driver_usb::host::xhci::ring:49] enqueued,next index: 5
[ 60.833428 0:2 driver_usb::host::usb::drivers::driver_usb_hid:222] [USB-HID DRIVER] Post control transfer!
[ 60.844279 0:2 driver_usb::host::xhci:456] [XHCI] Wait result
[ 60.851223 0:2 driver_usb::host::xhci:462] received temp!:TransferEvent(TransferEvent { completion_code: Ok(EndpointNotEnabledError), trb_pointer: 0, trb_transfer_length: 0, event_data: false, endpoint_id: 3, slot_id: 1, cycle_bit: true })
[ 60.873617 0:2 driver_usb::host::xhci::ring:59] next index
[ 60.880301 0:2 driver_usb::host::xhci:467] [XHCI] Transfer @0 got result, cycle true
[ 60.894241 0:2 driver_usb::host::usb::drivers::driver_usb_hid:236] [USB-HID DRIVER]: result: Ok(TransferEvent { completion_code: Ok(EndpointNotEnabledError), trb_pointer: 0, trb_transfer_length: 0, event_data: false, endpoint_id: 3, slot_id: 1, cycle_bit: true })
[ 60.915850 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] 00 00 00 00 
[ 61.424356 0:2 driver_usb::dma:125] allocated data:0x901bc160
[ 61.428428 0:2 driver_usb::host::usb::drivers::driver_usb_hid:185] [USB-HID DRIVER]: post IN Transfer report request
[ 61.440146 0:2 driver_usb::host::xhci::ring:46] enqueue trb into 6
[ 61.447524 0:2 driver_usb::host::xhci::ring:59] next index
[ 61.454207 0:2 driver_usb::host::xhci::ring:49] enqueued,next index: 6
[ 61.461932 0:2 driver_usb::host::usb::drivers::driver_usb_hid:222] [USB-HID DRIVER] Post control transfer!
[ 61.472783 0:2 driver_usb::host::xhci:456] [XHCI] Wait result
[ 61.479727 0:2 driver_usb::host::xhci:462] received temp!:TransferEvent(TransferEvent { completion_code: Ok(EndpointNotEnabledError), trb_pointer: 0, trb_transfer_length: 0, event_data: false, endpoint_id: 3, slot_id: 1, cycle_bit: true })
[ 61.502121 0:2 driver_usb::host::xhci::ring:59] next index
[ 61.508805 0:2 driver_usb::host::xhci:467] [XHCI] Transfer @0 got result, cycle true
[ 61.522745 0:2 driver_usb::host::usb::drivers::driver_usb_hid:236] [USB-HID DRIVER]: result: Ok(TransferEvent { completion_code: Ok(EndpointNotEnabledError), trb_pointer: 0, trb_transfer_length: 0, event_data: false, endpoint_id: 3, slot_id: 1, cycle_bit: true })
[ 61.544354 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] 00 00 00 00 
[ 62.052860 0:2 driver_usb::dma:125] allocated data:0x901bc160
[ 62.056932 0:2 driver_usb::host::usb::drivers::driver_usb_hid:185] [USB-HID DRIVER]: post IN Transfer report request
[ 62.068650 0:2 driver_usb::host::xhci::ring:46] enqueue trb into 7
[ 62.076028 0:2 driver_usb::host::xhci::ring:59] next index
[ 62.082711 0:2 driver_usb::host::xhci::ring:49] enqueued,next index: 7
[ 62.090437 0:2 driver_usb::host::usb::drivers::driver_usb_hid:222] [USB-HID DRIVER] Post control transfer!
[ 62.101287 0:2 driver_usb::host::xhci:456] [XHCI] Wait result
[ 62.108231 0:2 driver_usb::host::xhci:462] received temp!:TransferEvent(TransferEvent { completion_code: Ok(EndpointNotEnabledError), trb_pointer: 0, trb_transfer_length: 0, event_data: false, endpoint_id: 3, slot_id: 1, cycle_bit: true })
[ 62.130625 0:2 driver_usb::host::xhci::ring:59] next index
[ 62.137309 0:2 driver_usb::host::xhci:467] [XHCI] Transfer @0 got result, cycle true
[ 62.151249 0:2 driver_usb::host::usb::drivers::driver_usb_hid:236] [USB-HID DRIVER]: result: Ok(TransferEvent { completion_code: Ok(EndpointNotEnabledError), trb_pointer: 0, trb_transfer_length: 0, event_data: false, endpoint_id: 3, slot_id: 1, cycle_bit: true })
[ 62.172858 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] 00 00 00 00 
[ 62.681364 0:2 driver_usb::dma:125] allocated data:0x901bc160
[ 62.685436 0:2 driver_usb::host::usb::drivers::driver_usb_hid:185] [USB-HID DRIVER]: post IN Transfer report request
[ 62.697155 0:2 driver_usb::host::xhci::ring:46] enqueue trb into 8
[ 62.704532 0:2 driver_usb::host::xhci::ring:59] next index
[ 62.711216 0:2 driver_usb::host::xhci::ring:49] enqueued,next index: 8
[ 62.718941 0:2 driver_usb::host::usb::drivers::driver_usb_hid:222] [USB-HID DRIVER] Post control transfer!
[ 62.729791 0:2 driver_usb::host::xhci:456] [XHCI] Wait result
[ 62.736735 0:2 driver_usb::host::xhci:462] received temp!:TransferEvent(TransferEvent { completion_code: Ok(EndpointNotEnabledError), trb_pointer: 0, trb_transfer_length: 0, event_data: false, endpoint_id: 3, slot_id: 1, cycle_bit: true })
[ 62.759129 0:2 driver_usb::host::xhci::ring:59] next index
[ 62.765813 0:2 driver_usb::host::xhci:467] [XHCI] Transfer @0 got result, cycle true
[ 62.779753 0:2 driver_usb::host::usb::drivers::driver_usb_hid:236] [USB-HID DRIVER]: result: Ok(TransferEvent { completion_code: Ok(EndpointNotEnabledError), trb_pointer: 0, trb_transfer_length: 0, event_data: false, endpoint_id: 3, slot_id: 1, cycle_bit: true })
[ 62.801362 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] 00 00 00 00 
[ 63.309868 0:2 driver_usb::dma:125] allocated data:0x901bc160
[ 63.313940 0:2 driver_usb::host::usb::drivers::driver_usb_hid:185] [USB-HID DRIVER]: post IN Transfer report request
[ 63.325659 0:2 driver_usb::host::xhci::ring:46] enqueue trb into 9
[ 63.333036 0:2 driver_usb::host::xhci::ring:59] next index
[ 63.339720 0:2 driver_usb::host::xhci::ring:49] enqueued,next index: 9
[ 63.347445 0:2 driver_usb::host::usb::drivers::driver_usb_hid:222] [USB-HID DRIVER] Post control transfer!
[ 63.358295 0:2 driver_usb::host::xhci:456] [XHCI] Wait result
[ 63.365239 0:2 driver_usb::host::xhci:462] received temp!:TransferEvent(TransferEvent { completion_code: Ok(EndpointNotEnabledError), trb_pointer: 0, trb_transfer_length: 0, event_data: false, endpoint_id: 3, slot_id: 1, cycle_bit: true })
[ 63.387633 0:2 driver_usb::host::xhci::ring:59] next index
[ 63.394318 0:2 driver_usb::host::xhci:467] [XHCI] Transfer @0 got result, cycle true
[ 63.408258 0:2 driver_usb::host::usb::drivers::driver_usb_hid:236] [USB-HID DRIVER]: result: Ok(TransferEvent { completion_code: Ok(EndpointNotEnabledError), trb_pointer: 0, trb_transfer_length: 0, event_data: false, endpoint_id: 3, slot_id: 1, cycle_bit: true })
[ 63.429866 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] 00 00 00 00 
[ 63.938372 0:2 driver_usb::dma:125] allocated data:0x901bc160
[ 63.942444 0:2 driver_usb::host::usb::drivers::driver_usb_hid:185] [USB-HID DRIVER]: post IN Transfer report request
[ 63.954163 0:2 driver_usb::host::xhci::ring:46] enqueue trb into 10
[ 63.961627 0:2 driver_usb::host::xhci::ring:59] next index
[ 63.968311 0:2 driver_usb::host::xhci::ring:49] enqueued,next index: 10
[ 63.976123 0:2 driver_usb::host::usb::drivers::driver_usb_hid:222] [USB-HID DRIVER] Post control transfer!
[ 63.986973 0:2 driver_usb::host::xhci:456] [XHCI] Wait result
[ 63.993917 0:2 driver_usb::host::xhci:462] received temp!:TransferEvent(TransferEvent { completion_code: Ok(EndpointNotEnabledError), trb_pointer: 0, trb_transfer_length: 0, event_data: false, endpoint_id: 3, slot_id: 1, cycle_bit: true })
[ 64.016311 0:2 driver_usb::host::xhci::ring:59] next index
[ 64.022995 0:2 driver_usb::host::xhci:467] [XHCI] Transfer @0 got result, cycle true
[ 64.036935 0:2 driver_usb::host::usb::drivers::driver_usb_hid:236] [USB-HID DRIVER]: result: Ok(TransferEvent { completion_code: Ok(EndpointNotEnabledError), trb_pointer: 0, trb_transfer_length: 0, event_data: false, endpoint_id: 3, slot_id: 1, cycle_bit: true })
[ 64.058544 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] 00 00 00 00 
[ 64.567050 0:2 driver_usb::dma:125] allocated data:0x901bc160
[ 64.571122 0:2 driver_usb::host::usb::drivers::driver_usb_hid:185] [USB-HID DRIVER]: post IN Transfer report request
[ 64.582841 0:2 driver_usb::host::xhci::ring:46] enqueue trb into 11
[ 64.590305 0:2 driver_usb::host::xhci::ring:59] next index
[ 64.596988 0:2 driver_usb::host::xhci::ring:49] enqueued,next index: 11
[ 64.604800 0:2 driver_usb::host::usb::drivers::driver_usb_hid:222] [USB-HID DRIVER] Post control transfer!
[ 64.615651 0:2 driver_usb::host::xhci:456] [XHCI] Wait result
[ 64.622595 0:2 driver_usb::host::xhci:462] received temp!:TransferEvent(TransferEvent { completion_code: Ok(EndpointNotEnabledError), trb_pointer: 0, trb_transfer_length: 0, event_data: false, endpoint_id: 3, slot_id: 1, cycle_bit: true })
[ 64.644989 0:2 driver_usb::host::xhci::ring:59] next index
[ 64.651673 0:2 driver_usb::host::xhci:467] [XHCI] Transfer @0 got result, cycle true
[ 64.665613 0:2 driver_usb::host::usb::drivers::driver_usb_hid:236] [USB-HID DRIVER]: result: Ok(TransferEvent { completion_code: Ok(EndpointNotEnabledError), trb_pointer: 0, trb_transfer_length: 0, event_data: false, endpoint_id: 3, slot_id: 1, cycle_bit: true })
[ 64.687222 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] 00 00 00 00 
[ 65.195728 0:2 driver_usb::dma:125] allocated data:0x901bc160
[ 65.199800 0:2 driver_usb::host::usb::drivers::driver_usb_hid:185] [USB-HID DRIVER]: post IN Transfer report request
[ 65.211519 0:2 driver_usb::host::xhci::ring:46] enqueue trb into 12
[ 65.218983 0:2 driver_usb::host::xhci::ring:59] next index
[ 65.225666 0:2 driver_usb::host::xhci::ring:49] enqueued,next index: 12
[ 65.233478 0:2 driver_usb::host::usb::drivers::driver_usb_hid:222] [USB-HID DRIVER] Post control transfer!
[ 65.244329 0:2 driver_usb::host::xhci:456] [XHCI] Wait result
[ 65.251273 0:2 driver_usb::host::xhci:462] received temp!:TransferEvent(TransferEvent { completion_code: Ok(EndpointNotEnabledError), trb_pointer: 0, trb_transfer_length: 0, event_data: false, endpoint_id: 3, slot_id: 1, cycle_bit: true })
[ 65.273667 0:2 driver_usb::host::xhci::ring:59] next index
[ 65.280351 0:2 driver_usb::host::xhci:467] [XHCI] Transfer @0 got result, cycle true
[ 65.294291 0:2 driver_usb::host::usb::drivers::driver_usb_hid:236] [USB-HID DRIVER]: result: Ok(TransferEvent { completion_code: Ok(EndpointNotEnabledError), trb_pointer: 0, trb_transfer_length: 0, event_data: false, endpoint_id: 3, slot_id: 1, cycle_bit: true })
[ 65.315899 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] 00 00 00 00 
[ 65.824405 0:2 driver_usb::dma:125] allocated data:0x901bc160
[ 65.828477 0:2 driver_usb::host::usb::drivers::driver_usb_hid:185] [USB-HID DRIVER]: post IN Transfer report request
[ 65.840196 0:2 driver_usb::host::xhci::ring:46] enqueue trb into 13
[ 65.847660 0:2 driver_usb::host::xhci::ring:59] next index
[ 65.854344 0:2 driver_usb::host::xhci::ring:49] enqueued,next index: 13
[ 65.862156 0:2 driver_usb::host::usb::drivers::driver_usb_hid:222] [USB-HID DRIVER] Post control transfer!
[ 65.873006 0:2 driver_usb::host::xhci:456] [XHCI] Wait result
[ 65.879951 0:2 driver_usb::host::xhci:462] received temp!:TransferEvent(TransferEvent { completion_code: Ok(EndpointNotEnabledError), trb_pointer: 0, trb_transfer_length: 0, event_data: false, endpoint_id: 3, slot_id: 1, cycle_bit: true })
[ 65.902344 0:2 driver_usb::host::xhci::ring:59] next index
[ 65.909029 0:2 driver_usb::host::xhci:467] [XHCI] Transfer @0 got result, cycle true
[ 65.922969 0:2 driver_usb::host::usb::drivers::driver_usb_hid:236] [USB-HID DRIVER]: result: Ok(TransferEvent { completion_code: Ok(EndpointNotEnabledError), trb_pointer: 0, trb_transfer_length: 0, event_data: false, endpoint_id: 3, slot_id: 1, cycle_bit: true })
[ 65.944577 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] 00 00 00 00 
[ 66.453083 0:2 driver_usb::dma:125] allocated data:0x901bc160
[ 66.457155 0:2 driver_usb::host::usb::drivers::driver_usb_hid:185] [USB-HID DRIVER]: post IN Transfer report request
[ 66.468874 0:2 driver_usb::host::xhci::ring:46] enqueue trb into 14
[ 66.476338 0:2 driver_usb::host::xhci::ring:59] next index
[ 66.483022 0:2 driver_usb::host::xhci::ring:49] enqueued,next index: 14
[ 66.490834 0:2 driver_usb::host::usb::drivers::driver_usb_hid:222] [USB-HID DRIVER] Post control transfer!
[ 66.501684 0:2 driver_usb::host::xhci:456] [XHCI] Wait result
[ 66.508628 0:2 driver_usb::host::xhci:462] received temp!:TransferEvent(TransferEvent { completion_code: Ok(EndpointNotEnabledError), trb_pointer: 0, trb_transfer_length: 0, event_data: false, endpoint_id: 3, slot_id: 1, cycle_bit: true })
[ 66.531022 0:2 driver_usb::host::xhci::ring:59] next index
[ 66.537706 0:2 driver_usb::host::xhci:467] [XHCI] Transfer @0 got result, cycle true
[ 66.551646 0:2 driver_usb::host::usb::drivers::driver_usb_hid:236] [USB-HID DRIVER]: result: Ok(TransferEvent { completion_code: Ok(EndpointNotEnabledError), trb_pointer: 0, trb_transfer_length: 0, event_data: false, endpoint_id: 3, slot_id: 1, cycle_bit: true })
[ 66.573255 0:2 driver_usb::host::usb::drivers::driver_usb_hid:249] 00 00 00 00
```

配置端点返回值已由`ParameterError`变为`Success`，但是后续的发送传输请求，设备返回值依然为`EndpointNotEnabledError`


根据Linux打印的一些信息，发现是端点配置中传入的一些信息问题，现在已修复，端点成功启用：
```
 

Phytium-Pi#go 0x90100000
## Starting application at 0x90100000 ...
aaaaaaaaaaaacarch = aarch64
platform = aarch64-phytium-pi
target = aarch64-unknown-none-softfloat
smp = 1
build_mode = release
log_level = debug

ccc[ 39.153072 0 axruntime:138] Logging is enabled.
[ 39.158801 0 axruntime:139] Primary CPU 512 started, dtb = 0x1.
[ 39.165918 0 axruntime:141] Found physcial memory regions:
c[ 39.172689 0 axruntime:144]   [PA:0x90100000, PA:0x90126000) .text (READ | EXECUTE | RESERVED)
[ 39.182497 0 axruntime:144]   [PA:0x90126000, PA:0x9012e000) .rodata (READ | RESERVED)
[ 39.191611 0 axruntime:144]   [PA:0x9012e000, PA:0x90132000) .data .tdata .tbss .percpu (READ | WRITE | RESERVED)
[ 39.203068 0 axruntime:144]   [PA:0x90132000, PA:0x90172000) boot stack (READ | WRITE | RESERVED)
[ 39.213137 0 axruntime:144]   [PA:0x90172000, PA:0x90198000) .bss (READ | WRITE | RESERVED)
[ 39.222685 0 axruntime:144]   [PA:0x0, PA:0x1000) spintable (READ | WRITE | RESERVED)
[ 39.231713 0 axruntime:144]   [PA:0x90198000, PA:0x90898000) nocache memory (READ | WRITE | DEVICE)
[ 39.241955 0 axruntime:144]   [PA:0x90898000, PA:0xff900000) free memory (READ | WRITE | FREE)
[ 39.251763 0 axruntime:144]   [PA:0x2800c000, PA:0x2800d000) mmio (READ | WRITE | DEVICE | RESERVED)
[ 39.262093 0 axruntime:144]   [PA:0x2800d000, PA:0x2800e000) mmio (READ | WRITE | DEVICE | RESERVED)
[ 39.272422 0 axruntime:144]   [PA:0x2800e000, PA:0x2800f000) mmio (READ | WRITE | DEVICE | RESERVED)
[ 39.282751 0 axruntime:144]   [PA:0x2800f000, PA:0x28010000) mmio (READ | WRITE | DEVICE | RESERVED)
[ 39.293080 0 axruntime:144]   [PA:0x30000000, PA:0x38000000) mmio (READ | WRITE | DEVICE | RESERVED)
[ 39.303409 0 axruntime:144]   [PA:0x40000000, PA:0x80000000) mmio (READ | WRITE | DEVICE | RESERVED)
[ 39.313739 0 axruntime:144]   [PA:0x1000000000, PA:0x3000000000) mmio (READ | WRITE | DEVICE | RESERVED)
[ 39.324415 0 axruntime:223] Initialize global memory allocator...
[ 39.331706 0 axruntime:224]   use TLSF allocator.
[ 39.337611 0 axalloc:284] initialize global allocator at: free-[0xffff000090898000, 0xffff0000ff900000)
[ 39.348522 0 axruntime:158] Initialize kernel page table...
[ 39.355060 0 axruntime:258] Initialize global no cache memory allocator...
[ 39.363042 0 axalloc:300] initialize global allocator at: nocache-[0x90198000,0x90898000)
[ 39.372418 0 axruntime:165] Initialize platform devices...
[ 39.379099 0 axhal::platform::aarch64_common::gic:51] Initialize GICv2...
[ 39.387085 0 axtask::api:66] Initialize scheduling...
[ 39.393338 0 axtask::task:146] new task: Task(1, "idle")
[ 39.399848 0 axtask::task:146] new task: Task(3, "gc")
[ 39.406185 0 axalloc:126] expand heap memory: [0xffff0000908aa000, 0xffff0000908ea000)
[ 39.415302 0 axalloc:126] expand heap memory: [0xffff0000908ea000, 0xffff00009096a000)
[ 39.424411 0 axtask::api:72]   use Round-robin scheduler.
[ 39.431006 0 axdriver:158] Initialize device drivers...
[ 39.437429 0 axdriver:159]   device model: static
[ 39.443331 0 driver_pci::phytium:18] PCIe link start @0xFFFF000040000000...
[ 39.451490 0 driver_pci::phytium:19] theroticly, since uboot had already initialized it, we need't to operate it any more!
[ 39.463729 0 axdriver::bus::pci:14] probing in pci.rs!
[ 39.470066 0 driver_pci::root_complex:96] into next!
[ 39.476229 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 39.483173 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 39.490117 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 39.497061 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 39.504005 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 39.510948 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 39.517893 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 39.524837 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 39.531781 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 39.538724 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 39.545669 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 39.552613 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 39.559556 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 39.566500 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 39.573445 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 39.580389 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 39.587332 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 39.594277 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 39.601221 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 39.608165 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 39.615108 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 39.622053 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 39.628997 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 39.635941 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 39.642884 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 39.649828 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 39.656773 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 39.663717 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 39.670660 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 39.677605 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 39.684549 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 39.691493 0 driver_pci::root_complex:139] vid FFFF, did FFFF
[ 39.698436 0 driver_pci::root_complex:116] none!
[ 39.704252 0 axdriver:190] number of usb host controller: 0
[ 39.711022 0 axruntime:191] Initialize interrupt handlers...
[ 39.717880 0 axruntime:201] Primary CPU 512 init OK.
[ 39.724043 0:2 driver_usb::host::xhci:80] [XHCI] Base addr: VA:0xffff000031a08000
[ 39.732725 0:2 driver_usb::host::xhci:91] [XHCI] Max_slots: 16, max_ports: 2, max_irqs: 1, page size: 1
[ 39.744031 0:2 driver_usb::dma:125] allocated data:0x901b9880
[ 39.750291 0:2 driver_usb::dma:125] allocated data:0x901ba900
[ 39.757235 0:2 driver_usb::host::xhci:142] [XHCI] Reset begin
[ 39.764144 0:2 driver_usb::host::xhci:143] [XHCI] Stop
[ 39.770481 0:2 driver_usb::host::xhci:151] [XHCI] Until halt
[ 39.777338 0:2 driver_usb::host::xhci:153] [XHCI] Halted
[ 39.783848 0:2 driver_usb::host::xhci:158] [XHCI] Wait for ready...
[ 39.791313 0:2 driver_usb::host::xhci:160] [XHCI] Ready
[ 39.797737 0:2 driver_usb::host::xhci:168] [XHCI] Reset HC
[ 39.804420 0:2 driver_usb::host::xhci:182] [XHCI] XCHI reset ok
[ 39.811537 0:2 driver_usb::host::xhci:188] [XHCI] Setting enabled slots to 16.
[ 39.819957 0:2 driver_usb::host::xhci:198] [XHCI] Writing DCBAAP: 90199000
[ 39.828030 0:2 driver_usb::host::xhci:209] [XHCI] Writing CRCR: 901B9880
[ 39.835929 0:2 driver_usb::host::xhci:253] [XHCI] Disable interrupts
[ 39.843480 0:2 driver_usb::host::xhci:263] [XHCI] Writing ERSTZ
[ 39.850597 0:2 driver_usb::host::xhci:267] [XHCI] Writing ERDP: 901BA900
[ 39.858496 0:2 driver_usb::host::xhci:274] [XHCI] Writing ERSTBA: 901BA8C0
[ 39.866569 0:2 driver_usb::host::xhci:285] [XHCI] Enabling primary interrupter.
[ 39.875075 0:2 driver_usb::host::xhci:508] [XHCI] Scratch buf count: 0
[ 39.882800 0:2 driver_usb::host::xhci:235] [XHCI] Start run
[ 39.889571 0:2 driver_usb::host::xhci:242] [XHCI] Is running
[ 39.896428 0:2 driver_usb::host::xhci:491] [XHCI] Test command ring
[ 39.903893 0:2 driver_usb::host::xhci::ring:48] enqueue trb: [0, 0, 0, 23553]
[ 39.912225 0:2 driver_usb::host::xhci:308] [XHCI] Post cmd Noop(Noop { cycle_bit: true }) @901B9880
[ 39.922468 0:2 driver_usb::host::xhci:320] [XHCI] Wait result
[ 39.929413 0:2 driver_usb::host::xhci:345] event: PortStatusChange(PortStatusChange { completion_code: Ok(Success), port_id: 1, cycle_bit: true })
[ 39.943734 0:2 driver_usb::host::xhci:335] [XHCI] Cmd @901B9880 got result, cycle true
[ 39.952847 0:2 driver_usb::host::xhci::ring:48] enqueue trb: [0, 0, 0, 23553]
[ 39.961180 0:2 driver_usb::host::xhci:308] [XHCI] Post cmd Noop(Noop { cycle_bit: true }) @901B9890
[ 39.971423 0:2 driver_usb::host::xhci:320] [XHCI] Wait result
[ 39.978367 0:2 driver_usb::host::xhci:335] [XHCI] Cmd @901B9890 got result, cycle true
[ 39.987480 0:2 driver_usb::host::xhci::ring:48] enqueue trb: [0, 0, 0, 23553]
[ 39.995813 0:2 driver_usb::host::xhci:308] [XHCI] Post cmd Noop(Noop { cycle_bit: true }) @901B98A0
[ 40.006056 0:2 driver_usb::host::xhci:320] [XHCI] Wait result
[ 40.013000 0:2 driver_usb::host::xhci:335] [XHCI] Cmd @901B98A0 got result, cycle true
[ 40.022114 0:2 driver_usb::host::xhci:495] [XHCI] Command ring ok
[ 40.029405 0:2 driver_usb::host::xhci:551] [XHCI] Port 0 start reset
[ 40.094799 0:2 driver_usb::host::xhci:564] [XHCI] Port 0 reset ok
[ 40.099219 0:2 driver_usb::host::xhci:551] [XHCI] Port 1 start reset
[ 40.106776 0:2 driver_usb::host::xhci:564] [XHCI] Port 1 reset ok
[ 40.114062 0:2 driver_usb::host::xhci:116] [XHCI] Init success
[ 40.421095 0:2 driver_usb::host::xhci:576] [XHCI] Port 0: Enabled: true, Connected: true, Speed 2, Power true
[ 40.429336 0:2 driver_usb::host::xhci:576] [XHCI] Port 1: Enabled: false, Connected: false, Speed 0, Power true
[ 40.440618 0:2 driver_usb::host::xhci:896] [XHCI] CMD: enable slot
[ 40.447995 0:2 driver_usb::host::xhci::ring:48] enqueue trb: [0, 0, 0, 9217]
[ 40.456241 0:2 driver_usb::host::xhci:308] [XHCI] Post cmd EnableSlot(EnableSlot { slot_type: 0, cycle_bit: true }) @901B98B0
[ 40.468741 0:2 driver_usb::host::xhci:320] [XHCI] Wait result
[ 40.475685 0:2 driver_usb::host::xhci:345] event: PortStatusChange(PortStatusChange { completion_code: Ok(Success), port_id: 1, cycle_bit: true })
[ 40.490007 0:2 driver_usb::host::xhci:335] [XHCI] Cmd @901B98B0 got result, cycle true
[ 40.499121 0:2 driver_usb::host::xhci:901] [XHCI] Result: CommandCompletion { completion_code: Ok(Success), command_trb_pointer: 2417727664, command_completion_parameter: 0, vf_id: 0, slot_id: 1, cycle_bit: true }, slot id: 1
[ 40.520300 0:2 driver_usb::host::xhci:904] new slot!
[ 40.526463 0:2 driver_usb::dma:125] allocated data:0x901bb940
[ 40.533411 0:2 driver_usb::dma:125] allocated data:0x901bbb80
[ 40.540355 0:2 driver_usb::dma:125] allocated data:0x901bbdc0
[ 40.547299 0:2 driver_usb::dma:125] allocated data:0x901bc000
[ 40.554243 0:2 driver_usb::dma:125] allocated data:0x901bc240
[ 40.561187 0:2 driver_usb::dma:125] allocated data:0x901bc480
[ 40.568131 0:2 driver_usb::dma:125] allocated data:0x901bc6c0
[ 40.575075 0:2 driver_usb::dma:125] allocated data:0x901bc900
[ 40.582019 0:2 driver_usb::dma:125] allocated data:0x901bcb40
[ 40.588963 0:2 driver_usb::dma:125] allocated data:0x901bcd80
[ 40.595907 0:2 driver_usb::dma:125] allocated data:0x901bcfc0
[ 40.602851 0:2 driver_usb::dma:125] allocated data:0x901bd200
[ 40.609795 0:2 driver_usb::dma:125] allocated data:0x901bd440
[ 40.616739 0:2 driver_usb::dma:125] allocated data:0x901bd680
[ 40.623683 0:2 driver_usb::dma:125] allocated data:0x901bd8c0
[ 40.630627 0:2 driver_usb::dma:125] allocated data:0x901bdb00
[ 40.637571 0:2 driver_usb::host::xhci::context:76] new rings!
[ 40.644511 0:2 driver_usb::host::xhci::context:87] new desc container
[ 40.652150 0:2 driver_usb::host::xhci::context:93] insert complete!
[ 40.659614 0:2 driver_usb::host::xhci:594] assign complete!
[ 40.666391 0:2 driver_usb::host::xhci::ring:48] enqueue trb: [2417602560, 0, 0, 16788481]
[ 40.675759 0:2 driver_usb::host::xhci:308] [XHCI] Post cmd AddressDevice(AddressDevice { input_context_pointer: 2417602560, block_set_address_request: false, slot_id: 1, cycle_bit: true }) @901B98C0
[ 40.694595 0:2 driver_usb::host::xhci:320] [XHCI] Wait result
[ 40.701539 0:2 driver_usb::host::xhci:335] [XHCI] Cmd @901B98C0 got result, cycle true
[ 40.710652 0:2 driver_usb::host::xhci:869] address [1] ok
[ 40.717249 0:2 driver_usb::host::xhci:596] address complete!
[ 40.724109 0:2 driver_usb::host::xhci:764] [XHCI] CMD: get endpoint0 packet size
[ 40.732701 0:2 driver_usb::host::xhci::ring:48] enqueue trb: [16778880, 1179648, 8, 198721]
[ 40.742247 0:2 driver_usb::host::xhci::ring:48] enqueue trb: [2417750016, 0, 18, 68609]
[ 40.751448 0:2 driver_usb::host::xhci::ring:48] enqueue trb: [0, 0, 0, 4129]
[ 40.759695 0:2 driver_usb::host::xhci:450] [XHCI] Post control transfer!
[ 40.767594 0:2 driver_usb::host::xhci:464] [XHCI] Wait result
[ 40.774538 0:2 driver_usb::host::xhci:470] received temp!:TransferEvent(TransferEvent { completion_code: Ok(Success), trb_pointer: 2417736032, trb_transfer_length: 0, event_data: false, endpoint_id: 1, slot_id: 1, cycle_bit: true })
[ 40.796325 0:2 driver_usb::host::xhci:475] [XHCI] Transfer @901BB960 got result, cycle true
[ 40.805873 0:2 driver_usb::host::xhci:771] [XHCI] Result: TransferEvent { completion_code: Ok(Success), trb_pointer: 2417736032, trb_transfer_length: 0, event_data: false, endpoint_id: 1, slot_id: 1, cycle_bit: true }
[ 40.826357 0:2 driver_usb::host::xhci:785] [XHCI] CMD: evaluating context for set endpoint0 packet size 8
[ 40.837120 0:2 driver_usb::host::xhci::ring:48] enqueue trb: [2417602560, 0, 0, 16790529]
[ 40.846494 0:2 driver_usb::host::xhci:308] [XHCI] Post cmd EvaluateContext(EvaluateContext { input_context_pointer: 2417602560, slot_id: 1, cycle_bit: true }) @901B98D0
[ 40.862726 0:2 driver_usb::host::xhci:320] [XHCI] Wait result
[ 40.869671 0:2 driver_usb::host::xhci:335] [XHCI] Cmd @901B98D0 got result, cycle true
[ 40.878784 0:2 driver_usb::host::xhci:794] [XHCI] Result: CommandCompletion { completion_code: Ok(Success), command_trb_pointer: 2417727696, command_completion_parameter: 0, vf_id: 0, slot_id: 1, cycle_bit: true }
[ 40.898923 0:2 driver_usb::host::xhci:598] packet size complete!
[ 40.906128 0:2 driver_usb::dma:125] allocated data:0x901bf000
[ 40.913345 0:2 driver_usb::host::xhci:734] [XHCI] Transfer Control: Fetching device desc
[ 40.922359 0:2 driver_usb::host::xhci::ring:48] enqueue trb: [16778880, 268435456, 8, 198721]
[ 40.932079 0:2 driver_usb::host::xhci::ring:48] enqueue trb: [2417750016, 0, 4096, 68609]
[ 40.941453 0:2 driver_usb::host::xhci::ring:48] enqueue trb: [0, 0, 0, 4129]
[ 40.949700 0:2 driver_usb::host::xhci:450] [XHCI] Post control transfer!
[ 40.957599 0:2 driver_usb::host::xhci:464] [XHCI] Wait result
[ 40.964543 0:2 driver_usb::host::xhci:470] received temp!:TransferEvent(TransferEvent { completion_code: Ok(Success), trb_pointer: 2417736080, trb_transfer_length: 0, event_data: false, endpoint_id: 1, slot_id: 1, cycle_bit: true })
[ 40.986330 0:2 driver_usb::host::xhci:475] [XHCI] Transfer @901BB990 got result, cycle true
[ 40.995878 0:2 driver_usb::host::xhci:743] [XHCI] Result: TransferEvent { completion_code: Ok(Success), trb_pointer: 2417736080, trb_transfer_length: 0, event_data: false, endpoint_id: 1, slot_id: 1, cycle_bit: true }
[ 41.016367 0:2 driver_usb::dma:125] allocated data:0x901bf000
[ 41.023581 0:2 driver_usb::host::xhci:706] [XHCI] Transfer Control: Fetching config desc
[ 41.032595 0:2 driver_usb::host::xhci::ring:48] enqueue trb: [33556096, 268435456, 8, 198721]
[ 41.042315 0:2 driver_usb::host::xhci::ring:48] enqueue trb: [2417750016, 0, 4096, 68609]
[ 41.051689 0:2 driver_usb::host::xhci::ring:48] enqueue trb: [0, 0, 0, 4129]
[ 41.059936 0:2 driver_usb::host::xhci:450] [XHCI] Post control transfer!
[ 41.067835 0:2 driver_usb::host::xhci:464] [XHCI] Wait result
[ 41.074779 0:2 driver_usb::host::xhci:470] received temp!:TransferEvent(TransferEvent { completion_code: Ok(Success), trb_pointer: 2417736128, trb_transfer_length: 0, event_data: false, endpoint_id: 1, slot_id: 1, cycle_bit: true })
[ 41.096566 0:2 driver_usb::host::xhci:475] [XHCI] Transfer @901BB9C0 got result, cycle true
[ 41.106113 0:2 driver_usb::host::xhci:715] [XHCI] Result: TransferEvent { completion_code: Ok(Success), trb_pointer: 2417736128, trb_transfer_length: 0, event_data: false, endpoint_id: 1, slot_id: 1, cycle_bit: true }
[ 41.126607 0:2 driver_usb::host::xhci:687] fetched descriptors:[
    Device(
        Device {
            len: 18,
            descriptor_type: 1,
            cd_usb: 272,
            class: 0,
            subclass: 0,
            protocol: 0,
            max_packet_size0: 8,
            vendor: 6127,
            product_id: 24717,
            device: 9304,
            manufacture: 1,
            product: 2,
            serial_number: 0,
            num_configurations: 1,
        },
    ),
    Configuration(
        Configuration {
            length: 9,
            ty: 2,
            total_length: 34,
            num_interfaces: 1,
            config_val: 1,
            config_string: 0,
            attributes: 160,
            max_power: 50,
        },
    ),
    Interface(
        Interface {
            len: 9,
            descriptor_type: 4,
            interface_number: 0,
            alternate_setting: 0,
            num_endpoints: 1,
            interface_class: 3,
            interface_subclass: 1,
            interface_protocol: 2,
            interface: 0,
        },
    ),
    Hid(
        Hid {
            len: 9,
            descriptor_type: 33,
            hid_bcd: 273,
            country_code: 0,
            num_descriptions: 1,
            report_descriptor_type: 34,
            report_descriptor_len: 62,
        },
    ),
    Endpoint(
        Endpoint {
            len: 7,
            descriptor_type: 5,
            endpoint_address: 129,
            attributes: 3,
            max_packet_size: 4,
            interval: 10,
            ssc: None,
        },
    ),
]
[ 41.273724 0:2 driver_usb::host::xhci:600] fetch all complete!
[ 41.280756 0:2 driver_usb::host::xhci:606] set cfg!
[ 41.286833 0:2 driver_usb::host::xhci::xhci_device:88] found last entry: 0x81
[ 41.295167 0:2 driver_usb::host::xhci::xhci_device:238] set a interrupt endpoint! addr:3
[ 41.304452 0:2 driver_usb::host::xhci::xhci_device:118] [XHCI DEVICE] CMD: configure endpoint
[ 41.314173 0:2 driver_usb::host::xhci::ring:48] enqueue trb: [2417602560, 0, 0, 16789505]
[ 41.323547 0:2 driver_usb::host::xhci:308] [XHCI] Post cmd ConfigureEndpoint(ConfigureEndpoint { input_context_pointer: 2417602560, deconfigure: false, slot_id: 1, cycle_bit: true }) @901B98E0
[ 41.341863 0:2 driver_usb::host::xhci:320] [XHCI] Wait result
[ 41.348807 0:2 driver_usb::host::xhci:335] [XHCI] Cmd @901B98E0 got result, cycle true
[ 41.357920 0:2 driver_usb::host::xhci::xhci_device:128] [XHCI DEVICE] CMD: result:CommandCompletion { completion_code: Ok(Success), command_trb_pointer: 2417727712, command_completion_parameter: 0, vf_id: 0, slot_id: 1, cycle_bit: true }
[ 41.380142 0:2 driver_usb::host::xhci::xhci_device:59] try creating!
[ 41.387692 0:2 driver_usb::host::usb::drivers::driver_usb_hid:80] creating!
[ 41.395853 0:2 driver_usb::host::usb::drivers::driver_usb_hid:84] desc_device: [Device { len: 18, descriptor_type: 1, cd_usb: 272, class: 0, subclass: 0, protocol: 0, max_packet_size0: 8, vendor: 6127, product_id: 24717, device: 9304, manufacture: 1, product: 2, serial_number: 0, num_configurations: 1 }]
[ 41.423976 0:2 driver_usb::host::usb::drivers::driver_usb_hid:108] interface csp:3,1,2
[ 41.433090 0:2 driver_usb::host::usb::drivers::driver_usb_hid:134] ###driver usbhid working!###
[ 41.442984 0:2 driver_usb::host::usb::drivers::driver_usb_hid:60] dumped output context at slot 1:
 Device {
    slot: Slot {
        route_string: 0,
        speed: 2,
        multi_tt: false,
        hub: false,
        context_entries: 3,
        max_exit_latency: 0,
        root_hub_port_number: 1,
        number_of_ports: 0,
        parent_hub_slot_id: 0,
        parent_port_number: 0,
        tt_think_time: 0,
        interrupter_target: 0,
        usb_device_address: 1,
        slot_state: Configured,
    },
    endpoints: [
        Endpoint {
            endpoint_state: Running,
            mult: 0,
            max_primary_streams: 0,
            linear_stream_array: false,
            interval: 0,
            max_endpoint_service_time_interval_payload_high: 0,
            error_count: 3,
            endpoint_type: Control,
            host_initiate_disable: false,
            max_burst_size: 0,
            max_packet_size: 8,
            dequeue_cycle_state: true,
            tr_dequeue_pointer: 2417736145,
            average_trb_length: 8,
            max_endpoint_service_time_interval_payload_low: 0,
        },
        Endpoint {
            endpoint_state: Disabled,
            mult: 0,
            max_primary_streams: 0,
            linear_stream_array: false,
            interval: 0,
            max_endpoint_service_time_interval_payload_high: 0,
            error_count: 0,
            endpoint_type: NotValid,
            host_initiate_disable: false,
            max_burst_size: 0,
            max_packet_size: 0,
            dequeue_cycle_state: false,
            tr_dequeue_pointer: 0,
            average_trb_length: 0,
            max_endpoint_service_time_interval_payload_low: 0,
        },
        Endpoint {
            endpoint_state: Running,
            mult: 0,
            max_primary_streams: 0,
            linear_stream_array: false,
            interval: 3,
            max_endpoint_service_time_interval_payload_high: 0,
            error_count: 3,
            endpoint_type: InterruptIn,
            host_initiate_disable: false,
            max_burst_size: 0,
            max_packet_size: 4,
            dequeue_cycle_state: true,
            tr_dequeue_pointer: 2417737729,
            average_trb_length: 0,
            max_endpoint_service_time_interval_payload_low: 4,
        },
        Endpoint {
            endpoint_state: Disabled,
            mult: 0,
            max_primary_streams: 0,
            linear_stream_array: false,
            interval: 0,
            max_endpoint_service_time_interval_payload_high: 0,
            error_count: 0,
            endpoint_type: NotValid,
            host_initiate_disable: false,
            max_burst_size: 0,
            max_packet_size: 0,
            dequeue_cycle_state: false,
            tr_dequeue_pointer: 0,
            average_trb_length: 0,
            max_endpoint_service_time_interval_payload_low: 0,
        },
        Endpoint {
            endpoint_state: Disabled,
            mult: 0,
            max_primary_streams: 0,
            linear_stream_array: false,
            interval: 0,
            max_endpoint_service_time_interval_payload_high: 0,
            error_count: 0,
            endpoint_type: NotValid,
            host_initiate_disable: false,
            max_burst_size: 0,
            max_packet_size: 0,
            dequeue_cycle_state: false,
            tr_dequeue_pointer: 0,
            average_trb_length: 0,
            max_endpoint_service_time_interval_payload_low: 0,
        },
        Endpoint {
            endpoint_state: Disabled,
            mult: 0,
            max_primary_streams: 0,
            linear_stream_array: false,
            interval: 0,
            max_endpoint_service_time_interval_payload_high: 0,
            error_count: 0,
            endpoint_type: NotValid,
            host_initiate_disable: false,
            max_burst_size: 0,
            max_packet_size: 0,
            dequeue_cycle_state: false,
            tr_dequeue_pointer: 0,
            average_trb_length: 0,
            max_endpoint_service_time_interval_payload_low: 0,
        },
        Endpoint {
            endpoint_state: Disabled,
            mult: 0,
            max_primary_streams: 0,
            linear_stream_array: false,
            interval: 0,
            max_endpoint_service_time_interval_payload_high: 0,
            error_count: 0,
            endpoint_type: NotValid,
            host_initiate_disable: false,
            max_burst_size: 0,
            max_packet_size: 0,
            dequeue_cycle_state: false,
            tr_dequeue_pointer: 0,
            average_trb_length: 0,
            max_endpoint_service_time_interval_payload_low: 0,
        },
        Endpoint {
            endpoint_state: Disabled,
            mult: 0,
            max_primary_streams: 0,
            linear_stream_array: false,
            interval: 0,
            max_endpoint_service_time_interval_payload_high: 0,
            error_count: 0,
            endpoint_type: NotValid,
            host_initiate_disable: false,
            max_burst_size: 0,
            max_packet_size: 0,
            dequeue_cycle_state: false,
            tr_dequeue_pointer: 0,
            average_trb_length: 0,
            max_endpoint_service_time_interval_payload_low: 0,
        },
        Endpoint {
            endpoint_state: Disabled,
            mult: 0,
            max_primary_streams: 0,
            linear_stream_array: false,
            interval: 0,
            max_endpoint_service_time_interval_payload_high: 0,
            error_count: 0,
            endpoint_type: NotValid,
            host_initiate_disable: false,
            max_burst_size: 0,
            max_packet_size: 0,
            dequeue_cycle_state: false,
            tr_dequeue_pointer: 0,
            average_trb_length: 0,
            max_endpoint_service_time_interval_payload_low: 0,
        },
        Endpoint {
            endpoint_state: Disabled,
            mult: 0,
            max_primary_streams: 0,
            linear_stream_array: false,
            interval: 0,
            max_endpoint_service_time_interval_payload_high: 0,
            error_count: 0,
            endpoint_type: NotValid,
            host_initiate_disable: false,
            max_burst_size: 0,
            max_packet_size: 0,
            dequeue_cycle_state: false,
            tr_dequeue_pointer: 0,
            average_trb_length: 0,
            max_endpoint_service_time_interval_payload_low: 0,
        },
        Endpoint {
            endpoint_state: Disabled,
            mult: 0,
            max_primary_streams: 0,
            linear_stream_array: false,
            interval: 0,
            max_endpoint_service_time_interval_payload_high: 0,
            error_count: 0,
            endpoint_type: NotValid,
            host_initiate_disable: false,
            max_burst_size: 0,
            max_packet_size: 0,
            dequeue_cycle_state: false,
            tr_dequeue_pointer: 0,
            average_trb_length: 0,
            max_endpoint_service_time_interval_payload_low: 0,
        },
        Endpoint {
            endpoint_state: Disabled,
            mult: 0,
            max_primary_streams: 0,
            linear_stream_array: false,
            interval: 0,
            max_endpoint_service_time_interval_payload_high: 0,
            error_count: 0,
            endpoint_type: NotValid,
            host_initiate_disable: false,
            max_burst_size: 0,
            max_packet_size: 0,
            dequeue_cycle_state: false,
            tr_dequeue_pointer: 0,
            average_trb_length: 0,
            max_endpoint_service_time_interval_payload_low: 0,
        },
        Endpoint {
            endpoint_state: Disabled,
            mult: 0,
            max_primary_streams: 0,
            linear_stream_array: false,
            interval: 0,
            max_endpoint_service_time_interval_payload_high: 0,
            error_count: 0,
            endpoint_type: NotValid,
            host_initiate_disable: false,
            max_burst_size: 0,
            max_packet_size: 0,
            dequeue_cycle_state: false,
            tr_dequeue_pointer: 0,
            average_trb_length: 0,
            max_endpoint_service_time_interval_payload_low: 0,
        },
        Endpoint {
            endpoint_state: Disabled,
            mult: 0,
            max_primary_streams: 0,
            linear_stream_array: false,
            interval: 0,
            max_endpoint_service_time_interval_payload_high: 0,
            error_count: 0,
            endpoint_type: NotValid,
            host_initiate_disable: false,
            max_burst_size: 0,
            max_packet_size: 0,
            dequeue_cycle_state: false,
            tr_dequeue_pointer: 0,
            average_trb_length: 0,
            max_endpoint_service_time_interval_payload_low: 0,
        },
        Endpoint {
            endpoint_state: Disabled,
            mult: 0,
            max_primary_streams: 0,
            linear_stream_array: false,
            interval: 0,
            max_endpoint_service_time_interval_payload_high: 0,
            error_count: 0,
            endpoint_type: NotValid,
            host_initiate_disable: false,
            max_burst_size: 0,
            max_packet_size: 0,
            dequeue_cycle_state: false,
            tr_dequeue_pointer: 0,
            average_trb_length: 0,
            max_endpoint_service_time_interval_payload_low: 0,
        },
        Endpoint {
            endpoint_state: Disabled,
            mult: 0,
            max_primary_streams: 0,
            linear_stream_array: false,
            interval: 0,
            max_endpoint_service_time_interval_payload_high: 0,
            error_count: 0,
            endpoint_type: NotValid,
            host_initiate_disable: false,
            max_burst_size: 0,
            max_packet_size: 0,
            dequeue_cycle_state: false,
            tr_dequeue_pointer: 0,
            average_trb_length: 0,
            max_endpoint_service_time_interval_payload_low: 0,
        },
        Endpoint {
            endpoint_state: Disabled,
            mult: 0,
            max_primary_streams: 0,
            linear_stream_array: false,
            interval: 0,
            max_endpoint_service_time_interval_payload_high: 0,
            error_count: 0,
            endpoint_type: NotValid,
            host_initiate_disable: false,
            max_burst_size: 0,
            max_packet_size: 0,
            dequeue_cycle_state: false,
            tr_dequeue_pointer: 0,
            average_trb_length: 0,
            max_endpoint_service_time_interval_payload_low: 0,
        },
        Endpoint {
            endpoint_state: Disabled,
            mult: 0,
            max_primary_streams: 0,
            linear_stream_array: false,
            interval: 0,
            max_endpoint_service_time_interval_payload_high: 0,
            error_count: 0,
            endpoint_type: NotValid,
            host_initiate_disable: false,
            max_burst_size: 0,
            max_packet_size: 0,
            dequeue_cycle_state: false,
            tr_dequeue_pointer: 0,
            average_trb_length: 0,
            max_endpoint_service_time_interval_payload_low: 0,
        },
        Endpoint {
            endpoint_state: Disabled,
            mult: 0,
            max_primary_streams: 0,
            linear_stream_array: false,
            interval: 0,
            max_endpoint_service_time_interval_payload_high: 0,
            error_count: 0,
            endpoint_type: NotValid,
            host_initiate_disable: false,
            max_burst_size: 0,
            max_packet_size: 0,
            dequeue_cycle_state: false,
            tr_dequeue_pointer: 0,
            average_trb_length: 0,
            max_endpoint_service_time_interval_payload_low: 0,
        },
        Endpoint {
            endpoint_state: Disabled,
            mult: 0,
            max_primary_streams: 0,
            linear_stream_array: false,
            interval: 0,
            max_endpoint_service_time_interval_payload_high: 0,
            error_count: 0,
            endpoint_type: NotValid,
            host_initiate_disable: false,
            max_burst_size: 0,
            max_packet_size: 0,
            dequeue_cycle_state: false,
            tr_dequeue_pointer: 0,
            average_trb_length: 0,
            max_endpoint_service_time_interval_payload_low: 0,
        },
        Endpoint {
            endpoint_state: Disabled,
            mult: 0,
            max_primary_streams: 0,
            linear_stream_array: false,
            interval: 0,
            max_endpoint_service_time_interval_payload_high: 0,
            error_count: 0,
            endpoint_type: NotValid,
            host_initiate_disable: false,
            max_burst_size: 0,
            max_packet_size: 0,
            dequeue_cycle_state: false,
            tr_dequeue_pointer: 0,
            average_trb_length: 0,
            max_endpoint_service_time_interval_payload_low: 0,
        },
        Endpoint {
            endpoint_state: Disabled,
            mult: 0,
            max_primary_streams: 0,
            linear_stream_array: false,
            interval: 0,
            max_endpoint_service_time_interval_payload_high: 0,
            error_count: 0,
            endpoint_type: NotValid,
            host_initiate_disable: false,
            max_burst_size: 0,
            max_packet_size: 0,
            dequeue_cycle_state: false,
            tr_dequeue_pointer: 0,
            average_trb_length: 0,
            max_endpoint_service_time_interval_payload_low: 0,
        },
        Endpoint {
            endpoint_state: Disabled,
            mult: 0,
            max_primary_streams: 0,
            linear_stream_array: false,
            interval: 0,
            max_endpoint_service_time_interval_payload_high: 0,
            error_count: 0,
            endpoint_type: NotValid,
            host_initiate_disable: false,
            max_burst_size: 0,
            max_packet_size: 0,
            dequeue_cycle_state: false,
            tr_dequeue_pointer: 0,
            average_trb_length: 0,
            max_endpoint_service_time_interval_payload_low: 0,
        },
        Endpoint {
            endpoint_state: Disabled,
            mult: 0,
            max_primary_streams: 0,
            linear_stream_array: false,
            interval: 0,
            max_endpoint_service_time_interval_payload_high: 0,
            error_count: 0,
            endpoint_type: NotValid,
            host_initiate_disable: false,
            max_burst_size: 0,
            max_packet_size: 0,
            dequeue_cycle_state: false,
            tr_dequeue_pointer: 0,
            average_trb_length: 0,
            max_endpoint_service_time_interval_payload_low: 0,
        },
        Endpoint {
            endpoint_state: Disabled,
            mult: 0,
            max_primary_streams: 0,
            linear_stream_array: false,
            interval: 0,
            max_endpoint_service_time_interval_payload_high: 0,
            error_count: 0,
            endpoint_type: NotValid,
            host_initiate_disable: false,
            max_burst_size: 0,
            max_packet_size: 0,
            dequeue_cycle_state: false,
            tr_dequeue_pointer: 0,
            average_trb_length: 0,
            max_endpoint_service_time_interval_payload_low: 0,
        },
        Endpoint {
            endpoint_state: Disabled,
            mult: 0,
            max_primary_streams: 0,
            linear_stream_array: false,
            interval: 0,
            max_endpoint_service_time_interval_payload_high: 0,
            error_count: 0,
            endpoint_type: NotValid,
            host_initiate_disable: false,
            max_burst_size: 0,
            max_packet_size: 0,
            dequeue_cycle_state: false,
            tr_dequeue_pointer: 0,
            average_trb_length: 0,
            max_endpoint_service_time_interval_payload_low: 0,
        },
        Endpoint {
            endpoint_state: Disabled,
            mult: 0,
            max_primary_streams: 0,
            linear_stream_array: false,
            interval: 0,
            max_endpoint_service_time_interval_payload_high: 0,
            error_count: 0,
            endpoint_type: NotValid,
            host_initiate_disable: false,
            max_burst_size: 0,
            max_packet_size: 0,
            dequeue_cycle_state: false,
            tr_dequeue_pointer: 0,
            average_trb_length: 0,
            max_endpoint_service_time_interval_payload_low: 0,
        },
        Endpoint {
            endpoint_state: Disabled,
            mult: 0,
            max_primary_streams: 0,
            linear_stream_array: false,
            interval: 0,
            max_endpoint_service_time_interval_payload_high: 0,
            error_count: 0,
            endpoint_type: NotValid,
            host_initiate_disable: false,
            max_burst_size: 0,
            max_packet_size: 0,
            dequeue_cycle_state: false,
            tr_dequeue_pointer: 0,
            average_trb_length: 0,
            max_endpoint_service_time_interval_payload_low: 0,
        },
        Endpoint {
            endpoint_state: Disabled,
            mult: 0,
            max_primary_streams: 0,
            linear_stream_array: false,
            interval: 0,
            max_endpoint_service_time_interval_payload_high: 0,
            error_count: 0,
            endpoint_type: NotValid,
            host_initiate_disable: false,
            max_burst_size: 0,
            max_packet_size: 0,
            dequeue_cycle_state: false,
            tr_dequeue_pointer: 0,
            average_trb_length: 0,
            max_endpoint_service_time_interval_payload_low: 0,
        },
        Endpoint {
            endpoint_state: Disabled,
            mult: 0,
            max_primary_streams: 0,
            linear_stream_array: false,
            interval: 0,
            max_endpoint_service_time_interval_payload_high: 0,
            error_count: 0,
            endpoint_type: NotValid,
            host_initiate_disable: false,
            max_burst_size: 0,
            max_packet_size: 0,
            dequeue_cycle_state: false,
            tr_dequeue_pointer: 0,
            average_trb_length: 0,
            max_endpoint_service_time_interval_payload_low: 0,
        },
        Endpoint {
            endpoint_state: Disabled,
            mult: 0,
            max_primary_streams: 0,
            linear_stream_array: false,
            interval: 0,
            max_endpoint_service_time_interval_payload_high: 0,
            error_count: 0,
            endpoint_type: NotValid,
            host_initiate_disable: false,
            max_burst_size: 0,
            max_packet_size: 0,
            dequeue_cycle_state: false,
            tr_dequeue_pointer: 0,
            average_trb_length: 0,
            max_endpoint_service_time_interval_payload_low: 0,
        },
    ],
}
[ 43.147304 0:2 driver_usb::host::usb::drivers::driver_usb_hid:151] [USB-HID DRIVER]: post idle request to control endpoint
[ 43.159542 0:2 driver_usb::host::xhci::ring:48] enqueue trb: [2593, 0, 8, 2113]
[ 43.168047 0:2 driver_usb::host::xhci::ring:48] enqueue trb: [0, 0, 0, 4129]
[ 43.176293 0:2 driver_usb::host::xhci:450] [XHCI] Post control transfer!
[ 43.184193 0:2 driver_usb::host::xhci:464] [XHCI] Wait result
[ 43.191136 0:2 driver_usb::host::xhci:470] received temp!:TransferEvent(TransferEvent { completion_code: Ok(Success), trb_pointer: 2417736160, trb_transfer_length: 0, event_data: false, endpoint_id: 1, slot_id: 1, cycle_bit: true })
[ 43.212923 0:2 driver_usb::host::xhci:475] [XHCI] Transfer @901BB9E0 got result, cycle true
[ 43.222471 0:2 driver_usb::host::usb::drivers::driver_usb_hid:160] [USB-HID DRIVER]: result: Ok(TransferEvent { completion_code: Ok(Success), trb_pointer: 2417736160, trb_transfer_length: 0, event_data: false, endpoint_id: 1, slot_id: 1, cycle_bit: true })
[ 43.246341 0:2 driver_usb::host::usb::drivers::driver_usb_hid:176] [USB-HID DRIVER]: post set protocol request
[ 43.257539 0:2 driver_usb::host::xhci::ring:48] enqueue trb: [68385, 0, 8, 2113]
[ 43.266131 0:2 driver_usb::host::xhci::ring:48] enqueue trb: [0, 0, 0, 4129]
[ 43.274377 0:2 driver_usb::host::xhci:450] [XHCI] Post control transfer!
[ 43.282276 0:2 driver_usb::host::xhci:464] [XHCI] Wait result
[ 43.289220 0:2 driver_usb::host::xhci:470] received temp!:TransferEvent(TransferEvent { completion_code: Ok(Success), trb_pointer: 2417736192, trb_transfer_length: 0, event_data: false, endpoint_id: 1, slot_id: 1, cycle_bit: true })
[ 43.311007 0:2 driver_usb::host::xhci:475] [XHCI] Transfer @901BBA00 got result, cycle true
[ 43.320555 0:2 driver_usb::host::usb::drivers::driver_usb_hid:187] [USB-HID DRIVER]: result: TransferEvent { completion_code: Ok(Success), trb_pointer: 2417736192, trb_transfer_length: 0, event_data: false, endpoint_id: 1, slot_id: 1, cycle_bit: true }
[ 43.844078 0:2 driver_usb::dma:125] allocated data:0x901be180
[ 43.848154 0:2 driver_usb::host::usb::drivers::driver_usb_hid:210] [USB-HID DRIVER]: post report request
[ 43.858828 0:2 driver_usb::host::xhci::ring:48] enqueue trb: [570427009, 4063232, 8, 198721]
[ 43.868461 0:2 driver_usb::host::xhci::ring:48] enqueue trb: [2417746304, 0, 62, 68609]
[ 43.877662 0:2 driver_usb::host::xhci::ring:48] enqueue trb: [0, 0, 0, 4129]
[ 43.885909 0:2 driver_usb::host::xhci:396] [XHCI] Post control transfer!
[ 43.893807 0:2 driver_usb::host::xhci:406] [XHCI] Wait result
[ 43.900751 0:2 driver_usb::host::xhci:464] [XHCI] Wait result
[ 43.907696 0:2 driver_usb::host::xhci:470] received temp!:TransferEvent(TransferEvent { completion_code: Ok(Success), trb_pointer: 2417736240, trb_transfer_length: 0, event_data: false, endpoint_id: 1, slot_id: 1, cycle_bit: true })
[ 43.929483 0:2 driver_usb::host::xhci:475] [XHCI] Transfer @901BBA30 got result, cycle true
[ 43.939030 0:2 driver_usb::host::usb::drivers::driver_usb_hid:221] [USB-HID DRIVER]: result: TransferEvent { completion_code: Ok(Success), trb_pointer: 2417736240, trb_transfer_length: 0, event_data: false, endpoint_id: 1, slot_id: 1, cycle_bit: true }
[ 43.962558 0:2 driver_usb::host::usb::drivers::driver_usb_hid:294] 05 01 09 02 
[ 43.971061 0:2 driver_usb::host::usb::drivers::driver_usb_hid:294] a1 01 09 01 
[ 43.979568 0:2 driver_usb::host::usb::drivers::driver_usb_hid:294] a1 00 05 09 
[ 43.988074 0:2 driver_usb::host::usb::drivers::driver_usb_hid:294] 19 01 29 03 
[ 43.996580 0:2 driver_usb::host::usb::drivers::driver_usb_hid:294] 15 00 25 01 
[ 44.005087 0:2 driver_usb::host::usb::drivers::driver_usb_hid:294] 95 03 75 01 
[ 44.013593 0:2 driver_usb::host::usb::drivers::driver_usb_hid:294] 81 02 95 05 
[ 44.022100 0:2 driver_usb::host::usb::drivers::driver_usb_hid:294] 75 01 81 03 
[ 44.030606 0:2 driver_usb::host::usb::drivers::driver_usb_hid:294] 05 01 09 30 
[ 44.039112 0:2 driver_usb::host::usb::drivers::driver_usb_hid:294] 09 31 15 81 
[ 44.047619 0:2 driver_usb::host::usb::drivers::driver_usb_hid:294] 25 7f 75 08 
[ 44.056125 0:2 driver_usb::host::usb::drivers::driver_usb_hid:294] 95 02 81 06 
[ 44.064632 0:2 driver_usb::host::usb::drivers::driver_usb_hid:294] 09 38 15 81 
[ 44.073138 0:2 driver_usb::host::usb::drivers::driver_usb_hid:294] 25 7f 75 08 
[ 44.081644 0:2 driver_usb::host::usb::drivers::driver_usb_hid:294] 95 01 81 06 
[ 44.090150 0:2 driver_usb::host::usb::drivers::driver_usb_hid:299] c0 c0 
[ 45.098137 0:2 driver_usb::dma:125] allocated data:0x901be160
[ 45.102209 0:2 driver_usb::host::usb::drivers::driver_usb_hid:236] [USB-HID DRIVER]: post IN Transfer report request
[ 45.113928 0:2 driver_usb::host::xhci::ring:48] enqueue trb: [2417746272, 0, 4, 1061]
[ 45.122954 0:2 driver_usb::host::usb::drivers::driver_usb_hid:267] [USB-HID DRIVER] Post control transfer! at slot_id:1,dci:3
[ 45.135454 0:2 driver_usb::host::xhci:464] [XHCI] Wait result
[ 45.142398 0:2 driver_usb::host::xhci:470] received temp!:TransferEvent(TransferEvent { completion_code: Ok(UsbTransactionError), trb_pointer: 2417737728, trb_transfer_length: 4, event_data: false, endpoint_id: 3, slot_id: 1, cycle_bit: true })
[ 45.165226 0:2 driver_usb::host::xhci:475] [XHCI] Transfer @901BC000 got result, cycle true
[ 45.174774 0:2 driver_usb::host::usb::drivers::driver_usb_hid:281] [USB-HID DRIVER]: result: Ok(TransferEvent { completion_code: Ok(UsbTransactionError), trb_pointer: 2417737728, trb_transfer_length: 4, event_data: false, endpoint_id: 3, slot_id: 1, cycle_bit: true })
[ 45.199688 0:2 driver_usb::host::usb::drivers::driver_usb_hid:294] 00 00 00 00 
[ 45.208249 0:2 axtask::run_queue:86] task exit: Task(2, "main"), exit_code=0
[ 45.216439 0:2 axhal::platform::aarch64_phytium_pi::misc:22] Shutting down...
```

端点启用后，发送中断传输请求，但是出现了传输错误UsbTransactionError

