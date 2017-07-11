---
applicable: Lync Server 2010, Lync Server 2013, Skype for Business Server 2015
schema: 2.0.0
---

# Get-CsApplicationEndpoint

## SYNOPSIS
Below Content Applies To: Lync Server 2010

Retrieves endpoints for the Application service.

Below Content Applies To: Lync Server 2013, Skype for Business Server 2015

Retrieves endpoints for the Application service.
This cmdlet was introduced in Lync Server 2010.



## SYNTAX

```
Get-CsApplicationEndpoint [[-Identity] <UserIdParameter>] [-ApplicationId <String>]
 [-Credential <PSCredential>] [-DomainController <Fqdn>] [-Filter <String>] [-OU <OUIdParameter>]
 [-PoolFqdn <String>] [-ResultSize <Microsoft.Rtc.Management.ADConnect.Core.Unlimited`1[System.UInt32]>]
 [<CommonParameters>]
```

## DESCRIPTION
Below Content Applies To: Lync Server 2010, Lync Server 2013

This cmdlet retrieves one or more application contacts from Active Directory Domain Services (AD DS).
These objects are stored in Active Directory in the Application Contacts container of the RTC service.

Who can run this cmdlet: By default, members of the following groups are authorized to run the Get-CsApplicationEndpoint cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins, RTCUniversalReadOnlyAdmins.
To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsApplicationEndpoint"}

Below Content Applies To: Skype for Business Server 2015

This cmdlet retrieves one or more application contacts from Active Directory Domain Services.
These objects are stored in Active Directory in the Application Contacts container of the RTC service.



## EXAMPLES

### -------------------------- Example 1 ------------------------ (Lync Server 2010)
```
Get-CsApplicationEndpoint
```

This example retrieves information about all application endpoints defined within the Lync Server 2010 deployment.

### -------------------------- EXAMPLE 1 -------------------------- (Lync Server 2013)
```

```

This example retrieves information about all application endpoints defined within the Lync Server deployment.

Get-CsApplicationEndpoint

### -------------------------- EXAMPLE 1 -------------------------- (Skype for Business Server 2015)
```

```

This example retrieves information about all application endpoints defined within the Skype for Business Server 2015 deployment.

Get-CsApplicationEndpoint

### -------------------------- Example 2 ------------------------ (Lync Server 2010)
```
Get-CsApplicationEndpoint -Identity "Call Park Service Contact"
```

Example 2 retrieves information about the application endpoint contact with the display name "Call Park Service Contact".

### -------------------------- EXAMPLE 2 -------------------------- (Lync Server 2013)
```

```

Example 2 retrieves all application endpoints that have the string "endpoint" anywhere within their display name.
To do this, the command uses the Filter parameter.
The value of the parameter filters to find endpoint objects that have a display name (DisplayName) that contains (-like) the string endpoint (*endpoint* - the wildcard characters indicate that any characters can come before or after the string endpoint, meaning endpoint can be anywhere within the display name).

Get-CsApplicationEndpoint -Filter {DisplayName -like "*endpoint*"}

### -------------------------- EXAMPLE 2 -------------------------- (Skype for Business Server 2015)
```

```

Example 2 retrieves all application endpoints that have the string "endpoint" anywhere within their display name.
To do this, the command uses the Filter parameter.
The value of the parameter filters to find endpoint objects that have a display name (DisplayName) that contains (-like) the string endpoint (*endpoint* - the wildcard characters indicate that any characters can come before or after the string endpoint, meaning endpoint can be anywhere within the display name).

Get-CsApplicationEndpoint -Filter {DisplayName -like "*endpoint*"}

### -------------------------- Example 3 ------------------------ (Lync Server 2010)
```
Get-CsApplicationEndpoint -Filter {DisplayName -like "*endpoint*"}
```

Example 3 retrieves all application endpoints that have the string "endpoint" anywhere within their display name.
To do this, the command uses the Filter parameter.
The value of the parameter filters to find endpoint objects that have a display name (DisplayName) that contains (-like) the string endpoint (*endpoint* - the wildcard characters indicate that any characters can come before or after the string endpoint, meaning endpoint can be anywhere within the display name).

### -------------------------- EXAMPLE 3 -------------------------- (Lync Server 2013)
```

