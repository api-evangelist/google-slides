---
title: "Centralized policy meets distributed logic: Getting to know Eventarc Advanced"
url: "https://cloud.google.com/blog/products/application-modernization/getting-to-know-eventarc-advanced/"
date: "Fri, 27 Feb 2026 17:00:00 +0000"
author: "Milen Kovachev"
feed_url: "https://cloudblog.withgoogle.com/products/application-development/rss"
---
<div class="block-paragraph_advanced"><p><span style="vertical-align: baseline;">Enterprise architects often face a fundamental dilemma: choosing between developer agility and organizational control. Development teams need to move fast and deploy independent microservices without waiting for permission. Security and compliance teams need to be safe, and ensure that data flow is observable and governed by policies.</span></p>
<p><span style="vertical-align: baseline;">That’s why we built </span><a href="https://docs.cloud.google.com/eventarc/advanced/docs/overview"><strong style="text-decoration: underline; vertical-align: baseline;">Eventarc Advanced</strong></a><strong style="vertical-align: baseline;">,</strong><span style="vertical-align: baseline;"> a serverless eventing platform and the evolution of </span><a href="https://docs.cloud.google.com/eventarc/standard/docs/overview"><strong style="text-decoration: underline; vertical-align: baseline;">Eventarc Standard</strong></a><span style="vertical-align: baseline;">. Eventarc Advanced provides</span><strong style="vertical-align: baseline;"> </strong><span style="vertical-align: baseline;">an improved architectural pattern for the modern cloud, where </span><strong style="vertical-align: baseline;">centralized policy meets distributed logic</strong><span style="vertical-align: baseline;">. By clearly separating the governance layer (the "bus") from the processing layer (the "pipeline"), Eventarc Advanced gives SecOps teams the visibility and control they demand, while freeing developers to choreograph AI agents and build event-driven applications with the autonomy they want. </span><a href="https://cloud.google.com/blog/products/application-modernization/eventarc-advanced-orchestrates-complex-microservices-environments?e=48754805"><span style="text-decoration: underline; vertical-align: baseline;">Eventarc Advanced became generally available</span></a><span style="vertical-align: baseline;"> in August 2025. </span></p></div>
<div class="block-image_full_width">






  
    <div class="article-module h-c-page">
      <div class="h-c-grid">
  

    <figure class="article-image--large
      
      
        h-c-grid__col
        h-c-grid__col--6 h-c-grid__col--offset-3
        
        
      ">

      
      
        
        <img alt="1 - evolution-of-architecture" src="https://storage.googleapis.com/gweb-cloudblog-publish/images/1_-_evolution-of-architecture.max-1000x1000.png" />
        
        </a>
      
    </figure>

  
      </div>
    </div>
  




