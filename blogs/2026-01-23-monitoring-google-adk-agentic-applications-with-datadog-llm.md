---
title: "Monitoring Google ADK agentic applications with Datadog LLM Observability"
url: "https://cloud.google.com/blog/products/management-tools/datadog-integrates-agent-development-kit-or-adk/"
date: "Fri, 23 Jan 2026 17:00:00 +0000"
author: "Trammell Saltzgaber"
feed_url: "https://cloudblog.withgoogle.com/products/application-development/rss"
---
<div class="block-paragraph_advanced"><p><span style="vertical-align: baseline;">Google’s </span><a href="https://google.github.io/adk-docs/" rel="noopener" target="_blank"><span style="text-decoration: underline; vertical-align: baseline;">Agent Development Kit (ADK)</span></a><span style="vertical-align: baseline;"> gives you the building blocks to create powerful agentic systems. These multi-step agents can plan, loop, collaborate, and call tools dynamically to solve problems on their own. However, this flexibility also makes them unpredictable, leading to potential issues like incomplete outputs, unexpected costs, and security risks. To help you manage this complexity, </span><a href="https://www.datadoghq.com/product/llm-observability/" rel="noopener" target="_blank"><span style="text-decoration: underline; vertical-align: baseline;">Datadog LLM Observability</span></a><span style="vertical-align: baseline;"> now provides automatic instrumentation for systems built with ADK. This integration gives you the visibility to monitor agent behavior, track costs and errors, and optimize agents for response quality and safety through offline experimentation and online evaluation without extensive manual setup.</span></p>
<p><span style="vertical-align: baseline;">This is significant as agentic systems are complex, and interagent interactions and the non-deterministic nature of LLMs makes it difficult to predict responses. </span></p>
<p><span style="vertical-align: baseline;">Common risks when running these agents include:</span></p>
<ul>
<li style="vertical-align: baseline;">
<p><strong style="vertical-align: baseline;">Pace of change:</strong><span style="vertical-align: baseline;"> New foundation models drop weekly and “best-practice” prompting patterns change just as fast. Teams must constantly evaluate new combinations. </span></p>
</li>
<li style="vertical-align: baseline;">
<p><strong style="vertical-align: baseline;">Multi-agent handoffs:</strong><span style="vertical-align: baseline;"> If one agent produces low-quality output, it can cascade downstream and cause other agents to make poor decisions.</span></p>
</li>
<li style="vertical-align: baseline;">
<p><strong style="vertical-align: baseline;">Loops and retries:</strong><span style="vertical-align: baseline;"> Planners can get stuck calling the same tool repeatedly, such as retrying a search query indefinitely, which causes latency spikes.</span></p>
</li>
<li style="vertical-align: baseline;">
<p><strong style="vertical-align: baseline;">Hidden costs:</strong><span style="vertical-align: baseline;"> A single misrouted planner step can multiply token usage or API calls, pushing costs over budget.</span></p>
</li>
<li style="vertical-align: baseline;">
<p><strong style="vertical-align: baseline;">Safety and accuracy:</strong><span style="vertical-align: baseline;"> LLM responses may contain hallucinations, sensitive data, or prompt injection attempts, risking security incidents and reduced customer trust.</span></p>
</li>
</ul>
<p><span style="vertical-align: baseline;">Finally, ADK is just one of many agentic frameworks available on the market. Having to manually instrument it  only adds another learning curve to an already tedious and error-prone process.</span></p>
<h3><strong style="vertical-align: baseline;">Trace agent decisions and unexpected behaviors</strong></h3>
<p><span style="vertical-align: baseline;">Datadog LLM Observability addresses these pains by automatically instrumenting and tracing your ADK agents, so you can start evaluating your agents offline and monitoring them in production in minutes — without code changes. This allows you to visualize every step and planner choice — from agent orchestration to tool calls — on a single trace timeline.</span></p>
<p><span style="vertical-align: baseline;">For example, if an agent selects an incorrect tool to respond to a user query, it can yield unexpected errors or inaccurate responses. You can use Datadog’s visualizations to pinpoint the exact step where the incorrect tool was selected, making troubleshooting easier and helping you reproduce the issue.</span></p>
<h3><strong style="vertical-align: baseline;">Monitor token usage and latency </strong></h3>
<p><span style="vertical-align: baseline;">Sudden increases in latency or cost are often a sign of trouble in agentic applications. Datadog lets you view token usage and latency per tool, branch, and workflow to identify where errors happened and how they affected downstream steps.</span></p>
<p><span style="vertical-align: baseline;">For example, if a planner agent retries a summarization tool five times, it can significantly increase latency. Datadog highlights these loops, showing you exactly how long they took and the associated cost impact.</span></p>
<h3><strong style="vertical-align: baseline;">Evaluate agent response quality and security</strong></h3>
<p><span style="vertical-align: baseline;">Operational performance metrics like latency are critical monitoring signals, but for a holistic view of how agentic applications are performing, teams also need to evaluate the semantic quality of the LLM and agentic responses. Datadog provides built-in evaluations to detect hallucinations, PII leaks, prompt injections, and unsafe responses.</span></p>
<p><span style="vertical-align: baseline;">You can also add custom evaluators, including </span><a href="https://docs.datadoghq.com/llm_observability/evaluations/custom_llm_as_a_judge_evaluations/?tab=boolean" rel="noopener" target="_blank"><span style="text-decoration: underline; vertical-align: baseline;">LLM-as-a-judge evaluators</span></a><span style="vertical-align: baseline;">, for domain-specific checks. For instance, if a retrieval agent fetches irrelevant documents that lead to off-topic answers, a custom evaluator can flag that trace as having low retrieval relevance.</span></p>
<h3><strong style="vertical-align: baseline;">Iterate quickly and confidently with experiments</strong></h3>
<p><span style="vertical-align: baseline;">When you roll out a new system prompt, you might notice spikes in latency or drifts in output consistency. Datadog allows you to replay production LLM calls in its Playground to test different models, prompts, or parameters to find the configurations that move you closer to your ideal behavior.</span></p>
<p><span style="vertical-align: baseline;">From there, you can run </span><a href="https://www.datadoghq.com/blog/llm-experiments/" rel="noopener" target="_blank"><span style="text-decoration: underline; vertical-align: baseline;">structured experiments</span></a><span style="vertical-align: baseline;"> to compare versions side-by-side using datasets built from real traffic to optimize operational and functional performance. Because every agent step is logged through ADK instrumentation, you have the full context you need to reproduce regressions and validate fixes before you deploy.</span></p>
<h3><strong style="vertical-align: baseline;">Get started with Datadog LLM Observability</strong></h3>
<p><span style="vertical-align: baseline;">Datadog LLM Observability simplifies monitoring and debugging for Google ADK systems, helping users debug agent operations, evaluate responses, iterate quickly, and validate changes before deploying them to production. </span></p>
<p><span style="vertical-align: baseline;">You can get started today with the latest version of the LLM Observability SDK, or start a </span><a href="https://console.cloud.google.com/marketplace/product/datadog-public/datadog" rel="noopener" target="_blank"><span style="text-decoration: underline; vertical-align: baseline;">free trial</span></a><span style="vertical-align: baseline;"> if you are new to Datadog.</span></p>
<p><span style="vertical-align: baseline;">For more information on how to debug agent operations and evaluate responses, view Datadog’s </span><a href="https://docs.datadoghq.com/llm_observability/" rel="noopener" target="_blank"><span style="text-decoration: underline; vertical-align: baseline;">LLM Observability documentation</span></a><strong style="vertical-align: baseline;">.</strong></p></div>
