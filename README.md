Presentation Script — Shannon vs OWASP Juice Shop
Slide 1 — Introduction
 
Hi everyone! Today, I'd like to share a tool I've been testing recently, called Shannon.
Shannon is an AI-powered penetration testing tool designed to automate security testing for web applications and APIs.
In this presentation, I'll explain how Shannon works, its main features, and how it uses AI agents to identify and exploit vulnerabilities.
I'll also share the results of a published assessment and my own experience testing the tool against OWASP Juice Shop.


Slide 2 — Shannon: AI-Powered Autonomous Pentesting
 
First, let me give you a quick overview of Shannon.
Shannon is an open-source tool developed by Keygraph.
It uses specialized AI agents to automate different penetration testing activities.
One interesting feature is that it combines source code analysis with dynamic testing.
This means Shannon can understand parts of the application logic and use that information to guide its security tests.
The main goal is to identify vulnerabilities and try to demonstrate their real impact.


Slide 3 — What Is Shannon?
 
So, what makes Shannon interesting?
Unlike traditional vulnerability scanners, Shannon doesn't rely only on predefined checks.
It uses AI agents to analyze the source code, understand the application, and plan security tests.
Another important concept is proof by exploitation.
Instead of just reporting a potential vulnerability, Shannon attempts to exploit it and collect technical evidence.
It also uses multiple specialized agents to work on different vulnerability categories.

Slide 4 — Main Differentiators
 
Here are the main differences compared to traditional security scanners.
First, Shannon uses source code analysis to better understand the application.
Second, AI agents can adapt their testing strategy based on what they discover.
Third, Shannon focuses on demonstrating real exploitation, not just identifying potential issues.
Another advantage is automation. It can handle several steps of the penetration testing process with limited human interaction.
Of course, this doesn't mean it can completely replace manual penetration testing.

Slide 5 — Architecture & Operation
 
Now, let's take a look at how Shannon works.
The process starts with access to the application's source code and a running instance of the application.
Shannon performs reconnaissance and code analysis to identify potential vulnerabilities.
After that, it organizes the findings and sends them to specialized exploitation agents.
These agents attempt to exploit the vulnerabilities against the running application.
The idea is to generate technical evidence before producing the final security report.
So, the workflow goes from code analysis to real-world exploitation.


Slide 6 — Multi-Agent Architecture
 
One of Shannon's main features is its multi-agent architecture.
Instead of using a single AI agent for everything, Shannon has specialized agents for different security tasks.
For example, there are agents focused on Injections, authentication, and authorization.
Some agents can run in parallel, which helps distribute the workload.
However, running multiple agents also increases the demand on the AI model.
And this was actually one of the challenges I experienced during my tests.

Slide 7 — Security Coverage
 Regarding security coverage, Shannon focuses on several common web application vulnerabilities.
These include Injection, Cross-Site Scripting, Server-Side Request Forgery, authentication issues, and broken access control.
One important point is that Shannon uses information from the source code to guide dynamic testing.
However, the coverage is not complete.
I see Shannon as a complementary tool that can work alongside solutions like Burp Suite, SAST, DAST, and manual penetration testing.

Slide 8 — Requirements and Integrations
 
Let's talk about the technical requirements.
Shannon can run in a Docker-based environment, using Node.js and its command-line interface.
For my tests, I used Kali Linux, Docker, and a local instance of OWASP Juice Shop.
The tool also needs access to an AI model.
I tested two different integrations: OpenAI Codex through Pi authentication, and Claude Code through OAuth.
These integrations used different Shannon setups, and each one had its own limitations.

Slide 9 — OWASP Juice Shop Assessment
 
For the testing environment, I selected OWASP Juice Shop.
Juice Shop is an intentionally vulnerable web application, widely used for security training and testing.
It contains different types of vulnerabilities, making it a good target for evaluating security tools.
Here, I'm showing a published security assessment from Keygraph, the company behind Shannon.
This is a reference report, not the result of my own execution.
It helps us understand the type of results Shannon is designed to produce.


Slide 10 — Vulnerabilities Identified
 
In the published assessment, Shannon reported 27 vulnerability records.
Eight were classified as critical, fourteen as high, and five as medium severity.
The findings cover different categories, including Injection, authentication, authorization, XSS, and SSRF.
An important detail is that some issues appear in more than one category, and not all exploitation attempts were successful.
So, these numbers represent records in the published report, not necessarily 27 unique vulnerabilities.
They are also not findings from my own PoC.


