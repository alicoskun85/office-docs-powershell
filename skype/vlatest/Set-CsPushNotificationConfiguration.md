---
applicable: Lync Server 2013, Skype for Business Online, Skype for Business Server 2015
schema: 2.0.0
---

# Set-CsPushNotificationConfiguration

## SYNOPSIS
Below Content Applies To: Lync Server 2013

Modifies an existing collection of push notification configuration settings.
The push notification service (Apple Push Notification Service and Microsoft Push Notification Service) provides a way to send notifications about events such as new instant messages or new voice mail to mobile devices such as iPhones and Windows Phones, even if the Lync application on those devices is currently suspended or running in the background.
This cmdlet was introduced in the cumulative update for Lync Server 2010: November 2011.

Below Content Applies To: Skype for Business Online

Set-CsPushNotificationConfiguration \[\[-Identity\] \<XdsIdentity\>\] \[-Tenant \<guid\>\] \[-EnableApplePushNotificationService \<bool\>\] \[-EnableMicrosoftPushNotificationService \<bool\>\] \[-BypassDualWrite \<bool\>\] \[-Force\] \[-WhatIf\] \[-Confirm\] \[\<CommonParameters\>\]

Set-CsPushNotificationConfiguration \[-Tenant \<guid\>\] \[-EnableApplePushNotificationService \<bool\>\] \[-EnableMicrosoftPushNotificationService \<bool\>\] \[-Instance \<psobject\>\] \[-BypassDualWrite \<bool\>\] \[-Force\] \[-WhatIf\] \[-Confirm\] \[\<CommonParameters\>\]

Below Content Applies To: Skype for Business Server 2015

Modifies an existing collection of push notification configuration settings.
The push notification service (Apple Push Notification Service and Microsoft Push Notification Service) provides a way to send notifications about events such as new instant messages or new voice mail to mobile devices such as iPhones and Windows Phones, even if the Skype for Business application on those devices is currently suspended or running in the background.
This cmdlet was introduced in the cumulative update for Lync Server 2010: November 2011.



## SYNTAX

### Identity
```
Set-CsPushNotificationConfiguration [[-Identity] <XdsIdentity>] [-Confirm]
 [-EnableApplePushNotificationService <Boolean>] [-EnableMicrosoftPushNotificationService <Boolean>] [-Force]
 [-Tenant <Guid>] [-WhatIf] [<CommonParameters>]
```

### Instance
```
Set-CsPushNotificationConfiguration [-Confirm] [-EnableApplePushNotificationService <Boolean>]
 [-EnableMicrosoftPushNotificationService <Boolean>] [-Force] [-Instance <PSObject>] [-Tenant <Guid>] [-WhatIf]
 [<CommonParameters>]
```

###  (Default)
```
Set-CsPushNotificationConfiguration [[-Identity] <Object>] [-BypassDualWrite <Object>] [-Confirm]
 [-EnableApplePushNotificationService <Object>] [-EnableMicrosoftPushNotificationService <Object>] [-Force]
 [-Instance <Object>] [-Tenant <Object>] [-WhatIf] [-AsJob] [<CommonParameters>]
```

## DESCRIPTION
Below Content Applies To: Lync Server 2013

The Apple Push Notification Service and the Microsoft Push Notification Service enable users running Lync on their Apple iPhone or Windows Phone to receive notifications about Lync events even when Lync is suspended or running in the background.
For example, users can receive notice for events such as these:

- Invitations to a new instant messaging session or conference
- New instant messages
- New voice mail

Without the push notification service users would receive these notices only when Lync was in the foreground and serving as the active application.

Administrators have the ability to enable or disable push notifications for iPhone users and/or Windows Phone users.
(By default, push notifications are disabled for both iPhone users and Windows Phone users.) Administrators can enable or disable push notifications at the global scope by using the Set-CsPushNotificationConfiguration cmdlet.
They can also create custom push notification settings at the site scope by using the New-CsPushNotificationConfiguration cmdlet.
These custom settings can also be modified by using the Set-CsPushNotificationConfiguration cmdlet.

