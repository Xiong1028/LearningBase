# HTML Temlaplate Language (HTL) / Sightly

## [What is HTL?](https://experienceleague.adobe.com/docs/experience-manager-htl/using/getting-started/update.html?lang=en)

- Templating language working in Server side
- HTL is HTML5
- Alternative of JSP

## HTL syntax
```mermaid
	flowchart TB
	a((HTL/Sightly)) --> b[Expression] & c[Sly element] & Attributes & Comments

```

### Comments
```html
html comments: <!----> (remain in browser)
htl/sightly comments: <!--/* This is htl comments */--> (recommended, removed in browser)

```

### Expressions

- written in `${}`
- used in attrbites, element content and comments

### Sly Element

- removed from output


### Slighty attribute
>Start with data, please see [block statements](https://experienceleague.adobe.com/docs/experience-manager-htl/using/htl/block-statements.html?lang=en)
```
...
data-sly-include
data-sly-test
data-sly-text
data-sly-list
data-sly-repeat
...
```

### Predefined objects
```mermaid
	 flowchart LR
	 a[APIs] --> b[currentPage] === c([instance of the page class]) ---|currentPage.Title| abc[AEM API] 
	 a -->  d[properties] ===f([instance of ValueMap class]) ---|properties.jcr:title| adf[Sling API]
	 a --> a3[currentNode] === a31[Instance of the Node] ---|currentNode.Name| a32[JCR API]
```

#### How to use predefined objects?

```html
	<h1>Hello World!!</h1>
	<h3>Sling PropertiesObject</h3>
	<p>Page Title : ${properties.jcr:title}</p>

	<h3>Page Details</h3>
	<p>currentPage Title: ${currentPage.Title}</p>
	<p>currentPage Name: ${currentPage.Name}</p>
	<p>currentPage Path: ${currentPage.Path}</p>
	<p>currentPage Depth: ${currentPage.Depth}</p>

	<h3> Node Details </h3>
	<p>currentNode Name: ${currentNode.Name}</p>
	<p>currentNode Path: ${currentNode.Path}</p>
	<p>currentNode Depth: ${currentNode.Depth}</p>
```
