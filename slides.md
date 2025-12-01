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

# <img id="DiracX" src="/public/images/LHCb.png" class="mx-auto w-2/5"> </img>

**Federico Stagni, deputy LHCb Computing PL** <Email v="federico.stagni@cern.ch" />
On behalf of the LHCb collaboration

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

WLCG has been (and largely still is) about connecting "sites" with **vastly homogeneous architectures**: right now *x86_64* (*amd64*) **CPUs**.

Experiments like LHCb created a collection of highly specialized software for such architecture.

Nowadays:
- LHCb, "like everyone", is looking for SW speedups, also exploring "heterogeneous" hardware.
- Heterogeneous HW which, at the same time, seems "inevitable"

Several questions:
- Which non-amd64 PUs is LHCb *actually* exploring?
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
| **TPUs/NPUs/FPGA**    |                             |                                                      |                                     |


---
layout: section
color: cyan
title: grid_reminders
---

# What we have, and what we'll need

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

FIXME: usual plots

---
layout: top-title-two-cols
color: gray-light
align: c-lm-cm
title: predictions
---

:: title ::

# Predictions

:: left ::

FIXME: plots from Conc

:: right ::

&nbsp;
&nbsp;
&nbsp;

<Admonition title="Key takeaway" color="teal-light" width="400px">
Simulation is, and will likely stay, the largest consumer of processing cycles of LHCb Grid, so, when talking about heterogeneous architectures, we can't avoid asking: where will we be able to run **Gauss**, the LHCb Simulation SW?
</Admonition>


---
layout: section
color: cyan
title: ongoingwork
---

# LHCb software and non-amd64 PUs

### ARM
### GPUs (and which ones)
### Quantum
### TPUs/NPUs/FPGA


---
layout: top-title-two-cols
color: gray-light
align: c-cm-lm
title: gauss
---

:: title ::

# Gauss crash course

:: left ::

![](/public/images/Gauss_architecture.png)

:: right ::

- "Gaussino" contains experiment-independent core elements. It is the ideal test-bed for new developments.
- **Pythia** is the generator used nowadays for 90%+ of the production requests. Will likely stay the same in the future. [FIXME]
- 


---
layout: top-title-two-cols
color: gray-light
align: c-lm-lm
title: ARM
columns: is-7
---

:: title ::

# Simulations on ARM64: "the easy one"

:: left ::

![](/public/images/ARM_DPopov_090925.png)

![](/public/images/Gauss_ARM.png)


:: right ::

- The LHCb simulation software (Gauss) is ready for using ARM64 cores.
- There is still no sustained production load.
- LHCb started exploiting (few) ARM queues, still in an opportunistic way.
- Dirac(X) support is basically *done* (minor caveats).
- --> will increase the load on WLCG ARM queues gradually in 2026.


---
layout: top-title-two-cols
color: gray-light
align: c-lm-lm
title: GPUs-generators
---

:: title ::

# Simulation: using GPUs for generators

:: left ::

- **Pythia** does not plan nowadays a porting to GPUs.
- **MadGraph** is something for which there’s ongoing work to integrate, but will represent a fraction of what will actually be used.
- **Sherpa** is not used

:: right ::

## MadGraph

Can be used for offloading calculations of matrix elements

![](/public/images/madgraph.png)


---
layout: top-title-two-cols
color: gray-light
align: c-lm-lm
title: GPUs-detector
---

:: title ::

# Simulation: using GPUs for detectors

:: left ::

:: right ::


---
layout: top-title-two-cols
color: gray-light
align: c-lm-lm
title: fastFlashSim
---

:: title ::

# Simulations: GPUs for fast and flash

:: left ::

:: right ::


---
layout: top-title-two-cols
color: gray-light
align: c-lm-lm
title: GPUAnal
columns: is-5
---

:: title ::

# Analysis: ARM, and GPUs

:: left ::

Reminders:
- LHCb makes use of *Analysis Productions* for centralised tupling
    - an analysis facility in themselves
- Data volumes in run 4 will be similar to run 3 -> analysis workflows will likely be similar as well.

:: right ::

- `ARM64` will soon be used also for *Analysis Productions*
- Initiatives for ML-driven analysis exists within LHCb.
- At the moment, there are no specific plans for centrally-managed APs requesting GPUs.
- ML training, whenever will be requested (for analysis and not) will be pushed to the Grid.


---
layout: top-title
color: gray-light
align: c
title: QC
---

:: title ::

# Analysis: Quantum Computing

:: content ::

LHCb has a broad QC program with several institutes and publications. 


---
layout: top-title
color: gray-light
align: c
title: PU
---

:: title ::

# Other PUs

:: content ::


---
layout: top-title
color: gray-light
align: c
title: sw-conclusions
---

:: title ::

# Few early conclusions

:: content ::

FIXME

- For simulations LHCb plans to offload calculations to GPUs. While doing so, the CPU waits. The processing efficiency will need to be calculated differently wrt to what we do now.
- ML: higher GPU occupation?
- 



---
layout: top-title
color: gray-light
align: c
title: dirac
---

:: title ::

# Scheduling for distributed computing

:: content ::

Full node scheduling

Match-making for DiracX


---
layout: top-title
color: gray-light
align: c
title: ML
---

:: title ::

# ML training

:: content ::

FIXME

A topic that needs study

at first it does not seem to fit in our model (which is of course everyone's model). Still, maybe (?) ML training scripts can be wrapped as batch jobs just like we do, and inputs read via the usual protocols. I suspect the issues would come:
- Because of the scale of inputs
- GPU nodes interconnection which is something that happens for ML training but never for us (e.g. we do not use MPI...)

---
layout: top-title-two-cols
color: gray-light
align: c-lm-lm
title: risks
---

:: title ::

# Risk

:: left ::

![](/public/images/risks.png)

:: right ::

## Economic models?

What if we are just given a "credit card"?
- and then we buy from clouds the resources we need (those not pledged/guaranteed)?

![](/public/images/eco_model.png)

--> in order to save money, the WMS (DiracX) would need to implement economic models
not very different, conceptually, from implementing green computing models.


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

|                       | **LHCb software readyness**    | **resources readyness (availability to LHCb users)** | **distributed computing (Dirac+X)** |
|:--------------------- |:------------------------------ |:---------------------------------------------------- |:----------------------------------- |
| **ARM CPUs**          | Ready                          | via WLCG                                             | Ready                               |
| **GPUs (which ones?)**| Ongoing                        | LHCb-owned                                           | Not ready                           |
| **Quantum**           | Exploring                      | "private"                                            | Not planned                         |
| **TPUs/NPUs/FPGA**    | Specific applications, online  | LHCb-owned                                           | Not planned                         |


---
layout: credits
color: navy
loop: true
speed: 1.0
title: credits/people
---

<div class="grid text-size-4 grid-cols-3 w-3/4 gap-y-10 auto-rows-min ml-auto mr-auto">
    <div class="grid-item text-center mr-0- col-span-3">
        <strong>Colleagues that helped in putting these slides together</strong><br>
    </div>
    <div class="grid-item col-span-2">
        Concezio Bozzi <i>INFN Ferrara</i><br/>
        Gloria Corti <i>CERN</i><br/>
        Ben Couturier <i>CERN</i><br/>
        Nicole Skidmore <i>University of Warwick</i><br/>
        Andrea Valassi <i>CERN</i>
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
