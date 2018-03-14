---
title: Campaign Data Object - Campaign Management
ms.service: bing-ads-campaign-management-service
ms.topic: article
author: eric-urban
ms.author: eur
description: Defines a campaign.
---
# Campaign Data Object - Campaign Management
Defines a campaign.

## Syntax
```xml
<xs:complexType name="Campaign" xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:sequence>
    <xs:element minOccurs="0" name="BiddingScheme" nillable="true" type="tns:BiddingScheme" />
    <xs:element minOccurs="0" name="BudgetType" nillable="true" type="tns:BudgetLimitType" />
    <xs:element minOccurs="0" name="DailyBudget" nillable="true" type="xs:double" />
    <xs:element minOccurs="0" name="Description" nillable="true" type="xs:string" />
    <xs:element minOccurs="0" name="ForwardCompatibilityMap" nillable="true" type="q6:ArrayOfKeyValuePairOfstringstring" xmlns:q6="http://schemas.datacontract.org/2004/07/System.Collections.Generic" />
    <xs:element minOccurs="0" name="Id" nillable="true" type="xs:long" />
    <xs:element minOccurs="0" name="Name" nillable="true" type="xs:string" />
    <xs:element minOccurs="0" name="NativeBidAdjustment" nillable="true" type="xs:int" />
    <xs:element minOccurs="0" name="Status" nillable="true" type="tns:CampaignStatus" />
    <xs:element minOccurs="0" name="TimeZone" nillable="true" type="xs:string" />
    <xs:element minOccurs="0" name="TrackingUrlTemplate" nillable="true" type="xs:string" />
    <xs:element minOccurs="0" name="UrlCustomParameters" nillable="true" type="q7:CustomParameters" xmlns:q7="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" />
    <xs:element minOccurs="0" name="CampaignType" nillable="true" type="tns:CampaignType" />
    <xs:element minOccurs="0" name="Settings" nillable="true" type="tns:ArrayOfSetting" />
    <xs:element minOccurs="0" name="BudgetId" nillable="true" type="xs:long" />
    <xs:element minOccurs="0" name="Languages" nillable="true" type="q8:ArrayOfstring" xmlns:q8="http://schemas.microsoft.com/2003/10/Serialization/Arrays" />
  </xs:sequence>
</xs:complexType>
```

