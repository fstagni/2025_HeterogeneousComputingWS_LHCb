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

# <img id="DiracX" src="/public/images/LHCb.jpg" class="mx-auto w-2/5"> </img>

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

WLCG has been (and largely still is) about connecting "sites" with **vastly homogeneous architectures**: right now `x86_64` (`amd64`) **CPUs**.

Experiments like LHCb created a collection of highly specialized software for such architecture.

Nowadays LHCb, "like everyone", is looking for SW speedups, also exploring "heterogeneous" hardware.

Several questions:
- Which non-`amd64` PUs is LHCb *actually* exploring? and how far from *actually using* them? 
- Can WLCG help? (or, even before, need to care about it)
- Which **new problems** will we (LHCb, WLCG) face?

Still: **heterogeneous architectures are an opportunity**.


---
layout: top-title
color: gray-light
align: cm
title: What
---

:: title ::

# Trying to fill up the table below

:: content ::
<table>
  <tr>
    <td><strong></strong></td>
    <td><strong>LHCb software readiness</strong></td>
    <td><strong>Resources readiness (availability to LHCb users)</strong></td>
    <td><strong>Distributed computing (Dirac+X)</strong></td>
  </tr>

  <tr>
    <td><strong>CPUs: ARM and Risc-V</strong></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>

  <tr>
    <td><strong>GPUs</strong></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>

  <tr>
    <td><strong>TPUs/NPUs/FPGA</strong></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>

  <tr>
    <td><strong>Quantum</strong></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>

</table>

---
layout: section
color: cyan
title: grid_reminders
---

# What we have, and what we'll need

---
layout: top-title-two-cols
color: gray-light
align: c-lm-lm
title: online
columns: is-9
---

:: title ::

# Online, LHCb uses CPUs and GPUs

:: left ::

<div class="relative">
  <img src="/public/images/online.png" class="w-full" />

  <div class="absolute bottom-0 left-0 text-xs text-gray-500">
    Source: https://cds.cern.ch/record/2730181/
  </div>
</div>


:: right ::

