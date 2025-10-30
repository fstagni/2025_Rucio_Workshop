---
colorSchema: light
favicon: /public/images/diracx-logo-square.png
color: orange-light
layout: cover
routerMode: hash
title: DIRAC+X status
theme: neversink
neversink_string: "8th Rucio Community Workshop"
---

# DIRAC+X status

**Federico Stagni** <Email v="federico.stagni@cern.ch" />

4 November 2025
\_\_ <a href="https://indico.cern.ch/e/duw11" class="ns-c-iconlink"><mdi-open-in-new />8th Rucio Community Workshop</a>

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

layout: top-title-two-cols
color: gray-light
align: c-lt-lm
title: summary

---

:: title ::

# Extreme summary of what happened since the last workshop

:: left ::

```mermaid {scale:0.4}
%%{init: { 'logLevel': 'debug', 'theme': 'base', 'timeline': {'disableMulticolor': true}}}%%
    timeline
        section DIRAC only (DIRAC v8)
            Q2 2022 : DIRAC v8.0
            Q3 2023 : First DiracX demo
            Q2 2025 : LHCb deploys in production alpha versions of DIRAC (v9.0.0aX) and DiracX (v0.0.1aX)
                    : All existing DiracX components are tested and extended.
                    : Several scalability and performance issues were addressed
        section DIRAC and DiracX coexisting (forcefully)
            Last week (Sept 2025) : Release of DIRAC v9.0 and DiracX 0.0.1
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

---

layout: top-title-two-cols
color: gray-light
align: c-lm-lm
title: Timeline-long

---

:: title ::

# Standalone DiracX will take at least 2 years from now

:: left ::

```mermaid {scale:0.5}
%%{init: { 'logLevel': 'debug', 'theme': 'base', 'timeline': {'disableMulticolor': true}}}%%
    timeline
        section DIRAC and DiracX coexisting (forcefully)
            Q4 2026 : DIRAC v8 EOL (by the next workshop)
        section Possible standalone DiracX
            Q4 2027 : DiracX v1.0
```

<SpeechBubble position="l" color='amber' shape="round"  v-drag="[330,125,160,180]">
NB: **very** indicative guess, maybe not for everyone (e.g. not for LHCb).
</SpeechBubble>

:: right ::

## **notes**

- Dear friends administrator of DIRAC's installations, you have one year to migrate to DiracX
- There's a lot of guesswork in understanding how things will be in one year time, and even more in what will happen after
- This community **needs** to work together as much as possible

---

layout: top-title
color: gray-light
align: c
title: roadmap

---

:: title ::

# The long road to DiracX v1

:: content ::

After **DiracX 0.1.0** (the one bringing _tasks_ to DiracX, coming **Q1 2026**) there are many areas that will be "free to proceed" ([roadmap](https://diracx.diracgrid.org/en/latest/roadmap/)), in parallel:

<ul class="text-sm">
  <li>WMS
    <ul>
      <li>Pilots machinery (in DIRAC terms: SiteDirectors, Matcher)
        <ul>
          <li>this needs to include "Computing Resources"</li>
        </ul>
      </li>
      <li>Jobs description (adoption of CWL)</li>
    </ul>
  </li>
  <li>DMS (effectively needed for WMS to work)
    <ul>
      <li>this needs to include "Storage Resources" and "Catalog Resources"
        <ul>
          <li>DiracX to Rucio bridge</li>
        </ul>
      </li>
    </ul>
  </li>
  <li>RSS (effectively needed for WMS to work)</li>
  <li>RMS</li>
  <li>TS (also CWL)
    <ul>
      <li>DIRAC also provides a generic Production System</li>
    </ul>
  </li>
  <li>Accounting and Monitoring</li>
</ul>

<ul class="text-sm">
  <li>Caveats:
    <ul>
      <li>moving a DIRAC service to a DiracX one</li>
    </ul>
  </li>
</ul>

<SpeechBubble position="l" color='amber' shape="round"  v-drag="[680,185,160,180]">
We need your help on pretty much all these topics
</SpeechBubble>

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

layout: top-title
color: gray-light
align: c
title: CLI

---

:: title ::

# CLI Interactions

:: content ::

1. Logging in (using the `diracx cli`):

```bash
❯ dirac login gridpp
Logging in with scopes: ['vo:gridpp']
Now go to: https://diracx-cert.app.cern.ch/api/auth/device?user_code=XYZXYZXYZ
...Saved credentials to /home/fstagni/.cache/diracx/credentials.json
Login successful!
```

2. Submitting a job (using Python `requests`):

```python
import requests

requests.post('https://diracx-cert.app.cern.ch/api/jobs/', headers={'accept': 'application/json', 'Authorization': 'Bearer eyJhbG...', 'Content-Type': 'application/json'}, json=jdl)
```

3. Getting its status (using `curl`):

````md magic-move
```bash
curl -X 'GET' \
  'https://diracx-cert.app.cern.ch/api/jobs/status?job_ids=8971' \
  -H 'accept: application/json' \
  -H 'Authorization: Bearer eyJhbG...'  | jq
```

```json
{
  "8971": {
    "Status": "Done",
    "MinorStatus": "Execution Complete",
    "ApplicationStatus": "Unknown"
  }
}
```
````

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

layout: iframe-left
title: WebApp
url: <https://diracx-cert.app.cern.ch>
class: webapp
slide_info: false
color: gray-light
align: lm

---

# DiracX web

We are also rewriting [the Web App](https://github.com/DIRACGrid/diracx-web) from scratch.

Software stack:

- NextJS <devicon-nextjs-wordmark class="text-4xl align-middle inline-block mx-2" />
- Material UI <devicon-materialui class="text-3xl align-middle inline-block mx-2" />
- TypeScript <devicon-typescript class="text-3xl align-middle inline-block mx-2" />

<AdmonitionType type='caution' >
What is on the left is the certification WebApp, loaded live. Use with caution!
</AdmonitionType>

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
  <li>DiracX, "the neXt Dirac incarnation", is here!
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