With the push notification configuration settings there are only two property values for Administrators to manage: EnableApplePushNotificationService, which determines whether push notifications are sent to iPhone users; and EnableMicrosoftPushNotificationService, which determines whether push notifications are sent to Windows Phone users.
Note that these property values do not have to be set to the same value.
For example, you could enable push notifications to Windows Phone users (by setting EnableMicrosoftPushNotificationService to True) yet, at the same, disable notifications to iPhone users by setting EnableApplePushNotificationService to False.

Who can run this cmdlet: By default, members of the following groups are authorized to run the Set-CsPushNotificationConfiguration cmdlet locally: RTCUniversalServerAdmins.

Below Content Applies To: Skype for Business Online

{{Fill in the Description}}

Below Content Applies To: Skype for Business Server 2015

The Apple Push Notification Service and the Microsoft Push Notification Service enable users running Skype for Business on their Apple iPhone or Windows Phone to receive notifications about Skype for Business Server 2015 events even when Skype for Business is suspended or running in the background.
For example, users can receive notice for events such as these:

- Invitations to a new instant messaging session or conference
- New instant messages
- New voice mail

Without the push notification service users would receive these notices only when Skype for Business was in the foreground and serving as the active application.

Administrators have the ability to enable or disable push notifications for iPhone users and/or Windows Phone users.
(By default, push notifications are disabled for both iPhone users and Windows Phone users.) Administrators can enable or disable push notifications at the global scope by using the Set-CsPushNotificationConfiguration cmdlet.
They can also create custom push notification settings at the site scope by using the New-CsPushNotificationConfiguration cmdlet.
These custom settings can also be modified by using the Set-CsPushNotificationConfiguration cmdlet.

With the push notification configuration settings there are only two property values for Administrators to manage: EnableApplePushNotificationService, which determines whether push notifications are sent to iPhone users; and EnableMicrosoftPushNotificationService, which determines whether push notifications are sent to Windows Phone users.
Note that these property values do not have to be set to the same value.
For example, you could enable push notifications to Windows Phone users (by setting EnableMicrosoftPushNotificationService to True) yet, at the same, disable notifications to iPhone users by setting EnableApplePushNotificationService to False.



## EXAMPLES

### -------------------------- EXAMPLE 1 -------------------------- (Lync Server 2013)
```

```

The command shown in Example 1 disables push notifications from the Apple Push Notification Service for the Redmond site.

Set-CsPushNotificationConfiguration -Identity "site:Redmond" -EnableApplePushNotificationService $False

### Example 1 (Skype for Business Online)
```
PS C:\> {{ Add example code here }}
```

{{ Add example description here }}

### -------------------------- EXAMPLE 1 -------------------------- (Skype for Business Server 2015)
```

```

The command shown in Example 1 disables push notifications from the Apple Push Notification Service for the Redmond site.

Set-CsPushNotificationConfiguration -Identity "site:Redmond" -EnableApplePushNotificationService $False

### -------------------------- EXAMPLE 2 -------------------------- (Lync Server 2013)
```

```

Example 2 disables push notifications from the Apple Push Notification Service for all the sites currently hosting push notification settings.
To do this, the command first uses Get-CsPushNotificationConfiguration and the Filter parameter to return all the push notification settings configured at the site scope; the filter value "site:*" limits the returned settings to those that have an Identity that begins with the string value "site:".
That collection of settings is then piped to the Set-CsPushNotificationConfiguration cmdlet, which takes each item in the collection and sets the EnableApplePushNotificationService property to False.

Get-CsPushNotificationConfiguration -Filter "site:*" | Set-CsPushNotificationService -EnableApplePushNotificationService $False

### -------------------------- EXAMPLE 2 -------------------------- (Skype for Business Server 2015)
```

```

Example 2 disables push notifications from the Apple Push Notification Service for all the sites currently hosting push notification settings.
To do this, the command first uses the Get-CsPushNotificationConfiguration cmdlet and the Filter parameter to return all the push notification settings configured at the site scope; the filter value "site:*" limits the returned settings to those that have an Identity that begins with the string value "site:".
That collection of settings is then piped to the Set-CsPushNotificationConfiguration cmdlet, which takes each item in the collection and sets the EnableApplePushNotificationService property to False.

