---
colorSchema: light
favicon: /public/images/diracx-logo-square.png
color: orange-light
layout: cover
routerMode: hash
title: DIRAC+X+Rucio
theme: neversink
neversink_string: "8th Rucio Community Workshop"
---

# On DIRAC, DiracX, & Rucio

**Federico Stagni** <Email v="federico.stagni@cern.ch" />

4 November 2025
\_\_ <a href="https://indico.cern.ch/event/1545309" class="ns-c-iconlink"><mdi-open-in-new />8th Rucio Community Workshop</a>


---
layout: top-title
color: gray-light
align: c
title: DIRAC
---

:: title ::

# What is DIRAC, actually?

:: content ::

- An "interware" (a tool for doing distributed computing)
- Started by LHCb, today is used by few dozens communities
- It can be used for managing jobs (via pilots), data, productions, dataset transfers, etc
- The recently refurbished [diracgrid.org](https://diracgrid.org/) explains everything and has many links for your info

In general, DIRAC has a pretty active community of users and developers.
- Apart from the regular zoom meetings, we meet for hackathons 3 times per year, plus once in a workshop. Next will be [14-16 Oct 2025 in Prague](https://indico.cern.ch/event/1588323/).
- For the latest presentations, check [our latest WS](https://indico.cern.ch/event/1433941/)

---
layout: top-title-two-cols
color: gray-light
align: c-lm-lm
title: numbers
---

:: title ::

# Few DIRAC numbers

:: left ::

(from A. Tsaregorodtsev)

![alt text](/public/images/Andrei_communities.png)

:: right :: 

![alt text](/public/images/LHCb_WMS_peak.png)

(LHCb, peak usage in the last year)


---
layout: top-title
color: gray-light
align: c
title: why
---

:: title ::

# Why this talk

:: content ::

- DIRAC is, like Rucio, a project serving several communities in their struggles to exploit distributed computing resources
- Few communities (Belle2 and CTAO, also few IUUC in GridPP) have been using, or will soon use, DIRAC and Rucio together, with (*en-gros*):
  - DIRAC as WMS (so, not using DIRAC's DMS)
  - Rucio as DMS
- There are also exploratory works on using parts of DIRAC that are not the WMS 


---
layout: top-title
color: gray-light
align: c
title: encounters
---

:: title ::

# Previous encounters

:: content ::

- Rucio was presented in the [8th DIRAC's workshop](https://indico.cern.ch/event/676817/contributions/2975871/)
- a DIRAC-Rucio setup was first mentioned in the [2nd Rucio WS](https://indico.cern.ch/event/773489/contributions/3316669/attachments/1803652/2942717/laycock_Rucio.pdf) and in the [9th DIRAC WS](https://indico.cern.ch/event/756635/contributions/3384793/attachments/1844896/3026476/BelleIIRucio.pdf)
- in 2023 we organized a [DIRAC & Rucio WS at KEK](https://indico.cern.ch/event/1252369/)
- at the beginning of this year a [Dirac & Rucio mini-workshop and hackathon](https://indico.cern.ch/event/1443765/)

We also have a dedicated [mattermost channel](https://mattermost.web.cern.ch/diracx/channels/rucio---dirac)


---
layout: top-title
color: gray-light
align: c
title: integration
---

:: title ::

# How DIRAC and Rucio work together

:: content ::

The entry point is the DIRAC's `RucioFileCatalog`, which is an implementation of the `FileCatalog` "abstract" class (DIRAC has few different implementation of the same class)
- in DIRAC since 2021
- by now it supports *Multi VO* and *Rucio metadata*

Once the data is in the Rucio catalog:
- All the replication policies, 3rd party copy are handled by Rucio subscriptions and rules
- The synchronization between DIRAC and Rucio is done via DIRAC
agents

This also means that:
- Admins still updates the DIRAC configuration
- No change for the download/upload from jobs: still done via the DIRAC's `DataManager`

---
layout: top-title
color: gray-light
align: c
title: namespace
---

:: title ::

# How DIRAC and Rucio work together -- namespace

:: content ::

- By default, Rucio has a flat namespace that contains files
  - Files that can be aggregated to datasets
  - Then datasets can be aggregated to container
- DIRAC uses a hierarchical namespace

The `RucioFileCatalog` "translates" from DIRAC to Rucio's namespace. All details in [this vCHEP presentation](https://indico.cern.ch/event/948465/contributions/4323983/attachments/2247115/3811355/The%20Rucio%20File%20Catalog%20in%20Dirac%20implemented%20for%20Belle%20II-2.pdf)


---
layout: section
color: lime-light
---

<div style="display: flex; align-items: center; justify-content: center;">
    <img id="DIRAC" src="/public/images/DIRAC-logo-extended.png" alt="DIRAC logo" style="width: 300px;">
    <span style="margin: 0 50px;">--></span>
    <img id="DiracX" src="https://raw.githubusercontent.com/DIRACGrid/management/master/branding/diracx/svg/diracx-logo-full.svg" alt="DiracX" style="width: 300px;">
</div>


---
layout: side-title
side: left
color: gray-light
titlewidth: is-5
align: rm-lm
title: DiracX
---

:: title ::

# What is DiracX?

:: content ::

- A cloud native app
- Multi-VO from the get-go
- Standards-based

<AdmonitionType type='important' >
Still DIRAC, in terms of functionalities.
</AdmonitionType>


-

---
layout: top-title-two-cols
color: gray-light
align: c-lt-lm
title: summary
---

:: title ::

# Extreme summary of what happened in the last few years

:: left ::

```mermaid {scale:0.4}
%%{init: { 'logLevel': 'debug', 'theme': 'base', 'timeline': {'disableMulticolor': true}}}%%
    timeline
        section DIRAC only (DIRAC v8)
            Q2 2022 : DIRAC v8.0
            Q3 2023 : First DiracX demo (during)
            Q2 2025 : LHCb deploys in production alpha versions of DIRAC (v9.0.0aX) and DiracX (v0.0.1aX)
                    : All existing DiracX components are tested and extended.
                    : Several scalability and performance issues were addressed
        section DIRAC and DiracX coexisting (forcefully)
            Q4 2025 : Release of DIRAC v9.0 and DiracX 0.0.1
                    : JobStateUpdate service migrated and tested
                    : Possible adoption by non-LHCb DIRAC users
```

:: right ::

(a somewhat personal take)

- We kept doing 2-days hackathons every quarter
  - if not during workshops, at CERN, and with good participation
- DIRAC v8 kept receiving updates, but most of them were "for DiracX"
- In April 2025 LHCb moved the production setup to DIRAC v9 and DiracX 0.0.1 alpha versions
- We kept postponing "real" releases for excellent technical reasons, until last week, when we tagged the first non-alpha versions of v9 and DiracX

---
layout: top-title-two-cols
color: gray-light
align: c-lm-lm
title: DiracX v0.0.1
columns: is-8
---

:: title ::

# Getting to **DiracX 0.0.1**

:: left ::

## This first release contains

- All service/client underpinnings
- Extension support
- Jobs sandboxes can be stored in an object store (and you should do it)
- The DIRAC `WorkloadManagement/JobStateUpdateHandler` service can be replaced by an "equivalent" DiracX service
- The helm chart is considered "stable enough"
- Documentation "sufficiently complete"

We will keep working, within the patches of this first version, on adding new services and documentation.

:: right ::

## DiracX brings a new "mindset"

- a cloud-native app
- from "in-house" to "standing-on-the-shoulders"

---
layout: top-title-two-cols
color: gray-light
align: c-lm-lm
title: Timeline
columns: is-8
---

:: title ::

# Timeline of the next year

:: left ::

```mermaid {scale:0.5}
%%{init: { 'logLevel': 'debug', 'theme': 'base', 'timeline': {'disableMulticolor': true}}}%%
    timeline
        section DIRAC and DiracX coexisting (forcefully)
            Last week (Sept 2025) : Release of DIRAC v9.0 and DiracX 0.0.1
                                  : JobStateUpdate service migrated and tested
                                  : Possible adoption by non-LHCb DIRAC users
            This or next week : Release DiracX 0.0.2
                              : Pilot and JobMonitoring services migrated to DiracX (being tested) -- DiracX-Web first practical usage (Jobs Monitoring)
            Q1 2026 : Release DiracX 0.1.0
                    : DiracX introduces a task management system
            Q3 2026 : Release DIRAC v9.1 and 0.1.X (or 0.2.0)
                    : First DiracX-only service.
                    : Adoption of new Pilot security mechanism
                    : First DiracX replacements for DIRAC agents or executors using DiracX tasks
```

:: right ::

- There are developments done by stagiare that could not be included in DiracX's first release
- DiracX 0.1.0 will bring "tasks", for replacing DIRAC's _agents_, _executors_, and the RMS machinery (the _RequestExecutingAgent_)
- We will need a DIRAC v9.1 because there will be database changes (some PRs already in _draft_)
- Standalone DiracX will take at least 2 years from now

---
layout: top-title
color: gray-light
align: c
title: Users-WhatsNew
---

:: title ::

# What's new

:: content ::

DiracX brings updates for

- Users
- Administrators
- Developers

As of now:

- we are more concerned about solving **administrator**'s issues.
- **Developers** "need to know" already if you have an DIRAC (or WebAppDIRAC) extension.
- **Users** "do not yet need to know".

Here, I only briefly talk about users.

---
layout: section
color: cyan
title: toV9-users
---

# From DIRAC v8 to v9+0.0.1 : **Users**

---
layout: top-title
color: gray-light
align: c
title: Users-WhatsNew
---

:: title ::

# What's new for users

:: content ::

<ul class="text-sm">
  <li><strong>Logging-in</strong> requires that you are previously registered in an IdP implementing OpenID Connect protocol
    <ul>
      <li>essentially this is the VOMS-&gt;IaM migration. Admins should have done this already, transparently, for all the users of a VO</li>
      <li>if a VO is not migrated to IaM, it can't be "enabled" (see later on)</li>
    </ul>
  </li>
  <li>New <strong>Web app</strong> (which, for DiracX 0.1 will not be of much use)</li>
  <li>Enriched and modern <strong>CLI</strong> (but not many functionalities in there)</li>
  <li><strong>REST</strong> interface for programmatic usage (for advanced users -- but again, not much user-facing info to use)</li>
</ul>

<p>But effectively, for now <strong>users can largely be agnostic</strong> of DiracX, as for the first version users' interactions will still be done via the DIRAC tools they know (and love?).</p>

<p>Also, users should be setting the correct environment variables (<code>DIRACX_URL</code> mostly)</p>

<ul class="text-sm">
  <li>admins should be setting it already for the users</li>
</ul>

---
layout: iframe-right
title: Web API
url: <https://diracx-cert.app.cern.ch/api/docs>
class: webAPI
slide_info: false
color: gray-light
align: lm
---

# DiracX Web API

<AdmonitionType type='caution' >
What is on the right is the certification Web API (VOs: `dteam` and `gridpp`), loaded live. Use with caution!
</AdmonitionType>

DIRAC Web APIs with <devicon-fastapi-wordmark class="text-7xl align-middle inline-block mx-0"></devicon-fastapi-wordmark>

<ul class="text-sm">
  <li>
    Nicely documented by
    <devicon-swagger-wordmark class="text-7xl align-middle inline-block mx-0"></devicon-swagger-wordmark>
    <ul class="text-xs ml-4">
      <li class="text-xs">--> this is what you see on the right</li>
    </ul>
  </li>
  <li>
    Follows the <devicon-plain-openapi-wordmark class="text-7xl align-middle inline-block mx-1"></devicon-plain-openapi-wordmark> specification, with the (python) client generated by <a href="https://github.com/Azure/autorest/blob/main/docs/introduction.md">AutoREST</a>.
  </li>
</ul>

<!--
- there is also redoc
- AutoREST supports several langagues, not only python
-->

---
layout: top-title
color: gray-light
align: c
title: DiracX-Web
---

:: title ::

# DiracX web

:: content ::

We are also rewriting [the Web App](https://github.com/DIRACGrid/diracx-web) from scratch.

Software stack:

- NextJS <devicon-nextjs-wordmark class="text-4xl align-middle inline-block mx-2" />
- Material UI <devicon-materialui class="text-3xl align-middle inline-block mx-2" />
- TypeScript <devicon-typescript class="text-3xl align-middle inline-block mx-2" />

---
layout: top-title
color: gray-light
align: c
title: DiracX and Rucio
---

:: title ::

# DiracX and Rucio

:: content ::




---
layout: top-title-two-cols
color: gray-light
align: cm-lm-lm
title: tokens
---

:: title ::

# Few tokens considerations

:: left ::

![](/public/images/Cedric_Rucio_tokens_fromDUW.png)

:: right ::

- DiracX is 




---
layout: top-title-two-cols
align: cm-cm-lm
color: orange-light
columns: is-4
title: summary
--- 
:: title ::

# Summary

:: left :: 

<img id="DiracX" src="https://raw.githubusercontent.com/DIRACGrid/management/master/branding/diracx/svg/diracx-logo-square.svg" class="mx-auto w-4/5"> </img>

:: right ::

<ul class="text-base">
  <li>DiracX is "the neXt Dirac incarnation", ensuring the future of the widely used Dirac
    <ul class="text-sm">
      <li>We are rewriting the code, but it is still Dirac that you love!</li>
    </ul>
  </li>
  <li>DiracX will ease the interoperability with Rucio and/or dask and/or any other tool out there
    <ul class="text-sm">
      <li>DiracX will still have the Data Management part, but its Workload Management functionalities will come first</li>
    </ul>
  </li>
  <li>The first DiracX release is here
    <ul class="text-sm">
      <li>It will live together with DIRAC v9 for a while, until it will replace it completely</li>
    </ul>
  </li>
</ul>


---
layout: credits
color: navy
loop: true
speed: 1.0
title: credits/people
---

<div class="grid text-size-4 grid-cols-3 w-3/4 gap-y-10 auto-rows-min ml-auto mr-auto">
    <div class="grid-item text-center mr-0- col-span-3">
        <strong>People</strong><br>
    </div>
    <div class="grid-item text-right mr-4 col-span-1">
        <strong>Current Developers, maintainers, supporters</strong>
    </div>
    <div class="grid-item col-span-2">
        Chris Burr <i>CERN, LHCb</i><br/>
        Christophe Haen <i>CERN, LHCb</i><br/>
        Alexandre Boyer <i>CERN, LHCb</i><br/>
        Natthan Piggoux <i>LUPM (FR), CTA</i><br/>
        Cedric Serfon <i>Brookhaven National Laboratory (US), Belle2</i><br/>
        Ryunosuke O'Neil <i>CERN, LHCb</i><br/>
        Daniela Bauer <i>Imperial college (UK), GridPP</i><br/>
        Simon Fayer <i>Imperial college (UK), GridPP</i><br/>
        Janusz Martyniak <i>Imperial college (UK), GridPP</i><br/>
        Xiaomei Zhang <i>Beijing, Inst. High Energy Phys. (CN), Juno</i><br/>
        Luisa Arrabito <i>LUPM (FR), CTA</i><br/>
        André Sailer <i>CERN</i><br/>
        Jorge Lisa Laborda <i>Univ. of Valencia and CSIC (ES), LHCb</i><br/>
        Bertrand Rigaud <i>IN2P3 (FR)</i>
    </div>
    <div class="grid-item text-right mr-4 col-span-1">
        <strong>Project lead</strong>
    </div>
    <div class="grid-item col-span-2">
        Federico Stagni <i>CERN, LHCb</i><br/>
        Andrei Tsaregorotsev <i>CPPM (FR), EGI and LHCb</i>
    </div>
</div>

&nbsp;
&nbsp;
&nbsp;

<div class="grid-item col-span-3 text-center mt-180px mb-auto font-size-1.5rem">
    <strong>Questions?</strong>
</div>

---
layout: section
color: cyan-light
title: Backup
---

# Backup


---
layout: side-title
align: lm-lm
color: gray-light
title: WMS
titlewidth: is-3
---

:: title ::

## Workload Management System
- Pull model based on Pilot jobs
- Also "Push" solution for HPCs that do not support pilots (because of limited internet access).
- Will integrate [CWL (Common Workflow Language)](https://www.commonwl.org) as a way of defining jobs (replacing JDL) --> see poster #217

:: content ::

```mermaid
%%{init: { 'theme': 'default' }}%%
flowchart LR;
Jobs["`Users see only **Jobs**`"]
A@{ shape: sl-rect, label: "APIs" }
WMS[("`**Workload
Management
System**`")]
style WMS fill:#bbf
HPC["`High
Perfomance
Computers`"]
style HPC fill:#A145
clusters["`Computer clusters`"]
style clusters fill:#A145
Grid_Nodes["Grid"]
Pilots["`**Pilots**
administer computing slots, and match (pull) jobs`"]

style HTCondorCE fill:#F23A
style ARC-AREX fill:#F23A
style libcloud fill:#F23A
style SSH fill:#F23A
style Grid_Nodes fill:#A145
style Iaas:Clouds fill:#A145
style HTCondor fill:#F26
style SLURM fill:#F26
style Jobs fill:#FFF
style Pilots fill:#FFF

A-->|jobs|WMS

WMS-->|pilots|libcloud
WMS-->|pilots|HTCondorCE
WMS-->|pilots|ARC-AREX
WMS-. jobs .->HPC
WMS-->|pilots|SSH

libcloud-->|VMs starting pilots|Iaas:Clouds
HTCondorCE-->Grid_Nodes
ARC-AREX-->Grid_Nodes
ARC-AREX-->HPC
SSH-->|pilots|SLURM
SSH-->|pilots|HTCondor
SSH-->|pilots|clusters
SLURM-->HPC
SLURM-->clusters
HTCondor-->clusters
```

---
layout: side-title
align: lm-lm
color: gray-light
title: DMS
titlewidth: is-5
---

:: title ::

## Data Management System
It’s about **files**:​ placing, replicating, removing files​

- there are **LFNs** (logical file names)
- **LFNs** are registered in *catalog(s)​*
    - where are the LFNs? (in the DIRAC File Catalog (DFC), or in Rucio)​
    - where are their metadata? (in the DFC, or in the LHCb Bookkeeping, or in AMGA)​
- LFNs *may* have **PFNs** (physical file names), stored in **SEs** (Storage Elements), that can be accessed with several protocols.​

:: content ::

```mermaid
%%{init: { 'theme': 'default' }}%%
flowchart LR;
A@{ shape: sl-rect, label: "APIs" }
DMS[("`**Data
Management
System**`")]
style DMS fill:#bbf
FC[["`**Catalog**`"]]
style FC fill:#bbf
StorageBase[["`**Storage Base**`"]]
style StorageBase fill:#bbf
DFC[("`DIRAC
Files
Catalog`")]
Rucio[("Rucio")]
style Rucio fill:#6001
TS[("`DIRAC
Transformation
System`")]
WebDav@{ shape: lin-cyl, label: "WebDav (http)" }
XRootD@{ shape: lin-cyl, label: "XRootD" }

style WebDav fill:#F23A
style XRootD fill:#F23A

A-->DMS
DMS-->FC
DMS-->StorageBase
FC-->DFC
FC-->Rucio
FC-->TS
StorageBase-->WebDav
StorageBase-->XRootD
```

<!-- 
A catalog is effectively an interface, that needs implementation. Such implementation can be the DIRAC Files Catalog, or Rucio, or any other, including extension specific ones
-->


---
layout: side-title
color: gray-light
align: lm-lm  
title: TS
---

:: title ::

## Transformation System
### For productions and Dataset management

- A *Data Processing* **transformation** (e.g. Simulation, Merge, DataReconstruction...) creates jobs in the WMS (and re-submits them if needed, eventually destroys them).​

- A *Data Manipulation* **transformation** replicates, or removes, data from storage elements.

:: content ::

<span class="bg-cyan-100 text-cyan-600 p-4 border-l-6 border-2 border-cyan-400 rounded-lg pl-8 pr-8 w-full block">
The Transformation System is used to automate common tasks related to production activities. It can handle thousands of productions, millions of files and jobs.
</span>

&nbsp;
&nbsp;

```mermaid
%%{init: { 'theme': 'default' }}%%
flowchart LR;
TS[("`**Transformation
System**`")]
style TS fill:#bbf
WMS[("`**Workload
Management
System**`")]
style WMS fill:#bba
RMS[("`**Request
Management
System**`")]
style RMS fill:#bba
DMS[("`**Data
Management
System**`")]
style DMS fill:#bba
PM@{ shape: sl-rect, label: "Productions Management" }
DM@{ shape: sl-rect, label: "DataSets Management" }

PM-->|Productions Definitions|TS
DM-->|DataSets Operations|TS
TS-->|Jobs|WMS
TS-->|Data Operations|RMS
RMS-->DMS
```

