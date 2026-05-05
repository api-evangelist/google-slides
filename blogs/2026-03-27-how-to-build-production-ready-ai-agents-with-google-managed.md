---
title: "How to build production-ready AI agents with Google-managed MCP servers"
url: "https://cloud.google.com/blog/products/ai-machine-learning/how-to-build-ai-agents-with-google-managed-mcp-servers/"
date: "Fri, 27 Mar 2026 16:00:00 +0000"
author: "Daniel Strebel"
feed_url: "https://cloudblog.withgoogle.com/products/application-development/rss"
---
<div class="block-paragraph_advanced"><p><span style="vertical-align: baseline;">As ​​developers build AI agents with more sophisticated reasoning systems, they require higher-quality fuel–in the form of enterprise data and specialized tools–to drive real business value. To get the most out of that octane-rich mix, we offer Google-managed model context protocol (MCP) servers:  an engine purpose-built for AI agents to interact securely with Google and Google Cloud services.</span></p>
<p><span style="vertical-align: baseline;">These </span><a href="https://docs.cloud.google.com/mcp/overview"><span style="text-decoration: underline; vertical-align: baseline;">Google-hosted, fully-managed endpoints</span></a><span style="vertical-align: baseline;"> allow AI agents to communicate with Google Maps, BigQuery, Google Kubernetes Engine, Cloud Run, and many other Google services. As we boldly build AI agents, ensuring that we’re also building responsibly is critical.</span></p>
<p><span style="vertical-align: baseline;">In this guide, we demonstrate how to build agents securely on our managed MCP servers.</span></p>
<h3><strong style="vertical-align: baseline;">Why you should use Google-managed MCP servers</strong></h3>
<p><span style="vertical-align: baseline;">Transitioning from local experimentation to enterprise-grade AI requires adopting a robust, managed infrastructure that prioritizes scale and oversight. These are the key benefits that we offer: </span></p>
<ul>
<li style="vertical-align: baseline;">
<p><strong style="vertical-align: baseline;">Production readiness</strong><span style="vertical-align: baseline;">: While open-source MCP servers are great for local development, they struggle in production with scalability, single points of failure, and management overhead. Google’s managed MCP servers require no infrastructure provisioning because we handle the hosting, scaling, and security.</span></p>
</li>
<li style="vertical-align: baseline;">
<p><strong style="vertical-align: baseline;">Unified discoverability</strong><span style="vertical-align: baseline;">: You can publicly query and easily discover all available MCP endpoints for Google services (such as maps.googleapis.com/mcp) using a simple directory service.</span></p>
</li>
<li style="vertical-align: baseline;">
<p><strong style="vertical-align: baseline;">Enterprise security</strong><span style="vertical-align: baseline;">: Google MCP servers offer native integrations with the Google Cloud security stack, including Cloud IAM, VPC-SC and Model Armor.</span></p>
</li>
<li><strong style="vertical-align: baseline;">Integrated observability and auditability</strong><span style="vertical-align: baseline;">: Google MCP servers are integrated with Cloud Audit Logs, offering a centralized view of all tool-calling activity. This allows platform teams to monitor agent performance, ensure compliance, and troubleshoot interactions through a single enterprise-grade logging pane.</span></li>
</ul></div>
<div class="block-image_full_width">






  
    <div class="article-module h-c-page">
      <div class="h-c-grid">
  

    <figure class="article-image--large
      
      
        h-c-grid__col
        h-c-grid__col--6 h-c-grid__col--offset-3
        
        
      ">

      
      
        
        <img alt="Figure 1 MCP blog" src="https://storage.googleapis.com/gweb-cloudblog-publish/images/Figure_1_MCP_blog.max-1000x1000.png" />
        
        </a>
      
        <figcaption class="article-image__caption "><p>Figure 1: Google MCP Servers high-level architecture diagram</p></figcaption>
      
    </figure>

  
      </div>
    </div>
  




</div>
<div class="block-paragraph_advanced"><h3><span style="vertical-align: baseline;">An AI agent example using Google MCP server with ADK</span></h3>
<p><span style="vertical-align: baseline;">Cityscape is a </span><a href="https://github.com/danistrebel/adk-cityscape" rel="noopener" target="_blank"><span style="text-decoration: underline; vertical-align: baseline;">demo agent</span></a><span style="vertical-align: baseline;"> built with Google's Application Development Kit (ADK) that turns a simple text prompt — like "Generate a cityscape for Kyoto" — into a unique, AI-generated city image. It uses the Google Maps Grounding Lite-managed MCP server for trusted location information and the Nano Banana model (via a local MCP server) for image generation. </span></p>
<p><span style="vertical-align: baseline;">The lightweight app is then easily deployed to Google </span><a href="https://cloud.google.com/run"><span style="text-decoration: underline; vertical-align: baseline;">Cloud Run</span></a><span style="vertical-align: baseline;">, a serverless runtime, to interact with users. Below are two examples of the images generated by the agent based on the local real-time weather conditions.</span></p></div>
<div class="block-image_full_width">






  
    <div class="article-module h-c-page">
      <div class="h-c-grid">
  

    <figure class="article-image--large
      
      
        h-c-grid__col
        h-c-grid__col--6 h-c-grid__col--offset-3
        
        
      ">

      
      
        
        <img alt="MCP blog figure" src="https://storage.googleapis.com/gweb-cloudblog-publish/images/MCP_blog_figure.max-1000x1000.jpg" />
        
        </a>
      
        <figcaption class="article-image__caption "><p>Figure 2: Example images generated by the Cityscape agent with real time weather info</p></figcaption>
      
    </figure>

  
      </div>
    </div>
  