Get-CsPushNotificationConfiguration -Filter "site:*" | Set-CsPushNotificationConfiguration -EnableApplePushNotificationService $False

### -------------------------- EXAMPLE 3 -------------------------- (Lync Server 2013)
```

```

Example 3 demonstrates how you can locate all the push notification settings where push notifications from the Microsoft Push Notification Service are disabled, and then disable push notifications from the Apple Push Notification Service for each of those settings as well.
To carry out this task, the command first uses Get-CsPushNotificationConfiguration to return a collection of all the push notification settings currently in use the organization.
This collection is then piped to the Where-Object cmdlet, which selects only those settings where the EnableMicrosoftPushNotificationService property is equal to (-eq) False.
That filtered collection is then piped to Set-CsPushNotificationConfiguration, which takes each item in the filtered collection and sets the EnableApplePushNotificationService property to False.

Get-CsPushNotificationConfiguration | Where-Object {$_.EnableMicrosoftPushNotificationService -eq $False} | Set-CsPushNotificationConfiguration -EnableApplePushNotificationService $False

### -------------------------- EXAMPLE 3 -------------------------- (Skype for Business Server 2015)
```

```

Example 3 demonstrates how you can locate all the push notification settings where push notifications from the Microsoft Push Notification Service are disabled, and then disable push notifications from the Apple Push Notification Service for each of those settings as well.
To carry out this task, the command first uses the Get-CsPushNotificationConfiguration cmdlet to return a collection of all the push notification settings currently in use the organization.
This collection is then piped to the Where-Object cmdlet, which selects only those settings where the EnableMicrosoftPushNotificationService property is equal to (-eq) False.
That filtered collection is then piped to the Set-CsPushNotificationConfiguration cmdlet, which takes each item in the filtered collection and sets the EnableApplePushNotificationService property to False.

Get-CsPushNotificationConfiguration | Where-Object {$_.EnableMicrosoftPushNotificationService -eq $False} | Set-CsPushNotificationConfiguration -EnableApplePushNotificationService $False

## PARAMETERS

### -Confirm
Below Content Applies To: Lync Server 2013, Skype for Business Server 2015

Prompts you for confirmation before executing the command.



Below Content Applies To: Skype for Business Online

Prompts you for confirmation before running the cmdlet.



```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: cf
Applicable: Lync Server 2013, Skype for Business Online, Skype for Business Server 2015

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EnableApplePushNotificationService
Below Content Applies To: Lync Server 2013, Skype for Business Server 2015

When set to True, iPhone users will receive push notifications from the Apple Push Notification Service.
When set to False, iPhone users will not receive these notifications.

The default value is False.



Below Content Applies To: Skype for Business Online

{{Fill EnableApplePushNotificationService Description}}



```yaml
Type: Boolean
Parameter Sets: (All)
Aliases: 
Applicable: Lync Server 2013, Skype for Business Online, Skype for Business Server 2015

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EnableMicrosoftPushNotificationService
Below Content Applies To: Lync Server 2013, Skype for Business Server 2015

When set to True, Windows Phone users will receive push notifications from the Microsoft Push Notification Service.
When set to False, Windows Phone users will not receive these notifications.

The default value is False.



Below Content Applies To: Skype for Business Online

{{Fill EnableMicrosoftPushNotificationService Description}}



```yaml
Type: Boolean
Parameter Sets: (All)
Aliases: 
Applicable: Lync Server 2013, Skype for Business Online, Skype for Business Server 2015

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force
Below Content Applies To: Lync Server 2013, Skype for Business Server 2015

Suppresses the display of any non-fatal error message that might occur when running the command.



Below Content Applies To: Skype for Business Online

{{Fill Force Description}}



```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 
Applicable: Lync Server 2013, Skype for Business Online, Skype for Business Server 2015

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Identity
Below Content Applies To: Lync Server 2013, Skype for Business Server 2015

Indicates the Identity of the push notification configuration settings to be modified.
To refer to the global settings, use this syntax:

-Identity global

To refer to site settings, use syntax similar to this:

-Identity site:Redmond

