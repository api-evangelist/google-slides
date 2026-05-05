---
title: "Day 2 at Google Cloud Next: A marathon developer keynote"
url: "https://cloud.google.com/blog/topics/google-cloud-next/next26-day-2-recap/"
date: "Thu, 23 Apr 2026 13:00:00 +0000"
author: "Google Cloud Content & Editorial"
feed_url: "https://cloudblog.withgoogle.com/products/application-development/rss"
---
<div class="block-paragraph_advanced"><p><span style="vertical-align: baseline;">At Google Cloud, every day is Developer Day, but none so much as day 2 of Google Cloud Next, when we hold the developer keynote.  This year’s topic? An in-depth look at </span><a href="https://cloud.google.com/blog/products/ai-machine-learning/introducing-gemini-enterprise-agent-platform"><span style="text-decoration: underline; vertical-align: baseline;">Gemini Enterprise Agent Platform</span></a><span style="vertical-align: baseline;">. This year’s theme? Planning a marathon for 10,000 participants through the Las Vegas Strip.</span></p>
<p><span style="vertical-align: baseline;">OK, let’s run with it. </span></p>
<h3><span style="vertical-align: baseline;">Gemini Enterprise Agent Platform: A warm up</span></h3>
<p><span style="vertical-align: baseline;">As the evolution of Vertex AI, </span><strong style="vertical-align: baseline;">Agent Platform</strong><span style="vertical-align: baseline;"> “allows you to build autonomous agents that proactively help users — and complete tasks independently,” said Brad Calder, President, GCP and SRE. The platform does so with a whole suite of tools and capabilities to build, scale, govern, and optimize your agents. </span></p></div>
<div class="block-image_full_width">






  
    <div class="article-module h-c-page">
      <div class="h-c-grid">
  

    <figure class="article-image--large
      
      
        h-c-grid__col
        h-c-grid__col--6 h-c-grid__col--offset-3
        
        
      ">

      
      
        
        <img alt="1" src="https://storage.googleapis.com/gweb-cloudblog-publish/images/1_cBnVOvk.max-1000x1000.jpg" />
        
        </a>
      
    </figure>

  
      </div>
    </div>
  




</div>
<div class="block-paragraph_advanced"><p><span style="vertical-align: baseline;">Brad then passed the baton to keynote emcees Richard Seroter, Chief Evangelist, and Emma Twersky, Developer Relations Engineer, for an in-depth run-through of the agentic marathon simulator.</span></p>
<p><span style="vertical-align: baseline;">The system uses three main agents: A planner to determine routes; an evaluator that assesses routes based on business and community requirements; and a simulator that takes the route, adding actors and randomized behaviors to test the impact on the city,</span></p>
<p><span style="vertical-align: baseline;">This, Emma said, turns out to be “a great example of how agents can help us plan, simulate, and think about solving a really big challenge.” </span></p></div>
<div class="block-image_full_width">






  
    <div class="article-module h-c-page">
      <div class="h-c-grid">
  

    <figure class="article-image--large
      
      
        h-c-grid__col
        h-c-grid__col--6 h-c-grid__col--offset-3
        
        
      ">

      
      
        
        <img alt="2" src="https://storage.googleapis.com/gweb-cloudblog-publish/images/2_u7NylGU.max-1000x1000.jpg" />
        
        </a>
      
    </figure>

  
      </div>
    </div>
  




</div>
<div class="block-paragraph_advanced"><h3><span style="vertical-align: baseline;">First off the blocks: Building the agent</span></h3>
<p><span style="vertical-align: baseline;">Mofi Rahman, Developer Relations Engineer, came onstage to demo how the </span><strong style="vertical-align: baseline;">Agent Development Kit (ADK)</strong><span style="vertical-align: baseline;">, Google Cloud remote </span><strong style="vertical-align: baseline;">Model Context Protocol (MCP) servers</strong><span style="vertical-align: baseline;">, and </span><strong style="vertical-align: baseline;">Agent Runtime</strong><span style="vertical-align: baseline;"> provide the planner agent with the </span><strong style="vertical-align: baseline;">Instructions</strong><span style="vertical-align: baseline;">, </span><strong style="vertical-align: baseline;">Skills</strong><span style="vertical-align: baseline;">, and </span><strong style="vertical-align: baseline;">Tools</strong><span style="vertical-align: baseline;"> it needs to improve the initial agent. By the end of the demo, the simulator had generated a route. </span></p>
<p><span style="vertical-align: baseline;">“The simulated route looks beautiful,” said Mofi. “Looks like the runners are going to get an amazing view of the entire Las Vegas Strip.”</span></p></div>
<div class="block-image_full_width">






  
    <div class="article-module h-c-page">
      <div class="h-c-grid">
  

    <figure class="article-image--large
      
      
        h-c-grid__col
        h-c-grid__col--6 h-c-grid__col--offset-3
        
        
      ">

      
      
        
        <img alt="3" src="https://storage.googleapis.com/gweb-cloudblog-publish/images/3_Fz2OBHO.max-1000x1000.jpg" />
        
        </a>
      
    </figure>

  
      </div>
    </div>
  