```

Example 3 returns all application endpoints associated with the application urn:application:tapp2.
This is accomplished by passing the ID tapp2 to the ApplicationId parameter.
Notice that we didn't supply a pool FQDN; this means that if an application with the ID tapp2 exists on more than one pool, endpoints for all those applications will be retrieved.
The next part of this command pipes the returned object or objects to the Select-Object cmdlet, which displays only the Identity, SipAddress, DisplayName, and OwnerUrn properties of those objects.

Get-CsApplicationEndpoint -ApplicationId tapp2 | Select-Object Identity, SipAddress, DisplayName, OwnerUrn

### -------------------------- EXAMPLE 3 -------------------------- (Skype for Business Server 2015)
```

```

Example 3 returns all application endpoints associated with the application urn:application:tapp2.
This is accomplished by passing the ID tapp2 to the ApplicationId parameter.
Notice that we didn't supply a pool FQDN; this means that if an application with the ID tapp2 exists on more than one pool, endpoints for all those applications will be retrieved.
The next part of this command pipes the returned object or objects to the Select-Object cmdlet, which displays only the Identity, SipAddress, DisplayName, and OwnerUrn properties of those objects.

Get-CsApplicationEndpoint -ApplicationId tapp2 | Select-Object Identity, SipAddress, DisplayName, OwnerUrn

### -------------------------- Example 4 ------------------------ (Lync Server 2010)
```
Get-CsApplicationEndpoint -ApplicationId tapp2 | Select-Object Identity, SipAddress, DisplayName, OwnerUrn
```

Example 4 will return all application endpoints associated with the application urn:application:tapp2.
This is accomplished by passing the ID tapp2 to the ApplicationId parameter.
Notice that we didn't supply a pool FQDN; this means that if an application with the ID tapp2 exists on more than one pool, endpoints for all those applications will be retrieved.
The next part of this command pipes the returned object or objects to the Select-Object cmdlet, which displays only the Identity, SipAddress, DisplayName, and OwnerUrn properties of those objects.

## PARAMETERS

### -Identity
The Identity, SIP address, or display name of the application endpoint to retrieve.
The Identity consists of the distinguished name of the endpoint.
This will typically contain a globally unique identifier (GUID) as part of the CN, for example: CN={8811fefe-e0bb-4fab-ae39-7aaeddd423dc},CN=Application Contacts,CN=RTC Service,CN=Services,CN=Configuration,DC=Vdomain,DC=com.

```yaml
Type: UserIdParameter
Parameter Sets: (All)
Aliases: 
Applicable: Lync Server 2010, Lync Server 2013, Skype for Business Server 2015

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -ApplicationId
The application ID of the application endpoint you want to retrieve.
The application ID is the value of the endpoint's OwnerUrn property.
For example, if the OwnerUrn property has a value of urn:application:Caa, the application ID is urn:application:Caa.
However, you can enter only the suffix, in this case Caa, to retrieve the endpoint.
For example: -ApplicationId Caa

```yaml
Type: String
Parameter Sets: (All)
Aliases: 
Applicable: Lync Server 2010, Lync Server 2013, Skype for Business Server 2015

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential
Alternate credentials under which the Get operation will proceed.
You can retrieve a PSCredential object by calling the Windows PowerShell cmdlet Get-Credential.

```yaml
Type: PSCredential
Parameter Sets: (All)
Aliases: 
Applicable: Lync Server 2010, Lync Server 2013, Skype for Business Server 2015

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DomainController
Allows you to specify a domain controller.
If no domain controller is specified, the first available will be used.

