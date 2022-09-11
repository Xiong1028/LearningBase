# Template

> *Blueprint/layout* - Template has the same hierarchy as page but with no content. <br><br>
> Be used to create a `page`.


## How to create a template?
```mermaid
flowchart LR
a[GO to CRX] -->b[Your project] --> c[Locate template folder] --> d[Right click, choose create template] -->f[Fill metadata of dialogue]

g([Page Template]) --resource type--> h{Page Component}
g --creation done--> i[Template can be choosen to create page] 
```

## Template properties
![template properties](/assets/img/aem/template-properties.png){width=600}

## Restrict Template
```mermaid
	flowchart LR
	a[Restrict Tetmpalte] --property--> b[allowedPaths] & c[allowedTemplates] & f[allowedParents] & g[allowedChildren]
	b -.- d([Define in which path the template can be used - Page level property])
	c -.- e([Define which templates can be uesed in a specific path - Template level property])
	f -.- f1([It can be only used under allowedParents - Template level property])
	g -.- g1([Define which template will be available to create child pages - Template level property])

```

### allowedPaths property
> Define in which path the `template` can be used
```mermaid
  flowchart LR
	a[template A] --> b[path /content/cbd] & c[path /content/exam] & d[path /content/icre] & e[path /content/newsroom] 
```

Examples:

- *allowedPaths: /content(/.\*)?*  - Any page can use this template
- *allowedPaths: /content/cbd(/.\*)?* - Only used in cbd sites.


### allowedTemplates property
> Define which templates can be used in a specific path <br>

<p class="call-out-1">Also as cq:allowedTemplates, all the pages under the node with cq:allowedTemplates will be restricted. </p>

```mermaid
  flowchart RL
	 b[template A] & c[template B] & d[template C] & e[template X] --> a[specified path. /content/cbd ] 
```
