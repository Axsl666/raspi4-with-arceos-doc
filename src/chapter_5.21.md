# USB最新进展

可以读取到设备描述符
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
   - 描述符的长度为18字节，这是USB设备描述符的标准长度。
2. **descriptor_type: 1**
   - 描述符类型为1，表示这是一个设备描述符（Device Descriptor）。
3. **cd_usb: 800**
   - USB协议版本，0x800表示USB 2.0版本。
4. **class: 0**
   - 设备类代码，0表示该设备由其接口描述符指定设备类。
5. **subclass: 0**
   - 设备子类代码，0表示无特定子类。
6. **protocol: 0**
   - 设备协议代码，0表示无特定协议。
7. **max_packet_size0: 9**
   - 端点0的最大包大小为9字节。
8. **vendor: 2385**
   - 供应商ID，2385是该设备制造商的唯一标识符。
9. **product_id: 5734**
   - 产品ID，5734是该设备的唯一标识符。
10. **device: 1**
    - 设备版本号，表示设备的版本信息。
11. **manufacture: 1**
    - 制造商字符串描述符的索引，值为1。
12. **product: 2**
    - 产品字符串描述符的索引，值为2。
13. **serial_number: 3**
    - 序列号字符串描述符的索引，值为3。
14. **num_configurations: 1**
    - 设备支持的配置数，值为1表示该设备有1个配置。

### 配置描述符 (Configuration Descriptor)

1. **length: 9**
   * 描述符的长度为9字节。

2. **ty: 2**
   * 描述符类型为2，表示这是一个配置描述符。

3. **total_length: 44**
   * 该配置所包含的所有描述符的总长度为44字节。

4. **num_interfaces: 1**
   * 该配置包含1个接口。

5. **config_val: 1**
   * 该配置的值为1，用于设置该配置。

6. **config_string: 0**
   * 配置字符串描述符的索引，值为0表示没有字符串描述符。

7. **attributes: 128**
   * 配置的属性，128表示总线供电。

8. **max_power: 37**
   * 设备所需的最大功率，单位为2mA，所以这里是74mA。

### 接口描述符 (Interface Descriptor)：

1. **len: 9**
   * 描述符的长度为9字节。

2. **descriptor_type: 4**
   * 描述符类型为4，表示这是一个接口描述符。

3. **interface_number: 0**
   * 接口编号为0。

4. **alternate_setting: 0**
   * 备用设置编号为0。

5. **num_endpoints: 2**
   * 该接口有2个端点（不包括端点0）。

6. **interface_class: 8**
   * 接口类代码为8，表示该接口属于大容量存储类。

7. **interface_subclass: 6**
   * 接口子类代码为6，表示SCSI传输命令集。

8. **interface_protocol: 80**
   * 接口协议代码为80，表示Bulk-Only传输。

9. **interface: 0**
   * 接口字符串描述符的索引，值为0表示没有字符串描述符。

### 端点描述符 (Endpoint Descriptor)：

1. **第一个端点描述符**
   - len: 7
     - 描述符的长度为7字节。
   - descriptor_type: 5
     - 描述符类型为5，表示这是一个端点描述符。
   - endpoint_address: 129
     - 端点地址为129（0x81），表示这是一个IN方向的端点，端点号为1。
   - attributes: 2
     - 端点属性为2，表示这是一个批量传输端点。
   - max_packet_size: 1024
     - 端点的最大包大小为1024字节。
   - interval: 0
     - 轮询间隔为0，表示不适用于批量传输端点。
2. **第二个端点描述符**
   - len: 7
     - 描述符的长度为7字节。
   - descriptor_type: 5
     - 描述符类型为5，表示这是一个端点描述符。
   - endpoint_address: 2
     - 端点地址为2，表示这是一个OUT方向的端点，端点号为2。
   - attributes: 2
     - 端点属性为2，表示这是一个批量传输端点。
   - max_packet_size: 1024
     - 端点的最大包大小为1024字节。
   - interval: 0
     - 轮询间隔为0，表示不适用于批量传输端点。
