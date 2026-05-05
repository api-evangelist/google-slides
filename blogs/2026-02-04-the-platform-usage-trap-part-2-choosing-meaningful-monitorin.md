---
title: "The platform usage trap part 2: Choosing meaningful monitoring metrics"
url: "https://cloud.google.com/blog/products/application-development/how-john-lewis-partnership-chose-its-monitoring-metrics/"
date: "Wed, 04 Feb 2026 18:00:00 +0000"
author: "Alex Moss"
feed_url: "https://cloudblog.withgoogle.com/products/application-development/rss"
---
<div class="block-paragraph_advanced"><p><span style="font-style: italic; vertical-align: baseline;">In </span><a href="https://cloud.google.com/blog/products/application-development/at-john-lewis-partnership-measuring-developer-platform-value"><span style="font-style: italic; text-decoration: underline; vertical-align: baseline;">part one</span></a><span style="font-style: italic; vertical-align: baseline;"> of this article, Alex Moss from the John Lewis Partnership covered the metrics that they use to measure the value of their developer platform. Now, let's talk about a crucial aspect of any measurement strategy: choosing the right things to measure. It's easy to get lost in a sea of data or to focus on metrics that look impressive, but don't actually reflect the health of your platform or the experience of your developers. Here, Alex shares the John Lewis philosophy on how to choose meaningful metrics and present them in a way that drives the right conversations and actions, ensuring that the data is always presented with as much context as possible. - Darren Evans</span></p>
<p><span style="vertical-align: baseline;">While the solution we detailed in the first half of this article worked very well, relying solely on objective measures comes with a number of traps. They are very easy to misinterpret: either wasting time (“the team is working on another product at the moment”) or not telling the right story (“the incident wasn’t closed properly”). This leads to a scaling challenge: Chatting with a small number of teams to understand a situation is one thing. But when you are only one small team trying to build a product, and you need to talk across several dozen teams, it’s not so easy.</span></p>
<h3><strong style="vertical-align: baseline;">Collecting engineers’ subjective feedback</strong></h3>
<p><span style="vertical-align: baseline;">We needed a way to collate more subjective feedback, ideally in a form that we could visualize and contrast to the objective DORA and other service metrics we held.</span></p>
<p><span style="vertical-align: baseline;">Our initial attempt at this involved creating Service Operability Assessments — questionnaires that tenants fill in every quarter. Service Operability Assessments are intended to hold a series of thought-provoking questions aimed at whether the team is following good practices for running their service. This worked well with an experienced facilitator (usually a senior platform engineer) who could ask further probing questions and pull out the key feedback and actions. But as you might imagine, this suffered from scaling challenges. We eventually let this be handled entirely self-service — an imperfect system, since many teams are quite happy to just copy/paste their answers from the previous quarter, which may or may not reflect reality!</span></p>
<p><span style="vertical-align: baseline;">We then learned about a tool called </span><a href="https://getdx.com/" rel="noopener" target="_blank"><span style="text-decoration: underline; vertical-align: baseline;">the DX platform</span></a><span style="vertical-align: baseline;">, which significantly changed how we approached this, and which is now used across our entire Engineering community. It works by surveying individual engineers (rather than teams) for a few minutes every three months. The questions are curated based on DX’s research, backed by the founders of DORA and other similar frameworks. We’ve found it very helpful to be able to slice the results in different ways, including looking at areas across whole platforms or deep-diving on particular teams. The latter, in combination with our DORA data, makes for rich conversations. For example, in the DX tool, a team which recently suffered through some highly impactful incidents might also have registered concerns on “Production Debugging,” while another team that saw a marked drop in release frequency flagged worries around “Change Confidence” or “Ease of Release.” The platforms team can at this point step in to offer advice or potentially implement new features to help with the issues the teams are seeing.</span></p></div>
<div class="block-image_full_width">






  
    <div class="article-module h-c-page">
      <div class="h-c-grid">
  

    <figure class="article-image--large
      
      
        h-c-grid__col
        h-c-grid__col--6 h-c-grid__col--offset-3
        
        
      ">

      
      
        
        <img alt="1" src="https://storage.googleapis.com/gweb-cloudblog-publish/images/1_J4WNCsj.max-1000x1000.png" />
        
        </a>
      
    </figure>

  
      </div>
    </div>
  




