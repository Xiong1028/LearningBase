# Package 

> A [package](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developer-tools/package-manager.html?lang=en) is a zip file holding repository content in file-system serialization form, called vault serialization, providing an easy-to-use and easy-to-edit representation of files and folders. Content included in the package is defined by using filters. <br><br>
> More info about [AEM package](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developer-tools/package-manager.html?lang=en)

## Accessing Package Manager 
``` mermaid
graph LR
	a([Accessing Package Manager ]) -->|Way 1| b[AEM Menu] --> Tools --> Deployment --> Packages --> Upload[Upload Package] & Create[Create Package]
	a -->|Way 2| c[From CRXDE Lite using the top switcher bar]
	a -->|Way 3| d[packmgr] 
```
