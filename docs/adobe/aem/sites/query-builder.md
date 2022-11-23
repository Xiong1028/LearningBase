# AEM Query Builder  

> AEM query builder is a tool/framework developed by adobe for writing simple and efficient queries in aem. <br><br>
> AEM Query Buidler Debugger Console - localhost:4502/libs/cq/search/content/querydebug.html <br><br>
> For more information, please see [AEM Query Builder API](https://experienceleague.adobe.com/docs/experience-manager-64/developing/platform/query-builder/querybuilder-api.html?lang=en) AND [JCR query](https://jackrabbit.apache.org/oak/docs/query/grammar-xpath.html)

## Two Search APIs  In AEM
```mermaid
flowchart LR

a["Search API in AEM"] --> b1["Query Builder"] & b2["JCR SQL 2"]
```

## How Query Builder works?
```mermaid
flowchart LR 
a["Query Builder\n\n  Converts Query Builder query to Xpath"] ==> b["OAK\n\n  Converts XPath Query to JCR SQL2"] ==> c["Query Engine\n\n  Execute Query and return results"]

```

