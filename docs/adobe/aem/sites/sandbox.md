# Sandbox Setup

A [`Sandbox`](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/programs/introduction-sandbox-programs.html?lang=en) is typically created to serve the purpose of training running demos, but not used to carry live traffic. 


<div class="mermaid">
	flowchart LR
		a[AEM Cloud Service] --> SandBox & A[Production program]
</div>

## Auto-Creation
<div class="mermaid">
	flowchart LR
	subgraph local
		a[AEM Project]
	end
	subgraph sandbox
		b[Development Enviroment]
	end
	local ==pipeline==> sandbox
</div>

## Creating Sandbox Programs

For more information, please go to [adobe documents](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/programs/creating-sandbox-programs.html?lang=en)