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
layout: top-title-two-cols
color: gray-light
align: c-lm-lm
title: online
columns: is-9
---

:: title ::

# Online, LHCb uses CPUs and GPUs

:: left ::

![](/public/images/online.png)

:: right ::

LHCb has experience with non-`amd64` PUs: HLT1 is fully on GPUs.


---
layout: top-title-two-cols
color: gray-light
align: c-lm-lm
title: offline
columns: is-7
---

:: title ::

# Offline

:: left ::

![](/public/images/offline.png)

...but offline, everything is on CPUs.

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
columns: is-9
---

:: title ::

# Simulations are CPU-hungry

:: left ::

Grid usage in Q3

![](/public/images/Grid_Q3.png)

:: right ::

Using the HLT2 (CPU) farm whenever possible

![](/public/images/running_peak.png)


---
layout: top-title-two-cols
color: gray-light
align: c-cm-lm
title: predictions
columns: is-9
---

:: title ::

# Predictions

:: left ::

![](/public/images/events_to_be_simulated.png)

![](/public/images/Simu_run5.png)

:: right ::

&nbsp;
&nbsp;

<Admonition title="Key takeaway" color="teal-light" width="200px">
Simulation is, and will likely stay, the largest consumer of processing cycles of LHCb Grid
</Admonition>

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

"Gaussino" contains experiment-independent core elements. It is the ideal test-bed for new developments.



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
- Other generators, like **Sherpa**, are also used for specific purposes.

:: right ::

**MadGraph** can be used for offloading calculations of matrix elements

![](/public/images/madgraph.png)


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

![](/public/images/Geant4-GPU.png)

:: right ::

AdePT has made a big progress recently and can now run the full LHCb simulation with a perfect physics agreement. The speed up we are obtaining is 2.1x with respect to the standard Gauss and 1.7x with respect to to Gauss+G4HepEm on CPU.    

LHCb is also interested in Optical Photons on GPUs, so we are favourably looking at what Celeritas is doing in that regard.


---
layout: top-title
color: gray-light
align: c
title: fastSim
---

:: title ::

# **Simulation**: GPUs for ML for parametrization

:: content :: 

![](/public/images/Gauss_ML.png)

---
layout: top-title-two-cols
color: gray-light
align: c-lm-cm
title: fastFlashSim
columns: is-3
---

:: title ::

# **Simulation**: GPUs for fast and flash simulations

:: left ::

**Lamarr** is a pipeline of ML-based modular parametrizations to replace both the simulation and reconstruction steps, for transforming generator-level particles into analysis-level reconstructed objects

:: right ::

![](/public/images/lamarr.png)


---
layout: top-title
color: gray-light
align: c
title: whichGPUs
---

:: title ::

# Which GPUs

:: content ::

- For AdePT, NVidia GPUs required (for the moment)
  - Double precision needed. If only machine with single-precision GPUs available will need developemnt to used them
- For ML: the market dominated by AI applications, so should not be a problem
- For optical photons: Opticks is 100% NVidia bound but there are alternatives emerging

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

LHCb makes use of **Analysis Productions** for centralised tupling
- an *analysis facility* in themselves
Data volumes in run 4 will be similar to run 3 --> analysis workflows will likely be similar as well.
- Run 5 is when things will likely change.

:: right ::

- `ARM64` will soon be used also for *Analysis Productions*. 
- Initiatives for ML-driven analysis exists within LHCb.
- At the moment, there are no specific plans for centrally-managed APs requesting GPUs.
- ML training, whenever will be requested (for analysis and not) will likely need to be pushed to the Grid.
    - LHCb at this moment can not make predictions on what will be its needs for training for analysis.


---
layout: top-title
color: gray-light
align: c
title: QC
---

:: title ::

# Quantum Computing, other PUs

:: content ::

LHCb has a broad QC program with several institutes and publications. Still, of course, experimental.

FPGA ...

All of the above seem, nonetheless, "still too far" from WLCG.


---
layout: top-title
color: gray-light
align: c
title: sw-conclusions
---

:: title ::

# Few early conclusions

:: content ::

- On one side, **for simulations LHCb plans to offload certain calculations to GPUs. GPUs are treated as accelerators**.
    - While doing so, the CPU waits (and the GPU waits to be given something to do).
    - It means that heterogeneous nodes a-la HPCs will actually be needed (while as of now, they are more like an annoyance)
    - Clearly, the processing efficiency will need to be calculated differently wrt to what we do now.
- **Training on ML** is instead a rather "different beast". On one side, it has the chance of yielding higher GPU efficiency, but:
    - it is unclear if we'll even need to run ML "on the Grid" (how often do we need to re-train?). 
    - at first it does not seem to fit in our model of jobs-with-inputs (which is of course everyone's model)



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
title: Summary
---

:: title ::

# Summary

:: content ::

In summary:

|                               | **LHCb software readyness**    | **resources readyness (availability to LHCb users)** | **distributed computing (Dirac+X)** |
|:----------------------------- |:------------------------------ |:---------------------------------------------------- |:----------------------------------- |
| **ARM CPUs**                  | Ready                          | via WLCG                                             | Ready                               |
| **GPUs for Sim accelerators** | Ongoing                        | LHCb-owned, or via HPCs (opportunistically)          | Not ready                           |
| **GPUs for ML**               | Ongoing                        | LHCb-owned, or via clouds                            | A very different paradigm           |
| **Quantum**                   | Exploring                      | "private"                                            | Not planned                         |
| **TPUs/NPUs/FPGA**            | Specific applications, online  | LHCb-owned                                           | Not planned                         |


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

What if we are just given a "credit card"?
- and then we buy from clouds the resources we need (those not pledged/guaranteed)?

![](/public/images/eco_model.png)

--> in order to save money, the WMS (DiracX) would need to implement economic models
not very different, conceptually, from implementing green computing models.
