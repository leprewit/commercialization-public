---
title: DF - Fuzz sub-opens with streams test (Reliability)
description: DF - Fuzz sub-opens with streams test (Reliability)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 01a240da-3fad-4e10-8744-d8af7959f2ab
---

# <span id="p_hlk_test.d7b43caa-9289-40dd-8ed2-bfce9eabe356"></span>DF - Fuzz sub-opens with streams test (Reliability)


During the Streams Test, the Fuzz test tries to open a variety of named data streams on the device. The tests use a series of arbitrary stream names with content and characters that might be valid for other uses on some devices. This test determines whether the driver can properly handle data stream requests, especially if the driver exports a device that does not support or anticipate data streams.

A *named data stream* is an attribute of a file object. You specify a named data stream by writing the name of the file, a colon, and the name of the data stream, for example, "File01.txt:AccessDate" where *AccessDate* is a named data stream, that is, an attribute of the File01.txt file.

The Fuzz test records the stream names used in the test.

-   **Test binary:** Devfund\_FuzzTest.dll
-   **Test method:** DoSubOpensWithStreamsTest

## Test details
|||
|---|---|
| **Specifications**  | <ul><li>Device.DevFund.Reliability.BasicReliabilityAndPerformance</li><li>Device.DevFund.Reliability.BasicSecurity</li><li>Device.DevFund.DriverFramework.KMDF.Reliability</li><li>Device.DevFund.DriverFramework.UMDF.Reliability</li></ul> |  
| **Platforms**   | <ul><li>Windows 10 client editions (x86)</li><li>Windows 10, client editions (x64)</li><li>Windows Server 2016 (x64)</li><li>Windows 10, client editions (ARM64)</li><li>Windows 10, mobile edition (ARM)</li><li>Windows 10, mobile edition (ARM64)</li></ul> |
| **Supported Releases** | <ul><li>Windows 10</li><li>Windows 10, version 1511</li><li>Windows 10, version 1607</li><li>Windows 10, version 1703</li><li>Windows 10, version 1709</li></ul> |
|**Expected run time (in minutes)**| 15 |
|**Category**| Scenario |
|**Timeout (in minutes)**| 180 |
|**Requires reboot**| false |
|**Requires special configuration**| true |
|**Type**| automatic |

 

## <span id="Additional_documentation"></span><span id="additional_documentation"></span><span id="ADDITIONAL_DOCUMENTATION"></span>Additional documentation


Tests in this feature area might have additional documentation, including prerequisites, setup, and troubleshooting information, that can be found in the following topic(s):

-   [Device.DevFund additional documentation](device-devfund-additional-documentation.md)

## <span id="Running_the_test"></span><span id="running_the_test"></span><span id="RUNNING_THE_TEST"></span>Running the test


Before you run the test, complete the test setup as described in the test requirements: [Device.Fundamentals Reliability Testing Prerequisites](devicefundamentals-reliability-testing-prerequisites.md).

## <span id="Troubleshooting"></span><span id="troubleshooting"></span><span id="TROUBLESHOOTING"></span>Troubleshooting


For generic troubleshooting of HLK test failures, see [Troubleshooting Windows HLK Test Failures](..\user\troubleshooting-windows-hlk-test-failures.md).

For troubleshooting information specific to the Device Fundamentals tests in the HLK and WDK, see [Device.DevFund additional documentation](device-devfund-additional-documentation.md).

## <span id="More_information"></span><span id="more_information"></span><span id="MORE_INFORMATION"></span>More information


### <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters

| Parameter name                           | Parameter description                                                                                                                                                                                                                                   |
|------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **DQ**                                   | A WDTF SDEL query that is used to identify the target device(s) - http://go.microsoft.com/fwlink/?LinkId=232678                                                                                                                                         |
| **Wpa2PskAesSsid**                       | Required ONLY if DUT or one of its child devices is a WiFi adapter. Please provide SSID of a WPA2 AES WiFi network that the test can use to test the WiFi adapter. The default is 'kitstestssid'.                                                       |
| **Wpa2PskPassword**                      | Required ONLY if DUT or one of its child devices is a WiFi adapter. Please provide password of the WPA2 AES WiFi network specified using the Wpa2PskAesSsid parameter. The default is 'password'.                                                       |
| **ChangeBufferProtectionFlags**          | True or False. Changes the memory protection flags of buffers passed to the tested device. The memory protection flags alternates between no access, read-only, and read-only with page guard.                                                          |
| **Impersonate**                          | True or False. Runs the test as a non administrative user.                                                                                                                                                                                              |
| **FillZeroPageWithNull**                 | True or False. Maps the zero page and fills it with NULL values. This test identifies drivers that do not verify a pointer reference before dereferencing a pointer.                                                                                    |
| **DoPoolCheck**                          | True or False. Monitors the driver's use of the paged and nonpaged system memory pools by using pool tags and lookaside lists. This option also monitors changes in the number of exceptions handled which might indicate errors in exception handling. |
| **DoSync**                               | True or False. Also opens device handles in SYNC mode (FILE\_SYNCHRONOUS\_IO\_ALERT). Random read and write operations are skipped.                                                                                                                     |
| **TestCycles**                           | Number of test cycles.                                                                                                                                                                                                                                  |
| **DriverVerifierAdditionalDrivers**      | Additional drivers that should have Driver Verifier enabled                                                                                                                                                                                             |
| **DriverVerifierExcludedFlags**          | Placeholder for Driver Verifier flags that may be manually excluded for the test run                                                                                                                                                                    |
| **WDKDeviceID**                          | Device id of device under test                                                                                                                                                                                                                          |
| **QueryHardwareID**                      | Hardware id of device under test                                                                                                                                                                                                                        |
| **WDTFREMOTESYSTEM**                     | Required ONLY if DUT or one of its child devices is a wired NIC that doesn't have an IPv6 gateway address. If determined to be required, please provide an IPv6 address that the test NIC can ping to test network I/O. Eg: fe80::78b6:810:9c12:46cd    |
| **DriverVerifierCustomizeConfiguration** | Specifies that this test may want to automatically update Driver Verifier settings                                                                                                                                                                      |

 

 

 