</div>
<div class="block-paragraph_advanced"><p><span style="vertical-align: baseline;">In this blog, we take a deeper look at the evolution of integration architectures — from service buses, to microservices, to where we are today — and go into depth with a real-world example. Let’s jump in. </span></p>
<h3><strong style="vertical-align: baseline;">The evolution of integration architectures</strong></h3>
<p><span style="vertical-align: baseline;">To understand the value of this new pattern, it helps to look at where we came from and why previous architecture patterns forced a compromise.</span></p>
<p><strong style="vertical-align: baseline;">The centralized bottleneck of the </strong><strong style="vertical-align: baseline;">Enterprise Service Bus</strong></p>
<p><span style="vertical-align: baseline;">One early integration architecture approach was the </span><strong style="vertical-align: baseline;">Enterprise Service Bus (ESB)</strong><span style="vertical-align: baseline;">, which prioritized centralized control. The ESB emerged to solve the "spaghetti architecture" of point-to-point integrations by providing a centralized communication layer that standardized how disparate systems interact. However, it often introduced serious pitfalls.</span></p>
<p><span style="vertical-align: baseline;">The primary issue was what’s referred to as a centralized logic trap. Organizations frequently embedded complex business logic — transformations and orchestration — directly into the governance layer. The resulting middleware layer was opaque, with critical business rules hidden from the developers who owned the services.</span></p>
<p><span style="vertical-align: baseline;">Consequently, integration changes typically required the intervention of a central middleware team. Development teams lost autonomy, forced to queue behind integration specialists to ship even minor features, often waiting weeks for updates.</span></p>
<p><strong style="vertical-align: baseline;">Microservices’ governance gap</strong></p>
<p><span style="vertical-align: baseline;">To address this, the industry shifted toward </span><strong style="vertical-align: baseline;">microservices</strong><span style="vertical-align: baseline;"> (often described as "smart endpoints and dumb pipes"), distributing logic to give teams the autonomy they were looking for. For synchronous traffic (REST, gRPC), tools like API gateways and service meshes restored a layer of governance by enforcing policies like authentication and rate limiting at the infrastructure level.</span></p>
<p><span style="vertical-align: baseline;">However, as architectures shifted to </span><strong style="vertical-align: baseline;">Event-Driven Architecture (EDA)</strong><span style="vertical-align: baseline;"> for greater resilience and decoupling, a new gap emerged. In a distributed, asynchronous world, centralized control often vanished. This created a </span><strong style="vertical-align: baseline;">governance gap</strong><span style="vertical-align: baseline;"> where SecOps teams struggled to maintain order. Three issues emerged to the forefront:</span></p>
<ul>
<li style="vertical-align: baseline;">
<p><strong style="vertical-align: baseline;">The visibility void</strong><span style="vertical-align: baseline;">: Without a central policy, shadow IT services could silently subscribe to sensitive events without detection.</span></p>
</li>
<li style="vertical-align: baseline;">
<p><strong style="vertical-align: baseline;">The policy problem</strong><span style="vertical-align: baseline;">: Enforcing data residency or PII masking is nearly impossible when the broker treats every message as an opaque blob.</span></p>
</li>
<li style="vertical-align: baseline;">
<p><strong style="vertical-align: baseline;">The dependency risk</strong><span style="vertical-align: baseline;">: Without clear contracts, changing an event schema risks silently breaking unknown downstream consumers.</span></p>
</li>
</ul>
<h3><span style="vertical-align: baseline;">A new pattern: Centralized policy, distributed logic</span></h3></div>
<div class="block-image_full_width">






  
    <div class="article-module h-c-page">
      <div class="h-c-grid">
  

    <figure class="article-image--large
      
      
        h-c-grid__col
        h-c-grid__col--6 h-c-grid__col--offset-3
        
        
      ">

      
      
        
        <img alt="2 - bus-vs-pipeline" src="https://storage.googleapis.com/gweb-cloudblog-publish/images/2_-_bus-vs-pipeline.max-1000x1000.jpg" />
        
        </a>
      
    </figure>

  
      </div>
    </div>
  