```yaml
Type: Fqdn
Parameter Sets: (All)
Aliases: 
Applicable: Lync Server 2010, Lync Server 2013, Skype for Business Server 2015

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Filter
Below Content Applies To: Lync Server 2010

Enables you to limit the returned data by filtering on specific attributes for Microsoft Lync Server 2010.
For example, you can limit returned data to contacts whose display names or SIP addresses match a certain wildcard pattern.

The Filter parameter uses the same Windows PowerShell filtering syntax that is used by the Where-Object cmdlet.
For example, a filter that returns only contacts that have been enabled for Enterprise Voice would look like this: {EnterpriseVoiceEnabled -eq $True}, with EnterpriseVoiceEnabled representing the Active Directory attribute, -eq representing the comparison operator (equal to), and $True (a built-in Windows PowerShell variable) representing the filter value.



Below Content Applies To: Lync Server 2013

Enables you to limit the returned data by filtering on specific attributes for Lync Server.
For example, you can limit returned data to contacts whose display names or SIP addresses match a certain wildcard pattern.

The Filter parameter uses the same Windows PowerShell filtering syntax that is used by the Where-Object cmdlet.
For example, a filter that returns only contacts that have been enabled for Enterprise Voice would look like this: {EnterpriseVoiceEnabled -eq $True}, with EnterpriseVoiceEnabled representing the Active Directory attribute, -eq representing the comparison operator (equal to), and $True (a built-in Windows PowerShell variable) representing the filter value.



Below Content Applies To: Skype for Business Server 2015

Enables you to limit the returned data by filtering on specific attributes for Skype for Business Server 2015.
For example, you can limit returned data to contacts whose display names or SIP addresses match a certain wildcard pattern.

The Filter parameter uses the same Windows PowerShell filtering syntax that is used by the Where-Object cmdlet.
For example, a filter that returns only contacts that have been enabled for Enterprise Voice would look like this: {EnterpriseVoiceEnabled -eq $True}, with EnterpriseVoiceEnabled representing the Active Directory attribute, -eq representing the comparison operator (equal to), and $True (a built-in Windows PowerShell variable) representing the filter value.



```yaml
Type: String
Parameter Sets: (All)
Aliases: 
Applicable: Lync Server 2010, Lync Server 2013, Skype for Business Server 2015

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OU
The organizational unit (OU) in which the endpoint resides.

```yaml
Type: OUIdParameter
Parameter Sets: (All)
Aliases: 
Applicable: Lync Server 2010, Lync Server 2013, Skype for Business Server 2015

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PoolFqdn
The fully qualified domain name (FQDN) of the pool on which the application endpoint resides.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 
Applicable: Lync Server 2010, Lync Server 2013, Skype for Business Server 2015

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ResultSize
The maximum number of endpoint records to retrieve.

```yaml
Type: Microsoft.Rtc.Management.ADConnect.Core.Unlimited`1[System.UInt32]
Parameter Sets: (All)
Aliases: 
Applicable: Lync Server 2010, Lync Server 2013, Skype for Business Server 2015

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
String.
Accepts a pipelined string value representing the Identity of the application endpoint.

## OUTPUTS

###  
Retrieves an object of type Microsoft.Rtc.Management.ADConnect.Schema.OCSADApplicationContact.

## NOTES

## RELATED LINKS

[Online Version](http://technet.microsoft.com/EN-US/library/820d3bbd-0348-4272-bdb3-c3d612d0836a(OCS.14).aspx)

[Move-CsApplicationEndpoint]()

[Online Version](http://technet.microsoft.com/EN-US/library/820d3bbd-0348-4272-bdb3-c3d612d0836a(OCS.15).aspx)

[Online Version](http://technet.microsoft.com/EN-US/library/820d3bbd-0348-4272-bdb3-c3d612d0836a(OCS.16).aspx)