</div>
<div class="block-paragraph_advanced"><p><span style="vertical-align: baseline;">The pre-built drivers and reports in DX are tremendously useful, but we also augment it with our own custom queries to help us understand areas of current focus. For example, we measure Customer Satisfaction (CSAT) for the platform and its portal (Backstage), and collect data on how long it takes for a newcomer to begin submitting pull requests and ask them about how they found the onboarding process. We also recently started assessing engineers’ opinions on the effectiveness of AI coding assistants to help justify further investment in them (instead of just relying on market insight).</span></p>
<p><span style="vertical-align: baseline;">An example of where this helped focus our efforts was with documentation, namely, building capabilities into our Backstage developer portal to make it easier for teams to view each others’ docs through pipelines that automatically publish content and make it discoverable.</span></p></div>
<div class="block-image_full_width">






  
    <div class="article-module h-c-page">
      <div class="h-c-grid">
  

    <figure class="article-image--large
      
      
        h-c-grid__col
        h-c-grid__col--6 h-c-grid__col--offset-3
        
        
      ">

      
      
        
        <img alt="2" src="https://storage.googleapis.com/gweb-cloudblog-publish/images/2_gf9lDAw.max-1000x1000.png" />
        
        </a>
      
    </figure>

  
      </div>
    </div>
  




</div>
<div class="block-paragraph_advanced"><h3><strong style="vertical-align: baseline;">Service health - Feature adoption &amp; beyond</strong></h3>
<p><span style="vertical-align: baseline;">Outside of the insights we generate from the likes of DORA and DX, we’ve recently begun questioning not only whether the platform itself is valuable, but whether tenants are </span><span style="font-style: italic; vertical-align: baseline;">getting the value they should</span><span style="vertical-align: baseline;"> from it. In other words, we’ve effectively started to measure platform feature adoption.</span></p>
<p><span style="vertical-align: baseline;">To do this, we built out what we refer to internally as our Technical Health feature. It takes the form of a custom plugin that integrates with our Backstage Developer Portal, which then queries an in-house API that surfaces data fed from a large number of small jobs that collect information on the things we want to measure. These jobs are independently releasable themselves, which allowed us to scale this up pretty quickly. </span></p>
<p><span style="vertical-align: baseline;">We currently capture four categories of health measures:</span></p>
<ol>
<li style="vertical-align: baseline;">
<p><strong style="vertical-align: baseline;">Technical health: </strong><span style="vertical-align: baseline;">We currently have 17 “technical” measures. Examples here include measuring whether teams are using our paved road pipeline and custom Microservice CRD (see previous articles </span><a href="https://cloud.google.com/blog/products/application-development/simplifying-platform-engineering-at-john-lewis-part-one"><span style="text-decoration: underline; vertical-align: baseline;">1</span></a><span style="vertical-align: baseline;"> and </span><a href="https://cloud.google.com/blog/products/application-development/simplifying-platform-engineering-at-john-lewis-part-two"><span style="text-decoration: underline; vertical-align: baseline;">2</span></a><span style="vertical-align: baseline;">) rather than “terraforming” their own resources, following our recommended Kubernetes practices (such as resource sizing, disruption budgets and lifecycle probes), keeping base images up to date, and the like. We also include some “softer” technical measures such as whether they are running pipelines frequently enough to pick up changes (we don’t run this for teams), reviewing their operability assessments, staying on top of git branches, and so on.</span></p>
</li>
<li style="vertical-align: baseline;">
<p><strong style="vertical-align: baseline;">Operational readiness:</strong><span style="vertical-align: baseline;"> Then, there are 18 measures relating to operational health — things like whether a pre-flight configuration is in place, whether runbooks are written, docs have been published, and so on. This is an evolution of an Operational Readiness checklist from several years ago (back when we used to have separate Delivery and Operations teams, and therefore these sorts of checks were mandatory for “handover”). We tailored this checklist to the specific features of the platform that help teams achieve good operability, rather than being a generic list. This also serves to help our Service Management team feel confident that the right practices are being followed, thereby eliminating a point of friction when carrying out manual reviews.</span></p>
</li>
<li style="vertical-align: baseline;">
<p><strong style="vertical-align: baseline;">Migrations: </strong><span style="vertical-align: baseline;">From time to time, the Platform requires tenants to carry out work to keep up with changes to the platform itself. A classic example of this is getting teams to deal with deprecated Kubernetes API versions. This also includes adoption of different features that we want to drive more forcefully in order to remove the older way of doing things (say for example, in favour of something more secure). We found that as the Platform grew, we had a long tail of migration work that we needed teams to perform, providing an easy way for Product Managers and Delivery Leads to prioritize their teams’ workloads.</span></p>
</li>
<li style="vertical-align: baseline;">
<p><strong style="vertical-align: baseline;">Broader engineering practices: </strong><span style="vertical-align: baseline;">We recently opened up the feature to allow other teams to contribute — in this case, our Engineering leadership — to build in their own measures, such as whether teams are keeping up to date with versions of our design system or whether they’re following broader engineering practices that extend beyond just the JL Digital Platform. </span></p>
</li>
</ol>
<p><span style="vertical-align: baseline;">We present this data through aggregated views (like the example shown below), as well as individual tasks and broader leaderboards — all designed to catch the eye of those with influence over a team’s priorities. We’ve found that the desire for an engineer to turn a traffic-light green can be a powerful motivator — far more effective than relying on documentation or announcements.</span></p></div>
<div class="block-image_full_width">






  
    <div class="article-module h-c-page">
      <div class="h-c-grid">
  

    <figure class="article-image--large
      
      
        h-c-grid__col
        h-c-grid__col--6 h-c-grid__col--offset-3
        
        
      ">

      
      
        
        <img alt="3" src="https://storage.googleapis.com/gweb-cloudblog-publish/images/3_paqGoLi.max-1000x1000.png" />
        
        </a>
      
    </figure>

  
      </div>
    </div>
  




