# bt-hci codebase overview

Crate: `bt-hci` (v0.9.0) — Rust `no_std` data types, traits, and parsers for Bluetooth HCI.
Repo: https://github.com/embassy-rs/bt-hci
Spec baseline: Bluetooth Core Specification v6.3

---

Overall: commands ~150/300, events ~80/100

## HCI Commands by OGF

### OGF 0x01 — Link Control (`src/cmd/link_control.rs`)
- Spec: Core v6.3, Vol 4, Part E, §7.1
- Implemented: 44 commands
- Missing: none (OCF range 0x0001–0x0045 complete)
- Status: **44/44**

### OGF 0x02 — Link Policy
- No file exists
- Status: **0/??**

### OGF 0x03 — Controller & Baseband (`src/cmd/controller_baseband.rs`)
- Spec: Core v6.3, Vol 4, Part E, [§7.3](https://www.bluetooth.com/wp-content/uploads/Files/Specification/HTML/Core_v6.3/out/en/host-controller-interface/host-controller-interface-functional-specification.html#UUID-5ced811b-a6ce-701a-16b2-70f2d9795c05)
- Status: **10/~85**

Implemented:
- `SetEventMask` (0x0001)
- `Reset` (0x0003)
- `ReadStoredLinkKey` (0x000D)
- `ReadTransmitPowerLevel` (0x002D)
- `SetControllerToHostFlowControl` (0x0031)
- `HostBufferSize` (0x0033)
- `HostNumberOfCompletedPackets` (0x0035)
- `SetEventMaskPage2` (0x0063)
- `ReadAuthenticatedPayloadTimeout` (0x007B)
- `WriteAuthenticatedPayloadTimeout` (0x007C)

Missing (spec subsection in §7.3):
- `SetEventFilter` (0x0005) — §7.3.3
- `Flush` (0x0008) — §7.3.4
- `ReadPinType` / `WritePinType` (0x0009–0x000A) — §7.3.5–§7.3.6
- `WriteStoredLinkKey` / `DeleteStoredLinkKey` (0x0011–0x0012) — §7.3.9–§7.3.10
- `ReadLocalName` / `WriteLocalName` (0x0013–0x0014) — §7.3.11–§7.3.12
- `ReadConnectionAcceptTimeout` / `WriteConnectionAcceptTimeout` (0x0015–0x0016) — §7.3.13–§7.3.14
- `ReadPageTimeout` / `WritePageTimeout` (0x0017–0x0018) — §7.3.15–§7.3.16
- `ReadScanEnable` / `WriteScanEnable` (0x0019–0x001A) — §7.3.17–§7.3.18
- `ReadPageScanActivity` / `WritePageScanActivity` (0x001B–0x001C) — §7.3.19–§7.3.20
- `ReadInquiryScanActivity` / `WriteInquiryScanActivity` (0x001D–0x001E) — §7.3.21–§7.3.22
- `ReadAuthenticationEnable` / `WriteAuthenticationEnable` (0x001F–0x0020) — §7.3.23–§7.3.24
- `ReadClassOfDevice` / `WriteClassOfDevice` (0x0023–0x0024) — §7.3.25–§7.3.26
- `ReadVoiceSetting` / `WriteVoiceSetting` (0x0025–0x0026) — §7.3.27–§7.3.28
- `ReadAutomaticFlushTimeout` / `WriteAutomaticFlushTimeout` (0x0027–0x0028) — §7.3.29–§7.3.30
- `ReadNumBroadcastRetransmissions` / `WriteNumBroadcastRetransmissions` (0x0029–0x002A) — §7.3.31–§7.3.32
- `ReadHoldModeActivity` / `WriteHoldModeActivity` (0x002B–0x002C) — §7.3.33–§7.3.34
- `ReadSynchronousFlowControlEnable` / `WriteSynchronousFlowControlEnable` (0x002E–0x002F) — §7.3.36–§7.3.37
- `ReadLinkSupervisionTimeout` / `WriteLinkSupervisionTimeout` (0x0036–0x0037) — §7.3.41–§7.3.42
- `ReadNumberOfSupportedIAC` (0x0038) — §7.3.43
- `ReadCurrentIacLap` / `WriteCurrentIacLap` (0x0039–0x003A) — §7.3.44–§7.3.45
- `SetAfhHostChannelClassification` (0x003F) — §7.3.46
- `ReadInquiryScanType` / `WriteInquiryScanType` (0x0042–0x0043) — §7.3.47–§7.3.48
- `ReadInquiryMode` / `WriteInquiryMode` (0x0044–0x0045) — §7.3.49–§7.3.50
- `ReadPageScanType` / `WritePageScanType` (0x0046–0x0047) — §7.3.51–§7.3.52
- `ReadAfhChannelAssessmentMode` / `WriteAfhChannelAssessmentMode` (0x0048–0x0049) — §7.3.53–§7.3.54
- `ReadExtendedInquiryResponse` / `WriteExtendedInquiryResponse` (0x0051–0x0052) — §7.3.55–§7.3.56
- `RefreshEncryptionKey` (0x0053) — §7.3.57
- `ReadSimplePairingMode` / `WriteSimplePairingMode` (0x0055–0x0056) — §7.3.58–§7.3.59
- `ReadLocalOobData` (0x0057) — §7.3.60
- `ReadInquiryResponseTransmitPowerLevel` (0x0058) — §7.3.61
- `WriteInquiryTransmitPowerLevel` (0x0059) — §7.3.62
- `ReadDefaultErroneousDataReporting` / `WriteDefaultErroneousDataReporting` (0x005A–0x005B) — §7.3.64–§7.3.65
- `EnhancedFlush` (0x005F) — §7.3.66
- `SendKeypressNotification` (0x0060) — §7.3.63
- `ReadFlowControlMode` / `WriteFlowControlMode` (0x0066–0x0067) — §7.3.72–§7.3.73
- `ReadEnhancedTransmitPowerLevel` (0x0068) — §7.3.74
- `ReadLeHostSupport` / `WriteLeHostSupport` (0x006C–0x006D) — §7.3.78–§7.3.79
- MWS commands (0x006E–0x0073) — §7.3.80–§7.3.85
- CPB commands (0x0074–0x0078) — §7.3.86–§7.3.90
- `ReadSecureConnectionsHostSupport` / `WriteSecureConnectionsHostSupport` (0x0079–0x007A) — §7.3.91–§7.3.92
- `ReadLocalOobExtendedData` (0x007D) — §7.3.95
- `ReadExtendedPageTimeout` / `WriteExtendedPageTimeout` (0x007E–0x007F) — §7.3.96–§7.3.97
- `ReadExtendedInquiryLength` / `WriteExtendedInquiryLength` (0x0080–0x0081) — §7.3.98–§7.3.99
- `SetEcosystemBaseInterval` (0x0082) — §7.3.100
- `ConfigureDataPath` (0x0083) — §7.3.101
- `SetMinEncryptionKeySize` (0x0084) — §7.3.102

### OGF 0x04 — Informational Parameters (`src/cmd/info.rs`)
- Spec: Core v6.3, Vol 4, Part E, [§7.4](https://www.bluetooth.com/wp-content/uploads/Files/Specification/HTML/Core_v6.3/out/en/host-controller-interface/host-controller-interface-functional-specification.html#UUID-42372304-c9ef-dcab-6905-4e5b64703d45)
- Status: **5/11**

Implemented:
- `ReadLocalVersionInformation` (0x0001)
- `ReadLocalSupportedCmds` (0x0002)
- `ReadLocalSupportedFeatures` (0x0003)
- `ReadLocalExtendedFeatures` (0x0004)
- `ReadBdAddr` (0x0009)

Missing (spec subsection in §7.4):
- `ReadBufferSize` (0x0005) — §7.4.5
- `ReadDataBlockSize` (0x000A) — §7.4.7
- `ReadLocalSupportedCodecs` (0x000B v1 / 0x000D v2) — §7.4.8
- `ReadLocalSimplePairingOptions` (0x000C) — §7.4.9
- `ReadLocalSupportedCodecCapabilities` (0x000E) — §7.4.10
- `ReadLocalSupportedControllerDelay` (0x000F) — §7.4.11

### OGF 0x05 — Status Parameters (`src/cmd/status.rs`)
- Spec: Core v6.3, Vol 4, Part E, [§7.5](https://www.bluetooth.com/wp-content/uploads/Files/Specification/HTML/Core_v6.3/out/en/host-controller-interface/host-controller-interface-functional-specification.html#UUID-40e8a930-65b3-c409-007e-388fd48e1041)
- Status: **1/8**

Implemented:
- `ReadRssi` (0x0005)

Missing (spec subsection in §7.5):
- `ReadFailedContactCounter` (0x0001) — §7.5.1
- `ResetFailedContactCounter` (0x0002) — §7.5.2
- `ReadLinkQuality` (0x0003) — §7.5.3
- `ReadAfhChannelMap` (0x0006) — §7.5.5
- `ReadClock` (0x0007) — §7.5.6
- `ReadEncryptionKeySize` (0x0008) — §7.5.7
- `GetMwsTransportLayerConfiguration` (0x000C) — §7.5.11
- `SetTriggeredClockCapture` (0x000D) — §7.5.12

### OGF 0x06 — Testing Commands
- Spec: Core v6.3, Vol 4, Part E, [§7.6](https://www.bluetooth.com/wp-content/uploads/Files/Specification/HTML/Core_v6.3/out/en/host-controller-interface/host-controller-interface-functional-specification.html#UUID-ec2ddbf2-ae4c-ec45-7a06-94f8b3327220)
- No file exists
- Status: **0/5**

Missing (spec subsection in §7.6):
- `ReadLoopbackMode` (0x0001) — §7.6.1
- `WriteLoopbackMode` (0x0002) — §7.6.2
- `EnableDeviceUnderTestMode` (0x0003) — §7.6.3
- `WriteSimplePairingDebugMode` (0x0004) — §7.6.4
- `WriteSecureConnectionsTestMode` (0x000A) — §7.6.8

### OGF 0x08 — LE Controller (`src/cmd/le.rs`)
- Spec: Core v6.3, Vol 4, Part E, [§7.8](https://www.bluetooth.com/wp-content/uploads/Files/Specification/HTML/Core_v6.3/out/en/host-controller-interface/host-controller-interface-functional-specification.html#UUID-0f07d2b9-81e3-6508-ee08-8c808e468fed)
- Status: **~90/~160**

Implemented by OCF range:

**0x0001–0x002F (legacy advertising, scanning, connection, security):**
`LeSetEventMask`[v1], `LeReadBufferSize`[v1], `LeReadLocalSupportedFeatures`, `LeSetRandomAddr`, `LeSetAdvParams`, `LeReadAdvPhysicalChannelTxPower`, `LeSetAdvData`, `LeSetScanResponseData`, `LeSetAdvEnable`, `LeSetScanParams`, `LeSetScanEnable`, `LeCreateConn`, `LeCreateConnCancel`, `LeReadFilterAcceptListSize`, `LeClearFilterAcceptList`, `LeAddDeviceToFilterAcceptList`, `LeRemoveDeviceFromFilterAcceptList`, `LeConnUpdate`, `LeSetHostChannelClassification`, `LeReadChannelMap`, `LeReadRemoteFeatures`, `LeEncrypt`, `LeRand`, `LeEnableEncryption`, `LeLongTermKeyRequestReply`, `LeLongTermKeyRequestNegativeReply`, `LeReadSupportedStates`, `LeTestEnd`, `LeRemoteConnectionParameterRequestReply`, `LeRemoteConnectionParameterRequestNegativeReply`, `LeSetDataLength`, `LeReadSuggestedDefaultDataLength`, `LeWriteSuggestedDefaultDataLength`, `LeReadResolvingListSize`, `LeSetAddrResolutionEnable`, `LeSetResolvablePrivateAddrTimeout`, `LeReadMaxDataLength`, `LeReadPhy`, `LeSetDefaultPhy`, `LeSetPhy`

**0x0035–0x005D (extended advertising, periodic advertising, CTE, power):**
`LeSetAdvSetRandomAddr`, `LeSetExtAdvParams`[v1], `LeSetExtAdvData`, `LeSetExtScanResponseData`, `LeSetExtAdvEnable`, `LeReadMaxAdvDataLength`, `LeReadNumberOfSupportedAdvSets`, `LeRemoveAdvSet`, `LeClearAdvSets`, `LeSetPeriodicAdvParams`[v1], `LeSetPeriodicAdvData`, `LeSetPeriodicAdvEnable`, `LeSetExtScanParams`, `LeSetExtScanEnable`, `LeExtCreateConn`[v1], `LePeriodicAdvCreateSync`, `LePeriodicAdvCreateSyncCancel`, `LePeriodicAdvTerminateSync`, `LeAddDeviceToPeriodicAdvList`, `LeRemoveDeviceFromPeriodicAdvList`, `LeClearPeriodicAdvList`, `LeReadPeriodicAdvListSize`, `LeReadTransmitPower`, `LeReadRfPathCompensation`, `LeWriteRfPathCompensation`, `LeSetPrivacyMode`, `LeSetConnectionlessCteTransmitParams`, `LeSetConnectionlessCteTransmitEnable`, `LeSetConnCteTransmitParams`, `LeConnCteResponseEnable`, `LeReadAntennaInformation`, `LeSetPeriodicAdvReceiveEnable`, `LePeriodicAdvSyncTransfer`, `LePeriodicAdvSetInfoTransfer`, `LeSetPeriodicAdvSyncTransferParams`, `LeSetDefaultPeriodicAdvSyncTransferParams`, `LeRequestPeerSca`, `LeSetHostFeature`[v1]

**0x0074–0x00A3 (power control, subrating, PAwR, frame space, rate):**
`LeSetHostFeature`[v2], `LeEnhancedReadTransmitPowerLevel`, `LeReadRemoteTransmitPowerLevel`, `LeSetPathLossReportingParams`, `LeSetPathLossReportingEnable`, `LeSetTransmitPowerReportingEnable`, `LeSetDataRelatedAddrChanges`, `LeSetDefaultSubrate`, `LeSubrateRequest`, `LeSetPeriodicAdvSubeventData`, `LeSetPeriodicAdvResponseData`, `LeSetPeriodicSyncSubevent`, `LeSetExtAdvParams`[v2], `LeExtCreateConn`[v2], `LeSetPeriodicAdvParams`[v2], `LeFrameSpaceUpdate`, `LeConnectionRateRequest`, `LeSetDefaultRateParameters`, `LeReadMinimumSupportedConnectionInterval`

Missing (by category):

Missing (spec subsection in §7.8):

**Legacy parity / v2 variants:**
- `LeReadBufferSize`[v2] (0x0004) — §7.8.2
- `LeSetEventMask`[v2] (0x00A4) — §7.8.1

**Resolving list / privacy:**
- `LeReadPeerResolvableAddress` (0x002B) — §7.8.42
- `LeReadLocalResolvableAddress` (0x002C) — §7.8.43

**DH Key / P-256:**
- `LeReadLocalP256PublicKey` (0x0025) — §7.8.36
- `LeGenerateDhKey`[v1/v2] (0x0026 / 0x005E) — §7.8.37

**Test commands:**
- `LeReceiverTest`[v2/v3] (0x0033 / 0x004F) — §7.8.28
- `LeTransmitterTest`[v2/v3] (0x0034 / 0x0050) — §7.8.29
- `LeTransmitterTest`[v4] (0x007B) — §7.8.29

**Isochronous (CIS/BIG):**
- `LeReadIsoTxSync` (0x0061) — §7.8.96
- `LeSetCigParameters` (0x0062) — §7.8.97
- `LeSetCigParametersTest` (0x0063) — §7.8.98
- `LeCreateCis` (0x0064) — §7.8.99
- `LeRemoveCig` (0x0065) — §7.8.100
- `LeAcceptCisRequest` (0x0066) — §7.8.101
- `LeRejectCisRequest` (0x0067) — §7.8.102
- `LeCreateBig` (0x0068) — §7.8.103
- `LeCreateBigTest` (0x0069) — §7.8.104
- `LeTerminateBig` (0x006A) — §7.8.105
- `LeBigCreateSync` (0x006B) — §7.8.106
- `LeBigTerminateSync` (0x006C) — §7.8.107
- `LeSetupIsoDataPath` (0x006E) — §7.8.109
- `LeRemoveIsoDataPath` (0x006F) — §7.8.110
- `LeIsoTransmitTest` (0x0070) — §7.8.111
- `LeIsoReceiveTest` (0x0071) — §7.8.112
- `LeIsoReadTestCounters` (0x0072) — §7.8.113
- `LeIsoTestEnd` (0x0073) — §7.8.114
- `LeReadIsoLinkQuality` (0x0075) — §7.8.116
- `LeReadBufferSize`[v2, ISO] (0x0060) — §7.8.2

**Decision-based advertising:**
- `LeSetDecisionData` (0x0080) — §7.8.144
- `LeSetDecisionInstructions` (0x0081) — §7.8.145

**Monitored advertisers:**
- `LeAddDeviceToMonitoredAdvertisersList` (0x0098) — §7.8.146
- `LeRemoveDeviceFromMonitoredAdvertisersList` (0x0099) — §7.8.147
- `LeClearMonitoredAdvertisersList` (0x009A) — §7.8.148
- `LeReadMonitoredAdvertisersListSize` (0x009B) — §7.8.150
- `LeEnableMonitoringAdvertisers` (0x009C) — §7.8.149

**Channel Sounding (CS):**
- `LeCsReadLocalSupportedCapabilities`[v1/v2] (0x0089 / 0x00A5) — §7.8.130
- `LeCsReadRemoteSupportedCapabilities` (0x008A) — §7.8.131
- `LeCsWriteCachedRemoteSupportedCapabilities`[v1/v2] (0x008B / 0x00A6) — §7.8.132
- `LeCsSecurityEnable` (0x008C) — §7.8.133
- `LeCsSetDefaultSettings` (0x008D) — §7.8.134
- `LeCsReadRemoteFaeTable` (0x008E) — §7.8.135
- `LeCsWriteCachedRemoteFaeTable` (0x008F) — §7.8.136
- `LeCsCreateConfig` (0x0090) — §7.8.137
- `LeCsRemoveConfig` (0x0091) — §7.8.138
- `LeCsSetChannelClassification` (0x0092) — §7.8.139
- `LeCsSetProcedureParameters` (0x0093) — §7.8.140
- `LeCsProcedureEnable` (0x0094) — §7.8.141
- `LeCsTest` (0x0095) — §7.8.142
- `LeCsTestEnd` (0x0096) — §7.8.143
- `LeCsSetSecurityRequirements` (0x00A7) — §7.8.157
- `LeCsSetDefaultSecurityRequirements` (0x00A8) — §7.8.158

**Other missing:**
- `LeReadAllLocalSupportedFeatures` (0x0087) — §7.8.128
- `LeReadAllRemoteFeatures` (0x0088) — §7.8.129
- `LeModifySleepClockAccuracy` (0x005F) — §7.8.94
- `LeSetResolvablePrivateAddrTimeout`[v2] (0x009E) — §7.8.45
- `LeEnableUtpOtaMode` (0x009F) — §7.8.152
- `LeUtpSend` (0x00A0) — §7.8.153

---

## HCI Events

### BR/EDR Events (`src/event.rs`)
- Spec: Core v6.3, Vol 4, Part E, §7.7
- Status: **~60/~65**

All standard events from code 0x01–0x59 implemented, plus Vendor (0xFF).
Notable: `PeriodicInquiryMode` / `ExitPeriodicInquiryMode` event (0x1F?) needs verification.

### LE Meta Events (`src/event/le.rs`)
- Spec: Core v6.3, Vol 4, Part E, §7.7.65
- Status: **~32/~56** (subevent codes 0x01–0x37)

Implemented: 0x01–0x34 (up to `LeBiginfoAdvertisingReport`), plus 0x35 (`LeSubrateChange`), 0x37 (`LeFrameSpaceUpdateComplete`), 0x55 (`LeConnectionRateChange`)
Missing: LE Periodic Advertising Subevent Data Request (0x26), LE Periodic Advertising Response Report (0x27), LE Enhanced Connection Complete v2 (0x28), LE CIS Established v2 (0x29), LE Read All Remote Features Complete (0x2A), LE CS events (0x2B–0x32), LE Monitored Advertisers Report (0x33), LE UTP Receive (0x35 in new numbering), LE CS Read Remote Supported Capabilities Complete v2 (0x37)

---

## Parameters

### LE Parameters (`src/param/le.rs`)
- Status: **comprehensive** — all major advertising/scanning/connection/CTE/ISO/CS parameter types
- Missing (not exhaustive): a few newer types for CS, PAwR response, decision-based filtering

### Classic Parameters (`src/param/classic.rs`)
- Status: **comprehensive** — all major BR/EDR parameter types

### Feature Masks (`src/param/feature_masks.rs`)
- Status: **comprehensive** — LMP pages 0–2, LE pages 0–1 feature masks with bitfield getters
- Missing: LE feature page 2+ (Channel Sounding, etc.)

### Event Masks (`src/param/event_masks.rs`)
- Status: **complete** — EventMask, EventMaskPage2, LeEventMask

### Cmd Mask (`src/param/cmd_mask.rs`)
- Status: **comprehensive** — 64-byte bitfield with ~350 getters up to Core 6.2 commands
- Missing: newer LE commands (CS, UTP, decision-based advertising, etc.)

### Status / Error Codes (`src/param/status.rs`)
- Status: **complete** — all ~80 HCI error codes

---

## Core Infrastructure

| Component | File | Status |
|-----------|------|--------|
| Core traits (FromHciBytes, WriteHci, etc.) | `src/lib.rs` | ✅ |
| Packet types (ACL, Sync, Iso) | `src/data.rs` | ✅ |
| Transport abstraction | `src/transport.rs` | ✅ |
| Controller trait & ExternalController | `src/controller.rs` | ✅ |
| Blocking controller | `src/controller/blocking.rs` | ✅ |
| Command macro & traits (`cmd!`) | `src/cmd.rs` | ✅ |
| Event types & event! macro | `src/event.rs` | ✅ |
| Parameter macros (`param!`, `param_slice!`) | `src/param/macros.rs` | ✅ |
| Dual logging (defmt/log) | `src/fmt.rs` | ✅ |
