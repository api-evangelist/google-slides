---
title: "Powering the next generation of agents with Google Cloud databases"
url: "https://cloud.google.com/blog/products/databases/managed-mcp-servers-for-google-cloud-databases/"
date: "Wed, 18 Feb 2026 18:00:00 +0000"
author: "Rahul Deshmukh"
feed_url: "https://cloudblog.withgoogle.com/products/application-development/rss"
---
<div class="block-paragraph_advanced"><p><span style="vertical-align: baseline;">For developers building AI applications, including custom agents and chatbots, the open-source </span><a href="https://www.anthropic.com/news/model-context-protocol" rel="noopener" target="_blank"><span style="text-decoration: underline; vertical-align: baseline;">Model Context Protocol (MCP)</span></a><span style="vertical-align: baseline;"> standard enables your innovations to access data and tools consistently and securely. At the end of 2025, </span><a href="https://cloud.google.com/blog/products/ai-machine-learning/announcing-official-mcp-support-for-google-services"><span style="text-decoration: underline; vertical-align: baseline;">we introduced managed and remote MCP support</span></a><span style="vertical-align: baseline;"> for services like Google Maps and </span><a href="https://cloud.google.com/bigquery"><span style="text-decoration: underline; vertical-align: baseline;">BigQuery</span></a><span style="vertical-align: baseline;">, establishing a standard method for AI to connect with tools, and effectively creating a universal interface for applications. Today, we are expanding this offering to include PostgreSQL with </span><a href="https://cloud.google.com/products/alloydb"><span style="text-decoration: underline; vertical-align: baseline;">AlloyDB</span></a><span style="vertical-align: baseline;">, </span><a href="https://cloud.google.com/spanner"><span style="text-decoration: underline; vertical-align: baseline;">Spanner</span></a><span style="vertical-align: baseline;"> and </span><a href="https://cloud.google.com/sql"><span style="text-decoration: underline; vertical-align: baseline;">Cloud SQL</span></a><span style="vertical-align: baseline;">, as well as  </span><a href="https://cloud.google.com/products/firestore"><span style="text-decoration: underline; vertical-align: baseline;">Firestore</span></a><span style="vertical-align: baseline;"> and </span><a href="https://cloud.google.com/bigtable"><span style="text-decoration: underline; vertical-align: baseline;">Bigtable</span></a><span style="vertical-align: baseline;"> for high-performance NoSQL workloads, and introducing a new </span><a href="https://developers.googleblog.com/introducing-the-developer-knowledge-api-and-mcp-server/" rel="noopener" target="_blank"><span style="text-decoration: underline; vertical-align: baseline;">Developer Knowledge MCP server</span></a><span style="vertical-align: baseline;">, which presents an API to connect IDEs to Google’s documentation. These servers run in Google Cloud, providing a secure interface for Gemini and other MCP-compliant clients to easily interact with data and infrastructure.</span></p>
<p><span style="vertical-align: baseline;">With the launch of Gemini 3, developers gained advanced reasoning capabilities to plan, build, and solve complex problems. But for an AI model to function as a useful "agent," it must reliably interact with its environment. Today’s announcement extends these capabilities more broadly to the database tools our customers leverage daily as the backbone of their work environment.</span></p>
<p><span style="vertical-align: baseline;">To connect your agents to these servers, you don’t need to deploy infrastructure. Just configure the MCP server endpoint in the agent configuration and immediately gain access to your operational data, backed by enterprise-grade auditing, observability and governance. With no infrastructure management, you can scale your agentic workloads without incurring operational overhead.</span></p>
<h3><span style="vertical-align: baseline;">Bringing operational data to agents</span></h3>
<p><span style="vertical-align: baseline;">These new managed servers enable agents to access specific capabilities across our portfolio:</span></p>
<ul>
<li style="vertical-align: baseline;">
<p><strong style="vertical-align: baseline;">AlloyDB for PostgreSQL:</strong><span style="vertical-align: baseline;"> Agents can interact with PostgreSQL workloads, enabling tasks such as schema creation, diagnosing  complex queries for slowness and performing vector similarity search.</span></p>
</li>
<li style="vertical-align: baseline;">
<p><strong style="vertical-align: baseline;">Spanner:</strong><span style="vertical-align: baseline;"> With unified multi-model capabilities in Spanner such as Spanner Graph, agents can model and query complex relationships directly alongside relational and semantic data using standard (SQL and GQL) queries. This allows agents to quickly uncover deep insights (like identifying fraud rings or generating product recommendations) using the MCP tools at its disposal.</span></p>
</li>
<li style="vertical-align: baseline;">
<p><strong style="vertical-align: baseline;">Cloud SQL for PostgreSQL, MySQL and SQL Server</strong><strong style="vertical-align: baseline;">:</strong><span style="vertical-align: baseline;"> Developers and database administrators can use the Cloud SQL MCP Server across MySQL, PostgreSQL, and SQL Server fleets for natural language interactions with the database, AI-assisted app development, query performance optimization and database troubleshooting via agents.</span></p>
</li>
<li style="vertical-align: baseline;">
<p><strong style="vertical-align: baseline;">Bigtable:</strong><span style="vertical-align: baseline;"> Bigtable’s flexible schema and high-throughput ingestion capabilities are commonly used for building digital integration hubs and managing time series data. MCP simplifies automating operational workflows and developing agentic customer support, CRM, human resources, IT operations, supply chain and logistics applications with this data.</span></p>
</li>
<li style="vertical-align: baseline;">
<p><strong style="vertical-align: baseline;">Firestore:</strong><span style="vertical-align: baseline;"> Focused on mobile and web development, the Firestore MCP server enables agents to sync with live document collections. This supports dynamic interactions such as checking user session states or verifying order statuses via natural language prompts.</span></p>
</li>
</ul>
<h3><span style="vertical-align: baseline;">Managing applications and infrastructure</span></h3>
<p><span style="vertical-align: baseline;">Beyond data retrieval, we are enabling agents to help build and manage applications. The </span><a href="https://developers.google.com/knowledge/mcp" rel="noopener" target="_blank"><strong style="text-decoration: underline; vertical-align: baseline;">Developer Knowledge MCP server</strong></a><span style="vertical-align: baseline;"> connects IDEs to Google’s documentation, allowing agents to answer technical questions and troubleshoot code with relevant context.</span></p>
<h3><span style="vertical-align: baseline;">Security and governance</span></h3>
<p><span style="vertical-align: baseline;">Connecting an agent to a database requires robust security and governance. These servers are built on Google Cloud's standard identity and observability frameworks:</span></p>
<ul>
<li style="vertical-align: baseline;">
<p><strong style="vertical-align: baseline;">Identity-first security:</strong><span style="vertical-align: baseline;"> Authentication is handled entirely through Identity and Access Management (IAM) rather than shared keys. This ensures agents can only access the specific tables or views explicitly authorized by the user.</span></p>
</li>
<li style="vertical-align: baseline;">
<p><strong style="vertical-align: baseline;">Full observability:</strong><span style="vertical-align: baseline;"> To track agent activity, every query and action taken via these MCP servers is logged in Cloud Audit Logs. This provides security teams with a record of every database interaction, maintaining visibility alongside ease of access.</span></p>
</li>
</ul>
<h3><span style="vertical-align: baseline;">Demo: From local code to managed data</span></h3>
<p><span style="vertical-align: baseline;">Let’s see these new MCP servers in action.</span></p>
<p><span style="vertical-align: baseline;">Imagine an agent designed to automate the migration of a full-stack event management platform for fitness communities. Through a series of natural language instructions in the Gemini CLI, the agent utilizes the </span><a href="https://docs.cloud.google.com/sql/docs/mysql/use-cloudsql-mcp"><strong style="text-decoration: underline; vertical-align: baseline;">Cloud SQL remote MCP server</strong></a><span style="vertical-align: baseline;"> to provision a managed PostgreSQL instance, apply the correct schema, and securely migrate your local data. You don't need to master complex </span><code style="vertical-align: baseline;">gcloud</code><span style="vertical-align: baseline;"> commands or become a Cloud SQL expert; the agent handles the heavy lifting. This transition is architected in real-time by the </span><strong style="vertical-align: baseline;">Developer Knowledge MCP server</strong><span style="vertical-align: baseline;">, which references official documentation to guide the agent through best practices — easily upgrading your application's backbone from local storage to a fully managed enterprise database.</span></p></div>
<div class="block-image_full_width">






  
    <div class="article-module h-c-page">
      <div class="h-c-grid">
  

    <figure class="article-image--large
      
      
        h-c-grid__col
        h-c-grid__col--6 h-c-grid__col--offset-3
        
        
      ">

      
      
        
        <img alt="1 onemcplaunchblogdemo" src="https://storage.googleapis.com/gweb-cloudblog-publish/original_images/1_onemcplaunchblogdemo.gif" />
        
        </a>
      
    </figure>

  
      </div>
    </div>
  




