﻿---
title: Update-CsTenantMeetingUrl
TOCTitle: Update-CsTenantMeetingUrl
ms:assetid: 9aed3ede-bbd3-405a-997f-f7553e66aecd
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn424754(v=OCS.15)
ms:contentKeyID: 56627307
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Update-CsTenantMeetingUrl

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-04-03_

Updates the meeting URL for the specified Lync Online tenant. The updated URL uses a simpler, more standardized format that makes it easier for clients to locate and connect to meetings.

This cmdlet is intended for use only with Lync Online.

<div>

## Syntax

    Update-CsTenantMeetingUrl [-Tenant] <guid> [-Force] [-WhatIf] [-Confirm]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

The command shown in Example 1 updates the meeting URL for the tenant with the tenant ID 38aad667-af54-4397-aaa7-e94c79ec2308. (Note that you must supply the tenant ID in order for this command to complete.) After pressing ENTER to run the command, you will be asked if you are sure you want to update the meeting URL. You must answer yes to this prompt before Update-CsTenantMeetingUrl will actually make any changes to your Lync Online configuration settings.

    Update-CsTenantMeetingUrl -Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"

</div>

<div>

## Example 2

Example 2 also updates the meeting URL for the tenant with the tenant ID 38aad667-af54-4397-aaa7-e94c79ec2308. In this case, however, the Force parameter is included; this bypasses the confirmation prompt that typically appears when you run Update-CsTenantMeetingUrl. In this case, as soon as you press ENTER the command will run and your Lync Online configuration settings will be modified.

    Update-CsTenantMeetingUrl -Tenant "38aad667-af54-4397-aaa7-e94c79ec2308" -Force

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

The Update-CsTenantMeetingUrl updates the Lync Online meeting URL to a simpler and more standardized format; this helps eliminate problems that occasionally occurred with the original meeting URL. For example, suppose an organization sets up an Office 365 domain with the name contoso.onmicrosoft.com. When they do that, meetings will have URLs similar to this:

https://meet.lync.com/contoso/user1/45GZFH99

Now, suppose the organization undergoes some changes and decides to use the “vanity” URL litwareinc.com instead of the onmicrosoft.com URL. The organization modifies their user email addresses to use the litwareinc.com domain. However, meeting URLs will still use the old domain name:

https://meet.lync.com/contoso/user1/45GZFH99

To fix this problem, administrators should run the Update-CsTenantMeetingUrl cmdlet. That will replace the old meeting URL with a new one that features the vanity URL instead:

https://meet.lync.com/litwareinc.com/user1/37JYLP71

Running the Update-CsTenantMeetingUrl cmdlet is the only way to make this change.

Note that, when you run Update-CsTenantMeetingUrl, your Lync Online tenant will switch to the new URL after a short sync delay. That will not create any problems for new meetings that your users might schedule: those meetings will automatically be scheduled using the new URL. However, previously-scheduled meetings will run into problems; that’s because they were scheduled using the older, defunct meeting URL. The only way to address this issue is to have your users reschedule those meetings.

Because this could potentially create problems in some organizations (particularly organizations where a large number of meetings have already been scheduled), by default Update-CsTenantMeetingUrl will prompt you before actually updating the meeting URL:

WARNING: This is a breaking change for users in this tenant. Meeting URL configuration will be updated\!Old meeting URLs will no longer function. This change cannot be reverted.  
Are you sure you want to continue?  
\[Y\] Yes \[A\] Yes to All \[N\] No \[L\] No to All \[S\] Suspend \[?\] Help (default is “Y”):

You must answer “Yes” or “Yes to All” before the command will actually be executed; if you answer “No” then the command will be cancelled and the meeting URL will not be updated. Keep in mind that once the meeting URL has been changed there is no way to revert back to the original URL. Once the command executes the URL will be changed and all previously-scheduled meetings will need to be rescheduled. This also means that you only need to run this command once per tenant. There is no need to periodically run and the command and re-update the meeting URL.

If you prefer to run the command without having to address the confirmation prompt, you can include the Force parameter. In that case, Update-CsTenantMeetingUrl will run without displaying the confirmation prompt:

WARNING: This is a breaking change for users in this tenant. Meeting URL configuration will be updated\!

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
<td><p><strong>Tenant</strong></p></td>
<td><p>Required</p></td>
<td><p>System.Guid</p></td>
<td><p>Globally unique identifier (GUID) of the tenant account whose federation settings are being returned. For example:</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>You can return the tenant ID for each of your tenants by running this command:</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p>
<p>If you do not include the Tenant parameter then Update-CsMeetingUrl will prompt you to enter that parameter before you can continue.</p></td>
</tr>
<tr class="even">
<td><p><strong>Confirm</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p>
<p>Note that the default behavior of the Update-CsMeetingUrl is to display the confirmation prompt before making any updates. That means that, if you want to display the confirmation prompt, you do not need to include the Confirm parameter.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Force</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suppresses the display of the confirmation prompt which would otherwise appear before Update-CsMeetingUrl makes any updates.</p></td>
</tr>
<tr class="even">
<td><p><strong>WhatIf</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Describes what would happen if you executed the command without actually executing the command.</p></td>
</tr>
</tbody>
</table>


</div>

<span id="InputTypes"></span>

<div>

## Input Types

None. Update-CsMeetingUrl does not accept pipelined input.

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

None.

</div>

<div>

## See Also


[Get-CsSimpleUrlConfiguration](get-cssimpleurlconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

