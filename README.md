# USB-C PD (Power Delivery) Example

This example is based on a copy of the following in-tree zephyr example, with overlays for the [OnSemi FUSB307](https://www.onsemi.com/products/interfaces/usb-type-c/fusb307b) TCPC (Type-C Port Controller)
https://github.com/zephyrproject-rtos/zephyr/tree/main/samples/subsys/usb_c/sink

Please note, consistent with the above example the build_rdo() will build a Request Data Object and select object position 1 (5V). It doesn't build the RDO from the Source Capabilities stored in the dpm_data object.

## Building

The example can be built using:

```
west build -b nrf52840dk/nrf52840
west flash
```

## Example Output

Output when connected to [UGREEN Model CD244 65W GaN Fast Charger](https://www.ugreen.com/products/65w-3-ports-gan-fast-charger?variant=39915659591742):

```
[00:00:00.251,556] <err> usbc_stack: Couldn't disable vconn: -5
[00:00:00.251,586] <inf> usbc_stack: ErrorRecovery
[00:00:00.251,617] <inf> usbc_stack: Disabled
[00:00:00.251,617] <inf> usbc_stack: PE_SUSPEND
[00:00:00.251,617] <inf> usbc_stack: PRL_HR_SUSPEND
[00:00:00.251,647] <inf> usbc_stack: PRL_TX_SUSPEND
*** Booting Zephyr OS build v4.2.0-1300-g850050b1b61d ***
[00:00:00.251,770] <err> usbc_stack: TCPC initialization failed: -11
[00:00:00.256,683] <inf> tcpc_fusb307: Initializing FUSB307 chip: fusb307_tcpc0@50
[00:00:00.256,835] <err> usbc_stack: TCPC initialization failed: -11
[00:00:00.259,033] <inf> tcpc_fusb307: Initialized chip is: 0779:0133:0202
[00:00:00.261,993] <inf> tcpc_fusb307: FUSB307 TCPC initialized
[00:00:00.262,023] <inf> usbc_stack: ErrorRecovery
[00:00:00.505,798] <inf> usbc_stack: Unattached.SNK
[00:00:00.507,995] <inf> usbc_stack: AttachWait.SNK
[00:00:00.712,524] <inf> usbc_stack: Attached.SNK
[00:00:00.716,674] <inf> usbc_stack: PE_SNK_Startup
[00:00:00.716,674] <inf> usbc_stack: PRL_INIT
[00:00:00.716,705] <inf> usbc_stack: PRL_HR_Wait_for_Request
[00:00:00.716,705] <inf> usbc_stack: PRL_Tx_PHY_Layer_Reset
[00:00:00.717,132] <inf> usbc_stack: PRL_Tx_Wait_for_Message_Request
[00:00:00.718,994] <inf> usbc_stack: PE_SNK_Discovery
[00:00:00.721,252] <inf> usbc_stack: PE_SNK_Wait_For_Capabilities
[00:00:00.739,746] <inf> main: PWR 3A0
[00:00:01.344,482] <inf> usbc_stack: PE_SNK_Hard_Reset
[00:00:01.344,512] <inf> usbc_stack: PRL_HR_Reset_Layer
[00:00:01.344,940] <inf> usbc_stack: PRL_Tx_PHY_Layer_Reset
[00:00:01.345,367] <inf> usbc_stack: PRL_Tx_Wait_for_Message_Request
[00:00:01.345,794] <inf> usbc_stack: PRL_HR_Wait_for_PHY_Hard_Reset_Complete
[00:00:01.352,905] <inf> usbc_stack: PRL_HR_Wait_For_PE_Hard_Reset_Complete
[00:00:01.358,703] <inf> usbc_stack: PE_SNK_Transition_to_default
[00:00:01.359,405] <inf> usbc_stack: PE_SNK_Startup
[00:00:01.359,436] <inf> usbc_stack: PRL_INIT
[00:00:01.359,436] <inf> usbc_stack: PRL_HR_Wait_for_Request
[00:00:01.359,466] <inf> usbc_stack: PRL_Tx_PHY_Layer_Reset
[00:00:01.359,863] <inf> usbc_stack: PRL_Tx_Wait_for_Message_Request
[00:00:01.360,565] <inf> usbc_stack: PE_SNK_Discovery
[00:00:01.362,854] <inf> usbc_stack: PE_SNK_Wait_For_Capabilities
[00:00:01.385,009] <inf> usbc_stack: PRL_TX_SUSPEND
[00:00:01.385,009] <inf> usbc_stack: PRL_HR_SUSPEND
[00:00:01.385,040] <inf> usbc_stack: PE_SUSPEND
[00:00:01.386,016] <inf> usbc_stack: Unattached.SNK
[00:00:01.388,519] <inf> usbc_stack: AttachWait.SNK
[00:00:02.302,124] <inf> usbc_stack: Attached.SNK
[00:00:02.308,044] <inf> usbc_stack: PE_SNK_Startup
[00:00:02.308,044] <inf> usbc_stack: PRL_INIT
[00:00:02.308,074] <inf> usbc_stack: PRL_HR_Wait_for_Request
[00:00:02.308,074] <inf> usbc_stack: PRL_Tx_PHY_Layer_Reset
[00:00:02.308,502] <inf> usbc_stack: PRL_Tx_Wait_for_Message_Request
[00:00:02.310,363] <inf> usbc_stack: PE_SNK_Discovery
[00:00:02.312,622] <inf> usbc_stack: PE_SNK_Wait_For_Capabilities
[00:00:02.331,207] <inf> main: PWR 3A0
[00:00:02.427,642] <inf> usbc_stack: RECV 61a1/6
[00:00:02.427,673] <inf> usbc_stack:    [0]0801912c
[00:00:02.427,673] <inf> usbc_stack:    [1]0002d12c
[00:00:02.427,673] <inf> usbc_stack:    [2]0003c12c
[00:00:02.427,673] <inf> usbc_stack:    [3]0004b12c
[00:00:02.427,703] <inf> usbc_stack:    [4]0006412c
[00:00:02.427,703] <inf> usbc_stack:    [5]c8dc213c
[00:00:02.428,802] <inf> usbc_stack: PE_SNK_Evaluate_Capability
[00:00:02.428,802] <inf> usbc_stack: PE_SNK_Select_Capability
[00:00:02.430,786] <inf> usbc_stack: PRL_Tx_Wait_for_PHY_response
[00:00:02.432,861] <inf> usbc_stack: PRL_Tx_Wait_for_Message_Request
[00:00:02.437,622] <inf> usbc_stack: RECV 03a3/0
[00:00:02.438,751] <inf> usbc_stack: PE_SNK_Transition_Sink
[00:00:02.565,734] <inf> usbc_stack: RECV 05a6/0
[00:00:02.566,894] <inf> usbc_stack: PE_SNK_Ready
[00:00:03.251,953] <inf> main: Source Caps:
[00:00:03.251,953] <inf> main: PDO 0:
[00:00:03.251,983] <inf> main:  Type:              FIXED
[00:00:03.251,983] <inf> main:  Current:           3000
[00:00:03.251,983] <inf> main:  Voltage:           5000
[00:00:03.252,014] <inf> main:  Peak Current:      0
[00:00:03.252,014] <inf> main:  Uchunked Support:  0
[00:00:03.252,014] <inf> main:  Dual Role Data:    0
[00:00:03.252,044] <inf> main:  USB Comms:         0
[00:00:03.252,044] <inf> main:  Unconstrained Pwr: 1
[00:00:03.252,044] <inf> main:  USB Suspend:       0
[00:00:03.252,075] <inf> main:  Dual Role Power:   0
[00:00:03.302,154] <inf> main: PDO 1:
[00:00:03.302,154] <inf> main:  Type:              FIXED
[00:00:03.302,154] <inf> main:  Current:           3000
[00:00:03.302,185] <inf> main:  Voltage:           9000
[00:00:03.302,185] <inf> main:  Peak Current:      0
[00:00:03.302,185] <inf> main:  Uchunked Support:  0
[00:00:03.302,215] <inf> main:  Dual Role Data:    0
[00:00:03.302,215] <inf> main:  USB Comms:         0
[00:00:03.302,215] <inf> main:  Unconstrained Pwr: 0
[00:00:03.302,215] <inf> main:  USB Suspend:       0
[00:00:03.302,246] <inf> main:  Dual Role Power:   0
[00:00:03.352,386] <inf> main: PDO 2:
[00:00:03.352,386] <inf> main:  Type:              FIXED
[00:00:03.352,386] <inf> main:  Current:           3000
[00:00:03.352,386] <inf> main:  Voltage:           12000
[00:00:03.352,416] <inf> main:  Peak Current:      0
[00:00:03.352,416] <inf> main:  Uchunked Support:  0
[00:00:03.352,416] <inf> main:  Dual Role Data:    0
[00:00:03.352,447] <inf> main:  USB Comms:         0
[00:00:03.352,447] <inf> main:  Unconstrained Pwr: 0
[00:00:03.352,447] <inf> main:  USB Suspend:       0
[00:00:03.352,447] <inf> main:  Dual Role Power:   0
[00:00:03.402,587] <inf> main: PDO 3:
[00:00:03.402,587] <inf> main:  Type:              FIXED
[00:00:03.402,587] <inf> main:  Current:           3000
[00:00:03.402,618] <inf> main:  Voltage:           15000
[00:00:03.402,618] <inf> main:  Peak Current:      0
[00:00:03.402,618] <inf> main:  Uchunked Support:  0
[00:00:03.402,648] <inf> main:  Dual Role Data:    0
[00:00:03.402,648] <inf> main:  USB Comms:         0
[00:00:03.402,648] <inf> main:  Unconstrained Pwr: 0
[00:00:03.402,679] <inf> main:  USB Suspend:       0
[00:00:03.402,679] <inf> main:  Dual Role Power:   0
[00:00:03.452,758] <inf> main: PDO 4:
[00:00:03.452,758] <inf> main:  Type:              FIXED
[00:00:03.452,758] <inf> main:  Current:           3000
[00:00:03.452,789] <inf> main:  Voltage:           20000
[00:00:03.452,789] <inf> main:  Peak Current:      0
[00:00:03.452,789] <inf> main:  Uchunked Support:  0
[00:00:03.452,819] <inf> main:  Dual Role Data:    0
[00:00:03.452,819] <inf> main:  USB Comms:         0
[00:00:03.452,819] <inf> main:  Unconstrained Pwr: 0
[00:00:03.452,819] <inf> main:  USB Suspend:       0
[00:00:03.452,850] <inf> main:  Dual Role Power:   0
[00:00:03.502,929] <inf> main: PDO 5:
[00:00:03.502,929] <inf> main:  Type:              AUGMENTED
[00:00:03.502,929] <inf> main:  Min Voltage:       3300
[00:00:03.502,960] <inf> main:  Max Voltage:       11000
[00:00:03.502,960] <inf> main:  Max Current:       3000
[00:00:03.502,960] <inf> main:  PPS Power Limited: 1
```