LHCb has experience with non-`amd64` PUs, as HLT1 is fully on GPUs -- via [Allen](https://cds.cern.ch/record/2713102)

(still, the trigger software also runs offline, on CPUs)


---
layout: top-title-two-cols
color: gray-light
align: c-lm-lm
title: offline
columns: is-7
---

:: title ::

# Offline, everything is on CPUs.

:: left ::

<div class="relative">
  <img src="/public/images/offline.png" class="w-full" />

  <div class="absolute bottom-0 right-0 text-xs text-gray-500">
    Source: https://cds.cern.ch/record/2730181/
  </div>
</div>


:: right ::

- WLCG computing resources (HTC) that are pledging to LHCb, plus a small fraction that is exploited opportunistically
- HPCs, opportunistically
- LHCb's HLT2 farm (CPUs)
  - ...HLT1 GPUs, eventually?

With the exception of few `arm64` queues from WLCG sites, all of them are `amd64` CPUs, with "enough" RAM/Core.


---
layout: top-title-two-cols
color: gray-light
align: c-cm-lm
title: grid
---

:: title ::

# Simulations are CPU-hungry

:: left ::

**Grid usage in Q3 and Q4**

![](/public/images/pie_grid_Q34.png)

Dominated by Simulation!

:: right ::

Using the HLT2 (CPU) farm whenever possible

![](/public/images/running_peak.png)


---
layout: top-title-two-cols
color: gray-light
align: c-cm-lm
title: predictions
---

:: title ::

# Predictions

:: left ::

<div class="relative">
  <img src="/public/images/events_to_be_simulated.png" class="w-full" />

  <div class="absolute top-0 left-0 text-xs text-gray-500">
    !DRAFT!
  </div>
</div>

<Admonition title="Key takeaway" color="teal-light" width="400px">
Simulation is, and will likely stay, the largest consumer of processing cycles of LHCb Grid
</Admonition>

:: right ::

<div class="relative">
  <img src="/public/images/Simu_run5.png" class="w-full" />

  <div class="absolute top-0 left-0 text-xs text-gray-500">
    !DRAFT!
  </div>
</div>

When talking about heterogeneous architectures, we can't avoid asking ourselves: where will we be able to run Gauss, the LHCb Simulation SW?

Even if general simulation is **not** a natural candidate for GPUs, as we shall see, they provide better performances for specific cases.


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
align: c-lm-lm
title: gauss
columns: is-8
---

:: title ::

# Gauss, the LHCb simulation software

:: left ::

<img src="/public/images/Gauss_architecture.png" alt="Gauss" width="600"/>

:: right ::

Modular:

- **Gaussino** contains experiment-independent core elements. It is the ideal test-bed for new developments.
- **Pythia** is the main generator.
- **Geant4** is not irreplaceble, but for some cases.



---
layout: top-title-two-cols
color: gray-light
align: c-lm-lm
title: ARM
columns: is-7
---

:: title ::

# **Simulation**: ARM64, "the easy one"

:: left ::

![](/public/images/ARM_DPopov_090925.png)

![](/public/images/Gauss_ARM.png)


:: right ::

- The LHCb simulation software (Gauss) is ready for using ARM64 cores.
- There is still no sustained production load.
- LHCb started exploiting (few) ARM queues, still in an opportunistic way.
- Dirac(X) support is basically *done* (minor caveats).
- LHCb will increase the load on WLCG ARM queues gradually in 2026.


---
layout: top-title-two-cols
color: gray-light
align: c-lm-lm
title: GPUs-generators
---

:: title ::

# **Simulation**: using GPUs for generators

:: left ::

- **Pythia** is the generator used nowadays for 90%+ of the production requests. Will likely stay the same in the future. It does not plan nowadays a porting to GPUs.
- **MadGraph** is something for which there’s ongoing work to integrate, but will represent a fraction of what will actually be used. Will still be used together with Pythia.
- Other generators, like **EPOS**, are also used for specific purposes.

:: right ::

**MadGraph** can be used for offloading calculations of matrix elements

<div class="relative">
  <img src="/public/images/madgraph.png" class="w-full" />

  <div class="absolute top-0 right-0 text-xs text-gray-500">
    Source: https://indico.cern.ch/event/1338689/contributions/6015964/
  </div>
</div>

---
layout: top-title-two-cols
color: gray-light
align: c-cm-lm
title: GPUs-detector
---

:: title ::

# **Simulation**: using GPUs for detectors

:: left ::

As we'll hear again in this WS:

&nbsp;


<div class="relative">
  <img src="/public/images/Geant4-GPU.png" class="w-full" />

  <div class="absolute top-0 right-0 text-xs text-gray-500">
    Source: G. Corti
  </div>
</div>

:: right ::

**AdePT** has made big progress recently and the full LHCb simulation can now be run using it with an excellent physics agreement. The speed up obtained is 2.1x with respect to the standard Gauss and 1.7x with respect to to Gauss+G4HepEm on CPU.

LHCb is also interested in Optical Photons on GPUs, so we are favourably looking at what **Celeritas** is doing in that regard.


---
layout: top-title
color: gray-light
align: c
title: fastSim
---

:: title ::

# **Simulation**: GPUs for ML, for *fast* simulations

:: content :: 

<div class="relative">
  <img src="/public/images/Gauss_ML.png" class="w-full" />

  <div class="absolute bottom-0 right-0 text-xs text-gray-500">
    Source: Michał Mazurek, "ML in LHCb Simulation", Taipei LHCP 2025
  </div>
</div>


---
layout: top-title-two-cols
color: gray-light
align: c-lm-cm
title: fastFlashSim
columns: is-3
---

:: title ::

# **Simulation**: GPUs for *ultrafast* and *flash* simulations

:: left ::

**Lamarr** is a pipeline of ML-based modular parametrizations to replace both the simulation and reconstruction steps, for transforming generator-level particles into analysis-level reconstructed objects

:: right ::

<div class="relative">
  <img src="/public/images/lamarr.png" class="w-full" />

  <div class="absolute bottom-0 right-0 text-xs text-gray-500">
    Source: M Barbetti and L Anderlini, CHEP 2024
  </div>
</div>


---
layout: top-title
color: gray-light
align: c
title: whichGPUs
---

:: title ::

# Which GPUs

:: content ::

- For *AdePT*, **NVidia** GPUs required (for the moment)
  - Double precision needed. If only machine with single-precision GPUs available will need development to used them
- For *ML*: the market dominated by AI applications, so should not be a problem
- For *optical photons*: `Opticks` is 100% **NVidia** bound but there are alternatives emerging (`Mitsuba`, `Celeritas`)

---
layout: top-title-two-cols
color: gray-light
align: c-lm-lm
title: GPUAnal
columns: is-5
---

:: title ::

# **Analysis**: ARM, and GPUs

:: left ::

&nbsp;

LHCb makes use of **Analysis Productions** for centralised tupling
- an *analysis facility* in themselves

Data volumes in run 4 will be similar to run 3, and analysis workflows will likely be similar as well.
- Run 5 is when things will likely change.

:: right ::

&nbsp;

- `ARM64` will soon (in months) be used also for *Analysis Productions*. 
- Initiatives for ML-driven analysis exists within LHCb.
- At the moment, there are no specific plans for centrally-managed APs requesting GPUs.
- ML training, whenever will be requested (for analysis and not) *might* need to be pushed to the Grid.
- *LHCb at this moment can not make predictions on what will be its needs for training for analysis.*


---
layout: top-title
color: gray-light
align: c
title: QC
---

:: title ::

# Quantum Computing, other PUs?

:: content ::

- **CPUs**: there are no current plans for Risc-V (we'll follow the evolution).
- **FPGAs**: Online, for specific use-cases.
- **TPUs/NPUs**: Keeping an eye.
- **Quantum Computing**: [broad QC program](https://indico.cern.ch/event/1519367/). Still, of course, experimental.

&nbsp;
&nbsp;


<Admonition title="Not for now" color="orange-light" width="600px">
But, all of the above seems, nonetheless, "still too far" from WLCG.
</Admonition>



---
layout: top-title
color: gray-light
align: c
title: sw-conclusions
---

:: title ::

# Few early conclusions

:: content ::

- On one side, **for simulations** *LHCb plans to offload certain calculations to GPUs*: **GPUs are treated as accelerators**.
    - We do not fully know how to balance the CPU/GPU loads.
    - **It means, IMHO, that heterogeneous nodes a-la HPCs will actually be welcome**
    - Clearly, the processing efficiency will need to be calculated differently wrt to what we do now.
- **Training on ML** is instead a rather "different beast". On one side, it has the chance of yielding higher GPU efficiency, but:
    - it is unclear if we'll even need to run ML "on the Grid" (how often do we need to re-train?)
    - at first it does not seem to fit in our model of jobs-with-inputs (which is of course everyone's model)



---
layout: top-title-two-cols
color: gray-light
align: c-lm-lm
title: dirac
columns: is-5
---

:: title ::

# DiracX and heterogeneous slots

:: left ::

- Nowadays *Dirac(X) can take a node consisting of several CPUs and partition it*. CPUs only.
- The **match-making** process (the process of matching job needs to job slots capabilities) can use a very simple system for tagging slots including GPUs. This is not fully applicable for heterogeneous nodes.

:: right ::

Would not be able to fully exploit nodes like this:

<div class="relative">
  <img src="/public/images/lumig-overview.svg" class="w-full" />

  <div class="absolute bottom-0 right-0 text-xs text-gray-500">
    Source: https://docs.lumi-supercomputer.eu/hardware/lumig/
  </div>
</div>



---
layout: top-title-two-cols
color: gray-light
align: c-lm-lm
title: diracx
columns: is-5
---

:: title ::

# DiracX and heterogeneous slots (cont)

:: left :: 

In the context of DiracX, LHCb is working on:

- Using CWL for jobs and workflow description

![](/public/images/CWL1.png)

:: right ::

![](/public/images/diracx-logo-full-transparent-background.png)

- A realistic **slot description for heterogeneous architectures**
- An advanced jobs match-making
- "Solving" the general case of **whole node scheduling**.


---
layout: top-title
color: gray-light
align: c
title: WLCG
---

:: title ::

# A collaborative work

:: content ::

- The exploitation of heterogeneous architectures does not come for free: it is the result of R&D.
- R&D can be done by *experienced* engineers, physicists and architect: ensuring proper *funding* is therefore a must.
- WLCG experiments can not work in isolation. We welcome this workshop, and subsequent common **work**.
- I still think WLCG needs a proper information system.


---
layout: top-title
color: gray-light
align: c
title: Summary
---

:: title ::

# Summary

:: content ::

<table>
  <tr>
    <td><strong></strong></td>
    <td><strong>LHCb software readiness</strong></td>
    <td><strong>resources readiness (availability to LHCb users)</strong></td>
    <td><strong>distributed computing (Dirac+X)</strong></td>
  </tr>

  <tr v-click>
    <td><strong>ARM CPUs</strong></td>
    <td>Ready</td>
    <td>via WLCG</td>
    <td>Ready</td>
  </tr>

  <tr v-click>
    <td><strong>GPUs for Sim accelerators</strong></td>
    <td>Ongoing. Needs double-precision GPUs</td>
    <td>LHCb-owned, or via HPCs (opportunistically)</td>
    <td>Ongoing</td>
  </tr>

  <tr v-click>
    <td><strong>GPUs for ML</strong></td>
    <td>Ongoing</td>
    <td>LHCb-owned, or via clouds</td>
    <td>A very different paradigm</td>
  </tr>

  <tr>
    <td><strong>TPUs/NPUs/FPGA</strong></td>
    <td>Specific applications, online</td>
    <td>LHCb-owned</td>
    <td>Not planned</td>
  </tr>

  <tr>
    <td><strong>Quantum</strong></td>
    <td>Exploring</td>
    <td>"private"</td>
    <td>Not planned</td>
  </tr>

</table>


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
        Jan Van Eldik <i>CERN</i><br/>
        Nicole Skidmore <i>University of Warwick</i><br/>
        Andrea Valassi <i>CERN</i><br/>
        Many others from which I stole slides
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


---
layout: top-title
color: gray-light
align: c
title: ML
---

:: title ::

# ML training on the Grid? (an aside)

:: content ::

Up to now, all ML training have been done outside of the Grid. Will we need, at some point, to use it?

A topic that needs study.

At first it does not seem to fit in our model of jobs-with-inputs (which is of course everyone's model). Still, maybe (?) ML training scripts can be wrapped as batch jobs just like we do, and inputs read via the usual protocols. I suspect the issues would come:
- Because of the scale of inputs
- GPU nodes interconnection which is something that happens for ML training but never for us (e.g. we do not use MPI...)

---
layout: top-title-two-cols
color: gray-light
align: c-lm-lm
title: risks
---

:: title ::

# Risks

:: left ::

There are risks:

![](/public/images/risks.png)

:: right ::

What if we could buy from clouds the resources we need (those not pledged/guaranteed)?

![](/public/images/eco_model.png)

--> in order to save money, the WMS (DiracX) would need to implement economic models (to keep the costs down).

Not very different, conceptually, from implementing green computing models.