</div>
<div class="block-paragraph_advanced"><h3><span style="vertical-align: baseline;">Support for third-party agents</span></h3>
<p><span style="vertical-align: baseline;">Because these servers follow the open MCP standard, they also work with your favorite AI agents. You can easily connect clients like Anthropic’s Claude by adding a Custom Connector in the settings. Simply point it to your Google Cloud database MCP endpoint, and you are ready to start building — no complex configuration files required.</span></p></div>
<div class="block-image_full_width">






  
    <div class="article-module h-c-page">
      <div class="h-c-grid">
  

    <figure class="article-image--large
      
      
        h-c-grid__col
        h-c-grid__col--6 h-c-grid__col--offset-3
        
        
      ">

      
      
        
        <img alt="2 onemcp launch claudegif" src="https://storage.googleapis.com/gweb-cloudblog-publish/original_images/2_onemcp_launch_claudegif.gif" />
        
        </a>
      
    </figure>

  
      </div>
    </div>
  




</div>
<div class="block-paragraph_advanced"><h3><span style="vertical-align: baseline;">What’s next</span></h3>
<p><span style="vertical-align: baseline;">We’ll continue to expand this ecosystem in the coming months with managed MCP support for Looker, Database Migration Service (DMS), BigQuery Migration Service, Memorystore, Database Center, Pub/Sub, Kafka and more.</span></p>
<p><span style="vertical-align: baseline;">To start building secure, data-driven agents, explore our guides for </span><a href="https://docs.cloud.google.com/alloydb/docs/ai/use-alloydb-mcp"><span style="text-decoration: underline; vertical-align: baseline;">AlloyDB</span></a><span style="vertical-align: baseline;">, </span><a href="https://docs.cloud.google.com/spanner/docs/use-spanner-mcp"><span style="text-decoration: underline; vertical-align: baseline;">Spanner</span></a><span style="vertical-align: baseline;">, </span><a href="https://docs.cloud.google.com/sql/docs/postgres/use-cloudsql-mcp"><span style="text-decoration: underline; vertical-align: baseline;">Cloud SQL</span></a><span style="vertical-align: baseline;">, </span><a href="https://docs.cloud.google.com/bigtable/docs/use-bigtable-mcp"><span style="text-decoration: underline; vertical-align: baseline;">Bigtable</span></a><span style="vertical-align: baseline;">, and </span><a href="https://docs.cloud.google.com/firestore/native/docs/use-firestore-mcp"><span style="text-decoration: underline; vertical-align: baseline;">Firestore</span></a><span style="vertical-align: baseline;">. You can also check out these codelabs for </span><a href="https://codelabs.developers.google.com/ai-mcp-dk-csql#0" rel="noopener" target="_blank"><span style="text-decoration: underline; vertical-align: baseline;">Cloud SQL</span></a><span style="vertical-align: baseline;"> and </span><a href="https://codelabs.developers.google.com/spanner-mcp-server" rel="noopener" target="_blank"><span style="text-decoration: underline; vertical-align: baseline;">Spanner</span></a><span style="vertical-align: baseline;">, along with this </span><a href="https://www.youtube.com/watch?v=SeuhYVg8-AU" rel="noopener" target="_blank"><span style="text-decoration: underline; vertical-align: baseline;">demo video</span></a><span style="vertical-align: baseline;"> walking through the app migration to Google Cloud.</span></p></div>
<div class="block-video">



<div class="article-module article-video ">
  <figure>
    <a class="h-c-video h-c-video--marquee" href="https://youtube.com/watch?v=SeuhYVg8-AU">

      
        <img alt="Gemini CLI + Google MCPs: Migrate &amp; deploy full stack apps" src="//img.youtube.com/vi/SeuhYVg8-AU/maxresdefault.jpg" />
      
      <svg class="h-c-video__play h-c-icon h-c-icon--color-white" xmlns="http://www.w3.org/2000/svg">
        <use xlink:href="#mi-youtube-icon" xmlns:xlink="http://www.w3.org/1999/xlink"></use>
      </svg>
    </a>

    
  </figure>
</div>

<div class="h-c-modal--video">
   <a class="glue-yt-video" href="https://youtube.com/watch?v=SeuhYVg8-AU">
   </a>
</div>

</div>
