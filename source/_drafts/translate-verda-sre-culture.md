---
title: 【翻譯】 [團隊 & 專案] 介紹 Site Reliability Engineering 團隊在 Verda platform 中所扮演的角色
categories: 翻譯
tags:
---

<style>
  section.compact {
    font-size: 150%  
  }
  img[alt~="center"] {
    display: block;
    margin: 0 auto;
  }
</style>

> 翻譯文章來自 LINE Engineering Blog - [[Team & Project] Introducing the team in charge of Site Reliability Engineering for the Verda platform](https://engineering.linecorp.com/en/blog/team-project-introducing-the-team-in-charge-of-site-reliability-engineering-for-the-verda-platform/)

在團隊與專案裡，每個部門與專案在 LINE 裡面都被介紹的很詳細，包含他們的職責、結構、技能樹、future issues 以及 roadmaps。本篇我們將會邀請負責 LINE 私有雲 - Verda 的 Site Reliability Engineering (SRE) 團隊成員 - Park Youngwoon、Hideki Yamada 以及 Kang Moon Joong 來做介紹。

![](https://nijialin.com/images/2021/translate/sre/1.png)

<!-- more -->

## 首先，請各位自我介紹自己吧！

**Park**: 大家好，我是 Verda 的 Site Reliability Engineering(簡稱 VRE) 主管，團隊位於來自韓國與日本，主要任務就是執行在 Verd 上的 SRE 相關任務。

**Yamada**: Hi，我是 VRE 團隊的資深工程師，平時在團隊中長處理 low-layer 層級的部分，包括 Server 以及 OS 相關的故障排除。由於**雲端基礎架構**的開發和營運中使用到許多技術，因此日常工作也會涉及管理雲端資源以及評估實體資源採購相關的作業。

**Kang**: 我在 2019 年畢業之後加入了位於韓國的團隊。在加入公司之前，我曾在大學實驗室中負責過系統監控相關工作，現在我也利用我學到的經驗來開發和營運整個 Verda 的系統。

## 為什麼你們想加入 LINE 呢？

**Park**: 在上一份工作中，我在一家提供公有雲服務的公司中擔任 IaaS 的開發和營運主管。但是因為前公司的策略關係讓我覺得與用戶距離越來越遠，且我想繼續增加更多 IaaS 領域的開發經驗，因緣際會下我決定加入 Verda 團隊，並為為內部開發人員提供更多私有雲層級的服務。

**Yamada**: 在上一份工作中，我主要負責為公司行號(或集團)尋找與開發雲端服務的解決方案，在這份工作中我無法親身經歷整個雲端的交付與營運週期。因此我決定加入 Verda 團隊，除了與我自身的專業能力相符之外，團隊提供我有許多開發以及營運的空間，並且讓我能夠開發出與使用者息息相關的平台。

**Kang**: 在我大學時期，我的技能面向 cloud computing，我一直將 LINE 視為我在韓國裡最想加入的公司，特別是因為 VRE 團隊的許多工作與我的專業相吻合，因此在我實習生涯結束之後決定加入該團隊。如果有人問我說我在實習經歷印象最深的是什麼，我覺得需要主動發現和解決問題的能力，這也是我收到很多團隊成員對我的回饋，這些回饋也是我持續留在這裡的動力之一。

![](https://nijialin.com/images/2021/translate/sre/2.png)

## 在 LINE 工作中做過最有意義的部分是什麼呢？

**Park**: 我能夠在一個以**可靠性為重要目標的**工作環境工作，並讓我可以全心全意挑戰大型基礎架構，如此的環境是很難能可貴的。除了 IaaS 之外，Verda 還提供服務管理功能，例如 container-based 的 PaaS 和 DB。每種服務的 SRE 都需要專業且深入的知識和經驗，並透過豐富知識和經驗改善跨系統操作和制定標準化的系統。另一方面，除了環境很開放之外，並能嘗試許多不同挑戰，因此我覺得這份工作非常有意義。

**Yamada**: 我撰寫的程式碼以及開發的系統都會在許多人的工作上甚至是整個大型基礎架構的環境中產生影響，看到自己的付出能夠產生的巨大影響，我感到非常興奮。此外，因為是內部系統，因此很容易獲得詳細的回饋，自然也會促進更快的開發和改進，目前我還沒看過有基礎設施相關產品開發週即彼 Verda 還短的(笑)。

## Please tell us about the composition and roles of the team.

Park: 我們這個團隊分布在日本和韓國兩個地點，日本有 5 名，韓國有 3 名，總共有 8 名成員，至於團隊的職責，由於它很複雜，讓我透過以下圖片來解釋，當前 VRE 的工作大致分為以下三種類型：

![](https://nijialin.com/images/2021/translate/sre/3.png)

Customer Reliability Engineering 會在團隊成員之間輪換，但是在 IaaS 裡可靠性工程、監控和系統開發與部署的角色都會分配在每個團隊成員身上。就 IaaS 而言，有超過 60,000 個虛擬機和將近 20,000 個實體伺服器來服務中的 Baremetal、Hypervisor 和 Storage，由於其運行成本巨大，透過自動化與增加穩定性來降低成本是 VRE 工作中其中一項重要任務。此外，需要監控以及部署的資源也非常大，因此我們試圖透過統一的整合系統來降低開發人員管理和開發功能的成本。

VRE 主要在幫忙內部用戶和解決方案架構師處理相關問題，並積極地整合技術解決方案，以一個例子來說，為了減少一些常見的問題，我們開發一個可以直接發送特定訊息給開發者的功能，或者是建立一個系統來自動檢查連線是否正常，但像是"**我無法連接到虛擬機**"這類的問題就還有很多層面的問題需要去討論。

Yamada: 就我而言，上圖的角色劃分不太能切分清楚每個工作領域，一般來說大多數成員通常都跨多個領域工作。例如我改善了 Baremetal 的設定程式以及處理開發和執行資源監控事情。因此我認為在分配角色定位時需要考慮到每個成員的專業領域與面向，如此一來在分配角色才能更加明確。

Kang: 我平常負責 SRE 的儲存服務以及跨服務監控基礎結構的開發和營運。此外，我也很積極的參與處理 Customer Reliability Engineering(CRE) 相關問題，來改善服務效能以及處理服務故障通知。

## — Please tell us about the technology and development environment you use.

Park: The relationship between Verda users, Verda developers, and us can be summarized as follows.

![](https://nijialin.com/images/2021/translate/sre/4.png)

In this diagram, there are three areas that we are responsible for developing and operating: Operation Automation System, CI/CD, and Monitoring. Actually, it is more complicated than that, but since this is an interview article, I have kept it simple.

![](https://nijialin.com/images/2021/translate/sre/5.png)

I will start off by explaining CI/CD simply. We use Ansible extensively for server configuration management and service deployment. We have developed modules to improve readability and stability and implemented event-driven Ansible execution by introducing execution platforms, such as AWX, so we feel we are using Ansible quite extensively.

For deployments and history management, we are currently using Jenkins, but since we are doing many manual operations, we are trying to sort out new requirements and consider alternative methods.
For operations automation, we often use Python. We write simple scripts and develop intermediate services with interfaces to simplify complex operations and provide them to users and developers.
Requests from users are basically received via Slack, and we are working on improvements to provide a more user-friendly interface by using bots.

As for monitoring, we are using standard technologies such as Prometheus for metrics management and Elasticsearch + Kibana for log management. Especially for Prometheus, we are actively developing our own exporters to monitor more detailed status of service processes and middleware. We use Go and Python for development. For services with Web APIs, we use API specs based on OpenAPI (swagger) to get Prometheus-style metrics, which have been implemented in various services.

Incident information is aggregated via Alertmanager to an external incident management and notification service called PagerDuty. We are also developing an event-driven recovery flow, such as by executing an automatic recovery playbook and issuing webhooks to AWX from the same Alertmanager.

Yamada: We often use Bash and Python to implement tools to facilitate operations. Python in particular is easy to use and works well with OpenStack and Ansible, so I use it frequently. I also use Bash to implement scripts using the CLI of each service, so coding skills are required in one way or the other.

## Please tell us about your current team issues and what you are doing to solve them.

Park: In the IaaS domain, one of the major challenges is the high usage of Baremetal.
In our company, there are many use cases that emphasize the upper limit of performance and stability of computing power, and the migration to VMs has not progressed very well. VM and Baremetal differ in their management methods in many ways, and the operational costs associated with Baremetal are particularly high, so the high usage of Baremetal leads to high overall operational costs.

We are currently trying to encourage users to migrate from Baremetal to VMs through projects, such as developing VM types with strict resource isolation to handle use cases with strict performance requirements and reducing the usage cost per VM by scheduling VMs efficiently.

The monitoring and deployment areas are still in the early stages of development, so there are very few areas that are not being addressed. The final scope of work, such as improving the monitoring system across services and streamlining the deployment mechanism, is very large, so we are moving forward step by step, starting with those areas that are most likely to be effective.

As for SRE activities for individual services, there are many areas that cannot be covered by VRE because they require deep expertise in virtualization and networking. I am not sure how to proceed with these projects since they need to be balanced with my other duties.

I feel that we lack the manpower to proceed in a balanced manner, so we are focusing on recruitment.

![](https://nijialin.com/images/2021/translate/sre/6.png)
Yamada: We are working to improve some inefficiencies in operations that require cooperation with other departments. For example, when adding servers, it is necessary to collaborate with the data center and the department that manages the configuration management DB, but in the series of workflows, such as rack management, server installation, asset registration, registration to operation tools, BIOS setting, RAID setting, registration to automatic OS installer, registration to private cloud, and user management, each task is divided into different departments and there are gaps in the workflows. Although the individual tasks are mostly automated, the tasks are not well coordinated, and there is a limit to the efficiency improvement in this situation.
Currently, we are working on a VRE-led project to organize a series of workflows and linkages between tasks and automate all of them, with the aim of solving this problem.

In the context of automation, in addition to organizing workflows among teams, we also routinely carry out activities to standardize and automate operations that occur on a daily basis. However, if we reduce the time we spend on operations because of our improvement activities, it will slow down our operations, so one of our challenges is how to strike a balance between the two.

![](https://nijialin.com/images/2021/translate/sre/7.png)

Kang: As long as we are developing and operating cloud services, it is our job to deal with problems that occur on physical machines and networks. It is important for us to properly contact users with a good understanding of which type of cloud resources will be impacted and which users and LINE services will be affected by a particular incident. Therefore, one of the missions of VRE is to create a notification method that is easy for users to understand. Right now, we feel that the UX of the contact method is still underdeveloped, so we are working on a project mainly organized by the Korean members to improve it.
![](https://nijialin.com/images/2021/translate/sre/8.png)

## — What is your roadmap for the future?

Park: We are aiming to Verda-ize all of LINE’s infrastructure in the future. Therefore, we are placing a high priority on improving and developing Verda so that LINE developers can use it with confidence. Our short-term roadmap is as follows;

- Establishing processes to guarantee the visualization and reliability of systems in the SLO/SLA definition of the SaaS hosting services currently under development
- Infrastructure design to operational design for providing a standard infrastructure base for services with special requirements, such as Healthcare/Fintech
- Implementation of OCP (Open Computing Project) to reduce and optimize the management cost of physical servers
- Standard monitoring system development and process establishment
- Platformization of admin management tools
- Common development process (CI/CD)
- Creating a system to strengthen CRE/SA Activity.

Over the long term, I’d like to work on improving scalability. Our goal is to make it possible to manage LINE services and infrastructure with Verda, even if the scale increases by 10 or 100 times the current scale.

## Finally, do you have any messages for those who are interested in joining the Verda Reliability Engineering team?

Park: The mission of the Verda Reliability Engineering team is to ensure that LINE developers can use Verda reliably. LINE has a variety of services, and improving the reliability of the infrastructure used for those services will ultimately benefit countless users, so this is a very challenging mission. If you are attracted by the background and scale of the mission, and if you are fascinated by working in the role of SRE across various services and specialized areas, we would love to have you join us. Our team members are not just cloud professionals, but people with various backgrounds. If you are interested, please feel free to come and talk to us!

Yamada: If you are thinking, “I want to see infrastructure and write code!” this is the place for you. These days, the term infrastructure engineer often refers to someone who uses the cloud, but if you want to be someone who creates the cloud, please come to Verda.

![](https://nijialin.com/images/2021/translate/sre/9.png)
The Verda Reliability Engineering team is looking for new members.

- [Cloud Platform Site Reliability Engineering](https://careers.linecorp.com/ko/jobs/242) (Link in Korean)
- [ソフトウェアエンジニア / SRE / Private Cloud Platform ](https://linecorp.com/ja/career/position/1357)(Link in Japanese)
