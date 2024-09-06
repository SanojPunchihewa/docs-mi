# Google Ads Connector Reference

The following operations allow you to work with the Google Ads API. Click an operation name to see parameter details and samples on how to use it.

---

## Initialize the connector

To use the Google Ads connector, first create the connection with your configuration. When calling a Google Ads operation, ensure the connection is referenced using the configKey attribute.

??? note "init"
    The init operation is used to initialize the connection to Google Ads API.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>name</td>
            <td>Unique name to identify the connection by.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>base</td>
            <td>The service root URL. The default value is `https://googleads.googleapis.com`.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>tokenEndpoint</td>
            <td>The HTTP endpoint that can be uses to obtain an access token. The default value is `https://www.googleapis.com/oauth2/v3/token`.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>clientId</td>
            <td>Client ID of the registered application.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>clientSecret</td>
            <td>Client secret of the registered application.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>refreshToken</td>
            <td>The refresh token that can be used to obtain a new access token.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>developerToken</td>
            <td>The developer token used to connect to the Google Ads API.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>loginCustomerId</td>
            <td>The customer ID of the Manager Account. Required if the operations are made by a manager to a client account.</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <googleAdNetwork.init>
        <connectionType>googleAdNetwork</connectionType>
        <name>GOOGLE_AD_NETWORK_CONNECTION_1</name>
        <base>https://googleads.googleapis.com</base>
        <clientId>REPLACE_WITH_CLIENT_ID</clientId>
        <clientSecret>REPLACE_WITH_CLIENT_SECRET</clientSecret>
        <refreshToken>REPLACE_WITH_REFRESH_TOKEN</refreshToken>
        <developerToken>REPLACE_WITH_DEVELOPER_TOKEN</developerToken>
        <tokenEndpoint>https://www.googleapis.com/oauth2/v3/token</tokenEndpoint>
        <loginCustomerId>REPLACE_WITH_MANAGER_ID</loginCustomerId>
    </googleAdNetwork.init>
    ```

---

## Operations

??? note "customers.assetGroupListingGroupFilters.mutate"
    Creates, updates or removes asset group listing group filters. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose asset group listing group filters are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual asset group listing group filters. Type: object [AssetGroupListingGroupFilterOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/AssetGroupListingGroupFilterOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.campaignBidModifiers.mutate"
    Creates, updates, or removes campaign bid modifiers. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>ID of the customer whose campaign bid modifiers are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual campaign bid modifiers. Type: object [CampaignBidModifierOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/CampaignBidModifierOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.searchAudienceInsightsAttributes"
    Searches for audience attributes that can be used to generate insights.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>dimensions</td>
            <td>The types of attributes to be returned. Type: enum [AudienceInsightsDimension](https://developers.google.com/google-ads/api/rest/reference/rest/v17/AudienceInsightsDimension)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>queryText</td>
            <td>A free text query. If the requested dimensions include Attributes CATEGORY or KNOWLEDGE_GRAPH, then the attributes returned for those dimensions will match or be related to this string. For other dimensions, this field is ignored and all available attributes are returned. Type: string</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>customerInsightsGroup</td>
            <td>The name of the customer being planned for. This is a user-defined value. Type: string</td>
            <td>No</td>
        </tr>
        <tr>
            <td>locationCountryFilters</td>
            <td>If SUB_COUNTRY_LOCATION attributes are one of the requested dimensions and this field is present, then the SUB_COUNTRY_LOCATION attributes returned will be located in these countries. If this field is absent, then location attributes are not filtered by country. Setting this field when SUB_COUNTRY_LOCATION attributes are not requested will return an error. Type: object [LocationInfo](https://developers.google.com/google-ads/api/rest/reference/rest/v17/LocationInfo)</td>
            <td>No</td>
        </tr>
        <tr>
            <td>youtubeReachLocation</td>
            <td>If present, potential YouTube reach estimates within the specified market will be returned for attributes for which they are available. Reach is only available for the AGE_RANGE, GENDER, AFFINITY_USER_INTEREST and IN_MARKET_USER_INTEREST dimensions, and may not be available for every attribute of those dimensions in every market. Type: object [LocationInfo](https://developers.google.com/google-ads/api/rest/reference/rest/v17/LocationInfo)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "keywordThemeConstants.suggest"
    Returns KeywordThemeConstant suggestions by keyword themes.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>queryText</td>
            <td>The query text of a keyword theme that will be used to map to similar keyword themes. For example, "plumber" or "roofer". Type: string</td>
            <td>No</td>
        </tr>
        <tr>
            <td>countryCode</td>
            <td>Upper-case, two-letter country code as defined by ISO-3166. This for refining the scope of the query, default to 'US' if not set. Type: string</td>
            <td>No</td>
        </tr>
        <tr>
            <td>languageCode</td>
            <td>The two letter language code for get corresponding keyword theme for refining the scope of the query, default to 'en' if not set. Type: string</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.remarketingActions.mutate"
    Creates or updates remarketing actions. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose remarketing actions are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual remarketing actions. Type: object [RemarketingActionOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/RemarketingActionOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.billingSetups.mutate"
    Creates a billing setup, or cancels an existing billing setup.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>Id of the customer to apply the billing setup mutate operation to.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operation</td>
            <td>The operation to perform. Type: object [BillingSetupOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/customers.billingSetups/mutate#BillingSetupOperation)</td>
            <td>Yes</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.AdGroupCriterionCustomizers.mutate"
    Creates, updates or removes ad group criterion customizers. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose ad group criterion customizers are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual ad group criterion customizers. Type: object [AdGroupCriterionCustomizerOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/AdGroupCriterionCustomizerOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.extensionFeedItems.mutate"
    Creates, updates, or removes extension feed items. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose extension feed items are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual extension feed items. Type: object [ExtensionFeedItemOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ExtensionFeedItemOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.batchJobs.run"
    Runs the batch job.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>resourceName</td>
            <td>The resource name of the BatchJob to run.</td>
            <td>Yes</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.assetSets.mutate"
    Creates, updates or removes asset sets. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose asset sets are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual asset sets. Type: object [AssetSetOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/AssetSetOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.feedMappings.mutate"
    Creates or removes feed mappings. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose feed mappings are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual feed mappings. Type: object [FeedMappingOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/FeedMappingOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.experiments.endExperiment"
    Immediately ends an experiment, changing the experiment's scheduled end date and without waiting for end of day. End date is updated to be the time of the request.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>experiment</td>
            <td>The resource name of the campaign experiment to end.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.campaignDrafts.mutate"
    Creates, updates, or removes campaign drafts. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose campaign drafts are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual campaign drafts. Type: object [CampaignDraftOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/CampaignDraftOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.userLists.mutate"
    Creates or updates user lists. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose user lists are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual user lists. Type: object [UserListOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/UserListOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <googleAdNetwork.customers.userLists.mutate configKey="GOOGLE_AD_NETWORK_CONNECTION_1">
        <customerId>{json-eval($.customer_id)}</customerId>
        <operations>{json-eval($.operations)}</operations>
    </googleAdNetwork.customers.userLists.mutate>
    ```
 
    **Sample request**

    ```json
    {
        "customer_id": "3411480876",
        "operations": [
            {
                "create": {
                    "type": "UNSPECIFIED",
                    "name": "User list 1",
                    "readOnly": true,
                    "basicUserList": {
                        "actions": [
                            {
                                "conversionAction": "customers/3411480876/conversionActions/6878226201"
                            }
                        ]
                    }
                }
            }
        ]
    }
    ```