## <a name="elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|<a name="biddingscheme"></a>BiddingScheme|The bid strategy type for how you want to manage your bids.<br/><br/>For campaigns you can use either of the [EnhancedCpcBiddingScheme](enhancedcpcbiddingscheme.md) or [ManualCpcBiddingScheme](manualcpcbiddingscheme.md) objects.<br/><br/>If you are signed up to pilot one or more of the auto bid strategy types, then you can also use the corresponding [MaxClicksBiddingScheme](maxclicksbiddingscheme.md), [MaxConversionsBiddingScheme](maxconversionsbiddingscheme.md), or [TargetCpaBiddingScheme](targetcpabiddingscheme.md) object.<br /><br />**IMPORTANT:** If the campaign bid strategy type is set to *MaxClicks*, *MaxConversions*, or *TargetCpa*, the behavior of existing features will change unless you set an individual ad group's or keyword's bid strategy to *ManualCpc*. <br/> -  You can continue to set the ad group and keyword bids; however they will not be used by Bing Ads.<br/> -  Bing Ads will periodically change your stored ad group or keyword bid settings. You can continue to set new bids, however Bing Ads may change them at any time using this bid strategy type.<br/> -  You can continue to set bid adjustments e.g. for age, gender, or location; however, the multiplier will inform rather than directly modify or override the automated bid. For auto bidding the multiplier is used as a weighted percentage to inform Bing Ads about how much you value the criterion relative to other criteria. For example, a -50% bid multiplier for a mobile device criterion with the Max Conversions bid strategy to indicate that you value conversions from mobile traffic half as much as other device types. The same bid multiplier with the Max Clicks bid strategy would indicate that you value clicks on mobile half as much as other device types. The valid range of values that you can use to inform auto bidding is -100.00 through 30.00.<br/> -  Whether you chose the *DailyBudgetAccelerated* or *DailyBudgetStandard* budget type, Bing Ads will use the *DailyBudgetStandard* budget type.<br/><br/>Also note that you must have conversion tracking (a UET tag and a conversion goal) set up for the *EnhancedCpc*, *MaxConversions*, and *TargetCpa* bid strategy types to work. See [Universal Event Tracking](../guides/universal-event-tracking.md) for more information.<br/><br/>To set the *MaxConversions* or *TargetCpa* bid strategy types, the campaign must have at least 15 conversions in the last 30 days. If you try to add or update a campaign to use one of these strategy types, the requested operation will fail if there is not enough conversion history. If an active campaign uses one of these bid strategy types, and then ceases to meet the minimum conversion history requirement at any time, Bing Ads will stop auto bidding but will continue to use the *DailyBudgetStandard* budget type. For a new campaign we recommend that you start with *EnhancedCpc* and then when the campaign has enough conversion history, you can update it to use either the *MaxConversions* or *TargetCpa* bid strategy.<br /><br />**Tip:** You can set your campaign's bid strategy to [EnhancedCpcBiddingScheme](enhancedcpcbiddingscheme.md), [MaxClicksBiddingScheme](maxclicksbiddingscheme.md), [MaxConversionsBiddingScheme](maxconversionsbiddingscheme.md), or [TargetCpaBiddingScheme](targetcpabiddingscheme.md) and then, at any time, set an individual ad group's or keyword's bid strategy to Manual CPC ([ManualCpcBiddingScheme](manualcpcbiddingscheme.md)).<br/><br/> For campaigns of type *Shopping* only the [EnhancedCpcBiddingScheme](enhancedcpcbiddingscheme.md) or [ManualCpcBiddingScheme](manualcpcbiddingscheme.md) objects can be used, and you must be in the Bing Shopping Enhanced CPC pilot. The pilot ID is 340.<br/><br/>**Add:** Optional. If you do not set this element, then [ManualCpcBiddingScheme](manualcpcbiddingscheme.md) is used by default.<br/>**Update:** Optional. If no value is specified on update, this Bing Ads setting is not changed.|[BiddingScheme](biddingscheme.md)|
|<a name="budgetid"></a>BudgetId|The unique Bing Ads identifier of the [Budget](budget.md) that this campaign shares with other campaigns in the account.<br /><br />If the value is not null and greater than zero, then the campaign is using a shared budget. If the value is null, then the campaign is not using a shared budget. If the campaign is using a shared budget, and you prefer that it use its own budget e.g. *DailyBudget* amount, set this element to '0' (zero) and set *DailyBudget* to a valid budget amount.<br/><br/>**Add:** Optional<br/>**Update:** Optional. If no value is specified on update, this Bing Ads setting is not changed.|**long**|
|<a name="budgettype"></a>BudgetType|The budget type determines how the budget is spent.<br/><br/>In the context of shared budgets, the budget type is a read-only property that is always returned regardless of whether or not the campaign uses a shared budget. If you try to update the budget type of a campaign that has a shared budget, the service will return the *CampaignServiceCannotUpdateSharedBudget* error code. You can continue to set this property for unshared budgets, and you can make other updates to the campaign regardless of whether the budget is shared. To determine whether the campaign uses a shared budget, check the value of the *BudgetId* element as described above.<br/><br/>**Add:** Required<br/>**Update:** Optional. If no value is specified on update, this Bing Ads setting is not changed.|[BudgetLimitType](budgetlimittype.md)|
|<a name="campaigntype"></a>CampaignType|The campaign type determines whether the campaign is a Bing Shopping campaign, Dynamic Search Ads campaign, or Search &amp; Content campaign.<br/><br/>**Add:** Optional. If not specified, then default value of *SearchAndContent* is used and you cannot set Bing Shopping or Dynamic Search Ads campaign settings.<br/>**Update:** Not allowed.|[CampaignType](campaigntype.md)|
|<a name="dailybudget"></a>DailyBudget|The amount to spend daily on the campaign. You must set the daily budget amount if *BudgetId* is not set.<br/><br/>In the context of shared budgets, the budget amount is a read-only property that is always returned regardless of whether or not the campaign uses a shared budget. When a campaign is associated to a shared budget the amount returned is that of the shared budget. If you try to update the budget amount of a campaign that has a shared budget, the service will return the *CampaignServiceCannotUpdateSharedBudget* error code. You can continue to set this property for unshared budgets, and you can make other updates to the campaign regardless of whether the budget is shared. To determine whether the campaign uses a shared budget, check the value of the *BudgetId* element as described above.<br/><br/>**Add:** Required<br/>**Update:** Optional. If no value is specified on update, this Bing Ads setting is not changed.|**double**|
|<a name="description"></a>Description|The description of the campaign.<br/><br/>The description can contain a maximum of 1,000 characters.<br/><br/>**Add:** Required<br/>**Update:** Optional. If no value is specified on update, this Bing Ads setting is not changed.|**string**|
|<a name="forwardcompatibilitymap"></a>ForwardCompatibilityMap|The list of key and value strings for forward compatibility to avoid otherwise breaking changes when new elements are added in the current API version.<br /><br /> Forward compatibility changes will be noted here in future releases. There are currently no forward compatibility changes for the *Campaign* object.|[KeyValuePairOfstringstring](keyvaluepairofstringstring.md) array|
|<a name="id"></a>Id|The unique Bing Ads identifier of the campaign.<br/><br/>**Add:** Read-only<br/>**Update:** Required|**long**|
|<a name="languages"></a>Languages|Your ad language setting determines the language you will use when you write your ads and should be the language of your customers.<br/><br/>For possible values, see the Language column of [Ad Languages](../guides/ad-languages.md#adlanguage). You can specify multiple languages individually in the list, or only include one list item set to *All* if you want to target all languages.<br/><br/>**IMPORTANT:** Support for multiple languages at the campaign level is in pilot. If languages are set at both the ad group and campaign level, the ad group-level language will override the campaign-level language. The customer is enabled for the pilot if the [GetCustomerPilotFeatures](../customer-management-service/getcustomerpilotfeatures.md) response includes pilot number *310*. Pilot participants will be able to set multiple languages at the campaign level, and will be able to delete the ad group level language. If your application depends on ad group language being set, then you must prepare for the possibility that ad group language will be nil. Also note that as a one time migration when the customer is added to pilot, campaign languages are set to the union of all individual ad group languages. For example if you have three ad groups with language set to *English*, *German*, and *French*, then at the time of pilot enablement this campaign's languages will be set to a list including *English*, *German*, and *French*.<br/><br/> For Dynamic Search Ads campaigns, only *English* is supported.<br/><br/>**Add:** Optional. If there is no campaign language set, then the language of each ad group within the campaign will be required.<br/>**Update:** Optional. If no value is specified on update, this Bing Ads setting is not changed. Once campaign languages are set, you cannot delete all of them. The list of languages that you specify during update replaces the previous settings i.e. does not append to the existing set of languages.|**string** array|
|<a name="name"></a>Name|The name of the campaign. The name must be unique among all active or paused campaigns within the account. The name can contain a maximum of 128 characters.<br /><br />The service performs a case-insensitive comparison when it compares the name to existing campaign names.<br/><br/>**Add:** Required<br/>**Update:** Optional. If no value is specified on update, this Bing Ads setting is not changed.|**string**|
|<a name="nativebidadjustment"></a>NativeBidAdjustment|The percent amount by which to adjust your bid for intent ads above or below the base ad group or keyword bid.<br/><br/> Not everyone has this feature yet. If you don't, don't worry. It's coming soon.<br /><br />Supported values are negative one hundred (-100) through positive nine hundred (900). Setting the bid adjustment to -100 will prevent intent ads from showing for this campaign.<br /><br />Set this element to zero (0) if you want to use the base ad group or keyword bid instead of specifying any bid adjustment for intent ads.<br /><br />As a best practice you should always specify a bid adjustment value. If you set this element to null the system default bid adjustment will be used. The system default bid adjustment is currently zero (0), and is subject to change.<br/><br/>**Add:** Optional<br/>**Update:** Optional. If no value is specified on update, this Bing Ads setting is not changed.|**int**|
|<a name="settings"></a>Settings|The settings will vary by campaign type.<br /><br />The contract specifies a list; however, currently a maximum of one setting is supported.<br /><br />If the *CampaignType* element is *SearchAndContent*, then this element must be nil or empty. If the *CampaignType* element is *Shopping*, this list will include a [ShoppingSetting](shoppingsetting.md) object. If the *CampaignType* element is *DynamicSearchAds*, this list will include a [DynamicSearchAdsSetting](dynamicsearchadssetting.md) object.<br/><br/>**Add:** Optional<br/>**Update:** Optional. If no value is specified on update, this Bing Ads setting is not changed.|[Setting](setting.md) array|
|<a name="status"></a>Status|The status of the campaign.<br /><br />Possible values are *Active* and *Paused*.<br /><br />The service will automatically pause the campaign if the budget is depleted.<br/><br/>**Add:** Optional. The default value is *Paused*.<br/>**Update:** Optional. If no value is specified on update, this Bing Ads setting is not changed.|[CampaignStatus](campaignstatus.md)|
|<a name="timezone"></a>TimeZone|The time zone where the campaign operates.<br /><br />The time zone is used for reporting and applying the start and end date of an ad group.<br /><br />For possible values, see [Time Zones](../guides/time-zones.md).<br/><br/>**Add:** Required<br/>**Update:** Optional. If no value is specified on update, this Bing Ads setting is not changed. You may not update the time zone if the campaign contains or has ever contained ad groups in the *Active* or *Paused* state.|**string**|
|<a name="trackingurltemplate"></a>TrackingUrlTemplate|The tracking template to use as a default for all URLs in your campaign.<br /><br />The following validation rules apply to tracking templates. For more details about supported templates and parameters, see the Bing Ads help article [What tracking or URL parameters can I use?](https://help.bingads.microsoft.com/#apex/3/en/56799/2)- Tracking templates defined for lower level entities e.g. ads override those set for higher level entities e.g. campaign. For more information, see [Entity Hierarchy and Limits](../guides/entity-hierarchy-limits.md).- The length of the tracking template is limited to 2,048 characters. The HTTP or HTTPS protocol string does count towards the 2,048 character limit.- The tracking template must be a well-formed URL beginning with one of the following: *http://*, *https://*, *{lpurl}*, or *{unescapedlpurl}*. - Bing Ads does not validate whether custom parameters exist. If you use custom parameters in your tracking template and they do not exist, then the landing page URL will include the key and value placeholders of your custom parameters without substitution. For example if your tracking template is for example *http://tracker.example.com/?season={_season}&promocode={_promocode}&u={lpurl}*, and neither *{_season}* or *{_promocode}* are defined at the campaign, ad group, criterion, keyword, or ad level, then the landing page URL will be the same.<br/><br/>**Add:** Optional<br/>**Update:** Optional. If no value is specified on update, this Bing Ads setting is not changed.|**string**|
|<a name="urlcustomparameters"></a>UrlCustomParameters|Your custom collection of key and value parameters for URL tracking.<br /><br />You may include up to 3 individual [CustomParameter](customparameter.md) objects within the [CustomParameters](customparameters.md) object. Each [CustomParameter](customparameter.md) contains a *Key* and *Value* element.<br /><br />**Add:** Optional<br/>**Update:** Optional. If no value is specified on update, this Bing Ads setting is not changed. Set the *UrlCustomParameters* element to null or empty to retain any existing custom parameters. To remove all custom parameters, set the *Parameters* element of the [CustomParameters](customparameters.md) object to null or empty. To remove a subset of custom parameters, specify the custom parameters that you want to keep in the *Parameters* element of the [CustomParameters](customparameters.md) object.|[CustomParameters](customparameters.md)|

## Requirements
Service: [CampaignManagementService.svc v11](https://campaign.api.bingads.microsoft.com/Api/Advertiser/CampaignManagement/v11/CampaignManagementService.svc)  
Namespace: https\://bingads.microsoft.com/CampaignManagement/v11  

## Used By
[AddCampaigns](addcampaigns.md)  
[GetCampaignsByAccountId](getcampaignsbyaccountid.md)  
[GetCampaignsByIds](getcampaignsbyids.md)  
[UpdateCampaigns](updatecampaigns.md)  