Slide 11 — Selected Security Findings
 
Here are four examples from the published security report.
The first is a SQL Injection in the login endpoint, which can allow an attacker to bypass authentication.
The second is another SQL Injection that can expose database information.
The third is an IDOR vulnerability that can allow access to another user's shopping basket.
And the fourth is an SSRF vulnerability related to loading profile images from external URLs.
These examples show different types of security impact, from unauthorized access to sensitive information exposure.


Slide 12 — Exploi Example
 
Now, I'd like to show a simple exploitation example.
This example is based on the SQL Injection described in the published report.
The attack targets the login endpoint and attempts to bypass authentication using a SQL Injection payload.
If the attack succeeds, the application returns an authentication token without a valid password.
This demonstrates the security impact, rather than just reporting a possible SQL Injection.
The request and response shown here are a simplified illustration of the published example, not evidence captured during my own PoC.


Slide 13 — Results and Reports
 
After the security assessment, Shannon can produce reports with technical information about the findings.
These reports can include the vulnerability description, affected endpoint, severity, security impact, and proof of concept.
They can also provide recommendations to fix the vulnerabilities.
Depending on the Shannon version, reports and integration outputs can be available in formats such as PDF, Markdown, and SARIF.
The image on the right illustrates how security findings can be organized. It is not a screenshot of the Shannon interface itself.


Slide 14 — My Practical Experience
 
Now, I'd like to share my own experience testing Shannon.
I set up the environment using Kali Linux, Docker, and OWASP Juice Shop.
My goal was to evaluate how much of the penetration testing process Shannon could automate.
I started with OpenAI Codex, using Pi authentication. The integration worked, and Shannon completed reconnaissance, but later the agents experienced execution failures.
Then I tested Claude Code through OAuth.
With Claude, I was able to complete the pre-reconnaissance and reconnaissance phases. Three specialized vulnerability analysis agents also completed their work.
At one point, Shannon had generated 36 candidates for the exploitation phase. These were potential vulnerabilities, not confirmed findings.
The main challenges were AI usage limits, repeated agent failures, and interruptions in the workflow.
So, the tool made real progress, but I wasn't able to complete a full security assessment or generate a final validated report.


Slide 15 — Execution Cost
 
Another important point is the execution cost.
Shannon is open source, so there is no software license fee for the open-source version.
However, running it is not necessarily free.
If you use an AI API, the cost depends on the model and the number of tokens consumed.
In one of my Claude tests, Shannon recorded approximately thirteen dollars in estimated AI usage during a partial execution.
This was an internal usage estimate, not an additional charge to my subscription.
I also tested subscription-based authentication, which has usage limits.
For me, the most important metric is not just the cost of a scan, but the cost of a successfully completed assessment.


Slide 16 — Final Evaluation
 
So, what is my final evaluation of Shannon?
I think Shannon is a promising tool, especially because it combines source code analysis, AI agents, and automated exploitation.
It also has potential to help security teams automate repetitive testing activities.
However, there are some important limitations.
In my tests, the biggest challenges were the usage limits of the AI models and the stability of the agents.
I couldn't complete a full end-to-end assessment, so I can't confirm its reliability for production use yet.
My recommendation is to continue testing Shannon in a controlled environment.
I see it as a complementary tool to support penetration testers, not as a replacement for manual security testing.


Slide 17 — References and Closing
 
Finally, here are some useful references.
You can find the Shannon source code on GitHub, along with documentation, configuration examples, and published assessment reports.
I've also included the OWASP Juice Shop repository, in case you want to try the tool in your own environment.
That's everything I wanted to share today.
I hope this overview was useful, especially for understanding both the potential and the current limitations of AI-powered penetration testing.
Thank you for your time!
I'm happy to answer any questions.

Dicas para apresentar com mais naturalidade
O roteiro foi escrito com frases que você consegue falar sem precisar memorizar palavra por palavra. Para dar uma sensação de conversa, use pequenas pausas após as frases principais e dê ênfase a expressões como "One important point", "In my tests" e "My recommendation".
Algumas frases de transição que você pode usar naturalmente entre os slides:
Situação
Frase em inglês
Passar ao próximo assunto
"Let's move on to the next slide."
Explicar um ponto importante
"One important thing to mention here is..."
Dar um exemplo
"Let me give you a quick example."
Falar sobre seu laboratório
"Based on my own experience..."
Ressaltar uma limitação
"However, there is one limitation to consider."
Concluir um assunto
"So, that's the main takeaway from this slide."