??? note "customers.generateKeywordIdeas"
    Returns a list of keyword ideas.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer with the recommendation.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>geoTargetConstants</td>
            <td>The resource names of the location to target. Maximum is 10. An empty list MAY be used to specify all targeting geos. Type: string</td>
            <td>No</td>
        </tr>
        <tr>
            <td>includeAdultKeywords</td>
            <td>If true, adult keywords will be included in response. The default value is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>pageToken</td>
            <td>Token of the page to retrieve. If not specified, the first page of results will be returned. To request next page of results use the value obtained fromnextPageTokenin the previous response. The request fields must match across pages. Type: string</td>
            <td>No</td>
        </tr>
        <tr>
            <td>pageSize</td>
            <td>Number of results to retrieve in a single page. A maximum of 10,000 results may be returned, if the pageSize exceeds this, it is ignored. If unspecified, at most 10,000 results will be returned. The server may decide to further limit the number of returned resources. If the response contains fewer than 10,000 results it may not be assumed as last page of results. Type: integer</td>
            <td>No</td>
        </tr>
        <tr>
            <td>keywordPlanNetwork</td>
            <td>Targeting network. If not set, Google Search And Partners Network will be used. Type: enum [KeywordPlanNetwork](https://developers.google.com/google-ads/api/rest/reference/rest/v17/KeywordPlanNetwork)</td>
            <td>No</td>
        </tr>
        <tr>
            <td>keywordAnnotation</td>
            <td>The keyword annotations to include in response. Type: enum [KeywordPlanKeywordAnnotation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/KeywordPlanKeywordAnnotation)</td>
            <td>No</td>
        </tr>
        <tr>
            <td>aggregateMetrics</td>
            <td>The aggregate fields to include in response. Type: object [KeywordPlanAggregateMetrics](https://developers.google.com/google-ads/api/rest/reference/rest/v17/KeywordPlanAggregateMetrics)</td>
            <td>No</td>
        </tr>
        <tr>
            <td>historicalMetricsOptions</td>
            <td>The options for historical metrics data. Type: object [HistoricalMetricsOptions](https://developers.google.com/google-ads/api/rest/reference/rest/v17/HistoricalMetricsOptions)</td>
            <td>No</td>
        </tr>
        <tr>
            <td>language</td>
            <td>The resource name of the language to target. Each keyword belongs to some set of languages; a keyword is included if language is one of its languages. If not set, all keywords will be included. Type: string</td>
            <td>No</td>
        </tr>
        <tr>
            <td>keywordAndUrlSeed</td>
            <td>A Keyword and a specific Url to generate ideas from for example, cars, www.example.com/cars. Type: object [KeywordAndUrlSeed](https://developers.google.com/google-ads/api/rest/reference/rest/v17/KeywordAndUrlSeed)</td>
            <td>No</td>
        </tr>
        <tr>
            <td>keywordSeed</td>
            <td>A Keyword or phrase to generate ideas from, for example, cars. Type: object [KeywordSeed](https://developers.google.com/google-ads/api/rest/reference/rest/v17/KeywordSeed)</td>
            <td>No</td>
        </tr>
        <tr>
            <td>urlSeed</td>
            <td>A specific url to generate ideas from, for example, www.example.com/cars. Type: object [UrlSeed](https://developers.google.com/google-ads/api/rest/reference/rest/v17/UrlSeed)</td>
            <td>No</td>
        </tr>
        <tr>
            <td>siteSeed</td>
            <td>The site to generate ideas from, for example, www.example.com. Type: object [SiteSeed](https://developers.google.com/google-ads/api/rest/reference/rest/v17/SiteSeed)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.smartCampaignSettings.getSmartCampaignStatus"
    Returns the status of the requested Smart campaign.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>resourceName</td>
            <td>The resource name of the Smart campaign setting belonging to the Smart campaign to fetch the status of.</td>
            <td>Yes</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.conversionValueRules.mutate"
    Creates, updates, or removes conversion value rules. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose conversion value rules are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual conversion value rules. Type: object [ConversionValueRuleOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ConversionValueRuleOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.thirdPartyAppAnalyticsLinks.regenerateShareableLinkId"
    Regenerate ThirdPartyAppAnalyticsLink.shareable_link_id that should be provided to the third party when setting up app analytics.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>resourceName</td>
            <td>Resource name of the third party app analytics link.</td>
            <td>Yes</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.productLinkInvitations.update"
    Update a product link invitation.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>productLinkInvitationStatus</td>
            <td>The product link invitation to be created. Type: enum [ProductLinkInvitationStatus](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ProductLinkInvitationStatus)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>resourceName</td>
            <td>Resource name of the product link invitation. Type: string</td>
            <td>Yes</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "googleAdsFields.get"
    Returns just the requested field.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>resourceName</td>
            <td>The resource name of the field to get.</td>
            <td>Yes</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.generateShareablePreviews"
    Returns the requested Shareable Preview.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The customer creating the shareable previews request.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>shareablePreviews</td>
            <td>The list of shareable previews to generate. Type: object [ShareablePreview](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ShareablePreview)</td>
            <td>Yes</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.campaignFeeds.mutate"
    Creates, updates, or removes campaign feeds. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose campaign feeds are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual campaign feeds. Type: object [CampaignFeedOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/CampaignFeedOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.customerLifecycleGoal.configureCustomerLifecycleGoals"
    Process the given customer lifecycle configurations.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer performing the upload.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operation</td>
            <td>The operation to perform customer lifecycle goal update. Type: object [CustomerLifecycleGoalOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/CustomerLifecycleGoalOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>Optional. If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.customerUserAccesses.mutate"
    Updates, removes permission of a user on a given customer. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operation</td>
            <td>The operation to perform on the customer Type: object [CustomerUserAccessOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/CustomerUserAccessOperation)</td>
            <td>Yes</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.generateAdGroupThemes"
    Returns a list of suggested AdGroups and suggested modifications (text, match type) for the given keywords.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>keywords</td>
            <td>A list of keywords to group into the provided AdGroups. Type: string</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>adGroups</td>
            <td>A list of resource names of AdGroups to group keywords into.  Resource name format:customers/{customerId}/adGroups/{adGroupId} Type: string</td>
            <td>Yes</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.experimentArms.mutate"
    Creates, updates, or removes experiment arms. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose experiments are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual experiment arm. Type: object [ExperimentArmOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ExperimentArmOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.adParameters.mutate"
    Creates, updates, or removes ad parameters. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose ad parameters are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual ad parameters. Type: object [AdParameterOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/AdParameterOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.campaignCustomizers.mutate"
    Creates, updates or removes campaign customizers. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose campaign customizers are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual campaign customizers. Type: object [CampaignCustomizerOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/CampaignCustomizerOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.generateReachForecast"
    Generates a reach forecast for a given targeting / product mix.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>campaignDuration</td>
            <td>Campaign duration. Type: object [CampaignDuration](https://developers.google.com/google-ads/api/rest/reference/rest/v17/CampaignDuration)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>cookieFrequencyCapSetting</td>
            <td>Chosen cookie frequency cap to be applied to each planned product. This is equivalent to the frequency cap exposed in Google Ads when creating a campaign, it represents the maximum number of times an ad can be shown to the same user during a specified time interval. If not specified, a default of 0 (no cap) is applied. Type: object [FrequencyCap](https://developers.google.com/google-ads/api/rest/reference/rest/v17/FrequencyCap)</td>
            <td>No</td>
        </tr>
        <tr>
            <td>targeting</td>
            <td>The targeting to be applied to all products selected in the product mix. Type: object [Targeting](https://developers.google.com/google-ads/api/rest/reference/rest/v17/Targeting)</td>
            <td>No</td>
        </tr>
        <tr>
            <td>plannedProducts</td>
            <td>The products to be forecast. The max number of allowed planned products is 15. Type: object [PlannedProduct](https://developers.google.com/google-ads/api/rest/reference/rest/v17/PlannedProduct)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>forecastMetricOptions</td>
            <td>Controls the forecast metrics returned in the response. Type: object [ForecastMetricOptions](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ForecastMetricOptions)</td>
            <td>No</td>
        </tr>
        <tr>
            <td>currencyCode</td>
            <td>The currency code. Three-character ISO 4217 currency code. Type: string</td>
            <td>No</td>
        </tr>
        <tr>
            <td>cookieFrequencyCap</td>
            <td>Chosen cookie frequency cap to be applied to each planned product. This is equivalent to the frequency cap exposed in Google Ads when creating a campaign, it represents the maximum number of times an ad can be shown to the same user. If not specified, no cap is applied. Type: integer</td>
            <td>No</td>
        </tr>
        <tr>
            <td>minEffectiveFrequency</td>
            <td>Chosen minimum effective frequency (the number of times a person was exposed to the ad) for the reported reach metrics [1-10]. This won't affect the targeting, but just the reporting. If not specified, a default of 1 is applied. Type: integer</td>
            <td>No</td>
        </tr>
        <tr>
            <td>effectiveFrequencyLimit</td>
            <td>The highest minimum effective frequency (the number of times a person was exposed to the ad) value [1-10] to include in Forecast.effective_frequency_breakdowns. If not specified, Forecast.effective_frequency_breakdowns will not be provided. Type: object [EffectiveFrequencyLimit](https://developers.google.com/google-ads/api/rest/reference/rest/v17/EffectiveFrequencyLimit)</td>
            <td>No</td>
        </tr>
        <tr>
            <td>customerReachGroup</td>
            <td>The name of the customer being planned for. This is a user-defined value. Type: string</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.uploadClickConversions"
    Processes the given click conversions.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer performing the upload.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>conversions</td>
            <td>The conversions that are being uploaded. Type: object [ClickConversion](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ClickConversion)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. This should always be set to true. Seehttps://developers.google.com/google-ads/api/docs/best-practices/partial-failuresfor more information about partial failure. Type: boolean</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>debugEnabled</td>
            <td>If true, the API will perform all upload checks and return errors if any are found. If false, it will perform only basic input validation, skip subsequent upload checks, and return success even if no click was found for the provideduserIdentifiers. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>jobId</td>
            <td>Optional. Optional input to set job ID. Must be a non-negative number that is less than 2^31 if provided. If this field is not provided, the API will generate a job ID in the range [2^31, (2^63)-1]. The API will return the value for this request in thejobIdfield of theUploadClickConversionsResponse. Type: integer</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.generateSuggestedTargetingInsights"
    Returns a collection of targeting insights (e.g. targetable audiences) that are relevant to the requested audience.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>audience</td>
            <td>The audience of interest for which insights are being requested. Type: object [InsightsAudience](https://developers.google.com/google-ads/api/rest/reference/rest/v17/InsightsAudience)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>baselineAudience</td>
            <td>Optional. The baseline audience. The default, if unspecified, is all people in the same country as the audience of interest. Type: object [InsightsAudience](https://developers.google.com/google-ads/api/rest/reference/rest/v17/InsightsAudience)</td>
            <td>No</td>
        </tr>
        <tr>
            <td>dataMonth</td>
            <td>Optional. The one-month range of historical data to use for insights, in the format "yyyy-mm". If unset, insights will be returned for the last thirty days of data. Type: string</td>
            <td>No</td>
        </tr>
        <tr>
            <td>customerInsightsGroup</td>
            <td>Optional. The name of the customer being planned for. This is a user-defined value. Type: string</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.assetGroupAssets.mutate"
    Creates, updates or removes asset group assets. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose asset group assets are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual asset group assets. Type: object [AssetGroupAssetOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/AssetGroupAssetOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.campaignConversionGoals.mutate"
    Creates, updates or removes campaign conversion goals. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose campaign conversion goals are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual campaign conversion goal. Type: object [CampaignConversionGoalOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/CampaignConversionGoalOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.customizerAttributes.mutate"
    Creates, updates or removes customizer attributes. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose customizer attributes are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual customizer attributes. Type: object [CustomizerAttributeOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/CustomizerAttributeOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.adGroupAdLabels.mutate"
    Creates and removes ad group ad labels. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>ID of the customer whose ad group ad labels are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on ad group ad labels. Type: object [AdGroupAdLabelOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/AdGroupAdLabelOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.campaignAssetSets.mutate"
    Creates, updates or removes campaign asset sets. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose campaign asset sets are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual campaign asset sets. Type: object [CampaignAssetSetOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/CampaignAssetSetOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.customerUserAccessInvitations.mutate"
    Creates or removes an access invitation.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose access invitation is being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operation</td>
            <td>The operation to perform on the access invitation Type: object [CustomerUserAccessInvitationOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/CustomerUserAccessInvitationOperation)</td>
            <td>Yes</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.uploadUserData"
    Uploads the given user data.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer for which to update the user data.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to be done. Type: object [UserDataOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/UserDataOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>customerMatchUserListMetadata</td>
            <td>Metadata for data updates to a Customer Match user list. Type: object [CustomerMatchUserListMetadata](https://developers.google.com/google-ads/api/rest/reference/rest/v17/CustomerMatchUserListMetadata)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.audiences.mutate"
    Creates audiences. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose audiences are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual audiences. Type: object [AudienceOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/AudienceOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.operations.get"
    Gets the latest state of a long-running operation. Clients can use this method to poll the operation result at intervals as recommended by the API service.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>name</td>
            <td>The name of the operation resource.</td>
            <td>Yes</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.suggestTravelAssets"
    Returns Travel Asset suggestions. Asset suggestions are returned on a best-effort basis. There are no guarantees that all possible asset types will be returned for any given hotel property.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>languageOption</td>
            <td>The language specifications in BCP 47 format (for example, en-US, zh-CN, etc.) for the asset suggestions. Text will be in this language. Usually matches one of the campaign target languages. Type: string</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>placeIds</td>
            <td>The Google Maps Place IDs of hotels for which assets are requested. Seehttps://developers.google.com/places/web-service/place-idfor more information. Type: string</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.experiments.promoteExperiment"
    Promotes the trial campaign thus applying changes in the trial campaign to the base campaign. This method returns a long running operation that tracks the promotion of the experiment campaign. If it fails, a list of errors can be retrieved using the experiments.listExperimentAsyncErrors method. The operation's metadata will be a string containing the resource name of the created experiment.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>resourceName</td>
            <td>The resource name of the experiment to promote.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.productLinks.create"
    Creates a product link.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer for which the product link is created.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>productLink</td>
            <td>The product link to be created. Type: object [ProductLink](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ProductLink)</td>
            <td>Yes</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.recommendations.apply"
    Applies given recommendations with corresponding apply parameters.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer with the recommendation.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to apply recommendations. If partialFailure=false all recommendations should be of the same type There is a limit of 100 operations per request. Type: object [ApplyRecommendationOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ApplyRecommendationOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, operations will be carried out as a transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.generateInsightsFinderReport"
    Creates a saved report that can be viewed in the Insights Finder tool.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>baselineAudience</td>
            <td>A baseline audience for this report, typically all people in a region. Type: object [BasicInsightsAudience](https://developers.google.com/google-ads/api/rest/reference/rest/v17/BasicInsightsAudience)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>specificAudience</td>
            <td>The specific audience of interest for this report. The insights in the report will be based on attributes more prevalent in this audience than in the report's baseline audience. Type: object [BasicInsightsAudience](https://developers.google.com/google-ads/api/rest/reference/rest/v17/BasicInsightsAudience)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>customerInsightsGroup</td>
            <td>The name of the customer being planned for. This is a user-defined value. Type: string</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.experiments.listExperimentAsyncErrors"
    Returns all errors that occurred during the last Experiment update (either scheduling or promotion). Supports standard list paging.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>resourceName</td>
            <td>The name of the experiment from which to retrieve the async errors.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>pageToken</td>
            <td>Token of the page to retrieve. If not specified, the first page of results will be returned. Use the value obtained fromnextPageTokenin the previous response in order to request the next page of results.</td>
            <td>No</td>
        </tr>
        <tr>
            <td>pageSize</td>
            <td>Number of elements to retrieve in a single page. When a page request is too large, the server may decide to further limit the number of returned resources. The maximum page size is 1000.</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.operations.wait"
    Waits until the specified long-running operation is done or reaches at most a specified timeout, returning the latest state. If the operation is already done, the latest state is immediately returned. If the timeout specified is greater than the default HTTP/RPC timeout, the HTTP/RPC timeout is used. If the server does not support this method, it returnsgoogle.rpc.Code.UNIMPLEMENTED. Note that this method is on a best-effort basis. It may return the latest state before the specified timeout (including immediately), meaning even an immediate response is no guarantee that the operation is done.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>name</td>
            <td>The name of the operation resource to wait on.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>timeout</td>
            <td>The maximum duration to wait before timing out. If left blank, the wait will be at most the time permitted by the underlying HTTP/RPC protocol. If RPC context deadline is also specified, the shorter one will be used. Type: string (Durationformat)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.productLinkInvitations.remove"
    Remove a product link invitation.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the product link invitation being removed.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>resourceName</td>
            <td>The resource name of the product link invitation being removed. expected, in this format: Type: string</td>
            <td>Yes</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.assetGroupSignals.mutate"
    Creates or removes asset group signals. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose asset group signals are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual asset group signals. Type: object [AssetGroupSignalOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/AssetGroupSignalOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.feedItems.mutate"
    Creates, updates, or removes feed items. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose feed items are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual feed items. Type: object [FeedItemOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/FeedItemOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.experiments.mutate"
    Creates, updates, or removes experiments. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose experiments are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual experiments. Type: object [ExperimentOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ExperimentOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.googleAds.mutate"
    Creates, updates, or removes resources. This method supports atomic transactions with multiple types of resources. For example, you can atomically create a campaign and a campaign budget, or perform up to thousands of mutates atomically.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose resources are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>mutateOperations</td>
            <td>The list of operations to perform on individual resources. Type: object [MutateOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/MutateOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. The mutable resource will only be returned if the resource has the appropriate response field. For example, MutateCampaignResult.campaign. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.labels.mutate"
    Creates, updates, or removes labels. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>ID of the customer whose labels are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on labels. Type: object [LabelOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/LabelOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.customerExtensionSettings.mutate"
    Creates, updates, or removes customer extension settings. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose customer extension settings are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual customer extension settings. Type: object [CustomerExtensionSettingOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/CustomerExtensionSettingOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.assets.mutate"
    Creates assets. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose assets are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual assets. Type: object [AssetOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/AssetOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.feedItemSets.mutate"
    Creates, updates or removes feed item sets. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose feed item sets are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual feed item sets. Type: object [FeedItemSetOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/FeedItemSetOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.campaignCriteria.mutate"
    Creates, updates, or removes criteria. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose criteria are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual criteria. Type: object [CampaignCriterionOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/CampaignCriterionOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.generateAudienceOverlapInsights"
    Returns a collection of audience attributes along with estimates of the overlap between their potential YouTube reach and that of a given input attribute.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>countryLocation</td>
            <td>The country in which to calculate the sizes and overlaps of audiences. Type: object [LocationInfo](https://developers.google.com/google-ads/api/rest/reference/rest/v17/LocationInfo)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>primaryAttribute</td>
            <td>The audience attribute that should be intersected with all other eligible audiences. This must be an Affinity or In-Market UserInterest, an AgeRange or a Gender. Type: object [AudienceInsightsAttribute](https://developers.google.com/google-ads/api/rest/reference/rest/v17/AudienceInsightsAttribute)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>dimensions</td>
            <td>The types of attributes of which to calculate the overlap with the primaryAttribute. The values must be a subset of AFFINITY_USER_INTEREST, IN_MARKET_USER_INTEREST, AGE_RANGE and GENDER. Type: enum [AudienceInsightsDimension](https://developers.google.com/google-ads/api/rest/reference/rest/v17/AudienceInsightsDimension)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>customerInsightsGroup</td>
            <td>The name of the customer being planned for. This is a user-defined value. Type: string</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.listAccessibleCustomers"
    Returns resource names of customers directly accessible by the user authenticating the call.

    **Sample configuration**

    ```xml
    <googleAdNetwork.customers.listAccessibleCustomers configKey="GOOGLE_AD_NETWORK_CONNECTION_1"/>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.invoices.list"
    Returns all invoices associated with a billing setup, for a given month.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer to fetch invoices for.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>billingSetup</td>
            <td>The billing setup resource name of the requested invoices.</td>
            <td>No</td>
        </tr>
        <tr>
            <td>issueYear</td>
            <td>The issue year to retrieve invoices, in yyyy format. Only invoices issued in 2019 or later can be retrieved.</td>
            <td>No</td>
        </tr>
        <tr>
            <td>issueMonth</td>
            <td>The issue month to retrieve invoices.</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.assetSetAssets.mutate"
    Creates, updates or removes asset set assets. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose asset set assets are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual asset set assets. Type: object [AssetSetAssetOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/AssetSetAssetOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.uploadCallConversions"
    Processes the given call conversions.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer performing the upload.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>conversions</td>
            <td>The conversions that are being uploaded. Type: object [CallConversion](https://developers.google.com/google-ads/api/rest/reference/rest/v17/CallConversion)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. This should always be set to true. Seehttps://developers.google.com/google-ads/api/docs/best-practices/partial-failuresfor more information about partial failure. Type: boolean</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.sharedSets.mutate"
    Creates, updates, or removes shared sets. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose shared sets are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual shared sets. Type: object [SharedSetOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/SharedSetOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.campaignSharedSets.mutate"
    Creates or removes campaign shared sets. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose campaign shared sets are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual campaign shared sets. Type: object [CampaignSharedSetOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/CampaignSharedSetOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.customerSkAdNetworkConversionValueSchemas.mutate"
    Creates or updates the CustomerSkAdNetworkConversionValueSchema.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose shared sets are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operation</td>
            <td>The operation to perform. Type: object [CustomerSkAdNetworkConversionValueSchemaOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/CustomerSkAdNetworkConversionValueSchemaOperation)</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>enableWarnings</td>
            <td>Optional. If true, enables returning warnings. Warnings return error messages and error codes without blocking the execution of the mutate operation. Type: boolean</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.createCustomerClient"
    Creates a new client under manager. The new client customer is returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the Manager under whom client customer is being created.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>customerClient</td>
            <td>The new client customer to create. The resource name on this customer will be ignored. Type: object [Customer](https://developers.google.com/google-ads/api/rest/reference/rest/v17/Customer)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>accessRole</td>
            <td>The proposed role of user on the created client customer. Accessible only to customers on the allow-list. Type: enum [AccessRole](https://developers.google.com/google-ads/api/rest/reference/rest/v17/AccessRole)</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>emailAddress</td>
            <td>Email address of the user who should be invited on the created client customer. Accessible only to customers on the allow-list. Type: string</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <googleAdNetwork.customers.createCustomerClient configKey="GOOGLE_AD_NETWORK_CONNECTION_1">
        <customerId>{json-eval($.account_id)}</customerId>
        <customerClient>{json-eval($.client_data)}</customerClient>
        <accessRole>{json-eval($.accessRole)}</accessRole>
        <validateOnly>{json-eval($.validateOnly)}</validateOnly>
        <emailAddress>{json-eval($.emailAddress)}</emailAddress>
    </googleAdNetwork.customers.createCustomerClient>
    ```
 
    **Sample request**

    ```json
    {
        "account_id":"7786178578",
        "accessRole": "STANDARD",
        "validateOnly": "true",
        "emailAddress":"test@test.com",
        "client_data":{
            "descriptiveName": "Client 1",
            "currencyCode": "USD",
            "timeZone": "America/New_York"
        }
    }
    ```

??? note "customers.productLinkInvitations.create"
    Creates a product link invitation.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>productLinkInvitation</td>
            <td>The product link invitation to be created. Type: object [ProductLinkInvitation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ProductLinkInvitation)</td>
            <td>Yes</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.customConversionGoals.mutate"
    Creates, updates or removes custom conversion goals. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose custom conversion goals are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual custom conversion goal. Type: object [CustomConversionGoalOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/CustomConversionGoalOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.customerLabels.mutate"
    Creates and removes customer-label relationships. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>ID of the customer whose customer-label relationships are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on customer-label relationships. Type: object [CustomerLabelOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/CustomerLabelOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.customerAssets.mutate"
    Creates, updates, or removes customer assets. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose customer assets are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual customer assets. Type: object [CustomerAssetOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/CustomerAssetOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.ads.mutate"
    Updates ads. Operation statuses are returned. Updating ads is not supported for TextAd, ExpandedDynamicSearchAd, GmailAd and ImageAd.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose ads are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual ads. Type: object [AdOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/AdOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.experiments.graduateExperiment"
    Graduates an experiment to a full campaign.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>experiment</td>
            <td>The experiment to be graduated.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>campaignBudgetMappings</td>
            <td>List of campaign budget mappings for graduation. Each campaign that appears here will graduate, and will be assigned a new budget that is paired with it in the mapping. The maximum size is one. Type: object [CampaignBudgetMapping](https://developers.google.com/google-ads/api/rest/reference/rest/v17/CampaignBudgetMapping)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.suggestSmartCampaignAd"
    Suggests a Smart campaign ad compatible with the Ad family of resources, based on data points such as targeting and the business to advertise.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>suggestionInfo</td>
            <td>Inputs used to suggest a Smart campaign ad. Required fields: finalUrl, languageCode, keywordThemes. Optional but recommended fields to improve the quality of the suggestion: business_setting and geo_target. Type: object [SmartCampaignSuggestionInfo](https://developers.google.com/google-ads/api/rest/reference/rest/v17/SmartCampaignSuggestionInfo)</td>
            <td>Yes</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.experiments.scheduleExperiment"
    Schedule an experiment. The in design campaign will be converted into a real campaign (called the experiment campaign) that will begin serving ads if successfully created.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>resourceName</td>
            <td>The scheduled experiment.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.feedItemSetLinks.mutate"
    Creates, updates, or removes feed item set links.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose feed item set links are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual feed item set links. Type: object [FeedItemSetLinkOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/FeedItemSetLinkOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.biddingDataExclusions.mutate"
    Creates, updates, or removes data exclusions. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>ID of the customer whose data exclusions are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual data exclusions. Type: object [BiddingDataExclusionOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/BiddingDataExclusionOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.productLinks.remove"
    Removes a product link.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>resourceName</td>
            <td>Remove operation: A resource name for the product link to remove is expected, in this format: Type: string</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.recommendations.dismiss"
    Dismisses given recommendations.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer with the recommendation.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to dismiss recommendations. If partialFailure=false all recommendations should be of the same type There is a limit of 100 operations per request. Type: object [DismissRecommendationOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/DismissRecommendationOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, operations will be carried in a single transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.assetGroups.mutate"
    Creates, updates or removes asset groups. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose asset groups are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual asset groups. Type: object [AssetGroupOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/AssetGroupOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.customerClientLinks.mutate"
    Creates or updates a customer client link. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose customer link are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operation</td>
            <td>The operation to perform on the individual CustomerClientLink. Type: object [CustomerClientLinkOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/CustomerClientLinkOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.customerFeeds.mutate"
    Creates, updates, or removes customer feeds. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose customer feeds are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual customer feeds. Type: object [CustomerFeedOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/CustomerFeedOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.sharedCriteria.mutate"
    Creates or removes shared criteria. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose shared criteria are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual shared criteria. Type: object [SharedCriterionOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/SharedCriterionOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.generateAudienceCompositionInsights"
    Returns a collection of attributes that are represented in an audience of interest, with metrics that compare each attribute's share of the audience with its share of a baseline audience.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>audience</td>
            <td>The audience of interest for which insights are being requested. Type: object [InsightsAudience](https://developers.google.com/google-ads/api/rest/reference/rest/v17/InsightsAudience)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>baselineAudience</td>
            <td>The baseline audience to which the audience of interest is being compared. Type: object [InsightsAudience](https://developers.google.com/google-ads/api/rest/reference/rest/v17/InsightsAudience)</td>
            <td>No</td>
        </tr>
        <tr>
            <td>dataMonth</td>
            <td>The one-month range of historical data to use for insights, in the format "yyyy-mm". If unset, insights will be returned for the last thirty days of data. Type: string</td>
            <td>No</td>
        </tr>
        <tr>
            <td>dimensions</td>
            <td>The audience dimensions for which composition insights should be returned. Type: enum [AudienceInsightsDimension](https://developers.google.com/google-ads/api/rest/reference/rest/v17/AudienceInsightsDimension)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>customerInsightsGroup</td>
            <td>The name of the customer being planned for. This is a user-defined value. Type: string</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.suggestKeywordThemes"
    Suggests keyword themes to advertise on.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>suggestionInfo</td>
            <td>Information to get keyword theme suggestions. Required fields: Type: object [SmartCampaignSuggestionInfo](https://developers.google.com/google-ads/api/rest/reference/rest/v17/SmartCampaignSuggestionInfo)</td>
            <td>Yes</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.offlineUserDataJobs.addOperations"
    Adds operations to the offline user data job.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>resourceName</td>
            <td>The resource name of the OfflineUserDataJob.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to be done. Type: object [OfflineUserDataJobOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/OfflineUserDataJobOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>enablePartialFailure</td>
            <td>True to enable partial failure for the offline user data job. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>enableWarnings</td>
            <td>True to enable warnings for the offline user data job. When enabled, a warning will not block the OfflineUserDataJobOperation, and will also return warning messages about malformed field values. Type: boolean</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.batchJobs.listResults"
    Returns the results of the batch job. The job must be done. Supports standard list paging.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>resourceName</td>
            <td>The resource name of the batch job whose results are being listed.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>pageToken</td>
            <td>Token of the page to retrieve. If not specified, the first page of results will be returned. Use the value obtained fromnextPageTokenin the previous response in order to request the next page of results.</td>
            <td>No</td>
        </tr>
        <tr>
            <td>pageSize</td>
            <td>Number of elements to retrieve in a single page. When a page request is too large, the server may decide to further limit the number of returned resources.</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned.</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.operations.cancel"
    Starts asynchronous cancellation on a long-running operation. The server makes a best effort to cancel the operation, but success is not guaranteed. If the server doesn't support this method, it returnsgoogle.rpc.Code.UNIMPLEMENTED. Clients can useOperations.GetOperationor other methods to check whether the cancellation succeeded or whether the operation completed despite cancellation. On successful cancellation, the operation is not deleted; instead, it becomes an operation with anOperation.errorvalue with agoogle.rpc.Status.codeof 1, corresponding toCode.CANCELLED.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>name</td>
            <td>The name of the operation resource to be cancelled.</td>
            <td>Yes</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.googleAds.search"
    Returns all rows that match the search query.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer being queried.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>query</td>
            <td>The query string. Type: string</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>pageToken</td>
            <td>Token of the page to retrieve. If not specified, the first page of results will be returned. Use the value obtained fromnextPageTokenin the previous response in order to request the next page of results. Type: string</td>
            <td>No</td>
        </tr>
        <tr>
            <td>pageSize</td>
            <td>Number of elements to retrieve in a single page. When too large a page is requested, the server may decide to further limit the number of returned resources. Type: integer</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>returnTotalResultsCount</td>
            <td>If true, the total number of results that match the query ignoring the LIMIT clause will be included in the response. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>summaryRowSetting</td>
            <td>Determines whether a summary row will be returned. By default, summary row is not returned. If requested, the summary row will be sent in a response by itself after all other query results are returned. Type: enum [SummaryRowSetting](https://developers.google.com/google-ads/api/rest/reference/rest/v17/SummaryRowSetting)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.customerNegativeCriteria.mutate"
    Creates or removes criteria. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose criteria are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual criteria. Type: object [CustomerNegativeCriterionOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/CustomerNegativeCriterionOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.generateKeywordForecastMetrics"
    Returns metrics (such as impressions, clicks, total cost) of a keyword forecast for the given campaign.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>forecastPeriod</td>
            <td>The date range for the forecast. The start date must be in the future and end date must be within 1 year from today. The reference timezone used is the one of the Google Ads account belonging to the customer. If not set, a default date range from next Sunday to the following Saturday will be used. Type: object [DateRange](https://developers.google.com/google-ads/api/rest/reference/rest/v17/DateRange)</td>
            <td>No</td>
        </tr>
        <tr>
            <td>campaign</td>
            <td>The campaign used in the forecast. Type: object [CampaignToForecast](https://developers.google.com/google-ads/api/rest/reference/rest/v17/CampaignToForecast)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>currencyCode</td>
            <td>The currency used for exchange rate conversion. By default, the account currency of the customer is used. Set this field only if the currency is different from the account currency. The list of valid currency codes can be found athttps://developers.google.com/google-ads/api/data/codes-formats#currency-codes. Type: string</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.feedItemTargets.mutate"
    Creates or removes feed item targets. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose feed item targets are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual feed item targets. Type: object [FeedItemTargetOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/FeedItemTargetOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.campaignBudgets.mutate"
    Creates, updates, or removes campaign budgets. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose campaign budgets are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual campaign budgets. Type: object [CampaignBudgetOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/CampaignBudgetOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <googleAdNetwork.customers.campaignBudgets.mutate configKey="GOOGLE_AD_NETWORK_CONNECTION_1">
        <customerId>{json-eval($.customer_id)}</customerId>
        <operations>{json-eval($.operations)}</operations>
    </googleAdNetwork.customers.campaignBudgets.mutate>
    ```
 
    **Sample request**

    ```json
    {
        "customer_id": "2219111829",
        "validateOnly": false,
        "operations": [
            {
                "create": {
                    "status": "UNSPECIFIED",
                    "type": "STANDARD",
                    "name": "Budget 1",
                    "amountMicros":"10000"
                }
            }
        ]
    }
    ```

??? note "customers.suggestBrands"
    Rpc to return a list of matching brands based on a prefix for this customer.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer onto which to apply the brand suggestion operation.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>selectedBrands</td>
            <td>Optional. Ids of the brands already selected by advertisers. They will be excluded in response. These are expected to be brand ids not brand names. Type: string</td>
            <td>No</td>
        </tr>
        <tr>
            <td>brandPrefix</td>
            <td>The prefix of a brand name. Type: string</td>
            <td>Yes</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.campaignDrafts.listAsyncErrors"
    Returns all errors that occurred during CampaignDraft promote. Throws an error if called before campaign draft is promoted. Supports standard list paging.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>resourceName</td>
            <td>The name of the campaign draft from which to retrieve the async errors.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>pageToken</td>
            <td>Token of the page to retrieve. If not specified, the first page of results will be returned. Use the value obtained fromnextPageTokenin the previous response in order to request the next page of results.</td>
            <td>No</td>
        </tr>
        <tr>
            <td>pageSize</td>
            <td>Number of elements to retrieve in a single page. When a page request is too large, the server may decide to further limit the number of returned resources.</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.customerManagerLinks.moveManagerLink"
    Moves a client customer to a new manager customer. This simplifies the complex request that requires two operations to move a client customer to a new manager, for example: 1. Update operation with Status INACTIVE (previous manager) and, 2. Update operation with Status ACTIVE (new manager).
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the client customer that is being moved.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>previousCustomerManagerLink</td>
            <td>The resource name of the previous CustomerManagerLink. The resource name has the form:customers/{customerId}/customerManagerLinks/{manager_customer_id}~{managerLinkId} Type: string</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>newManager</td>
            <td>The resource name of the new manager customer that the client wants to move to. Customer resource names have the format: "customers/{customerId}" Type: string</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.generateKeywordHistoricalMetrics"
    Returns a list of keyword historical metrics.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer with the recommendation.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>keywords</td>
            <td>A list of keywords to get historical metrics. Not all inputs will be returned as a result of near-exact deduplication. For example, if stats for "car" and "cars" are requested, only "car" will be returned. A maximum of 10,000 keywords can be used. Type: string</td>
            <td>No</td>
        </tr>
        <tr>
            <td>includeAdultKeywords</td>
            <td>If true, adult keywords will be included in response. The default value is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>geoTargetConstants</td>
            <td>The resource names of the location to target. Maximum is 10. An empty list MAY be used to specify all targeting geos. Type: string</td>
            <td>No</td>
        </tr>
        <tr>
            <td>keywordPlanNetwork</td>
            <td>Targeting network. If not set, Google Search And Partners Network will be used. Type: enum [KeywordPlanNetwork](https://developers.google.com/google-ads/api/rest/reference/rest/v17/KeywordPlanNetwork)</td>
            <td>No</td>
        </tr>
        <tr>
            <td>aggregateMetrics</td>
            <td>The aggregate fields to include in response. Type: object [KeywordPlanAggregateMetrics](https://developers.google.com/google-ads/api/rest/reference/rest/v17/KeywordPlanAggregateMetrics)</td>
            <td>No</td>
        </tr>
        <tr>
            <td>historicalMetricsOptions</td>
            <td>The options for historical metrics data. Type: object [HistoricalMetricsOptions](https://developers.google.com/google-ads/api/rest/reference/rest/v17/HistoricalMetricsOptions)</td>
            <td>No</td>
        </tr>
        <tr>
            <td>language</td>
            <td>The resource name of the language to target. Each keyword belongs to some set of languages; a keyword is included if language is one of its languages. If not set, all keywords will be included. Type: string</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.keywordPlanAdGroupKeywords.mutate"
    Creates, updates, or removes Keyword Plan ad group keywords. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose Keyword Plan ad group keywords are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual Keyword Plan ad group keywords. Type: object [KeywordPlanAdGroupKeywordOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/KeywordPlanAdGroupKeywordOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.customerConversionGoals.mutate"
    Creates, updates or removes customer conversion goals. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose customer conversion goals are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual customer conversion goal. Type: object [CustomerConversionGoalOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/CustomerConversionGoalOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.recommendationSubscriptions.mutateRecommendationSubscription"
    Mutates given subscription with corresponding apply parameters.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the subscribing customer.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of create or update operations. Type: object [RecommendationSubscriptionOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/RecommendationSubscriptionOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. The mutable resource will only be returned if the resource has the appropriate response field. For example, MutateCampaignResult.campaign. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.getIdentityVerification"
    Returns Identity Verification information.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer for whom we are requesting verification  information.</td>
            <td>Yes</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.conversionActions.mutate"
    Creates, updates or removes conversion actions. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose conversion actions are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual conversion actions. Type: object [ConversionActionOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ConversionActionOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <googleAdNetwork.customers.conversionActions.mutate configKey="GOOGLE_AD_NETWORK_CONNECTION_1">
        <customerId>{json-eval($.customer_id)}</customerId>
        <operations>{json-eval($.operations)}</operations>
    </googleAdNetwork.customers.conversionActions.mutate>
    ```
 
    **Sample request**

    ```json
    {
        "customer_id": "5500480119",
        "operations": [
            {
                "create": {
                    "status": "ENABLED",
                    "type": "AD_CALL",
                    "name": "Conversion action 1"
                }
            }
        ]
    }
    ```

??? note "customers.smartCampaignSettings.mutate"
    Updates Smart campaign settings for campaigns.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose Smart campaign settings are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual Smart campaign settings. Type: object [SmartCampaignSettingOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/SmartCampaignSettingOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.campaignDrafts.promote"
    Promotes the changes in a draft back to the base campaign.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>campaignDraft</td>
            <td>The resource name of the campaign draft to promote.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but no Long Running Operation is created. Only errors are returned. Type: boolean</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.startIdentityVerification"
    Starts Identity Verification for a given verification program type.  Statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The Id of the customer for whom we are creating this verification.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>verificationProgram</td>
            <td>The verification program type for which we want to start the verification. Type: enum [IdentityVerificationProgram](https://developers.google.com/google-ads/api/rest/reference/rest/v17/IdentityVerificationProgram)</td>
            <td>Yes</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.biddingSeasonalityAdjustments.mutate"
    Creates, updates, or removes seasonality adjustments. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>ID of the customer whose seasonality adjustments are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual seasonality adjustments. Type: object [BiddingSeasonalityAdjustmentOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/BiddingSeasonalityAdjustmentOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.accountLinks.mutate"
    Creates or removes an account link. From V5, create is not supported through AccountLinkService.MutateAccountLink. Use AccountLinkService.CreateAccountLink instead.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operation</td>
            <td>The operation to perform on the link. Type: object [AccountLinkOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/AccountLinkOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.googleAds.searchStream"
    Returns all rows that match the search stream query.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer being queried.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>query</td>
            <td>The query string. Type: string</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>summaryRowSetting</td>
            <td>Determines whether a summary row will be returned. By default, summary row is not returned. If requested, the summary row will be sent in a response by itself after all other query results are returned. Type: enum [SummaryRowSetting](https://developers.google.com/google-ads/api/rest/reference/rest/v17/SummaryRowSetting)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.batchJobs.mutate"
    Mutates a batch job.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer for which to create a batch job.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operation</td>
            <td>The operation to perform on an individual batch job. Type: object [BatchJobOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/BatchJobOperation)</td>
            <td>Yes</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "geoTargetConstants.suggest"
    Returns GeoTargetConstant suggestions by location name or by resource name.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>locale</td>
            <td>If possible, returned geo targets are translated using this locale. If not, en is used by default. This is also used as a hint for returned geo targets. Type: string</td>
            <td>No</td>
        </tr>
        <tr>
            <td>countryCode</td>
            <td>Returned geo targets are restricted to this country code. Type: string</td>
            <td>No</td>
        </tr>
        <tr>
            <td>locationNames</td>
            <td>The location names to search by. At most 25 names can be set. Type: object [LocationNames](https://developers.google.com/google-ads/api/rest/reference/rest/v17/LocationNames)</td>
            <td>No</td>
        </tr>
        <tr>
            <td>geoTargets</td>
            <td>The geo target constant resource names to filter by. Type: object [GeoTargets](https://developers.google.com/google-ads/api/rest/reference/rest/v17/GeoTargets)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <googleAdNetwork.geoTargetConstants.suggest configKey="GOOGLE_AD_NETWORK_CONNECTION_1">
        <locationNames>{json-eval($.location_names)}</locationNames>
    </googleAdNetwork.geoTargetConstants.suggest>
    ```
 
    **Sample request**

    ```json
    {
        "location_names": {
            "names":[
                "Colombo"
            ]
        }
    }
    ```

??? note "audienceInsights.listInsightsEligibleDates"
    Lists date ranges for which audience insights data can be requested.

    **Sample configuration**

    ```xml
    <googleAdNetwork.audienceInsights.listInsightsEligibleDates configKey="GOOGLE_AD_NETWORK_CONNECTION_1"/>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.adGroupBidModifiers.mutate"
    Creates, updates, or removes ad group bid modifiers. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>ID of the customer whose ad group bid modifiers are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual ad group bid modifiers. Type: object [AdGroupBidModifierOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/AdGroupBidModifierOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.conversionGoalCampaignConfigs.mutate"
    Creates, updates or removes conversion goal campaign config. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose custom conversion goals are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual conversion goal campaign config. Type: object [ConversionGoalCampaignConfigOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ConversionGoalCampaignConfigOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.accountBudgetProposals.mutate"
    Creates, updates, or removes account budget proposals. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operation</td>
            <td>The operation to perform on an individual account-level budget proposal. Type: object [AccountBudgetProposalOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/AccountBudgetProposalOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.customerAssetSets.mutate"
    Creates, or removes customer asset sets. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose customer asset sets are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual customer asset sets. Type: object [CustomerAssetSetOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/CustomerAssetSetOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.adGroupAds.mutate"
    Creates, updates, or removes ads. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose ads are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual ads. Type: object [AdGroupAdOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/AdGroupAdOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.batchJobs.addOperations"
    Add operations to the batch job.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>resourceName</td>
            <td>The resource name of the batch job.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>sequenceToken</td>
            <td>A token used to enforce sequencing. Type: string</td>
            <td>No</td>
        </tr>
        <tr>
            <td>mutateOperations</td>
            <td>The list of mutates being added. Type: object [MutateOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/MutateOperation)</td>
            <td>Yes</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.accountLinks.create"
    Creates an account link.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer for which the account link is created.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>accountLink</td>
            <td>The account link to be created. Type: object [AccountLink](https://developers.google.com/google-ads/api/rest/reference/rest/v17/AccountLink)</td>
            <td>Yes</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.mutate"
    Updates a customer. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operation</td>
            <td>The operation to perform on the customer Type: object [CustomerOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/CustomerOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <googleAdNetwork.customers.mutate configKey="GOOGLE_AD_NETWORK_CONNECTION_1">
        <customerId>{json-eval($.customer_id)}</customerId>
        <operation>{json-eval($.operation)}</operation>
        <validateOnly>{json-eval($.validate_only)}</validateOnly>
    </googleAdNetwork.customers.mutate>
    ```
 
    **Sample request**

    ```json
    {
        "customer_id": "2219900119",
        "validate_only": false,
        "operation": {
            "update": {
                "resourceName": "customers/2219900119",
                "descriptiveName": "MyClient Updated"
            },
            "updateMask": "descriptiveName"
        }
    }
    ```

??? note "customers.recommendations.generate"
    Generates Recommendations based off the requested recommendationTypes.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer generating recommendations.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>recommendationTypes</td>
            <td>List of eligible recommendationTypes to generate. If the uploaded criteria isn't sufficient to make a recommendation, or the campaign is already in the recommended state, no recommendation will be returned for that type. Generally, a recommendation is returned if all required fields for that recommendationType are uploaded, but there are cases where this is still not sufficient. Type: enum [RecommendationType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/RecommendationType)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>advertisingChannelType</td>
            <td>Advertising channel type of the campaign. The following advertisingChannelTypes are supported for recommendation generation: PERFORMANCE_MAX and SEARCH Type: enum [AdvertisingChannelType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/AdvertisingChannelType)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>adGroupInfo</td>
            <td>Optional. Current AdGroup Information. Supports information from a single AdGroup. This field is optional for the following recommendationTypes: KEYWORD Type: object [AdGroupInfo](https://developers.google.com/google-ads/api/rest/reference/rest/v17/AdGroupInfo)</td>
            <td>No</td>
        </tr>
        <tr>
            <td>campaignSitelinkCount</td>
            <td>Optional. Number of sitelinks on the campaign. This field is necessary for the following recommendationTypes: SITELINK_ASSET Type: integer</td>
            <td>No</td>
        </tr>
        <tr>
            <td>conversionTrackingStatus</td>
            <td>Optional. Current conversion tracking status. This field is necessary for the following recommendationTypes: MAXIMIZE_CLICKS_OPT_IN, MAXIMIZE_CONVERSIONS_OPT_IN, MAXIMIZE_CONVERSION_VALUE_OPT_IN, SET_TARGET_CPA, SET_TARGET_ROAS, TARGET_CPA_OPT_IN, TARGET_ROAS_OPT_IN Type: enum [ConversionTrackingStatus](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ConversionTrackingStatus)</td>
            <td>No</td>
        </tr>
        <tr>
            <td>biddingInfo</td>
            <td>Optional. Current bidding information of the campaign. This field is necessary for the following recommendationTypes: MAXIMIZE_CLICKS_OPT_IN, MAXIMIZE_CONVERSIONS_OPT_IN, MAXIMIZE_CONVERSION_VALUE_OPT_IN, SET_TARGET_CPA, SET_TARGET_ROAS, TARGET_CPA_OPT_IN, TARGET_ROAS_OPT_IN Type: object [BiddingInfo](https://developers.google.com/google-ads/api/rest/reference/rest/v17/BiddingInfo)</td>
            <td>No</td>
        </tr>
        <tr>
            <td>seedInfo</td>
            <td>Optional. Seed information for Keywords. This field is necessary for the following recommendationTypes: KEYWORD Type: object [SeedInfo](https://developers.google.com/google-ads/api/rest/reference/rest/v17/SeedInfo)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.userListCustomerTypes.mutate"
    Attach or remove user list customer types. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose user list customer types are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on the user list customer types. Type: object [UserListCustomerTypeOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/UserListCustomerTypeOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>Optional. If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>Optional. If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.adGroupCriterionLabels.mutate"
    Creates and removes ad group criterion labels. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>ID of the customer whose ad group criterion labels are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on ad group criterion labels. Type: object [AdGroupCriterionLabelOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/AdGroupCriterionLabelOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.customInterests.mutate"
    Creates or updates custom interests. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose custom interests are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual custom interests. Type: object [CustomInterestOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/CustomInterestOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.keywordPlanAdGroups.mutate"
    Creates, updates, or removes Keyword Plan ad groups. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose Keyword Plan ad groups are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual Keyword Plan ad groups. Type: object [KeywordPlanAdGroupOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/KeywordPlanAdGroupOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <googleAdNetwork.customers.adGroups.mutate configKey="GOOGLE_AD_NETWORK_CONNECTION_1">
        <customerId>{json-eval($.customer_id)}</customerId>
        <operations>{json-eval($.operations)}</operations>
        <validateOnly>{json-eval($.validateOnly)}</validateOnly>
    </googleAdNetwork.customers.adGroups.mutate>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.keywordPlans.mutate"
    Creates, updates, or removes keyword plans. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose keyword plans are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual keyword plans. Type: object [KeywordPlanOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/KeywordPlanOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.paymentsAccounts.list"
    Returns all payments accounts associated with all managers between the login customer ID and specified serving customer in the hierarchy, inclusive.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer to apply the PaymentsAccount list operation to.</td>
            <td>Yes</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.adGroupAds.removeAutomaticallyCreatedAssets"
    Remove automatically created assets from an ad.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>adGroupAd</td>
            <td>The resource name of the AdGroupAd from which to remove automatically created assets.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>assetsWithFieldType</td>
            <td>List of assets with field type to be removed from the AdGroupAd. Type: object [AssetsWithFieldType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/AssetsWithFieldType)</td>
            <td>Yes</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.conversionValueRuleSets.mutate"
    Creates, updates or removes conversion value rule sets. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose conversion value rule sets are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual conversion value rule sets. Type: object [ConversionValueRuleSetOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ConversionValueRuleSetOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.suggestSmartCampaignBudgetOptions"
    Returns BudgetOption suggestions.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose budget options are to be suggested.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>campaign</td>
            <td>The resource name of the campaign to get suggestion for. Type: string</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>suggestionInfo</td>
            <td>Information needed to get budget options Type: object [SmartCampaignSuggestionInfo](https://developers.google.com/google-ads/api/rest/reference/rest/v17/SmartCampaignSuggestionInfo)</td>
            <td>Yes</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.customerManagerLinks.mutate"
    Updates customer manager links. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose customer manager links are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual customer manager links. Type: object [CustomerManagerLinkOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/CustomerManagerLinkOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.campaignLifecycleGoal.configureCampaignLifecycleGoals"
    Process the given campaign lifecycle configurations.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer performing the upload.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operation</td>
            <td>The operation to perform campaign lifecycle goal update. Type: object [CampaignLifecycleGoalOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/CampaignLifecycleGoalOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>Optional. If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "listPlannableLocations"
    Returns the list of plannable locations (for example, countries).

    **Sample configuration**

    ```xml
    <googleAdNetwork.listPlannableLocations configKey="GOOGLE_AD_NETWORK_CONNECTION_1"/>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.feeds.mutate"
    Creates, updates, or removes feeds. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose feeds are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual feeds. Type: object [FeedOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/FeedOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.adGroups.mutate"
    Creates, updates, or removes ad groups. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose ad groups are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual ad groups. Type: object [AdGroupOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/AdGroupOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.campaignLabels.mutate"
    Creates and removes campaign-label relationships. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>ID of the customer whose campaign-label relationships are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on campaign-label relationships. Type: object [CampaignLabelOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/CampaignLabelOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.keywordPlanCampaigns.mutate"
    Creates, updates, or removes Keyword Plan campaigns. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose Keyword Plan campaigns are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual Keyword Plan campaigns. Type: object [KeywordPlanCampaignOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/KeywordPlanCampaignOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.offlineUserDataJobs.create"
    Creates an offline user data job.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer for which to create an offline user data job.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>job</td>
            <td>The offline user data job to be created. Type: object [OfflineUserDataJob](https://developers.google.com/google-ads/api/rest/reference/rest/v17/OfflineUserDataJob)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>enableMatchRateRangePreview</td>
            <td>If true, match rate range for the offline user data job is calculated and made available in the resource. Type: boolean</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.campaignAssets.mutate"
    Creates, updates, or removes campaign assets. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose campaign assets are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual campaign assets. Type: object [CampaignAssetOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/CampaignAssetOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.uploadConversionAdjustments"
    Processes the given conversion adjustments.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer performing the upload.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>conversionAdjustments</td>
            <td>The conversion adjustments that are being uploaded. Type: object [ConversionAdjustment](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ConversionAdjustment)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. This should always be set to true. Seehttps://developers.google.com/google-ads/api/docs/best-practices/partial-failuresfor more information about partial failure. Type: boolean</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>jobId</td>
            <td>Optional. Optional input to set job ID. Must be a non-negative number that is less than 2^31 if provided. If this field is not provided, the API will generate a job ID in the range [2^31, (2^63)-1]. The API will return the value for this request in thejobIdfield of theUploadConversionAdjustmentsResponse. Type: integer</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.biddingStrategies.mutate"
    Creates, updates, or removes bidding strategies. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose bidding strategies are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual bidding strategies. Type: object [BiddingStrategyOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/BiddingStrategyOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <googleAdNetwork.customers.biddingStrategies.mutate configKey="GOOGLE_AD_NETWORK_CONNECTION_1">
        <customerId>{json-eval($.customer_id)}</customerId>
        <operations>{json-eval($.operations)}</operations>
    </googleAdNetwork.customers.biddingStrategies.mutate>
    ```
 
    **Sample request**

    ```json
    {
        "customer_id": "5519120659",
        "operations": [
            {
                "create": {
                    "name": "Test Bidding strategy 1",
                    "maximizeConversionValue":{
                        "targetRoas":5,
                        "cpcBidCeilingMicros":"100000",
                        "cpcBidFloorMicros":"80000"
                    }
                }
            }
        ]
    }
    ```

??? note "customers.offlineUserDataJobs.run"
    Runs the offline user data job.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>resourceName</td>
            <td>The resource name of the OfflineUserDataJob to run.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.campaignGroups.mutate"
    Creates, updates, or removes campaign groups. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose campaign groups are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual campaign groups. Type: object [CampaignGroupOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/CampaignGroupOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.adGroupCriteria.mutate"
    Creates, updates, or removes criteria. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>ID of the customer whose criteria are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual criteria. Type: object [AdGroupCriterionOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/AdGroupCriterionOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "listPlannableProducts"
    Returns the list of per-location plannable YouTube ad formats with allowed targeting.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>plannableLocationId</td>
            <td>The ID of the selected location for planning. To list the available plannable location IDs useReachPlanService.ListPlannableLocations. Type: string</td>
            <td>Yes</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.adGroupLabels.mutate"
    Creates and removes ad group labels. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>ID of the customer whose ad group labels are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on ad group labels. Type: object [AdGroupLabelOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/AdGroupLabelOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.adGroupFeeds.mutate"
    Creates, updates, or removes ad group feeds. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose ad group feeds are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual ad group feeds. Type: object [AdGroupFeedOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/AdGroupFeedOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "googleAdsFields.search"
    Returns all fields that match the search query.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>query</td>
            <td>The query string. Type: string</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>pageToken</td>
            <td>Token of the page to retrieve. If not specified, the first page of results will be returned. Use the value obtained fromnextPageTokenin the previous response in order to request the next page of results. Type: string</td>
            <td>No</td>
        </tr>
        <tr>
            <td>pageSize</td>
            <td>Number of elements to retrieve in a single page. When too large a page is requested, the server may decide to further limit the number of returned resources. Type: integer</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.adGroupAssets.mutate"
    Creates, updates, or removes ad group assets. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose ad group assets are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual ad group assets. Type: object [AdGroupAssetOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/AdGroupAssetOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.customAudiences.mutate"
    Creates or updates custom audiences. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose custom audiences are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual custom audiences. Type: object [CustomAudienceOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/CustomAudienceOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.adGroupAssetSets.mutate"
    Creates, or removes ad group asset sets. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose ad group asset sets are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual ad group asset sets. Type: object [AdGroupAssetSetOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/AdGroupAssetSetOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.adGroupCustomizers.mutate"
    Creates, updates or removes ad group customizers. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose ad group customizers are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual ad group customizers. Type: object [AdGroupCustomizerOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/AdGroupCustomizerOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.localServices.appendLeadConversation"
    RPC to append Local Services Lead Conversation resources to Local Services Lead resources.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The Id of the customer which owns the leads onto which the conversations will be appended.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>conversations</td>
            <td>Conversations that are being appended. Type: object [Conversation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/Conversation)</td>
            <td>Yes</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.conversionCustomVariables.mutate"
    Creates or updates conversion custom variables. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose conversion custom variables are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual conversion custom variables. Type: object [ConversionCustomVariableOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ConversionCustomVariableOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.adGroupExtensionSettings.mutate"
    Creates, updates, or removes ad group extension settings. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose ad group extension settings are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual ad group extension settings. Type: object [AdGroupExtensionSettingOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/AdGroupExtensionSettingOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.CustomerCustomizers.mutate"
    Creates, updates or removes customer customizers. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose customer customizers are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual customer customizers. Type: object [CustomerCustomizerOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/CustomerCustomizerOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.campaigns.mutate"
    Creates, updates, or removes campaigns. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose campaigns are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual campaigns. Type: object [CampaignOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/CampaignOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.campaignExtensionSettings.mutate"
    Creates, updates, or removes campaign extension settings. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose campaign extension settings are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual campaign extension settings. Type: object [CampaignExtensionSettingOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/CampaignExtensionSettingOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>responseContentType</td>
            <td>The response content type setting. Determines whether the mutable resource or just the resource name should be returned post mutation. Type: enum [ResponseContentType](https://developers.google.com/google-ads/api/rest/reference/rest/v17/ResponseContentType)</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.keywordPlanCampaignKeywords.mutate"
    Creates, updates, or removes Keyword Plan campaign keywords. Operation statuses are returned.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>customerId</td>
            <td>The ID of the customer whose campaign keywords are being modified.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>operations</td>
            <td>The list of operations to perform on individual Keyword Plan campaign keywords. Type: object [KeywordPlanCampaignKeywordOperation](https://developers.google.com/google-ads/api/rest/reference/rest/v17/KeywordPlanCampaignKeywordOperation)</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>partialFailure</td>
            <td>If true, successful operations will be carried out and invalid operations will return errors. If false, all operations will be carried out in one transaction if and only if they are all valid. Default is false. Type: boolean</td>
            <td>No</td>
        </tr>
        <tr>
            <td>validateOnly</td>
            <td>If true, the request is validated but not executed. Only errors are returned, not results. Type: boolean</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```

??? note "customers.operations.list"
    Lists operations that match the specified filter in the request. If the server doesn't support this method, it returnsUNIMPLEMENTED.
    <table>
        <tr>
            <th>Parameter Name</th>
            <th>Description</th>
            <th>Required</th>
        </tr>
        <tr>
            <td>name</td>
            <td>The name of the operation's parent resource.</td>
            <td>Yes</td>
        </tr>
        <tr>
            <td>filter</td>
            <td>The standard list filter.</td>
            <td>No</td>
        </tr>
        <tr>
            <td>pageSize</td>
            <td>The standard list page size.</td>
            <td>No</td>
        </tr>
        <tr>
            <td>pageToken</td>
            <td>The standard list page token.</td>
            <td>No</td>
        </tr>
    </table>

    **Sample configuration**

    ```xml
    <>
    ```
 
    **Sample request**

    ```json
    {}
    ```