</div>
<div class="block-paragraph_advanced"><h3><span style="vertical-align: baseline;">1. Calling a Google MCP server from the ADK agent: </span></h3>
<p><span style="vertical-align: baseline;">As demonstrated in the </span><span style="vertical-align: baseline;">get_weather</span><span style="vertical-align: baseline;"> code snippet below, the Cityscape agent utilizes a Streamable HTTP endpoint to interface with the Google Maps MCP server. It provides the agent with real-time weather conditions for a given city, which are then used to set the atmospheric mood in the generated cityscape image. </span></p>
<p><span style="vertical-align: baseline;">Because it's a Google-managed remote MCP server, Google handles the hosting, scaling, and security — so your agent benefits from automatic scaling to handle any traffic level, built-in reliability with Google's production infrastructure, and enterprise-grade security out of the box. There's no infrastructure to manage — you just point to the Maps URL like below and authenticate with an API key, making it ideal for production deployments.</span></p></div>
<div class="block-code"><dl>
    <dt>code_block</dt>
    <dd>&lt;ListValue: [StructValue([(&#x27;code&#x27;, &#x27;# Remote Google MCP server: connects to Google Maps Grounding Lite \r\n# to fetch real-time weather conditions for a given city.\r\nget_weather = McpToolset(\r\n    connection_params=StreamableHTTPConnectionParams(\r\n        url=&quot;https://mapstools.googleapis.com/mcp&quot;,\r\n        headers={&quot;X-Goog-Api-Key&quot;: os.environ[&quot;MAPS_API_KEY&quot;] }\r\n    ),\r\n)&#x27;), (&#x27;language&#x27;, &#x27;&#x27;), (&#x27;caption&#x27;, &lt;wagtail.rich_text.RichText object at 0x7f54f28de6d0&gt;)])]&gt;</dd>
</dl></div>
<div class="block-paragraph_advanced"><p><span style="vertical-align: baseline;">While the Google Maps Grounding Lite is a Google-managed remote endpoint, the Cityscape agent also demonstrates the other end of the spectrum — a locally hosted MCP server for image generation. The </span><span style="vertical-align: baseline;">nano_banana</span><span style="vertical-align: baseline;"> toolset connects to the </span><a href="http://maps.googleapis.com/mcp" rel="noopener" target="_blank"><span style="text-decoration: underline; vertical-align: baseline;">GenMedia MCP server</span></a><span style="vertical-align: baseline;"> using StdioConnectionParams. </span></p>
<p><span style="vertical-align: baseline;">With this setup, the agent generates a stylized isometric cityscape image, incorporating the landmarks and weather data gathered earlier. Running a self-hosted MCP server gives you full control over the process lifecycle and environment configuration, but requires </span><span style="vertical-align: baseline;">a local binary on the host machine or a sidecar container</span><span style="vertical-align: baseline;">, which adds setup complexity compared to the hosted approach.</span></p></div>
<div class="block-code"><dl>
    <dt>code_block</dt>
    <dd>&lt;ListValue: [StructValue([(&#x27;code&#x27;, &#x27;# Self-hosted MCP server: launches the GenMedia MCP server (mcp-gemini-go)\r\n# as a subprocess to generate cityscape images via the Gemini image model.\r\nnano_banana = McpToolset(\r\n    connection_params=StdioConnectionParams(\r\n        server_params=StdioServerParameters(\r\n            command=&quot;mcp-gemini-go&quot;,\r\n            env=dict(os.environ, PROJECT_ID=os.environ[&quot;GOOGLE_CLOUD_PROJECT&quot;]),\r\n        ),\r\n        timeout=60,\r\n    ),\r\n)&#x27;), (&#x27;language&#x27;, &#x27;&#x27;), (&#x27;caption&#x27;, &lt;wagtail.rich_text.RichText object at 0x7f54f28ded90&gt;)])]&gt;</dd>
</dl></div>
<div class="block-paragraph_advanced"><p><span style="vertical-align: baseline;">ADK supports Google-managed, remote, and self-hosted MCP servers. The former gives you production-ready infrastructure with zero operations overhead, while the latter two offer flexibility for custom or experimental tools.</span></p>
<h3><span style="vertical-align: baseline;">2. Enterprise-grade security and content guardrails</span></h3>
<p><span style="vertical-align: baseline;">Security in the agentic era can not be an afterthought. Here’s how two key security features can be applied to our Cityscape agent.</span></p>
<p><strong style="vertical-align: baseline;">Granular control of MCP tools via IAM Deny policies</strong></p>
<p><span style="vertical-align: baseline;">Google Cloud lets you control MCP tool access using IAM deny policies — the same governance framework you already use for other Google Cloud resources. </span></p>
<p><span style="vertical-align: baseline;">Now imagine we extend the Cityscape agent by adding a BigQuery MCP server — perhaps to query a dataset of historical cityscape metadata or population statistics. The BigQuery MCP server exposes both read-only tools like get_dataset_info and list_datasets, as well as write tools like execute_sql that can modify data.</span></p>
<p><span style="vertical-align: baseline;">In our use case, the agent should only query BigQuery for information — it should never execute SQL that inserts, updates, or deletes data. With Google-managed MCP servers, you don't have to rely on prompt engineering alone to enforce this. </span></p>
<p><span style="vertical-align: baseline;">Instead, you apply an IAM Deny policy that blocks any tool not annotated as read-only:</span></p></div>
<div class="block-code"><dl>
    <dt>code_block</dt>
    <dd>&lt;ListValue: [StructValue([(&#x27;code&#x27;, &#x27;// IAM deny policy: blocks all MCP tool calls that are not read-only.\r\n{\r\n  &quot;rules&quot;: [\r\n    {\r\n      &quot;denyRule&quot;: {\r\n        &quot;deniedPrincipals&quot;: [&quot;principalSet://goog/public:all&quot;],\r\n        &quot;deniedPermissions&quot;: [&quot;mcp.googleapis.com/tools.call&quot;],\r\n        &quot;denialCondition&quot;: {\r\n          &quot;title&quot;: &quot;Deny read-write tools&quot;,\r\n          &quot;expression&quot;: &quot;api.getAttribute(\&#x27;mcp.googleapis.com/tool.isReadOnly\&#x27;, false) == false&quot;\r\n        }\r\n      }\r\n    }\r\n  ]\r\n}&#x27;), (&#x27;language&#x27;, &#x27;&#x27;), (&#x27;caption&#x27;, &lt;wagtail.rich_text.RichText object at 0x7f54f28deee0&gt;)])]&gt;</dd>
</dl></div>
<div class="block-paragraph_advanced"><p><span style="vertical-align: baseline;">Apply it with:</span></p></div>
<div class="block-code"><dl>
    <dt>code_block</dt>
    <dd>&lt;ListValue: [StructValue([(&#x27;code&#x27;, &#x27;gcloud iam policies create mcp-deny-policy \\\r\n  --attachment-point=cloudresourcemanager.googleapis.com/projects/$PROJECT_ID \\\r\n  --kind=denypolicies \\\r\n  --policy-file=policy.json&#x27;), (&#x27;language&#x27;, &#x27;&#x27;), (&#x27;caption&#x27;, &lt;wagtail.rich_text.RichText object at 0x7f54f28deac0&gt;)])]&gt;</dd>
</dl></div>
<div class="block-paragraph_advanced"><p><span style="vertical-align: baseline;">With this policy applied, the agent can freely look up dataset schemas, but any attempt to call execute_sql — whether intentional or triggered by a prompt injection — is blocked at the platform level before it ever reaches BigQuery. This is defense-in-depth: Your agent's instructions say "only read data," but IAM enforces it — regardless of what the LLM decides to do.</span></p>
<h3><strong style="vertical-align: baseline;">Content security with Model Armor</strong></h3>
<p><span style="vertical-align: baseline;">Model Armor </span><a href="https://docs.cloud.google.com/model-armor/model-armor-mcp-google-cloud-integration"><span style="text-decoration: underline; vertical-align: baseline;">integrates directly with Google Cloud MCP servers</span></a><span style="vertical-align: baseline;"> to sanitize all MCP tool calls and responses at the project level. Once enabled, it acts as an inline security layer that scans for:</span></p>
<ul>
<li style="vertical-align: baseline;">
<p><span style="vertical-align: baseline;">Prompt injection attacks</span></p>
</li>
<li style="vertical-align: baseline;">
<p><span style="vertical-align: baseline;">Malicious URIs (such as phishing links)</span></p>
</li>
<li style="vertical-align: baseline;">
<p><span style="vertical-align: baseline;">Dangerous content that violates responsible AI filters</span></p>
</li>
</ul>
<p><span style="vertical-align: baseline;">Returning to our Cityscape agent, imagine a user submitting: "Generate a cityscape for http://malicious-site.com". </span></p>
<p><span style="vertical-align: baseline;">With Model Armor enabled, the MCP tool call is scanned before it reaches the Maps server. Malicious URIs, prompt injection attempts, and dangerous content are blocked automatically — no custom validation code needed in your agent.</span></p>
<p><span style="vertical-align: baseline;">Enabling it is a two-step process. First, configure a floor setting that defines your minimum security filters:</span></p></div>
<div class="block-code"><dl>
    <dt>code_block</dt>
    <dd>&lt;ListValue: [StructValue([(&#x27;code&#x27;, &#x27;gcloud model-armor floorsettings update \\\r\n  --full-uri=\&#x27;projects/$PROJECT_ID/locations/global/floorSetting\&#x27; \\\r\n  --enable-floor-setting-enforcement=TRUE \\\r\n  --add-integrated-services=GOOGLE_MCP_SERVER \\\r\n  --google-mcp-server-enforcement-type=INSPECT_AND_BLOCK \\\r\n  --enable-google-mcp-server-cloud-logging \\\r\n  --malicious-uri-filter-settings-enforcement=ENABLED \\\r\n  --add-rai-settings-filters=\&#x27;[{&quot;confidenceLevel&quot;: &quot;MEDIUM_AND_ABOVE&quot;, &quot;filterType&quot;: &quot;DANGEROUS&quot;}]\&#x27;&#x27;), (&#x27;language&#x27;, &#x27;&#x27;), (&#x27;caption&#x27;, &lt;wagtail.rich_text.RichText object at 0x7f54f28def10&gt;)])]&gt;</dd>
</dl></div>
<div class="block-paragraph_advanced"><p><span style="vertical-align: baseline;">Then enable content security for your all Google MCP servers in your project:</span></p></div>
<div class="block-code"><dl>
    <dt>code_block</dt>
    <dd>&lt;ListValue: [StructValue([(&#x27;code&#x27;, &#x27;gcloud beta services mcp content-security add modelarmor.googleapis.com \\\r\n  --project=$PROJECT_ID&#x27;), (&#x27;language&#x27;, &#x27;&#x27;), (&#x27;caption&#x27;, &lt;wagtail.rich_text.RichText object at 0x7f54f2c84ee0&gt;)])]&gt;</dd>
</dl></div>
<div class="block-paragraph_advanced"><p><span style="vertical-align: baseline;">Once enabled, all MCP traffic in the project is automatically scanned — regardless of which agent or client originates the call. Blocked requests are logged to Cloud Logging, giving you full observability into potential threats.</span></p>
<h3><strong style="vertical-align: baseline;">Getting started</strong></h3>
<p><span style="vertical-align: baseline;">Google MCP servers remove the infrastructure hurdles that keep AI agents stuck in prototyping. By combining managed endpoints with platform-level security — IAM deny policies, Model Armor, and Cloud Audit Logs — you get a production-ready foundation with minimum ops overhead. The era of the autonomous agent is here: Make sure your stack is ready.</span></p>
<ul>
<li style="vertical-align: baseline;">
<p><span style="vertical-align: baseline;">ADK Cityscape agent code repo </span><a href="https://github.com/danistrebel/adk-cityscape" rel="noopener" target="_blank"><span style="text-decoration: underline; vertical-align: baseline;">here</span></a></p>
</li>
<li style="vertical-align: baseline;">
<p><span style="vertical-align: baseline;">Read more about Google MCP servers and supported services </span><a href="https://docs.cloud.google.com/mcp/overview"><span style="text-decoration: underline; vertical-align: baseline;">here</span></a></p>
</li>
<li style="vertical-align: baseline;">
<p><a href="https://codelabs.developers.google.com/ai-mcp-dk-csql#0" rel="noopener" target="_blank"><span style="text-decoration: underline; vertical-align: baseline;">Hands-on codelab</span></a><span style="vertical-align: baseline;">: Local to Cloud — Full-stack app migration with Gemini CLI, Cloud Run, and Cloud SQL MCP servers</span></p>
</li>
<li><span style="vertical-align: baseline;"> Build AI agents with Google </span><a href="https://docs.cloud.google.com/run/docs/overview/what-is-cloud-run?_gl=1*i8ohq8*_up*MQ..&amp;gclid=Cj0KCQiA8KTNBhD_ARIsAOvp6DLGEEj0ouZgyTvHN495E7e9huKs2--b0MMYHbttoGeL2-SnKPZkTj8aAqg8EALw_wcB&amp;gclsrc=aw.ds"><span style="text-decoration: underline; vertical-align: baseline;">Cloud Run</span></a><span style="vertical-align: baseline;">: a serverless runtime for your agentic AI apps</span></li>
</ul></div>