</div>
<div class="block-paragraph_advanced"><p><span style="vertical-align: baseline;">This technology works through custom plugins that we’ve built for the Backstage Portal. Each “health check” is itself its own microservice (often running as a job) which interrogates the appropriate system to determine whether the measure is met. For example, one microservice checks that a PodDisruptionBudget has been created by querying Kubernetes directly, while another that looks at whether distroless base images are in use, does so by inspecting container image layers. There’s a template for creating new metrics, which makes it easy for engineers to create new ones — including those outside the platform team themselves. The results are stored in BigQuery, with an API to make Backstage plugin development simpler.</span></p>
<p><span style="vertical-align: baseline;">A reality of introducing measures like this is that it drives more work into the product teams. It is important that your culture be ready for this. If we had implemented these measures very early in the platform’s life, this would likely have affected how the product was perceived — perhaps as very strict or inhibiting the pace of change with guardrails. This can negatively impact overall adoption. By introducing these later on, we benefited from many tenants who already saw the platform as very valuable, as well as the confidence that we had selected the right measures and could apply them consistently. That said, we did still see a small drop in CSAT for the platform after we started doing this. We try to be considerate about the pace that we launch each measure to give product teams the time to absorb the work, as well as provide a means for teams to suppress the indicators that aren’t relevant to them. For example, a tenant might deliberately choose not to use pod autoscaling for performance reasons, or have a functional reason why they can’t use our Microservice CRD.</span></p>
<p><span style="vertical-align: baseline;">The introduction of these sorts of assurance measures on tenant behaviour is a reflection of the maturity of the platform. In the early days, we relied on highly skilled teams to do the right thing whilst going fast. But as time has passed, we’ve witnessed a variety of skills and capabilities, combined with shifts in ownership of services, that pushed us to introduce techniques to drive the right outcomes. This is also due to the platform itself becoming complex — the cognitive load for a new team is much higher than it was, due to all its new features. We needed to put some lights along the edges of our paved road to help teams stay on it!</span></p>
<p><span style="vertical-align: baseline;">Throughout this evolution, we’ve continued to report on our key results for the business themselves: Are we still doing what they want of us? This has naturally shifted from “go fast, enable teams” (which we largely see as a solved problem, to be honest) towards “do it safely, and manage your technical debt.”</span></p>
<h3><strong style="vertical-align: baseline;">Are you being served? Key takeaways</strong></h3>
<p><span style="vertical-align: baseline;">Long story short, the question of whether a developer platform has value is complex, and can be answered in many ways. As you embark on building out — and quantifying — your own developer platform, here are a few concluding thoughts to keep in mind:  </span></p>
<ol>
<li style="vertical-align: baseline;">
<p><strong style="vertical-align: baseline;">Measurement is a journey, not a destination:</strong><span style="vertical-align: baseline;"> Start by measuring something meaningful to your stakeholders, but be prepared to adapt as your platform evolves. In the beginning, it’s okay to prioritize further investment in your product, but it’s better to actually measure how the platform is enabling your teams. The things that mattered when you were initially proving out the platform’s viability are unlikely to be what are important several years later when your features are more mature and your priorities have shifted.</span></p>
</li>
<li style="vertical-align: baseline;">
<p><strong style="vertical-align: baseline;">Listen to the humans: </strong><span style="vertical-align: baseline;">Don’t assume that just because your platform is being used, that it is providing value. The most powerful metrics are often qualitative; engineers wanting to use your tool and CSAT are strong signals, but asking them questions about how they are using it is a better way to gain insight into how you can improve it. It is hard to figure out what’s working (and what isn’t) through measurement alone.</span></p>
</li>
<li style="vertical-align: baseline;">
<p><strong style="vertical-align: baseline;">Data is for enabling, not just reporting:</strong><span style="vertical-align: baseline;"> Use your insights to help teams improve, not just to show graphs to leadership. Further, be transparent about what specific data led you to act. For example, when you see a dip in release frequency for a specific team, use that data to start a conversation about potential roadblocks rather than simply flagging it as a problem. By doing this, you build the trust and goodwill with both leadership and your tenants to keep moving the platform forward. </span></p>
</li>
</ol>
<hr />
<p><sub><span style="font-style: italic; vertical-align: baseline;">The evolution of the John Lewis Partnership’s measurement strategy serves as a compelling case study. By transitioning from basic lead-time tracking to a holistic model — blending DORA metrics with qualitative developer feedback — they demonstrated that true platform success is defined by the genuine value it delivers, not merely by adoption rates.</span></sub></p>
<p><sub><span style="font-style: italic; vertical-align: baseline;">To learn more about platform engineering on Google Cloud, check out some of our other articles: Using Platform Engineering to simplify the developer experience - </span><a href="https://cloud.google.com/blog/products/application-development/simplifying-platform-engineering-at-john-lewis-part-one"><span style="font-style: italic; text-decoration: underline; vertical-align: baseline;">part one</span></a><span style="font-style: italic; vertical-align: baseline;">, </span><a href="https://cloud.google.com/blog/products/application-development/simplifying-platform-engineering-at-john-lewis-part-two"><span style="font-style: italic; text-decoration: underline; vertical-align: baseline;">part two</span></a><span style="font-style: italic; vertical-align: baseline;">, </span><a href="https://cloud.google.com/blog/products/application-development/common-myths-about-platform-engineering"><span style="font-style: italic; text-decoration: underline; vertical-align: baseline;">5 myths about platform engineering: what it is and what it isn’t</span></a><span style="font-style: italic; vertical-align: baseline;"> and</span><span style="font-style: italic; vertical-align: baseline;"> </span><a href="https://cloud.google.com/blog/products/application-development/another-five-myths-about-platform-engineering"><span style="font-style: italic; text-decoration: underline; vertical-align: baseline;">Another five myths about platform engineering</span></a><span style="font-style: italic; vertical-align: baseline;">. We also recommend reading about </span><a href="https://cloud.google.com/blog/products/application-development/introducing-app-hub"><span style="text-decoration: underline; vertical-align: baseline;">App Hub</span></a><span style="vertical-align: baseline;">, </span><span style="font-style: italic; vertical-align: baseline;">our foundational tool for managing application-centric governance across your organization.</span></sub></p></div>