</div>
<div class="block-paragraph_advanced"><p><span style="vertical-align: baseline;">Eventarc Advanced addresses the trade-off between control and speed with a novel architectural pattern: </span><strong style="vertical-align: baseline;">centralized policy meets distributed logic</strong><span style="vertical-align: baseline;">.</span></p>
<p><span style="vertical-align: baseline;">Eventarc Advanced maps these distinct responsibilities to two specific architectural resources that each correspond to a distinct role:</span></p>
<ul>
<li><strong style="vertical-align: baseline;">The</strong><strong style="vertical-align: baseline;"> bus:</strong><span style="vertical-align: baseline;"> This governance layer is a managed, centralized hub where platform administrators enforce global constraints before events are routed. It synthesizes the centralized routing of the legacy ESB with the modern security architecture of a service mesh. It handles Identity and Access Management (IAM), including content-based access control, to strictly define who can publish, and integrates with </span><a href="https://docs.cloud.google.com/vpc-service-controls/docs/overview"><span style="text-decoration: underline; vertical-align: baseline;">VPC Service Controls</span></a><span style="vertical-align: baseline;"> to prevent data exfiltration.</span></li>
<li><strong style="vertical-align: baseline;">The pipeline:</strong><span style="vertical-align: baseline;"> Think of this distributed, team-owned resource as developers’ integration logic layer. This is where eventing patterns for AI agents and microservices are unlocked, allowing developers to configure event flow and delivery according to their specific business logic. Unlike many service meshes that treat data as opaque bits, the pipeline understands content. Developers can transform events, convert payloads between formats (like JSON to Avro), and configure retry policies and authentication independently.</span></li>
</ul>
<p><span style="vertical-align: baseline;">In other words, by decoupling these duties, Eventarc Advanced provides the </span><span style="font-style: italic; vertical-align: baseline;">control</span><span style="vertical-align: baseline;"> of an ESB with the </span><span style="font-style: italic; vertical-align: baseline;">agility</span><span style="vertical-align: baseline;"> of microservices and the </span><span style="font-style: italic; vertical-align: baseline;">resilience</span><span style="vertical-align: baseline;"> of modern event-driven architectures.</span></p>
<h3><strong style="vertical-align: baseline;">How it works: A retail event mesh example</strong></h3>
<p><span style="vertical-align: baseline;">A typical Eventarc Advanced solution can be implemented with minimal configuration, providing a streamlined experience for both administrative governance and distributed integration logic. To see this model in practice, let's look at a real-world implementation of </span><strong style="vertical-align: baseline;">a </strong><span style="vertical-align: baseline;">retail event mesh</span><strong style="vertical-align: baseline;">.</strong></p>
<p><span style="vertical-align: baseline;">Imagine an ecosystem at a global retailer with four autonomous teams in charge of the following services:</span></p>
<ul>
<li style="vertical-align: baseline;">
<p><strong style="vertical-align: baseline;">Commerce</strong></p>
</li>
<li style="vertical-align: baseline;">
<p><strong style="vertical-align: baseline;">Finance</strong></p>
</li>
<li style="vertical-align: baseline;">
<p><strong style="vertical-align: baseline;">Logistics</strong></p>
</li>
<li style="vertical-align: baseline;">
<p><strong style="vertical-align: baseline;">Intelligence (AI Insights Agent)</strong></p>
</li>
</ul>
<p><span style="vertical-align: baseline;">In a traditional setup, aligning these teams is difficult. The Intelligence team wants access to everything for their models, Finance wants to lock everything down for compliance, Logistics just needs a stable schema to ship boxes, and Commerce needs to roll out new features at a moment’s notice.</span></p>
<p><strong style="vertical-align: baseline;">The foundation: Built on CloudEvents</strong></p>
<p><span style="vertical-align: baseline;">Eventarc Advanced uses a data model based on the open </span><a href="https://cloudevents.io/" rel="noopener" target="_blank"><span style="text-decoration: underline; vertical-align: baseline;">CloudEvents standard</span></a><span style="vertical-align: baseline;">, which can carry any type of payload. This helps ensure governance and discoverability while retaining flexibility. In our example, before a single event is published, the platform administrator mandates that every message must contain standard attributes and a specific custom extension for governance. </span></p>
<p><span style="vertical-align: baseline;">In this example, every event on the bus must carry the following attributes:</span></p>
<ul>
<li style="vertical-align: baseline;">
<p><code style="vertical-align: baseline;">type</code><span style="vertical-align: baseline;">: Standard identifiers for the event instance (e.g., </span><code style="vertical-align: baseline;">com.retail.order.created</code><span style="vertical-align: baseline;">)</span></p>
</li>
<li style="vertical-align: baseline;">
<p><code style="vertical-align: baseline;">source</code><span style="vertical-align: baseline;">: A standard attribute identifying the producer (e.g., </span><code style="vertical-align: baseline;">//commerce/frontend</code><span style="vertical-align: baseline;">)</span></p>
</li>
<li style="vertical-align: baseline;">
<p><code style="vertical-align: baseline;">data_sensitivity</code><span style="vertical-align: baseline;">: A custom extension attribute to categorize risk</span></p>
</li>
</ul>
<p><span style="vertical-align: baseline;">In addition, the organization defines three data sensitivity levels:</span></p>
<ul>
<li style="vertical-align: baseline;">
<p><code style="vertical-align: baseline;">restricted</code><span style="vertical-align: baseline;"> </span><strong style="vertical-align: baseline;">(High)</strong><span style="vertical-align: baseline;">: Severe risk data like Credit Card Tokens or Tax IDs</span></p>
</li>
<li style="vertical-align: baseline;">
<p><code style="vertical-align: baseline;">confidential</code><span style="vertical-align: baseline;"> </span><strong style="vertical-align: baseline;">(Medium)</strong><span style="vertical-align: baseline;">: PII like home addresses</span></p>
</li>
<li style="vertical-align: baseline;">
<p><code style="vertical-align: baseline;">general</code><span style="vertical-align: baseline;"> </span><strong style="vertical-align: baseline;">(Low)</strong><span style="vertical-align: baseline;">: Safe operational data like Order IDs</span></p>
</li>
</ul>
<p><span style="vertical-align: baseline;">This standardized metadata layer allows the bus to enforce policies based on specific attribute names — checking </span><span style="font-style: italic; vertical-align: baseline;">who</span><span style="vertical-align: baseline;"> sent the data (</span><code style="vertical-align: baseline;">source</code><span style="vertical-align: baseline;">) and </span><span style="font-style: italic; vertical-align: baseline;">what</span><span style="vertical-align: baseline;"> kind of data it is (</span><code style="vertical-align: baseline;">data_sensitivity</code><span style="vertical-align: baseline;">).</span></p>
<p><strong style="vertical-align: baseline;">The workflow</strong></p>
<p><span style="vertical-align: baseline;">With this model, the lifecycle of a single order becomes a secure flow where sensitivity changes at every step.</span></p></div>
<div class="block-image_full_width">






  
    <div class="article-module h-c-page">
      <div class="h-c-grid">
  

    <figure class="article-image--large
      
      
        h-c-grid__col
        h-c-grid__col--6 h-c-grid__col--offset-3
        
        
      ">

      
      
        
        <img alt="3 - flow-no-bus" src="https://storage.googleapis.com/gweb-cloudblog-publish/images/3_-_flow-no-bus.max-1000x1000.png" />
        
        </a>
      
    </figure>

  
      </div>
    </div>
  




</div>
<div class="block-paragraph_advanced"><ol>
<li style="vertical-align: baseline;">
<p><strong style="vertical-align: baseline;">Order placement</strong><span style="vertical-align: baseline;">: The </span><strong style="vertical-align: baseline;">Commerce</strong><span style="vertical-align: baseline;"> service publishes </span><code style="vertical-align: baseline;">order.created</code><span style="vertical-align: baseline;"> to the Bus. The event’s data sensitivity is tagged as </span><code style="vertical-align: baseline;">general</code><span style="vertical-align: baseline;">. The </span><strong style="vertical-align: baseline;">AI Insights Agent</strong><span style="vertical-align: baseline;"> service subscribes to analyze market trends.</span></p>
</li>
<li style="vertical-align: baseline;">
<p><strong style="vertical-align: baseline;">Payment authorization</strong><span style="vertical-align: baseline;">: The </span><strong style="vertical-align: baseline;">Commerce</strong><span style="vertical-align: baseline;"> service publishes </span><code style="vertical-align: baseline;">payment.authorized</code><span style="vertical-align: baseline;"> tagged as </span><code style="vertical-align: baseline;">restricted</code><span style="vertical-align: baseline;"> (containing a secure token). The </span><strong style="vertical-align: baseline;">Finance</strong><span style="vertical-align: baseline;"> service subscribes to capture the token and executes the charge.</span></p>
</li>
<li style="vertical-align: baseline;">
<p><strong style="vertical-align: baseline;">Settlement</strong><span style="vertical-align: baseline;">: The </span><strong style="vertical-align: baseline;">Finance</strong><span style="vertical-align: baseline;"> service publishes </span><code style="vertical-align: baseline;">payment.success</code><span style="vertical-align: baseline;"> tagged as </span><code style="vertical-align: baseline;">general</code><span style="vertical-align: baseline;">, signaling the transaction is safe to fulfill without exposing financial secrets. </span><strong style="vertical-align: baseline;">Logistics</strong><span style="vertical-align: baseline;"> subscribes to ship the box, and </span><strong style="vertical-align: baseline;">Intelligence AI Insights Agent</strong><span style="vertical-align: baseline;"> is triggered to evaluate market trends for the next supply chain cycle.</span></p>
</li>
<li style="vertical-align: baseline;">
<p><strong style="vertical-align: baseline;">Fulfillment</strong><span style="vertical-align: baseline;">: The </span><strong style="vertical-align: baseline;">Logistics</strong><span style="vertical-align: baseline;"> service publishes </span><code style="vertical-align: baseline;">shipment.ready</code><span style="vertical-align: baseline;"> tagged as </span><code style="vertical-align: baseline;">confidential </code><span style="vertical-align: baseline;">(containing the customer phone number)</span><span style="vertical-align: baseline;">. The </span><strong style="vertical-align: baseline;">Logistics</strong><span style="vertical-align: baseline;"> own notification pipeline subscribes to it to trigger an SMS notification.</span></p>
</li>
</ol>
<p><span style="vertical-align: baseline;">In a legacy architecture, mixing PCI, PII, and operational data on a single bus would be a compliance nightmare. With Eventarc Advanced, it’s a solved problem.</span></p></div>
<div class="block-image_full_width">






  
    <div class="article-module h-c-page">
      <div class="h-c-grid">
  

    <figure class="article-image--large
      
      
        h-c-grid__col
        h-c-grid__col--6 h-c-grid__col--offset-3
        
        
      ">

      
      
        
        <img alt="4 - flow-with-bus" src="https://storage.googleapis.com/gweb-cloudblog-publish/images/4_-_flow-with-bus.max-1000x1000.png" />
        
        </a>
      
    </figure>

  
      </div>
    </div>
  




</div>
<div class="block-paragraph_advanced"><h3><strong style="vertical-align: baseline;">The bus: the governance layer</strong></h3>
<p><span style="vertical-align: baseline;">The platform administrator implements a </span><strong style="vertical-align: baseline;">secure strategy </strong><span style="vertical-align: baseline;">on the bus. Rather than blindly trusting internal services, they enforce global policies that inspect these CloudEvents attributes using </span><strong style="vertical-align: baseline;">fine-grained access control (FGAC)</strong><span style="vertical-align: baseline;">.</span></p>
<p><strong style="vertical-align: baseline;">Enforcing source integrity</strong></p>
<p><span style="vertical-align: baseline;">To ensure a compromised service cannot spoof events, the bus administrator enforces the producer's identity to match the source attribute.</span></p>
<p><span style="vertical-align: baseline;">For example, a bus policy can state that only the principal </span><code style="vertical-align: baseline;">sa-commerce@retail.com</code><span style="vertical-align: baseline;"> can publish events that match the expression </span><code style="vertical-align: baseline;">message.source.startsWith("//commerce/")</code><span style="vertical-align: baseline;">. If the Intelligence AI Insights Agent service tries to publish an event claiming to be from </span><code style="vertical-align: baseline;">//commerce/payments</code><span style="vertical-align: baseline;">, the bus rejects the request.</span></p>
<p><strong style="vertical-align: baseline;">Enforcing a data classification</strong></p>
<p><span style="vertical-align: baseline;">To ensure every event is categorized, the bus administrator requires that every payload received by the bus includes a valid sensitivity attribute. A bus policy can check that </span><code style="vertical-align: baseline;">message.data_sensitivity</code><span style="vertical-align: baseline;"> is one of </span><code style="vertical-align: baseline;">['general', 'confidential', 'restricted']</code><span style="vertical-align: baseline;">. This guarantees that the event mesh contains only classified, governance-ready data.</span></p>
<h3><strong style="vertical-align: baseline;">The Pipeline: the logic layer - autonomous team innovation</strong></h3>
<p><span style="vertical-align: baseline;">With the security posture established on the bus, development teams can then use </span><strong style="vertical-align: baseline;">pipelines</strong><span style="vertical-align: baseline;"> to solve complex integration challenges entirely within their own domains. Let’s take a look at a few of these challenges.</span></p>
<p><strong style="vertical-align: baseline;">Schema-aware formats conversion and payload transformation</strong></p>
<p><span style="vertical-align: baseline;">The Logistics team decides to upgrade their warehouse robots to use high-efficiency </span><strong style="vertical-align: baseline;">protocol buffers</strong><span style="vertical-align: baseline;">. Instead of forcing the Finance team to change their JSON output (which would break other consumers), Logistics configures a </span><strong style="vertical-align: baseline;">transformation</strong><span style="vertical-align: baseline;"> step in their own pipeline.</span></p></div>
<div class="block-image_full_width">






  
    <div class="article-module h-c-page">
      <div class="h-c-grid">
  

    <figure class="article-image--large
      
      
        h-c-grid__col
        h-c-grid__col--6 h-c-grid__col--offset-3
        
        
      ">

      
      
        
        <img alt="5 - pipeline-json-proto-transform" src="https://storage.googleapis.com/gweb-cloudblog-publish/images/5_-_pipeline-json-proto-transform.max-1000x1000.png" />
        
        </a>
      
    </figure>

  
      </div>
    </div>
  




</div>
<div class="block-paragraph_advanced"><p><span style="vertical-align: baseline;">A typical </span><code style="vertical-align: baseline;">com.retail.payment.success</code><span style="vertical-align: baseline;"> event from Finance arrives as JSON:</span></p></div>
<div class="block-code"><dl>
    <dt>code_block</dt>
    <dd>&lt;ListValue: [StructValue([(&#x27;code&#x27;, &#x27;{\r\n  &quot;id&quot;: &quot;89d5663e-789e-4d9f-a65f-f7d83742d987&quot;,\r\n  &quot;source&quot;: &quot;//finance/ledger&quot;,\r\n  &quot;type&quot;: &quot;com.retail.payment.success&quot;,\r\n  &quot;data_sensitivity&quot;: &quot;general&quot;,\r\n  &quot;datacontenttype&quot;: &quot;application/json&quot;,\r\n  &quot;data&quot;: {\r\n    &quot;order_number&quot;: &quot;ORD-2023-8841&quot;,\r\n    &quot;total_amount&quot;: 249.99,\r\n    &quot;currency&quot;: &quot;USD&quot;,\r\n    &quot;transaction_id&quot;: &quot;tx_77382910&quot;,\r\n    &quot;status&quot;: &quot;SETTLED&quot;\r\n  }\r\n}&#x27;), (&#x27;language&#x27;, &#x27;&#x27;), (&#x27;caption&#x27;, &lt;wagtail.rich_text.RichText object at 0x7f54c8cab040&gt;)])]&gt;</dd>
</dl></div>
<div class="block-paragraph_advanced"><p><span style="vertical-align: baseline;">The warehouse robots service expects a binary Protobuf message:</span></p></div>
<div class="block-code"><dl>
    <dt>code_block</dt>
    <dd>&lt;ListValue: [StructValue([(&#x27;code&#x27;, &#x27;message PaymentConfirmed {\r\n  string order_id = 1;\r\n  double insured_value = 2;\r\n  string currency_code = 3;\r\n  string ledger_reference = 4;\r\n}&#x27;), (&#x27;language&#x27;, &#x27;&#x27;), (&#x27;caption&#x27;, &lt;wagtail.rich_text.RichText object at 0x7f54c8cabeb0&gt;)])]&gt;</dd>
</dl></div>
<div class="block-paragraph_advanced"><p><span style="vertical-align: baseline;">The Logistics team configures their pipeline to accept </span><code style="vertical-align: baseline;">json</code><span style="vertical-align: baseline;"> as input and output to </span><code style="vertical-align: baseline;">protobuf</code><span style="vertical-align: baseline;">. To map the data, they use </span><strong style="vertical-align: baseline;">Common Expression Language (CEL)</strong><span style="vertical-align: baseline;"> to configure a </span><strong style="vertical-align: baseline;">transformation</strong><span style="vertical-align: baseline;">:</span></p></div>
<div class="block-code"><dl>
    <dt>code_block</dt>
    <dd>&lt;ListValue: [StructValue([(&#x27;code&#x27;, &#x27;// CEL Transformation to Construct the target Protobuf message\r\n{\r\n  &quot;order_id&quot;: message.data.order_number,\r\n  // 110% of total to cover replacement cost\r\n  &quot;insured_value&quot;: message.data.total_amount * 1.1,\r\n  // Standardize currency to uppercase\r\n  &quot;currency_code&quot;: message.data.currency.upperAscii(),\r\n  &quot;ledger_reference&quot;: message.data.transaction_id,\r\n}&#x27;), (&#x27;language&#x27;, &#x27;&#x27;), (&#x27;caption&#x27;, &lt;wagtail.rich_text.RichText object at 0x7f54c8cab1c0&gt;)])]&gt;</dd>
</dl></div>
<div class="block-paragraph_advanced"><p><span style="vertical-align: baseline;">This transformation not only maps the input but also applies business logic — calculating the insured value and normalizing the currency code. The Logistics team implements this modernization without a single meeting with the Finance team.</span></p>
<p><strong style="vertical-align: baseline;">Agentic workflows: Filtering and triggering AI agents </strong></p>
<p><span style="vertical-align: baseline;">Eventarc Advanced enables agentic workflows by allowing pipelines to communicate directly with AI agents using open standard protocols like </span><a href="https://github.com/a2aproject/A2A" rel="noopener" target="_blank"><span style="text-decoration: underline; vertical-align: baseline;">Agent2Agent (A2A)</span></a><span style="vertical-align: baseline;"> and </span><a href="https://modelcontextprotocol.io/" rel="noopener" target="_blank"><span style="text-decoration: underline; vertical-align: baseline;">Model Context Protocol (MCP)</span></a><span style="vertical-align: baseline;">, while also offering rich capabilities like filtering to optimize when those agents are invoked.</span></p>
<p><span style="vertical-align: baseline;">The Intelligence team uses a pipeline they name </span><code style="vertical-align: baseline;">ai-insights</code><span style="vertical-align: baseline;"> and the </span><strong style="vertical-align: baseline;">A2A protocol</strong><span style="vertical-align: baseline;"> to connect with an </span><strong style="vertical-align: baseline;">AI Insights Agent</strong><span style="vertical-align: baseline;"> that proactively analyzes market trends based on placed orders. Because the agent’s processing is resource-intensive, the team uses a filter to only invoke the agent for high-value orders that warrant deeper analysis.</span></p></div>
<div class="block-image_full_width">






  
    <div class="article-module h-c-page">
      <div class="h-c-grid">
  

    <figure class="article-image--large
      
      
        h-c-grid__col
        h-c-grid__col--6 h-c-grid__col--offset-3
        
        
      ">

      
      
        
        <img alt="6 - pipeline-filter-mdb-agent" src="https://storage.googleapis.com/gweb-cloudblog-publish/images/6_-_pipeline-filter-mdb-agent.max-1000x1000.png" />
        
        </a>
      
    </figure>

  
      </div>
    </div>
  




</div>
<div class="block-paragraph_advanced"><p><span style="vertical-align: baseline;">The pipeline filter is configured with the following expression:</span></p></div>
<div class="block-code"><dl>
    <dt>code_block</dt>
    <dd>&lt;ListValue: [StructValue([(&#x27;code&#x27;, &#x27;message.type == &quot;order.created&quot; &amp;&amp; \r\ndouble(message.amount) &gt; 5000.0&#x27;), (&#x27;language&#x27;, &#x27;&#x27;), (&#x27;caption&#x27;, &lt;wagtail.rich_text.RichText object at 0x7f54f312e0a0&gt;)])]&gt;</dd>
</dl></div>
<div class="block-paragraph_advanced"><p><span style="vertical-align: baseline;">When the filter is passed, the pipeline uses a </span><strong style="vertical-align: baseline;">HTTP Message Destination Binding (MDB)</strong><span style="vertical-align: baseline;"> expression to directly trigger the agent. By defining a CEL template, the pipeline handles the complexity of constructing a native A2A </span><code style="vertical-align: baseline;">SendMessage</code><span style="vertical-align: baseline;"> request to the </span><strong style="vertical-align: baseline;">AI strategic insights agent</strong><span style="vertical-align: baseline;">. This allows the agent to receive a </span><strong style="vertical-align: baseline;">conversational prompt</strong><span style="vertical-align: baseline;"> derived from technical event data without any manual "glue code":</span></p></div>
<div class="block-code"><dl>
    <dt>code_block</dt>
    <dd>&lt;ListValue: [StructValue([(&#x27;code&#x27;, &#x27;{\r\n  &quot;headers&quot;: headers.merge({ &quot;Content-Type&quot;: &quot;application/json&quot;, &quot;A2A-Version&quot;: &quot;1.0&quot; }),\r\n  &quot;body&quot;: {\r\n    &quot;jsonrpc&quot;: &quot;2.0&quot;,\r\n    &quot;id&quot;: message.id,\r\n    &quot;method&quot;: &quot;message/send&quot;,\r\n    &quot;params&quot;: {\r\n      &quot;message&quot;: {\r\n        &quot;messageId&quot;: message.id,\r\n        &quot;role&quot;: &quot;ROLE_USER&quot;,\r\n        &quot;parts&quot;: [\r\n          { \r\n            &quot;text&quot;: &quot;Analyze Order &quot; + message.data.order_number + &quot; for market trends.&quot; \r\n          }\r\n        ]\r\n      }\r\n    }\r\n  }\r\n}&#x27;), (&#x27;language&#x27;, &#x27;&#x27;), (&#x27;caption&#x27;, &lt;wagtail.rich_text.RichText object at 0x7f54f3119e20&gt;)])]&gt;</dd>
</dl></div>
<div class="block-paragraph_advanced"><p><span style="vertical-align: baseline;">A similar prompt message can be crafted for other popular agentic communication protocols like MCP.</span></p>
<p><span style="vertical-align: baseline;">This combination of filtering and agentic protocol translation ensures that AI resources are used precisely where they add value. The Intelligence team implements this independently – without writing ingestion code or coordinating with the Commerce or Admin team. The agent can then publish its own strategic recommendation back to the bus, enabling a choreography of AI experts that turns standard cloud events into competitive intelligence.</span></p>
<p><strong style="vertical-align: baseline;">Advanced API request modeling</strong></p>
<p><span style="vertical-align: baseline;">When a shipment is ready, the Logistics team uses a pipeline to send an SMS using a legacy gateway API. Integrating with legacy third-party APIs often requires writing "glue code" services just to format requests.</span></p>
<p><span style="vertical-align: baseline;">The Logistics team eliminates this maintenance burden by configuring a dedicated pipeline to fully construct the exact request expected by the legacy service. </span></p></div>
<div class="block-image_full_width">






  
    <div class="article-module h-c-page">
      <div class="h-c-grid">
  

    <figure class="article-image--large
      
      
        h-c-grid__col
        h-c-grid__col--6 h-c-grid__col--offset-3
        
        
      ">

      
      
        
        <img alt="7 - mdb" src="https://storage.googleapis.com/gweb-cloudblog-publish/images/7_-_mdb.max-1000x1000.png" />
        
        </a>
      
    </figure>

  
      </div>
    </div>
  




</div>
<div class="block-paragraph_advanced"><p><span style="vertical-align: baseline;">They use a </span><strong style="vertical-align: baseline;">HTTP Message Destination Binding </strong><span style="vertical-align: baseline;">CEL expression, which standardizes the phone number and maps it to the </span><code style="vertical-align: baseline;">X-SMS-To</code><span style="vertical-align: baseline;"> HTTP header required by the API. It also construct the SMS text:</span></p></div>
<div class="block-code"><dl>
    <dt>code_block</dt>
    <dd>&lt;ListValue: [StructValue([(&#x27;code&#x27;, &#x27;{\r\n    &quot;headers&quot;: { &quot;X-SMS-To&quot;, \r\n        message.data.phone.matches(\&#x27;^\\\\+1\&#x27;) ?\r\n            message.data.phone : \r\n            \&#x27;+1\&#x27; + message.data.phone \r\n    },\r\n\r\n    &quot;body&quot;: {\r\n        &quot;sms_text&quot;: &quot;Order &quot; + message.data.order_id + &quot; shipped!&quot;\r\n    }\r\n}&#x27;), (&#x27;language&#x27;, &#x27;&#x27;), (&#x27;caption&#x27;, &lt;wagtail.rich_text.RichText object at 0x7f54f3119310&gt;)])]&gt;</dd>
</dl></div>
<div class="block-paragraph_advanced"><p><span style="vertical-align: baseline;">Finally, they configure a robust retry policy (linear backoff, max five attempts) directly on the pipeline, so that temporary network interruptions don't result in lost notifications. In addition to HTTP endpoints, the pipeline supports guaranteed delivery and out-of-the-box authentication for destinations like Cloud Run, Pub/Sub, Bus, Workflows, and over 200 Google services.</span></p>
<h3><strong style="vertical-align: baseline;">The future of agile integration</strong></h3>
<p><span style="vertical-align: baseline;">Eventarc Advanced closes an important gap in event-driven architectures: It brings the same level of maturity to asynchronous communication by introducing the pattern of </span><strong style="vertical-align: baseline;">centralized policy, distributed logic</strong><span style="vertical-align: baseline;">.</span></p>
<ul>
<li style="vertical-align: baseline;">
<p><strong style="vertical-align: baseline;">For the Platform team</strong><span style="vertical-align: baseline;">, Eventarc Advanced provides assurance that a bus can strictly enforce integrity and confidentiality on every message, bringing "service-mesh-like" security to the event layer.</span></p>
</li>
<li style="vertical-align: baseline;">
<p><strong style="vertical-align: baseline;">For the developer</strong><span style="vertical-align: baseline;">, it restores autonomy. The pipeline allows teams to filter, transform, convert, and route events to fit their specific needs, enabling them to treat events as first-class products rather than opaque artifacts.</span></p>
</li>
</ul>
<p><span style="vertical-align: baseline;">This architecture lays the foundation for the next generation of intelligent applications. A secure, typed, and trustworthy event mesh can serve as the backbone for generative AI agents and real-time analytics, allowing you to safely expose business context to the systems that need it most.</span></p>
<h3><strong style="vertical-align: baseline;">Get started</strong></h3>
<p><span style="vertical-align: baseline;">Don't let governance slow down your innovation. Here are some Eventarc Advanced resources to get you on your way:</span></p>
<ul>
<li style="vertical-align: baseline;">
<p><strong style="vertical-align: baseline;">Learn more:</strong><span style="vertical-align: baseline;"> Dive into the full capabilities of the Bus and Pipeline in the </span><a href="https://cloud.google.com/eventarc/docs"><span style="text-decoration: underline; vertical-align: baseline;">Eventarc Advanced documentation</span></a><span style="vertical-align: baseline;">.</span></p>
</li>
<li style="vertical-align: baseline;">
<p><strong style="vertical-align: baseline;">Get hands-on:</strong><span style="vertical-align: baseline;"> Deploy the "Retail Event Mesh" scenario yourself and explore enterprise patterns with our </span><a href="https://cloud.google.com/eventarc/docs/quickstarts"><span style="text-decoration: underline; vertical-align: baseline;">Quickstarts and Tutorials</span></a><span style="vertical-align: baseline;">.</span></p>
</li>
<li style="vertical-align: baseline;">
<p><strong style="vertical-align: baseline;">Start building:</strong><span style="vertical-align: baseline;"> Go to the </span><a href="https://console.cloud.google.com/eventarc"><span style="text-decoration: underline; vertical-align: baseline;">Google Cloud console</span></a><span style="vertical-align: baseline;"> to configure your first bus and pipeline today.</span></p>
</li>
<li><strong style="vertical-align: baseline;">Let's talk:</strong><span style="vertical-align: baseline;"> Have a complex enterprise use case? </span><a href="https://cloud.google.com/contact"><span style="text-decoration: underline; vertical-align: baseline;">Contact Google Cloud Sales</span></a><span style="vertical-align: baseline;"> to discuss how Eventarc Advanced fits into your broader integration strategy.</span></li>
</ul></div>