</div>
<div class="block-paragraph_advanced"><h3><span style="vertical-align: baseline;">An agent to evaluate the agent</span></h3>
<p><span style="vertical-align: baseline;">Next, Ivan Nardini, Developer Relations Engineer, and Casey West, Architecture Advocate, showed us how to evaluate the agent, and build a UI for it. “We want to show you how to move from fragile, unpredictable agentic loops, to a rigorously evaluated network of experts that literally build their own UI,” Casey said.</span></p>
<p><span style="vertical-align: baseline;">They did so by deploying a separate model to judge the route, checking both deterministic (e.g., route length) and non-deterministic (e.g., community impact) criteria. For UI development, they showed off the </span><strong style="vertical-align: baseline;">Agent-to-User Interface</strong><span style="vertical-align: baseline;">, or </span><strong style="vertical-align: baseline;">A2UI</strong><span style="vertical-align: baseline;">, an open-source standard developed by Google that created an interface in a single shot. They also used the </span><strong style="vertical-align: baseline;">Agent-to-Agent Protocol</strong><span style="vertical-align: baseline;">, or </span><strong style="vertical-align: baseline;">A2A</strong><span style="vertical-align: baseline;">, and Agent Platform’s </span><strong style="vertical-align: baseline;">Agent Registry</strong><span style="vertical-align: baseline;">, to connect and see which agents are deployed. </span></p>
<p><span style="vertical-align: baseline;">“Think of Agent Registry as the DNS of your internet of agents,” Casey said. </span></p>
<h3><span style="vertical-align: baseline;">Agents that never forget</span></h3>
<p><span style="vertical-align: baseline;">Richard then mused about how to build agents that get better with time, that “take the learnings from the simulation and optimize for the next run.” Because the answer shouldn’t be to “cram raw text in every request we send back to our agents.” </span></p>
<p><span style="vertical-align: baseline;">To capture this learned knowledge, Agent Platform offers </span><strong style="vertical-align: baseline;">Agent Platform Sessions</strong><span style="vertical-align: baseline;"> and </span><strong style="vertical-align: baseline;">Memory Bank</strong><span style="vertical-align: baseline;">, plus the ability to turn to tools like Spark or a database to retrieve more information, resulting in an even stronger simulator.</span></p></div>
<div class="block-paragraph_advanced"><h3><span style="vertical-align: baseline;">When agents go off course</span></h3>
<p><span style="vertical-align: baseline;">Thus far, everything had gone swimmingly, but then Richard accidentally “broke” the simulator agent. That provided a perfect opportunity for Megan O’Keefe, Senior Staff Developer Advocate, to show off </span><strong style="vertical-align: baseline;">Agent Interoperability</strong><span style="vertical-align: baseline;"> and </span><strong style="vertical-align: baseline;">Gemini Cloud Assist</strong><span style="vertical-align: baseline;">, and how to use them to debug agents at scale. </span></p>
<p><span style="vertical-align: baseline;">“With these autonomous agents, the production challenge isn’t just scaling the infrastructure, it’s managing the reasoning, the tool calls — all the places in the system where something can go wrong!” Megan said. </span></p>
<p><span style="vertical-align: baseline;">Megan used </span><strong style="vertical-align: baseline;">Agent Runtime trace view</strong><span style="vertical-align: baseline;"> to see where the problem was, and using natural language, launched a </span><strong style="vertical-align: baseline;">Cloud Assist Investigation</strong><span style="vertical-align: baseline;"> to explore logs and events, which pointed to a specific line of code as the offender. Megan then opened up her </span><strong style="vertical-align: baseline;">Antigravity IDE</strong><span style="vertical-align: baseline;"> (powered by </span><strong style="vertical-align: baseline;">Gemini 3</strong><span style="vertical-align: baseline;">, and connected via MCP) to find the problem (an insufficiently run “event compaction” run) and to suggest a fix (add a token_threshold parameter to the event compaction config). She approved the fix and committed it to source, triggering a redeployment to </span><strong style="vertical-align: baseline;">Agent Platform</strong><span style="vertical-align: baseline;">. Problem solved!</span></p>
<h3><span style="vertical-align: baseline;">Scaling the agents</span></h3>
<p><span style="vertical-align: baseline;">To this point, all of the presenters had been showing off agent services running as </span><strong style="vertical-align: baseline;">Cloud Run</strong><span style="vertical-align: baseline;"> services. Bobby Allen, Group Product Manager, then showed how to convert the apps to </span><strong style="vertical-align: baseline;">Google Kubernetes Engine (GKE)</strong><span style="vertical-align: baseline;">, which provides greater control, as well as to use a customized </span><strong style="vertical-align: baseline;">Gemma 4</strong><span style="vertical-align: baseline;"> model, all by vibe coding in the Antigravity editor, which is connected to Cloud Assist. Along the way, Bobby also migrated the agents from </span><strong style="vertical-align: baseline;">GCSFuse</strong><span style="vertical-align: baseline;"> to a high-performance </span><strong style="vertical-align: baseline;">Lustre </strong><span style="vertical-align: baseline;">file system. </span></p>
<p><span style="vertical-align: baseline;">Closely related to scaling is sharing — making agents available for the world to use and build on. Ines Envid, Senior Director, Product Management and Jason Davenport, Area Technical Lead, showed how to build no-code agents from the </span><strong style="vertical-align: baseline;">Gemini Enterprise</strong><span style="vertical-align: baseline;"> app, and how to integrate them with other, “high-code” agents. </span></p>
<h3><span style="vertical-align: baseline;">Shifting down</span></h3>
<p><span style="vertical-align: baseline;">Last but not least, it was time to talk about security and governance. “Agents give users and other agents new ways to intentionally — or unintentionally — expose data and behavior in ways that we may not want,” mused Emma. </span></p>
<p><span style="vertical-align: baseline;">The standard response to that is to “shift left” — move testing, quality, and performance evaluation earlier in the development process — but for developers, that usually means more work, Richard said. “It’s not sustainable for developers to be responsible for all the layers of the stack,” he said. Instead, “we need to shift down.”</span></p>
<p><span style="vertical-align: baseline;">To help, there’s </span><strong style="vertical-align: baseline;">Agent Identity</strong><span style="vertical-align: baseline;"> and </span><strong style="vertical-align: baseline;">Agent Gateway</strong><span style="vertical-align: baseline;">, demoed by Ankur Kotwal, head of Cloud Developer Relations. Ankur showed how Agent Gateway uses IAM policies to ensure agent actions are only accessible by approved sources, and how Agent Identity provides each agent with a unique and immutable credential. Then, </span><strong style="vertical-align: baseline;">Agent Policies</strong><span style="vertical-align: baseline;"> can be configured to provide guardrails for the agents.</span></p>
<p><span style="vertical-align: baseline;">Yinon Costica, Co-Founder and VP of Product at Wiz, then went a step further and showed how Wiz can scan your agent code and infrastructure, and </span><strong style="vertical-align: baseline;">Wiz Green Agent</strong><span style="vertical-align: baseline;"> can suggest root cause remediations. </span></p>
<p><span style="vertical-align: baseline;">“It’s a full architecture for security to easily understand what you built without you having to actually explain it,” Yinon said. Better yet, he also showed using this functionality from </span><strong style="vertical-align: baseline;">Anthropic’s Claude Code with Opus. </strong><span style="vertical-align: baseline;">“With Wiz, we want to enable your choice of tools and models to fix and prevent real risks,” he said.</span></p></div>
<div class="block-video">



