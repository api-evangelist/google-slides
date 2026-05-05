---
title: "Gemini Cloud Assist: Proactive cloud operations that work for you, even before you ask"
url: "https://cloud.google.com/blog/products/application-development/gemini-cloud-assist-at-next26/"
date: "Wed, 22 Apr 2026 12:00:00 +0000"
author: "Ines Envid"
feed_url: "https://cloudblog.withgoogle.com/products/application-development/rss"
---
<div class="block-paragraph_advanced"><p><span style="vertical-align: baseline;">Today at Google Cloud Next, we are unveiling a more proactive Gemini Cloud Assist, our AI-assisted cloud operations platform. This update shifts your Google Cloud operations from manual workflows to a proactive, intelligent experience supported by a powerful ecosystem of agents.</span></p>
<p><strong style="vertical-align: baseline;">Why it matters: </strong><span style="vertical-align: baseline;">A new agentic architecture enables Gemini Cloud Assist to handle the heavy lifting of your cloud management. By embedding intelligence, your enterprise context, and the power of Gemini directly into the operational layer, Gemini Cloud Assist proactively executes complex tasks such as designing applications, troubleshooting issues, and preemptively optimizing costs, that previously required constant human oversight. In enterprise-scale systems, this approach accelerates development velocity and reduces resolution times. </span></p>
<p><strong style="vertical-align: baseline;">What’s new: </strong></p>
<ul>
<li style="vertical-align: baseline;">
<p><span style="vertical-align: baseline;">Using natural language and the power of Gemini, reduce the time from design to deployment of new or existing multi-resource deployments via a </span><strong style="vertical-align: baseline;">redesigned Application Design Center</strong><span style="vertical-align: baseline;">.</span></p>
</li>
<li style="vertical-align: baseline;">
<p><span style="vertical-align: baseline;">Automate infrastructure operations via </span><strong style="vertical-align: baseline;">gcloud, kubectl, and Terraform </strong><span style="vertical-align: baseline;">while using proactive multi-turn agents to troubleshoot and resolve incidents.</span></p>
</li>
<li style="vertical-align: baseline;">
<p><strong style="vertical-align: baseline;">Identify your cost anomalies 24/7 </strong><span style="vertical-align: baseline;">using a proactive FinOps agent that analyzes spending spikes and generates granular cost reports on demand.</span></p>
</li>
<li style="vertical-align: baseline;">
<p><strong style="vertical-align: baseline;">Assistance wherever you are. </strong><span style="vertical-align: baseline;">Powered by </span><a href="https://docs.cloud.google.com/mcp/supported-products"><span style="text-decoration: underline; vertical-align: baseline;">Google Cloud MCP servers</span></a><span style="vertical-align: baseline;"> and our proactive agents under the hood, Gemini Cloud Assist also exposes its own design, operation, troubleshooting and optimization capabilities as published MCP servers, bringing them straight to your IDE. </span></p>
</li>
</ul>
<p style="padding-left: 40px;"><span style="font-style: italic; vertical-align: baseline;">“Gemini Cloud Assist has significantly helped our dev teams. It reduced the number of outreach and touch points I have with them regarding Google Cloud questions by 60%. This allows our cloud team to scale more effectively and focus on more complex tasks.” </span><span style="vertical-align: baseline;">- Oscar Aldana Assad, Senior Cloud Engineer, Petco</span></p>
<p><span style="vertical-align: baseline;">Let’s take a deeper look at how the agentic Gemini Cloud Assist can help your operations.</span></p>
<h3><span style="vertical-align: baseline;">Accelerate production-readiness with Application Design Center</span></h3>
<p><span style="vertical-align: baseline;">Gemini Cloud Assist serves as the intelligent reasoning engine for Application Design Center, acting as the bridge between natural-language intent, and a visual, production-ready architecture. By describing your infrastructure goals in plain language, Gemini Cloud Assist leverages Application Design Center to automatically lay out a visual design, including deployable Terraform. These templates are based on best-practice architecture guidance from Google Cloud and help bring security, reliability and compliance by design. Integrated with Security Command Center, quickly go from idea to deployment that conforms to your organizational policies.</span></p>
<p><span style="vertical-align: baseline;">Platform teams can then curate shared catalogs of pre-approved templates and integrate their own custom Terraform modules directly into the design process, providing a governed framework. This established, well-lit path helps developers adhere to organizational security and compliance guardrails from the first day of deployment. Beyond initial deployment, Gemini supports the full application lifecycle with interactive, multi-turn problem solving to update cloud resources. </span></p></div>
<div class="block-paragraph_advanced"><h3><span style="vertical-align: baseline;">Move from reactive to proactive remediation</span></h3>
<p><span style="vertical-align: baseline;">In production, Gemini Cloud Assist helps you shift operations from reactive troubleshooting to quickly analyzing hypotheses to drive a lower time to resolution. Triggered by alerts, Gemini Cloud Assist proactively clusters and analyzes signals to initiate investigations before issues escalate. Now with Gemini 3, Gemini Cloud Assist correlates logs and metrics and identifies root causes from infrastructure signals down to the application code. Gemini Cloud Assist explores parallel hypotheses via tool calls and presents a technical breakdown of observations in a centralized UI. If intervention is required to address an underlying Google Cloud issue, users can hand off complete context to Google support, minimizing the iterations required for sharing configuration and context data.</span></p></div>
<div class="block-image_full_width">






  
    <div class="article-module h-c-page">
      <div class="h-c-grid">
  

    <figure class="article-image--large
      
      
        h-c-grid__col
        h-c-grid__col--6 h-c-grid__col--offset-3
        
        
      ">

      
      
        
        <img alt="proactive_alert_investigations" src="https://storage.googleapis.com/gweb-cloudblog-publish/original_images/proactive_alert_investigations_blog.gif" />
        
        </a>
      
    </figure>

  
      </div>
    </div>
  




