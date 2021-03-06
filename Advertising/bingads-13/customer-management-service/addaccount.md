---
title: AddAccount Service Operation - Customer Management
ms.service: bing-ads-customer-management-service
ms.topic: article
author: eric-urban
ms.author: eur
description: Creates a new account within an existing customer.
dev_langs: 
  - csharp
  - java
  - php
  - python
---
# AddAccount Service Operation - Customer Management
Creates a new account within an existing customer. 

> [!NOTE]
> Only a user with Super Admin credentials can add accounts. For more information, see the [User Roles](../guides/account-hierarchy-permissions.md#user-roles) technical guide.  

> [!TIP]
> Resellers should call [SignupCustomer](signupcustomer.md) instead of *AddAccount*. For more details see the [Account Hierarchy](../guides/account-hierarchy-permissions.md#account-hierarchy) technical guide.

## <a name="request"></a>Request Elements
The *AddAccountRequest* object defines the [body](#request-body) and [header](#request-header) elements of the service operation request. The elements must be in the same order as shown in the [Request SOAP](#request-soap). 

> [!NOTE]
> Unless otherwise noted below, all request elements are required.

### <a name="request-body"></a>Request Body Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|<a name="account"></a>Account|The account that you want to add to the existing customer.<br/><br/>You must specify the ParentCustomerId in the advertiser account object.|[AdvertiserAccount](advertiseraccount.md)|

### <a name="request-header"></a>Request Header Elements
[!INCLUDE[request-header](./includes/request-header.md)]

## <a name="response"></a>Response Elements
The *AddAccountResponse* object defines the [body](#response-body) and [header](#response-header) elements of the service operation response. The elements are returned in the same order as shown in the [Response SOAP](#response-soap).

### <a name="response-body"></a>Response Body Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|<a name="accountid"></a>AccountId|A system-generated account identifier corresponding to the new account specified in the request.<br/><br/>Use this identifier with operation requests that require an *AccountId* element and a *CustomerAccountId* SOAP header element.|**long**|
|<a name="accountnumber"></a>AccountNumber|A system-generated account number that is used to identify the account in the Microsoft Advertising web application. The account number has the form, X*nnnnnnn*, where *nnnnnnn* is a series of digits.|**string**|
|<a name="createtime"></a>CreateTime|The date and time that the account was added. The date and time value reflects the date and time at the server, not the client. For information about the format of the date and time, see the dateTime entry in [Primitive XML Data Types](https://go.microsoft.com/fwlink/?linkid=859198).|**dateTime**|

### <a name="response-header"></a>Response Header Elements
[!INCLUDE[response-header](./includes/response-header.md)]

## <a name="request-soap"></a>Request SOAP
This template was generated by a tool to show the [order](../guides/services-protocol.md#element-order) of the [body](#request-body) and [header](#request-header) elements for the SOAP request. For supported types that you can use with this service operation, see the [Request Body Elements](#request-body) reference above.

```xml
<s:Envelope xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="https://bingads.microsoft.com/Customer/v13">
    <Action mustUnderstand="1">AddAccount</Action>
    <AuthenticationToken i:nil="false">ValueHere</AuthenticationToken>
    <DeveloperToken i:nil="false">ValueHere</DeveloperToken>
  </s:Header>
  <s:Body>
    <AddAccountRequest xmlns="https://bingads.microsoft.com/Customer/v13">
      <Account xmlns:e3="https://bingads.microsoft.com/Customer/v13/Entities" i:nil="false">
        <e3:BillToCustomerId i:nil="false">ValueHere</e3:BillToCustomerId>
        <e3:CurrencyCode i:nil="false">ValueHere</e3:CurrencyCode>
        <e3:AccountFinancialStatus i:nil="false">ValueHere</e3:AccountFinancialStatus>
        <e3:Id i:nil="false">ValueHere</e3:Id>
        <e3:Language i:nil="false">ValueHere</e3:Language>
        <e3:LastModifiedByUserId i:nil="false">ValueHere</e3:LastModifiedByUserId>
        <e3:LastModifiedTime i:nil="false">ValueHere</e3:LastModifiedTime>
        <e3:Name i:nil="false">ValueHere</e3:Name>
        <e3:Number i:nil="false">ValueHere</e3:Number>
        <e3:ParentCustomerId>ValueHere</e3:ParentCustomerId>
        <e3:PaymentMethodId i:nil="false">ValueHere</e3:PaymentMethodId>
        <e3:PaymentMethodType i:nil="false">ValueHere</e3:PaymentMethodType>
        <e3:PrimaryUserId i:nil="false">ValueHere</e3:PrimaryUserId>
        <e3:AccountLifeCycleStatus i:nil="false">ValueHere</e3:AccountLifeCycleStatus>
        <e3:TimeStamp i:nil="false">ValueHere</e3:TimeStamp>
        <e3:TimeZone i:nil="false">ValueHere</e3:TimeZone>
        <e3:PauseReason i:nil="false">ValueHere</e3:PauseReason>
        <e3:ForwardCompatibilityMap xmlns:e4="http://schemas.datacontract.org/2004/07/System.Collections.Generic" i:nil="false">
          <e4:KeyValuePairOfstringstring>
            <e4:key i:nil="false">ValueHere</e4:key>
            <e4:value i:nil="false">ValueHere</e4:value>
          </e4:KeyValuePairOfstringstring>
        </e3:ForwardCompatibilityMap>
        <e3:LinkedAgencies i:nil="false">
          <e3:CustomerInfo>
            <e3:Id i:nil="false">ValueHere</e3:Id>
            <e3:Name i:nil="false">ValueHere</e3:Name>
          </e3:CustomerInfo>
        </e3:LinkedAgencies>
        <e3:SalesHouseCustomerId i:nil="false">ValueHere</e3:SalesHouseCustomerId>
        <e3:TaxInformation xmlns:e5="http://schemas.datacontract.org/2004/07/System.Collections.Generic" i:nil="false">
          <e5:KeyValuePairOfstringstring>
            <e5:key i:nil="false">ValueHere</e5:key>
            <e5:value i:nil="false">ValueHere</e5:value>
          </e5:KeyValuePairOfstringstring>
        </e3:TaxInformation>
        <e3:BackUpPaymentInstrumentId i:nil="false">ValueHere</e3:BackUpPaymentInstrumentId>
        <e3:BillingThresholdAmount i:nil="false">ValueHere</e3:BillingThresholdAmount>
        <e3:BusinessAddress i:nil="false">
          <e3:City i:nil="false">ValueHere</e3:City>
          <e3:CountryCode i:nil="false">ValueHere</e3:CountryCode>
          <e3:Id i:nil="false">ValueHere</e3:Id>
          <e3:Line1 i:nil="false">ValueHere</e3:Line1>
          <e3:Line2 i:nil="false">ValueHere</e3:Line2>
          <e3:Line3 i:nil="false">ValueHere</e3:Line3>
          <e3:Line4 i:nil="false">ValueHere</e3:Line4>
          <e3:PostalCode i:nil="false">ValueHere</e3:PostalCode>
          <e3:StateOrProvince i:nil="false">ValueHere</e3:StateOrProvince>
          <e3:TimeStamp i:nil="false">ValueHere</e3:TimeStamp>
          <e3:BusinessName i:nil="false">ValueHere</e3:BusinessName>
        </e3:BusinessAddress>
        <e3:AutoTagType i:nil="false">ValueHere</e3:AutoTagType>
        <e3:SoldToPaymentInstrumentId i:nil="false">ValueHere</e3:SoldToPaymentInstrumentId>
      </Account>
    </AddAccountRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response-soap"></a>Response SOAP
This template was generated by a tool to show the order of the [body](#response-body) and [header](#response-header) elements for the SOAP response.

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="https://bingads.microsoft.com/Customer/v13">
    <TrackingId d3p1:nil="false" xmlns:d3p1="http://www.w3.org/2001/XMLSchema-instance">ValueHere</TrackingId>
  </s:Header>
  <s:Body>
    <AddAccountResponse xmlns="https://bingads.microsoft.com/Customer/v13">
      <AccountId>ValueHere</AccountId>
      <AccountNumber d4p1:nil="false" xmlns:d4p1="http://www.w3.org/2001/XMLSchema-instance">ValueHere</AccountNumber>
      <CreateTime>ValueHere</CreateTime>
    </AddAccountResponse>
  </s:Body>
</s:Envelope>
```

## <a name="example"></a>Code Syntax
The example syntax can be used with [Bing Ads SDKs](../guides/client-libraries.md). See [Bing Ads API Code Examples](../guides/code-examples.md) for more examples.
```csharp
public async Task<AddAccountResponse> AddAccountAsync(
	AdvertiserAccount account)
{
	var request = new AddAccountRequest
	{
		Account = account
	};

	return (await CustomerManagementService.CallAsync((s, r) => s.AddAccountAsync(r), request));
}
```
```java
static AddAccountResponse addAccount(
	AdvertiserAccount account) throws RemoteException, Exception
{
	AddAccountRequest request = new AddAccountRequest();

	request.setAccount(account);

	return CustomerManagementService.getService().addAccount(request);
}
```
```php
static function AddAccount(
	$account)
{

	$GLOBALS['Proxy'] = $GLOBALS['CustomerManagementProxy'];

	$request = new AddAccountRequest();

	$request->Account = $account;

	return $GLOBALS['CustomerManagementProxy']->GetService()->AddAccount($request);
}
```
```python
response=customermanagement_service.AddAccount(
	Account=Account)
```

## Requirements
Service: [CustomerManagementService.svc v13](https://clientcenter.api.bingads.microsoft.com/Api/CustomerManagement/v13/CustomerManagementService.svc)  
Namespace: https\://bingads.microsoft.com/Customer/v13  

