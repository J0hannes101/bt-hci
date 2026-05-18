# Missing LE Commands — bt-hci

Spec: Bluetooth Core Specification v6.3, Vol 4, Part E

---

## LE Controller Commands (`src/cmd/le.rs`)

Spec: [§7.8](https://www.bluetooth.com/wp-content/uploads/Files/Specification/HTML/Core_v6.3/out/en/host-controller-interface/host-controller-interface-functional-specification.html#UUID-0f07d2b9-81e3-6508-ee08-8c808e468fed)

### Legacy parity / v2 variants

| OCF | Name | Spec § |
|-----|------|--------|
| 0x0004 | LeReadBufferSize [v2] | §7.8.2 |
| 0x00A4 | LeSetEventMask [v2] | §7.8.1 |

### Resolving list / privacy

| OCF | Name | Spec § |
|-----|------|--------|
| 0x002B | LeReadPeerResolvableAddress | §7.8.42 |
| 0x002C | LeReadLocalResolvableAddress | §7.8.43 |

### DH Key / P-256

| OCF | Name | Spec § |
|-----|------|--------|
| 0x0025 | LeReadLocalP256PublicKey | §7.8.36 |
| 0x0026 | LeGenerateDhKey [v1] | §7.8.37 |
| 0x005E | LeGenerateDhKey [v2] | §7.8.37 |

### Test commands

| OCF | Name | Spec § |
|-----|------|--------|
| 0x0033 | LeReceiverTest [v2] | §7.8.28 |
| 0x0034 | LeTransmitterTest [v2] | §7.8.29 |
| 0x004F | LeReceiverTest [v3] | §7.8.28 |
| 0x0050 | LeTransmitterTest [v3] | §7.8.29 |
| 0x007B | LeTransmitterTest [v4] | §7.8.29 |

### Isochronous (CIS / BIG)

| OCF | Name | Spec § |
|-----|------|--------|
| 0x0060 | LeReadBufferSize [v2] (ISO) | §7.8.2 |
| 0x0061 | LeReadIsoTxSync | §7.8.96 |
| 0x0062 | LeSetCigParameters | §7.8.97 |
| 0x0063 | LeSetCigParametersTest | §7.8.98 |
| 0x0064 | LeCreateCis | §7.8.99 |
| 0x0065 | LeRemoveCig | §7.8.100 |
| 0x0066 | LeAcceptCisRequest | §7.8.101 |
| 0x0067 | LeRejectCisRequest | §7.8.102 |
| 0x0068 | LeCreateBig | §7.8.103 |
| 0x0069 | LeCreateBigTest | §7.8.104 |
| 0x006A | LeTerminateBig | §7.8.105 |
| 0x006B | LeBigCreateSync | §7.8.106 |
| 0x006C | LeBigTerminateSync | §7.8.107 |
| 0x006E | LeSetupIsoDataPath | §7.8.109 |
| 0x006F | LeRemoveIsoDataPath | §7.8.110 |
| 0x0070 | LeIsoTransmitTest | §7.8.111 |
| 0x0071 | LeIsoReceiveTest | §7.8.112 |
| 0x0072 | LeIsoReadTestCounters | §7.8.113 |
| 0x0073 | LeIsoTestEnd | §7.8.114 |
| 0x0075 | LeReadIsoLinkQuality | §7.8.116 |

### Decision-based advertising

| OCF | Name | Spec § |
|-----|------|--------|
| 0x0080 | LeSetDecisionData | §7.8.144 |
| 0x0081 | LeSetDecisionInstructions | §7.8.145 |

### Monitored advertisers

| OCF | Name | Spec § |
|-----|------|--------|
| 0x0098 | LeAddDeviceToMonitoredAdvertisersList | §7.8.146 |
| 0x0099 | LeRemoveDeviceFromMonitoredAdvertisersList | §7.8.147 |
| 0x009A | LeClearMonitoredAdvertisersList | §7.8.148 |
| 0x009B | LeReadMonitoredAdvertisersListSize | §7.8.150 |
| 0x009C | LeEnableMonitoringAdvertisers | §7.8.149 |

### Channel Sounding (CS)

| OCF | Name | Spec § |
|-----|------|--------|
| 0x0089 | LeCsReadLocalSupportedCapabilities [v1] | §7.8.130 |
| 0x008A | LeCsReadRemoteSupportedCapabilities | §7.8.131 |
| 0x008B | LeCsWriteCachedRemoteSupportedCapabilities [v1] | §7.8.132 |
| 0x008C | LeCsSecurityEnable | §7.8.133 |
| 0x008D | LeCsSetDefaultSettings | §7.8.134 |
| 0x008E | LeCsReadRemoteFaeTable | §7.8.135 |
| 0x008F | LeCsWriteCachedRemoteFaeTable | §7.8.136 |
| 0x0090 | LeCsCreateConfig | §7.8.137 |
| 0x0091 | LeCsRemoveConfig | §7.8.138 |
| 0x0092 | LeCsSetChannelClassification | §7.8.139 |
| 0x0093 | LeCsSetProcedureParameters | §7.8.140 |
| 0x0094 | LeCsProcedureEnable | §7.8.141 |
| 0x0095 | LeCsTest | §7.8.142 |
| 0x0096 | LeCsTestEnd | §7.8.143 |
| 0x00A5 | LeCsReadLocalSupportedCapabilities [v2] | §7.8.130 |
| 0x00A6 | LeCsWriteCachedRemoteSupportedCapabilities [v2] | §7.8.132 |
| 0x00A7 | LeCsSetSecurityRequirements | §7.8.157 |
| 0x00A8 | LeCsSetDefaultSecurityRequirements | §7.8.158 |

### Other missing

| OCF | Name | Spec § |
|-----|------|--------|
| 0x005F | LeModifySleepClockAccuracy | §7.8.94 |
| 0x0087 | LeReadAllLocalSupportedFeatures | §7.8.128 |
| 0x0088 | LeReadAllRemoteFeatures | §7.8.129 |
| 0x009E | LeSetResolvablePrivateAddrTimeout [v2] | §7.8.45 |
| 0x009F | LeEnableUtpOtaMode | §7.8.152 |
| 0x00A0 | LeUtpSend | §7.8.153 |

---

## Missing LE Meta Events (`src/event/le.rs`)

Spec: §7.7.65

| Subevent Code | Name |
|---------------|------|
| 0x26 | LePeriodicAdvertisingSubeventDataRequest |
| 0x27 | LePeriodicAdvertisingResponseReport |
| 0x28 | LeEnhancedConnectionComplete [v2] |
| 0x29 | LeCisEstablished [v2] |
| 0x2A | LeReadAllRemoteFeaturesComplete |
| 0x2B | LeCsReadRemoteSupportedCapabilitiesComplete [v1] |
| 0x2C | LeCsReadRemoteFaeTableComplete |
| 0x2D | LeCsSecurityEnableComplete |
| 0x2E | LeCsConfigComplete |
| 0x2F | LeCsProcedureEnableComplete |
| 0x30 | LeCsSubeventResult |
| 0x31 | LeCsSubeventResultContinue |
| 0x32 | LeCsTestEndComplete |
| 0x33 | LeMonitoredAdvertisersReport |
| 0x35 | LeUtpReceive |
| 0x37 | LeCsReadRemoteSupportedCapabilitiesComplete [v2] |
