# Missing HCI Commands — bt-hci

Spec: Bluetooth Core Specification v6.3

---

## OGF 0x02 — Link Policy
No file exists. Entire OGF group missing.

---

## OGF 0x03 — Controller & Baseband (`src/cmd/controller_baseband.rs`)

Spec: [Vol 4, Part E, §7.3](https://www.bluetooth.com/wp-content/uploads/Files/Specification/HTML/Core_v6.3/out/en/host-controller-interface/host-controller-interface-functional-specification.html#UUID-5ced811b-a6ce-701a-16b2-70f2d9795c05)

| OCF | Name | Spec § |
|-----|------|--------|
| 0x0005 | SetEventFilter | §7.3.3 |
| 0x0008 | Flush | §7.3.4 |
| 0x0009 | ReadPinType | §7.3.5 |
| 0x000A | WritePinType | §7.3.6 |
| 0x0011 | WriteStoredLinkKey | §7.3.9 |
| 0x0012 | DeleteStoredLinkKey | §7.3.10 |
| 0x0013 | WriteLocalName | §7.3.11 |
| 0x0014 | ReadLocalName | §7.3.12 |
| 0x0015 | ReadConnectionAcceptTimeout | §7.3.13 |
| 0x0016 | WriteConnectionAcceptTimeout | §7.3.14 |
| 0x0017 | ReadPageTimeout | §7.3.15 |
| 0x0018 | WritePageTimeout | §7.3.16 |
| 0x0019 | ReadScanEnable | §7.3.17 |
| 0x001A | WriteScanEnable | §7.3.18 |
| 0x001B | ReadPageScanActivity | §7.3.19 |
| 0x001C | WritePageScanActivity | §7.3.20 |
| 0x001D | ReadInquiryScanActivity | §7.3.21 |
| 0x001E | WriteInquiryScanActivity | §7.3.22 |
| 0x001F | ReadAuthenticationEnable | §7.3.23 |
| 0x0020 | WriteAuthenticationEnable | §7.3.24 |
| 0x0023 | ReadClassOfDevice | §7.3.25 |
| 0x0024 | WriteClassOfDevice | §7.3.26 |
| 0x0025 | ReadVoiceSetting | §7.3.27 |
| 0x0026 | WriteVoiceSetting | §7.3.28 |
| 0x0027 | ReadAutomaticFlushTimeout | §7.3.29 |
| 0x0028 | WriteAutomaticFlushTimeout | §7.3.30 |
| 0x0029 | ReadNumBroadcastRetransmissions | §7.3.31 |
| 0x002A | WriteNumBroadcastRetransmissions | §7.3.32 |
| 0x002B | ReadHoldModeActivity | §7.3.33 |
| 0x002C | WriteHoldModeActivity | §7.3.34 |
| 0x002E | ReadSynchronousFlowControlEnable | §7.3.36 |
| 0x002F | WriteSynchronousFlowControlEnable | §7.3.37 |
| 0x0036 | ReadLinkSupervisionTimeout | §7.3.41 |
| 0x0037 | WriteLinkSupervisionTimeout | §7.3.42 |
| 0x0038 | ReadNumberOfSupportedIAC | §7.3.43 |
| 0x0039 | ReadCurrentIacLap | §7.3.44 |
| 0x003A | WriteCurrentIacLap | §7.3.45 |
| 0x003F | SetAfhHostChannelClassification | §7.3.46 |
| 0x0042 | ReadInquiryScanType | §7.3.47 |
| 0x0043 | WriteInquiryScanType | §7.3.48 |
| 0x0044 | ReadInquiryMode | §7.3.49 |
| 0x0045 | WriteInquiryMode | §7.3.50 |
| 0x0046 | ReadPageScanType | §7.3.51 |
| 0x0047 | WritePageScanType | §7.3.52 |
| 0x0048 | ReadAfhChannelAssessmentMode | §7.3.53 |
| 0x0049 | WriteAfhChannelAssessmentMode | §7.3.54 |
| 0x0051 | ReadExtendedInquiryResponse | §7.3.55 |
| 0x0052 | WriteExtendedInquiryResponse | §7.3.56 |
| 0x0053 | RefreshEncryptionKey | §7.3.57 |
| 0x0055 | ReadSimplePairingMode | §7.3.58 |
| 0x0056 | WriteSimplePairingMode | §7.3.59 |
| 0x0057 | ReadLocalOobData | §7.3.60 |
| 0x0058 | ReadInquiryResponseTransmitPowerLevel | §7.3.61 |
| 0x0059 | WriteInquiryTransmitPowerLevel | §7.3.62 |
| 0x005A | ReadDefaultErroneousDataReporting | §7.3.64 |
| 0x005B | WriteDefaultErroneousDataReporting | §7.3.65 |
| 0x005F | EnhancedFlush | §7.3.66 |
| 0x0060 | SendKeypressNotification | §7.3.63 |
| 0x0066 | ReadFlowControlMode | §7.3.72 |
| 0x0067 | WriteFlowControlMode | §7.3.73 |
| 0x0068 | ReadEnhancedTransmitPowerLevel | §7.3.74 |
| 0x006C | ReadLeHostSupport | §7.3.78 |
| 0x006D | WriteLeHostSupport | §7.3.79 |
| 0x006E | SetMwsChannelParameters | §7.3.80 |
| 0x006F | SetExternalFrameConfiguration | §7.3.81 |
| 0x0070 | SetMwsSignaling | §7.3.82 |
| 0x0071 | SetMwsTransportLayer | §7.3.83 |
| 0x0072 | SetMwsScanFrequencyTable | §7.3.84 |
| 0x0073 | SetMwsPatternConfiguration | §7.3.85 |
| 0x0074 | SetReservedLtAddr | §7.3.86 |
| 0x0075 | DeleteReservedLtAddr | §7.3.87 |
| 0x0076 | SetConnectionlessPeripheralBroadcastData | §7.3.88 |
| 0x0077 | ReadSynchronizationTrainParameters | §7.3.89 |
| 0x0078 | WriteSynchronizationTrainParameters | §7.3.90 |
| 0x0079 | ReadSecureConnectionsHostSupport | §7.3.91 |
| 0x007A | WriteSecureConnectionsHostSupport | §7.3.92 |
| 0x007D | ReadLocalOobExtendedData | §7.3.95 |
| 0x007E | ReadExtendedPageTimeout | §7.3.96 |
| 0x007F | WriteExtendedPageTimeout | §7.3.97 |
| 0x0080 | ReadExtendedInquiryLength | §7.3.98 |
| 0x0081 | WriteExtendedInquiryLength | §7.3.99 |
| 0x0082 | SetEcosystemBaseInterval | §7.3.100 |
| 0x0083 | ConfigureDataPath | §7.3.101 |
| 0x0084 | SetMinEncryptionKeySize | §7.3.102 |

---

## OGF 0x04 — Informational Parameters (`src/cmd/info.rs`)

Spec: [Vol 4, Part E, §7.4](https://www.bluetooth.com/wp-content/uploads/Files/Specification/HTML/Core_v6.3/out/en/host-controller-interface/host-controller-interface-functional-specification.html#UUID-42372304-c9ef-dcab-6905-4e5b64703d45)

| OCF | Name | Spec § |
|-----|------|--------|
| 0x0005 | ReadBufferSize | §7.4.5 |
| 0x000A | ReadDataBlockSize | §7.4.7 |
| 0x000B | ReadLocalSupportedCodecs [v1] | §7.4.8 |
| 0x000C | ReadLocalSimplePairingOptions | §7.4.9 |
| 0x000D | ReadLocalSupportedCodecs [v2] | §7.4.8 |
| 0x000E | ReadLocalSupportedCodecCapabilities | §7.4.10 |
| 0x000F | ReadLocalSupportedControllerDelay | §7.4.11 |

---

## OGF 0x05 — Status Parameters (`src/cmd/status.rs`)

Spec: [Vol 4, Part E, §7.5](https://www.bluetooth.com/wp-content/uploads/Files/Specification/HTML/Core_v6.3/out/en/host-controller-interface/host-controller-interface-functional-specification.html#UUID-40e8a930-65b3-c409-007e-388fd48e1041)

| OCF | Name | Spec § |
|-----|------|--------|
| 0x0001 | ReadFailedContactCounter | §7.5.1 |
| 0x0002 | ResetFailedContactCounter | §7.5.2 |
| 0x0003 | ReadLinkQuality | §7.5.3 |
| 0x0006 | ReadAfhChannelMap | §7.5.5 |
| 0x0007 | ReadClock | §7.5.6 |
| 0x0008 | ReadEncryptionKeySize | §7.5.7 |
| 0x000C | GetMwsTransportLayerConfiguration | §7.5.11 |
| 0x000D | SetTriggeredClockCapture | §7.5.12 |

---

## OGF 0x06 — Testing Commands

Spec: [Vol 4, Part E, §7.6](https://www.bluetooth.com/wp-content/uploads/Files/Specification/HTML/Core_v6.3/out/en/host-controller-interface/host-controller-interface-functional-specification.html#UUID-ec2ddbf2-ae4c-ec45-7a06-94f8b3327220)

| OCF | Name | Spec § |
|-----|------|--------|
| 0x0001 | ReadLoopbackMode | §7.6.1 |
| 0x0002 | WriteLoopbackMode | §7.6.2 |
| 0x0003 | EnableDeviceUnderTestMode | §7.6.3 |
| 0x0004 | WriteSimplePairingDebugMode | §7.6.4 |
| 0x000A | WriteSecureConnectionsTestMode | §7.6.8 |

---

## OGF 0x08 — LE Controller (`src/cmd/le.rs`)

Spec: [Vol 4, Part E, §7.8](https://www.bluetooth.com/wp-content/uploads/Files/Specification/HTML/Core_v6.3/out/en/host-controller-interface/host-controller-interface-functional-specification.html#UUID-0f07d2b9-81e3-6508-ee08-8c808e468fed)

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

Spec: [Vol 4, Part E, §7.7.65](https://www.bluetooth.com/wp-content/uploads/Files/Specification/HTML/Core_v6.3/out/en/host-controller-interface/host-controller-interface-functional-specification.html)

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
