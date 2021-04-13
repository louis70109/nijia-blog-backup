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

## — 請告訴我們使用到的技術以及開發環境

Park: 這個問題關係到 Verda 用戶、開發人員，那與我們的關係可以參考下圖：

![](https://nijialin.com/images/2021/translate/sre/4.png)

在此圖中，我們負責的三個領域：營運自動化系統、CI/CD、監控。在日常生活中這部分會再複雜許多，我盡可能的簡化讓讀者們容易閱讀這篇採訪文章。

![](https://nijialin.com/images/2021/translate/sre/5.png)

我將簡單地從 CI/CD 開始解釋。我們很廣泛的使用 Ansible，像是我們將 Ansible 廣泛的用於 Server 的管理 Configuration 和部署，同時我們也著手開發一些模組來提高可讀性和穩定性，並透過引入類似 AWX 的執行平台來實現 event-driven Ansible execution。

對於部署和歷史記錄管理，我們當前使用的是 Jenkins，但由於我們有許多部分都是手動執行，因此我們試圖梳理新的需求並考慮替代方案。

對於自動化，我們大部分使用 Python，我們撰寫輕量的 scripts 並使用在服務之間以簡化過多的手動操作，最後我們會將這些 scripts 提供給用戶和開發人員。

基本上，用戶的需求是透過 Slack 發送過來，但如此以來訊息會非常多，因此我們正在努力透過 Bot 提供更好的介面給用戶。

關於監控，我們使用常見的技術，像是使用 Prometheus 進行 metrics 管理，Elasticsearch + Kibana 進行 log 管理。特別是 Prometheus，我們正積極開發自己的 exporters，提供監控服務流程以及套件的詳細狀態。

對於有 Web API 需求的服務，我們使用 Go 和 Python 進行開發 API 並使用基於 OpenAPI(Swagger) 的規範來獲取 Prometheus 的 metrics，目前這個 metrics 已在各種服務中。

事件訊息透過 Alertmanager 匯整到稱為 PagerDuty 的外部事件管理和通知服務。當前我們還正在開發 event-driven recovery 流程，像是透過執行自動 recovery 的 playbook 並從同樣的 Alertmanager 向 AWX 發出 Webhooks。

Yamada: 我們經常使用 Bash 和 Python 來開發操作的工具，特別是 Python 它易於使用，並且可以與 OpenStack 和 Ansible 有很高的整合。此外我還使用 Bash 建立 Scripts 處理通過每個服務的 CLI，在開發上會因不同的環境而使用對的語言去撰寫。

## 請告訴我們目前 VRE 團隊面臨的挑戰以及將如何應對這些挑戰


Park: 在 IaaS 領域裡，主要挑戰之一是實體機的高使用率。而在我們公司中，有許多案例是注重計算能力的性能和穩定性的上限，而實體機相關的營運成本本身就比較高，與此同時 VM 和實體機在很多方面都有不同的管理方式，因此實體機的高使用率就會導致增加整體營運成本。為了應對**性能要求較嚴格的案例**以及處理資源分離且獨立的虛擬機類型，透過有效地調度虛擬機推動用戶從實體機遷移到虛擬機，從而降低每個專案的成本。


整體而言，監視和部署領域仍處於起步階段，因此很難找到沒有問題的地方。由於改善服務監控系統和分配結構的效率等進展範圍非常廣泛，因此我們從似乎有效的領域處於逐步發展的狀態。

每個服務的SRE工作都需要深入的專業知識，例如虛擬化和網絡，因此VRE團隊無法覆蓋許多領域。我必須做其他工作，所以我正在考慮如何進行。總的來說，我覺得沒有足夠的員工來平衡地處理工作，因此我目前正在招聘。

此外，監控和部署部分仍處於早期開發的階段，隨著團隊越來越成熟，將會持續往改善跨服務的監控系統和簡化部署機制前進，與此同時，我們將從最有效率的部分開始逐步著手進行。

至於針對處理單個 SRE 職責，VRE 可能無法完全處理，因為它們需要更多關於虛擬化和網絡方面的深厚知識。有些項目我不確定該如何進行，因此我們也需要從中找到與其他職責間的平衡。

因為我們缺乏人力來讓工作上的職責更加平衡，因此我們也需要優秀的高手加入我們。

![](https://nijialin.com/images/2021/translate/sre/6.png)
Yamada: 我們正在努力改善需要與其他部門合作的營運效率下降問題。例如：增加 Server 時，必須與數據中心和管理資料庫設定的部門合作，但是在一個工作流程，從機房管理、Server 安裝、資產註冊、操作工具申請、BIOS 設定、RAID 設定、自動化系統安裝、私有雲的申請以及用戶管理，因為每個工作都有不同的部門負責，在申請的流程中有許多的等待的時間，儘管很多任務是自動化，但是在任務之間的連結不好的情況下，提升效率是有限制的。

當前我們正在展開一個由 VRE 團隊負責的專案，主要處理工作流程相關問題並使任務與自動化之間有所連結，以實現自動化來解決上述問題。

We are working to improve some inefficiencies in operations that require cooperation with other departments. For example, when adding servers, it is necessary to collaborate with the data center and the department that manages the configuration management DB,
but in the series of workflows, such as rack management, server installation, asset registration, registration to operation tools, BIOS setting, RAID setting, registration to automatic OS installer, registration to private cloud, and user management, each task is divided into different departments and there are gaps in the workflows. Although the individual tasks are mostly automated, the tasks are not well coordinated, and there is a limit to the efficiency improvement in this situation.
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