Note that you cannot use wildcards when specifying an Identity.



Below Content Applies To: Skype for Business Online

{{Fill Identity Description}}



```yaml
Type: XdsIdentity
Parameter Sets: Identity
Aliases: 
Applicable: Lync Server 2013, Skype for Business Online, Skype for Business Server 2015

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

```yaml
Type: XdsIdentity
Parameter Sets: (All)
Aliases: 
Applicable: Lync Server 2013, Skype for Business Online, Skype for Business Server 2015

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Instance
Below Content Applies To: Lync Server 2013, Skype for Business Server 2015

Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.



Below Content Applies To: Skype for Business Online

{{Fill Instance Description}}



```yaml
Type: PSObject
Parameter Sets: Instance
Aliases: 
Applicable: Lync Server 2013, Skype for Business Online, Skype for Business Server 2015

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

```yaml
Type: PSObject
Parameter Sets: (All)
Aliases: 
Applicable: Lync Server 2013, Skype for Business Online, Skype for Business Server 2015

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Tenant
Below Content Applies To: Lync Server 2013

Globally unique identifier (GUID) of the Office 365 tenant account for the push notification settings being modified.
For example:

-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"

You can return the tenant ID for each of your tenants by running this command:

Get-CsTenant | Select-Object DisplayName, TenantID



Below Content Applies To: Skype for Business Online

{{Fill Tenant Description}}



Below Content Applies To: Skype for Business Server 2015

Globally unique identifier (GUID) of the Skype for Business Online tenant account for the push notification settings being modified.
For example:

-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"

You can return the tenant ID for each of your tenants by running this command:

Get-CsTenant | Select-Object DisplayName, TenantID

If you are using a remote session of Windows PowerShell and are connected only to Skype for Business Online you do not have to include the Tenant parameter.
Instead, the tenant ID will automatically be filled in for you based on your connection information.
The Tenant parameter is primarily for use in a hybrid deployment.



```yaml
Type: Guid
Parameter Sets: (All)
Aliases: 
Applicable: Lync Server 2013, Skype for Business Online, Skype for Business Server 2015

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf
Below Content Applies To: Lync Server 2013, Skype for Business Server 2015

Describes what would happen if you executed the command without actually executing the command.



Below Content Applies To: Skype for Business Online

Shows what would happen if the cmdlet runs.
The cmdlet is not run.



```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: wi
Applicable: Lync Server 2013, Skype for Business Online, Skype for Business Server 2015

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -BypassDualWrite
{{Fill BypassDualWrite Description}}

```yaml
Type: Object
Parameter Sets: (All)
Aliases: 
Applicable: Skype for Business Online

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsJob
{{Fill AsJob Description}}

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 
Applicable: Skype for Business Online

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

###  
Microsoft.Rtc.Management.WriteableConfig.Settings.PushNotificationConfiguration.PushNotificationConfiguration.
Set-CsPushNotificationConfiguration accepts pipelined instances of the PushNotificationConfiguration object.

### System.Management.Automation.PSObject

###  
Microsoft.Rtc.Management.WriteableConfig.Settings.PushNotificationConfiguration.PushNotificationConfiguration.
The Set-CsPushNotificationConfiguration cmdlet accepts pipelined instances of the PushNotificationConfiguration object.

## OUTPUTS

###  
None.
Instead, Set-CsPushNotificationConfiguration modifies existing instances of the Microsoft.Rtc.Management.WriteableConfig.Settings.PushNotificationConfiguration.PushNotificationConfiguration object.

### System.Object

###  
None.
Instead, the Set-CsPushNotificationConfiguration cmdlet modifies existing instances of the Microsoft.Rtc.Management.WriteableConfig.Settings.PushNotificationConfiguration.PushNotificationConfiguration object.

## NOTES

## RELATED LINKS

[Online Version](http://technet.microsoft.com/EN-US/library/3aacdb2b-b6dd-4615-a3f9-68360f3ae483(OCS.15).aspx)

[Online Version](http://technet.microsoft.com/EN-US/library/3aacdb2b-b6dd-4615-a3f9-68360f3ae483(OCS.16).aspx)