</div>
<div class="block-paragraph_advanced"><h3><span style="vertical-align: baseline;">Identify cost anomalies 24/7</span></h3>
<p><span style="vertical-align: baseline;">To maintain economic health, Gemini Cloud Assist now acts as an proactive optimization agent for your projects. Running in the background 24/7, it monitors for cost anomalies and provides root-cause analysis, correlating spending spikes with specific engineering triggers like new resource creation, auto-scaling events, or pricing changes. You can query resource utilization via natural language to generate on-demand, tabulated reports, by project and applications registered in AppHub, providing granular visibility into "</span><span style="font-style: italic; vertical-align: baseline;">who, what, when, and how</span><span style="vertical-align: baseline;">" — without manual data aggregation. For example, you can ask ‘Why did the cost of my application increase yesterday?’ or ‘How much did my project cost last month?’ and Gemini Cloud Assist answers by correlating cost data with infrastructure change, audit, and monitoring logs to get you an accurate answer.</span></p></div>
<div class="block-image_full_width">






  
    <div class="article-module h-c-page">
      <div class="h-c-grid">
  

    <figure class="article-image--large
      
      
        h-c-grid__col
        h-c-grid__col--6 h-c-grid__col--offset-3
        
        
      ">

      
      
        
        <img alt="3" src="https://storage.googleapis.com/gweb-cloudblog-publish/original_images/3_Vz6FwaI.gif" />
        
        </a>
      
    </figure>

  
      </div>
    </div>
  




</div>
<div class="block-paragraph_advanced"><h3><span style="vertical-align: baseline;">Assistance everywhere</span></h3>
<p><span style="vertical-align: baseline;">We are meeting teams where they work by expanding the surfaces where Gemini Cloud Assist is available. A Gemini Cloud Assist agent is already accessible through the console and mobile interfaces. And with new support for the Model Context Protocol (MCP), Gemini Cloud Assist is now available in Gemini CLI, your favorite agentic IDE or CLI, and third-party toolchains like ServiceNow and Slack. Integrating proactive assistance within existing workflows helps teams to avoid context switching and maintain flow-state.</span></p>
<h3><span style="vertical-align: baseline;">Proactive capabilities at your fingertips</span></h3>
<p><span style="vertical-align: baseline;">We designed Gemini Cloud Assist to help manage the end-to-end lifecycle of your applications, providing a multi-agent approach from deploying new applications to managing existing applications in the cloud. With the help of Gemini 3, Gemini Cloud Assist can now:</span></p>
<ul>
<li><strong style="vertical-align: baseline;">Increase your development velocity: </strong><span style="vertical-align: baseline;">Accelerate production-readiness using intent-driven architectures that unify best practices, security policies, and enterprise compliance.</span></li>
<li><strong style="vertical-align: baseline;">Streamline production operations</strong><span style="vertical-align: baseline;">: Triage, diagnose and resolve production issues faster, through Gemini-based troubleshooting, recommendations and remediations.</span></li>
<li><strong style="vertical-align: baseline;">Automate cost optimization:  </strong><span style="vertical-align: baseline;">Automatically detect, analyze, root-cause, and alert you about cost anomalies for your projects on a daily basis. </span></li>
<li><strong style="vertical-align: baseline;">Meet your teams where they are:  </strong><span style="vertical-align: baseline;">Through proactive agents and MCP tools, engage with functionality using surfaces that range from the Google Cloud console to your CLI and IDE, so teams can stay in a flow-state.</span></li>
</ul>
<p><span style="vertical-align: baseline;">The future of operations is agentic. You can begin your journey with our proactive cloud by enabling </span><a href="https://console.cloud.google.com/gemini-admin/products"><span style="text-decoration: underline; vertical-align: baseline;">Gemini Cloud Assist</span></a><span style="vertical-align: baseline;"> in your project settings today.</span></p></div>
