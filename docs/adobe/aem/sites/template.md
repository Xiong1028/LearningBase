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

## Restrict Template
```mermaid
	flowchart LR
	a[Restrict Tetmpalte] --property--> b[allowedPaths] & c[allowedTemplates]
	b -.- d([Define in which path the template can be used])
	c -.- e([Define which templates can be uesed in a specific path])

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
> Define which templates can be uesed in a specific path
> 
```mermaid
  flowchart RL
	 b[template A] & c[template B] & d[template C] & e[template X] --> a[specified path. /content/cbd ] 
```
