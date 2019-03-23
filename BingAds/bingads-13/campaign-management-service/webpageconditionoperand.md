---
title: WebpageConditionOperand Value Set - Campaign Management
ms.service: bing-ads-campaign-management-service
ms.topic: article
author: eric-urban
ms.author: eur
description: Defines the possible operand values that can be applied to the argument of a webpage condition for dynamic search ads.
---
> [!IMPORTANT]
> The Bing Ads API Version 13 preview documentation is subject to change. To view version 12 content, use the version selector near the table of contents at the top and left side of the page.

# WebpageConditionOperand Value Set - Campaign Management
Defines the possible operand values that can be applied to the argument of a webpage condition for dynamic search ads. 

## Syntax
```xml
<xs:simpleType name="WebpageConditionOperand" xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:restriction base="xs:string">
    <xs:enumeration value="Unknown" />
    <xs:enumeration value="Url" />
    <xs:enumeration value="Category" />
    <xs:enumeration value="PageTitle" />
    <xs:enumeration value="PageContent" />
    <xs:enumeration value="CustomLabel" />
  </xs:restriction>
</xs:simpleType>
```

## <a name="values"></a>Values

|Value|Description|
|-----------|---------------|
|<a name="category"></a>Category|Set a condition that the [argument](webpagecondition.md#argument) must match one of the categories that Bing thinks is applicable for your site.|
|<a name="customlabel"></a>CustomLabel|Set a condition that the [argument](webpagecondition.md#argument) must match any of your page feed custom labels.<br/><br/>Although you can manage the page feeds source and custom labels via Bing Ads API, page feeds upload is only supported through the Bing Ads web application. For more details about uploading page feeds, see the [About dynamic search ads page feeds](https://help.bingads.microsoft.com/#apex/3/en/60010/0) help article.|
|<a name="pagecontent"></a>PageContent|Set a condition that the [argument](webpagecondition.md#argument) must match any of your site's content that is indexed by Bing.|
|<a name="pagetitle"></a>PageTitle|Set a condition that the [argument](webpagecondition.md#argument) must match any of your site's page titles that are indexed by Bing.|
|<a name="unknown"></a>Unknown|Reserved for future use.|
|<a name="url"></a>Url|Set a condition that the [argument](webpagecondition.md#argument) must match any of your site's URLs that are indexed by Bing.|

## Requirements
Service: [CampaignManagementService.svc v13](https://campaign.api.bingads.microsoft.com/Api/Advertiser/CampaignManagement/v13/CampaignManagementService.svc)  
Namespace: https\://bingads.microsoft.com/CampaignManagement/v13  

## Used By
[WebpageCondition](webpagecondition.md)  