<div class="article-module article-video ">
  <figure>
    <a class="h-c-video h-c-video--marquee" href="https://youtube.com/watch?v=A01DQ8_xy7Q">

      
        

        <div class="article-video__aspect-image">
          <span class="h-u-visually-hidden">Google Cloud Next &#x27;26 Developer Keynote</span>
        </div>
      
      <svg class="h-c-video__play h-c-icon h-c-icon--color-white" xmlns="http://www.w3.org/2000/svg">
        <use xlink:href="#mi-youtube-icon" xmlns:xlink="http://www.w3.org/1999/xlink"></use>
      </svg>
    </a>

    
  </figure>
</div>

<div class="h-c-modal--video">
   <a class="glue-yt-video" href="https://youtube.com/watch?v=A01DQ8_xy7Q">
   </a>
</div>

</div>
<div class="block-paragraph_advanced"><h3><span style="vertical-align: baseline;">The finish line</span></h3>
<p><span style="vertical-align: baseline;">With this, the developer keynote came to an end. But for Google Cloud developers, it’s just the beginning, as the entire solution is available as source code in GitHub, and all the </span><a href="https://codelabs.developers.google.com/next26/dev-keynote/build-multi-agent-marathon-planner#0" rel="noopener" target="_blank"><span style="text-decoration: underline; vertical-align: baseline;">demos are available as Codelabs</span></a><span style="vertical-align: baseline;">. Because when it comes to agentic development, these resources will really help you hit the ground running. </span></p></div>
