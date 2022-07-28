# AEM Introduction

This notebook summarizes the learning process of AEM. Most of notes are graphics, charts etc. It is used as a guide in workplace. For full documentation please visit [Adobe AEM](https://experienceleague.adobe.com/docs/experience-manager.html?lang=en).

## What is AEM?

AEM(Adobe Experience Manager) is basically CMS tool developed by Adobe. Its competitors are:

- [Liferay DXP](https://www.liferay.com/developers) - Java, Open Source
- [Wordpress](https://wordpress.org/) - PHP, Open Source
- [Drupal](https://www.drupal.org/) - PHP, Open Source

![AEM Market Share](/assets/img/aem/cm-adobeexperiencemanager.png)
<br>
<small> 
(Image from <a href="https://w3techs.com/technologies/details/cm-adobeexperiencemanager#:~:text=Adobe%20Experience%20Manager%20is%20used,is%200.1%25%20of%20all%20websites">W3Techs</a>) 
</small>

## AEM Core Features

<div class="mermaid">
		graph LR
		A((AEM)) --> Sites & Assets & Forms 
		Sites --> B[Server-side Rendering] & C[Headless/SPA]
</div>

## AEM Architecture


<div class="mermaid">
	flowchart BT
		subgraph 1
			direction LR
			OSGI --> b[Apache Felix] --> Bundle & Service
    end
		subgraph 2
			direction LR
			subgraph SLING
				direction TB
				apachesling([Apache Sling]) -->  HTL & Model & Servlet
			end
			SLING <===> JCR[(JCR)]
    end
		subgraph 3
			AEM --> Components & Templates
    end
		1 --> 2 --> 3
</div>