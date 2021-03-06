﻿---
title: Set-CsConferenceDisclaimer
TOCTitle: Set-CsConferenceDisclaimer
ms:assetid: 97afce6d-b031-466d-a170-3ca50d6df245
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398776(v=OCS.15)
ms:contentKeyID: 48184868
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Set-CsConferenceDisclaimer

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-07_

Modifies the property values of the conference disclaimer used in your organization. The conference disclaimer is a message displayed to users who join a conference by using a hyperlink (for example, by pasting a link to the conference into a browser such as Windows Internet Explorer). This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Set-CsConferenceDisclaimer [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsConferenceDisclaimer [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Body <String>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Header <String>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 modifies both the Header and Body properties for your organization’s conference disclaimer. Because you can have only one such disclaimer, you do not need to specify the Identity when running the **Set-CsConferenceDisclaimer** cmdlet.

    Set-CsConferenceDisclaimer -Header "Litwareinc.com Online Conference" -Body "Important note: Conferencing proceedings are recorded and archived."

</div>

</div>

<div>

## Detailed Description

When configuring conferencing settings, administrators can include a legal disclaimer to display to participants when they join conferences hosted by Lync Server. This disclaimer is typically used to explain legal and intellectual property laws regarding the conference. Users cannot join the conference without agreeing to the stipulations set forth in the disclaimer. Note, however, that this disclaimer is only shown to users who join a conference by using a hyperlink.

Lync Server allows for a single, global instance of the conference disclaimer. The **Set-CsConferenceDisclaimer** cmdlet enables you to modify the conference disclaimer used in your organization.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsConferenceDisclaimer** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsConferenceDisclaimer"}

</div>

<div>

## Parameters


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Required</th>
<th>Type</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Body</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Contents of the conference disclaimer.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suppresses the display of any non-fatal error message that might occur when running the command.</p></td>
</tr>
<tr class="even">
<td><p><em>Header</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Title given the conference disclaimer.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Unique Identity of the conference disclaimer. Because you can only have a single, global instance of the conference disclaimer, you do not need to specify an Identity when calling the <strong>Set-CsConferenceDisclaimer</strong> cmdlet. However, you can use the following syntax to reference the global disclaimer: -Identity global.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>Optional</p></td>
<td><p>ConferenceDisclaimer object</p></td>
<td><p>Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Describes what would happen if you executed the command without actually executing the command.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.WebConf.ConferenceDisclaimer object. The **Set-CsConferenceDisclaimer** cmdlet accepts pipelined input of conference disclaimer objects.

</div>

<div>

## Return Types

The **Set-CsConferenceDisclaimer** cmdlet does not return any objects or values. Instead, the cmdlet modifies existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.WebConf.ConferenceDisclaimer object.

</div>

<div>

## See Also


[Get-CsConferenceDisclaimer](get-csconferencedisclaimer.md)  
[Remove-CsConferenceDisclaimer](remove-csconferencedisclaimer.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

