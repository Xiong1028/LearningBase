# URL decomposition & Script resolution

## Decompoing a URL in AEM
During the `Resource Resolution` step, the client request URI (as being returned by `HttpServletRequest.getRequestURI()`) is decomposed into the following parts:

1. Resource Path
2. Selectors
3. Extension
4. Suffix

> For more information, please see [Apach Sling URL decomposition](https://sling.apache.org/documentation/the-sling-engine/url-decomposition.html).

![URL Decomposition](/assets/img/aem/url-decomposition.png){width="600"} <br>
<sup>[NOTE] Data from [AEM and Devops Tutorial](https://www.youtube.com/watch?v=UU8XmxN7Mx8&list=PL2rn7ZBYpBjtPyy5-pEBxwwIowcIoVv40&index=14&ab_channel=AEMandDevopsTutorial)</sup>

## Script resolution
![Script resolution](/assets/img/aem/scriptResolution.png){width="600"} <br>
<sup>[NOTE] Data from [adobe documents](https://experienceleague.adobe.com/docs/experience-manager-64/developing/platform/sling-cheatsheet.html?lang=en)</sup>


![Script Resolution](/assets/img/aem/resourceResolution.png){width="600"} <br>
<sup>[NOTE] Data from [aemgeeks](https://aemgeeks.wordpress.com/2017/07/31/sling-resource-resolution-sling-request-processing/)</sup>


### Mapping URL to files in CRX
![resource resolution](/assets/img/aem/Sling-resource-resolution-in-aem.webp){width="600"} <br>
<sup>[NOTE] Data from [AEM CQ5 Tutorials](https://www.aemcq5tutorials.com/tutorials/sling-resource-resolution-aem/)</sup>
