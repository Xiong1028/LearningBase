# Components

## What is Component?
`AEM` provides tons of OTB `core components` residing in */libs/wcm/foundation/componets* (`AEM clouds` might be different). 

- Collection of scripts
- a reusable unit 
- modular
  
> Componnet is a foundation unit of *Template/Page*.

## Inheritance

All components inherit functionalities e.g. setting box,  from  `sling:resourceSuperType`. The file with same name as parent component will override it.

```mermaid
	classDiagram
	Parent <|-- Child : Inheritance
	Child: + body.html(override parent)
	class Parent{
		+ header.html
		+ body.html
		+ footer.html
	}

	class Child{
		+ Sling:sourceSuperType
	}

```

## Base Page Component
![page component](/assets/img/aem/page-component.png){width=800}
<p><sup>- image from <a href="https://www.youtube.com/c/AEMGeeks" target="_blank">AEM GEEKS</a></sup></p>

## multifield Dialog
