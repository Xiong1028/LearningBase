# Dialog Validator

## Dialog Custom Validator

<details>
<summary>
 Create a new `clientlib` folder under the component node to hold js and css only for dialog.
</summary>

<img src="/assets/img/aem/dialog-custom-validator-0.png" alt="dialog custom validator" />
<p><sup>- image from <a href="https://www.youtube.com/c/AEMGeeks" target="_blank">AEM GEEKS</a></sup></p>
</details>

<details>
<summary>
Write a registry validator js file
</summary>

<img src="/assets/img/aem/dialog-custom-validator-1.png"/>
<p><sup>- image from <a href="https://www.youtube.com/c/AEMGeeks" target="_blank">AEM GEEKS</a></sup></p>
</details>


> Add property: validator on dialog node(textfield or multifield)

![dialog custom validator](/assets/img/aem/dialog-custom-validator-2.png)
<p><sup>- image from <a href="https://www.youtube.com/c/AEMGeeks" target="_blank">AEM GEEKS</a></sup></p>


<details>
<summary>
Call new clientlib in dialog
</summary>

<img src="/assets/img/aem/dialog-custom-validator-0-1.png"/>
<p><sup>- image from <a href="https://www.youtube.com/c/AEMGeeks" target="_blank">AEM GEEKS</a></sup></p>
</details>


## Demo
> The validator js and css files are only under editor and set a `extraClientlibs` property in dialog node, like author. by doing this,  The clientlibswill only be loaded in editor dialog.  
*/app/projectName/components/content/author*

<details>
<summary>
Add a multifield maximum and minimum items validationvalidation property 
</summary>

<img src="/assets/img/aem/dialog-validator-demo-1.png"/>
<p><sup>- image from <a href="https://www.youtube.com/c/AEMGeeks" target="_blank">AEM GEEKS</a></sup></p>
</details>


<details>
<summary>
How to setup multifield maximum and minimum items validation?
</summary>

<img src="/assets/img/aem/dialog-validator-demo-2.png"/>
<p><sup>- image from <a href="https://www.youtube.com/c/AEMGeeks" target="_blank">AEM GEEKS</a></sup></p>

```javascript
(function($, Coral){
	var registery = $(window).adaptTo("foundation-registry");

	registry.register("foundation.validation.validator",{
		selector:"[data-validation=geeks-multifield]",
		validate:function(element){
				var el = $(element);
				let max = el.data("max-items");
				let min = el.data("min-items");
				let childrenItems = el.children("coral-multifield-item").
				let childrenItemsNumber = childrenItems.length();

				if(childrenItemsNumber  > max){
					childrenItems.last().remove(); 
					return "You can add books no more than " + max; 
				}
				if(childrenItemsNumber  < min){
				 return "You add books no less than " + min;
				}
		}
	});
})(jQuery, Coral);
```
</details>




