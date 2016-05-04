---
author: joshbax-msft
title: UAS Stress Reset logo test for UAS on EHCI
description: UAS Stress Reset logo test for UAS on EHCI
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: ca9233d9-2ef1-4efe-833e-baf15839ab51
---

# UAS Stress Reset logo test for UAS on EHCI


This test verifies compliance with the USB UASP version 1.04 specification, the SCSI SPC 4 specification, and SBC3 for USB UASP storage devices.

## Test details


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Associated requirements</strong></p></td>
<td><p>Device.Storage.Hd.UasOnEHCI.BasicFunction</p>
<p>[See the device hardware requirements.](http://go.microsoft.com/fwlink/p/?linkid=254483)</p></td>
</tr>
<tr class="even">
<td><p><strong>Platforms</strong></p></td>
<td><p>Windows RT (ARM-based) Windows 8 (x64) Windows 8 (x86) Windows Server 2012 (x64) Windows RT 8.1 Windows 8.1 x64 Windows 8.1 x86 Windows Server 2012 R2</p></td>
</tr>
<tr class="odd">
<td><p><strong>Expected run time</strong></p></td>
<td><p>~50 minutes</p></td>
</tr>
<tr class="even">
<td><p><strong>Categories</strong></p></td>
<td><p>Certification Reliability</p></td>
</tr>
<tr class="odd">
<td><p><strong>Type</strong></p></td>
<td><p>Automated</p></td>
</tr>
</tbody>
</table>

 

## Running the test


Before you run the test, complete the test setup as described in the test requirements: [Hard Disk Drive Testing Prerequisites](hard-disk-drive-testing-prerequisites.md).

In addition, this test requires a UAS device connected to USB 2.0 controller.

## Troubleshooting


For troubleshooting information, see [Troubleshooting Device.Storage Testing](troubleshooting-devicestorage-testing.md).

## More Information


### Reset detection for different IO workloads

If different types of IO workloads are on the drive, then the test detects if there are any LUN, Target, or Bus resets. LUN reset is new to UAS devices and becomes costly if a reset needs to be performed. This is because a LUN reset to the device times out and a target reset gets sent to the device. The time lapse causes the drive to become unusable. This applies if you have synchronous workloads with varying transfer sizes for longer duration.

### Parameters

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Version</p></td>
<td><p>The USB version. The values can be either 2 or 3.</p></td>
</tr>
<tr class="even">
<td><p>StorageDriveLetter</p></td>
<td><p>The drive letter of the device.</p></td>
</tr>
<tr class="odd">
<td><p>StorageDriveNumber</p></td>
<td><p>The driver number of the device.</p></td>
</tr>
<tr class="even">
<td><p>QueryUASMaxTransferSize</p></td>
<td><p>The maximum transfer size supported by the device (in bytes).</p></td>
</tr>
<tr class="odd">
<td><p>Streams</p></td>
<td><p>The minimum number of streams supported by the device.</p>
<p>Default value: 16</p></td>
</tr>
<tr class="even">
<td><p>UAS_Adapter_ID</p></td>
<td><p>The adapter device instance ID.</p></td>
</tr>
</tbody>
</table>

 

### Command syntax

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Command option</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>powershell .\StressReset.ps1 /scenario “uas” /version [Version] /driveletter [StorageDriveLetter] /drivenumber [StorageDriveNumber] /iosize [QueryUASMaxTransferSize] /streams [Streams] /pnpDeviceID “[UAS_Adapter_ID]”</p></td>
<td><p>Runs the test</p></td>
</tr>
</tbody>
</table>

 

**Note**  
For command-line help for this test binary, type **/?**.

 

### File list

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>File</th>
<th>Location</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>csvresultparser.dll</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\\basetest\core_file_services\performance\diskspd\</p></td>
</tr>
<tr class="even">
<td><p>diskspd.exe</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\\basetest\core_file_services\performance\diskspd\</p></td>
</tr>
<tr class="odd">
<td><p>iorequestgenerator.dll</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\\basetest\core_file_services\performance\diskspd\</p></td>
</tr>
<tr class="even">
<td><p>resultparser.dll</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\\basetest\core_file_services\performance\diskspd\</p></td>
</tr>
<tr class="odd">
<td><p>StressReset.ps1</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\DriversTest\storage\wdk\</p></td>
</tr>
</tbody>
</table>

 

 

 

[Send comments about this topic to Microsoft](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_hck\p_hck%5D:%20UAS%20Stress%20Reset%20logo%20test%20for%20UAS%20on%20EHCI%20%20RELEASE:%20%284/27/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Send comments about this topic to Microsoft")



