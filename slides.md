---
colorSchema: light
favicon: /public/images/LHCb.png
color: orange-light
layout: cover
routerMode: hash
title: LHCb
theme: neversink
neversink_string: "Heterogeneous Architectures in WLCG" 
---

# <img id="DiracX" src="/public/images/LHCb.png" class="mx-auto w-1/5"> </img>

**Federico Stagni** <Email v="federico.stagni@cern.ch" />

3 December 2025
\_\_ <a href="https://indico.cern.ch/event/1526077" class="ns-c-iconlink"><mdi-open-in-new />Heterogeneous Architectures in WLCG</a>


---
layout: top-title
color: gray-light
align: c
title: Heterogeneity
---

:: title ::

# "Heterogeneity"

:: content ::

WLCG has been (and largely still is) about connecting "sites" with vastly homogeneous architectures: right now x86_64 (amd64) CPUs, but "in the beginning" we still had i386.
Experiments like LHCb created a collection of highly specialized software for such architectures.

Nowadays:
- LHCb, "like everyone", is looking for SW speedups. Some specialized, "heterogeneous" hardware is being explored.
- At the same time, Heterogeneous HW seems "inevitable" (as we well know, "the Grid is not anymore the Grid")

Several questions:
- Which PU architectures is LHCb *actually* exploring?
- How far is LHCb from *actually using* them? 
- Can WLCG help? (or, even before, need to care about it)

- Which **new** problems will we (LHCb, WCLG) face?


---
layout: top-title
color: gray-light
align: cm
title: What
---

:: title ::

# Schematically

:: content ::

Trying to fill up the table below:

|                       | **LHCb software readyness** | **resources readyness (availability to LHCb users)** | **distributed computing (Dirac+X)** |
|:--------------------- |:--------------------------- |:---------------------------------------------------- |:----------------------------------- |
| **ARM CPUs**          |                             |                                                      |                                     |
| **GPUs (which ones)** |                             |                                                      |                                     |
| **Quantum**           |                             |                                                      |                                     |
| **RiscV**             |                             |                                                      |                                     |
| **TPUs/NPUs/FPGA**    |                             |                                                      |                                     |


---
layout: top-title
color: gray-light
align: c
title: onlineoffline
---

:: title ::

# Online and offline

:: content ::

---
layout: top-title-two-cols
color: gray-light
align: c-lm-lm
title: Grid
---

:: title ::

# Reminders on LHCb's Grid

:: left ::

**LHCb exploits, via Dirac(+X):**
- WLCG computing resources (HTC) that are pledging to LHCb, plus a small fraction that is exploited opportunistically
- HPCs:
  - CSCS (an HPC masqueraded as a WLCG HTC site)
  - MareNostrum
  - SDumont
  - a small HPC in Costa Rica
  - VEGA (almost)
- LHCb's HLT2 farm

With the exception of few queues from WLCG sites, all of them are `amd64` CPUs, with "enough" RAM

:: right ::

usual plots

---
layout: top-title
color: gray-light
align: c
title: predictions
---

:: title ::

# Predictions

:: content ::



---
layout: top-title-two-cols
color: gray-light
align: c-lm-lm
title: ARM
columns: is-7
---

:: title ::

# "the easy one": ARM64

:: left ::

![](/public/images/ARM_DPopov_090925.png)

![](/public/images/Gauss_ARM.png)


:: right ::

- LHCb started exploiting (few) ARM queues, still in an opportunistic way
- Dirac(X) support is basically *done* (minor caveats)


---
layout: top-title
color: gray-light
align: c
title: Summary
---

:: title ::

# Summary

:: content ::

In summary:

|                       | **LHCb software readyness** | **resources readyness (availability to LHCb users)** | **distributed computing (Dirac+X)** |
|:--------------------- |:--------------------------- |:---------------------------------------------------- |:----------------------------------- |
| **ARM CPUs**          | Ready                       | via WLCG                                             | Ready                               |
| **GPUs (which ones?)**| Ongoing                     |                                                      | Not ready                           |
| **Quantum**           | Exploring                   |                                                      | Not planned                         |
| **RiscV**             |                             |                                                      | Not planned                         |
| **TPUs/NPUs/FPGA**    |                             |                                                      | Not planned                         |


---
layout: credits
color: navy
loop: true
speed: 1.0
title: credits/people
---

<div class="grid text-size-4 grid-cols-3 w-3/4 gap-y-10 auto-rows-min ml-auto mr-auto">
    <div class="grid-item text-center mr-0- col-span-3">
        <strong>Helpers</strong><br>
    </div>
    <div class="grid-item col-span-2">
        Ben Couturier <i>CERN, LHCb</i><br/>
        Andrea Valassi <i>CERN, LHCb</i><br/>
        Nicole <i></i>
    </div>
</div>

&nbsp;
&nbsp;
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
