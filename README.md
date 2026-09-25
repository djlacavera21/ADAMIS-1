# # ADAMAS-1
## Adaptive Diamond–And–Graphene Mesh Array System
### A Neuralink-class cortical interface built from NCD / UNCD / N-UNCD, boron-doped diamond, and graphene

**Status:** Conceptual engineering specification (not a Neuralink product)  
**Class:** Hybrid penetrating + conformal carbon neural mesh  
**Target:** High-channel bidirectional BCI with chronic chemical sensing  
**Revision:** 0.1 — 2026-09-25

---

## 1. Design intent

Neuralink’s clinical stack (polyimide + Ti/Pt/Au + PEDOT:PSS / IrOx) optimizes *flexibility + robotic insertion + channel count*. It does not optimize *Faradaic stability, hermetic carbon packaging, or neurotransmitter sensing*.

ADAMAS-1 keeps the Neuralink *problem statement* (1k–3k sites, wireless Link-class can, robot-insertable, flush cranial package) and replaces the materials system with crystalline carbon:

| Layer of the problem | Carbon answer |
|---|---|
| Conformal surface decoding / stimulation | Multilayer graphene / rGO micro-island mesh |
| Penetrating single-unit access | N-UNCD or BDD-coated carbon-fiber filaments |
| Insulation + hermetic barrier | Intrinsic nanocrystalline diamond (i-NCD) and diamond-in-polyimide hybrid |
| High charge-injection tips | Oxygen-plasma-activated N-UNCD |
| Neurochemical window (dopamine, etc.) | Boron-doped diamond (BDD) sensing pads |
| Feedthrough / package lid | Polycrystalline diamond or UNCD-sealed vias |

The mesh is not a Utah-array clone and not a pure ECoG sheet. It is a **two-story lattice**: a graphene cortical veil on the pia, with a sparse forest of diamond-coated filaments dropping 1.5–4.0 mm into cortex.

---

## 2. Architecture at a glance

                ┌─────────────────────────────────────┐
                │  ADAMAS Link can (PCTFE / diamond   │
                │  lid, ASIC, coil, battery)          │
                └──────────────────┬──────────────────┘
                                   │ hermetic BDD / UNCD
                                   │ feedthrough forest
                ┌──────────────────▼──────────────────┐
                │  Graphene veil (epicortical mesh)   │
                │  256–1024 surface contacts          │
                │  8–12 µm total stack                │
                └──────────────────┬──────────────────┘
                                   │ strain-relief
                                   │ diamond-PI hinges
          ┌──────────┬─────────────┼─────────────┬──────────┐
          ▼          ▼             ▼             ▼          ▼
     UNCD/BDD    UNCD/BDD      UNCD/BDD      UNCD/BDD   UNCD/BDD
     filament    filament      filament      filament   filament
     16 sites    16 sites      16 sites      16 sites   16 sites
     @ 200 µm    @ 200 µm      @ 200 µm      @ 200 µm   @ 200 µm

**Baseline configuration (ADAMAS-1A)**

- 64 penetrating filaments × 16 sites = **1,024 intracortical channels**
- Graphene veil: **512 epicortical channels** (recording) + **64 graphene micro-island stim clusters**
- BDD sensing subset: **32 dedicated neurochemical pads** (shared or interleaved)
- Total addressable sites: **1,632 electrical + 32 chemical**
- Package diameter: 23 mm (quarter-class), thickness 8–9 mm
- Insertion depth: 1.8–3.5 mm (motor / speech cortex profiles)

**Scale configuration (ADAMAS-1B)**

- 96 filaments × 32 sites = 3,072 intracortical
- Graphene veil 1,024 surface channels
- Same can, denser ASIC

---

## 3. Material assignment (what each carbon does)

### 3.1 Intrinsic nanocrystalline diamond (i-NCD)
- Role: dielectric, moisture barrier, abrasion face on the veil backside.
- Why: wide-bandgap insulator, chemically inert, can be grown as a few-hundred-nanometer film and patterned.
- Use: inter-trace insulation on the veil; hermetic cap over feedthroughs; optional diamond-in-polyimide bilayer where full rigidity is unacceptable.

### 3.2 Ultrananocrystalline diamond (UNCD) and nitrogen-included UNCD (N-UNCD)
- Role: conductive penetrating electrodes and high-capacitance stimulation sites.
- Why: N-UNCD conductivity lives in nitrogen-thickened sp² grain boundaries; after low-energy O₂ plasma (hours-scale), reported capacitance can exceed **1 mF/cm²** and charge injection **> 1 mC/cm²**.
- Use: exposed electrode windows on filaments; optional 3D nanostructured tips.

### 3.3 Boron-doped diamond (BDD)
- Role: Faradaic-stable stimulation *and* voltammetric sensing.
- Why: widest practical aqueous window among solid electrodes; low background current; gold-standard dopamine / serotonin electrochemistry.
- Use: every Nth filament site is a BDD pad instead of N-UNCD; 32 dedicated sensing islands on the veil edge.

### 3.4 Graphene / reduced graphene oxide (rGO)
- Role: the mesh itself — the thing that makes this a *mesh* rather than a thread bundle.
- Why: atomic-to-nanometer thickness, high in-plane conductivity, claimed ~200× charge injection vs metals before Faradaic onset, conformal “second-skin” mechanics, transparent for optical co-registration.
- Use:
  - Continuous or islanded rGO film as the epicortical electrode field (25–300 µm “dots”).
  - Graphene micro-islands (thousands per stim cluster) for focused stimulation without metal corrosion.
  - Optional graphene encapsulation over metal traces if a hybrid interconnect is retained in v0.1.

### 3.5 Carbon-fiber core (not a crystal, but the mechanical spine)
- Role: 5–7 µm PAN or pitch carbon fiber as the penetrating filament backbone.
- Why: already neuron-scale, low insertion force, proven single-unit recording; diamond is *grown onto* it rather than replacing it.
- Coat: 200–800 nm N-UNCD or BDD via seeded MWCVD after a thin carbide-forming interlayer (Mo/Nb or similar, per published CF–diamond hybrids).

### 3.6 What is *not* the primary conductor
- No PEDOT:PSS as the chronic stim workhorse (optional thin primer only).
- No IrOx as the default charge-injection film.
- Gold / Pt only as *buried* interconnect or ASIC bump metal, never as the tissue-facing electrode if the carbon path is intact.

---

## 4. Layer stacks

### 4.1 Epicortical graphene veil (the mesh sheet)

Top (pia-facing) → bottom (dura / package side)

1. Optional monolayer graphene or 4–8 layer rGO electrode islands, 25 µm and 80 µm two-size mix  
2. 50–80 nm i-NCD or parylene-C edge seal around each island  
3. 150–400 nm TiN or graphene-interconnect traces (TiN if graphene via yield is low in v0.1)  
4. 300–500 nm i-NCD insulator  
5. 6–8 µm medical polyimide or liquid-crystal polymer carrier (flexibility budget)  
6. 200 nm i-NCD or DLC backside moisture barrier  
7. Strain-relief diamond-PI “hinge” tabs at the 64 filament roots  

**Total veil thickness:** 8–12 µm over the array field, ~15 µm at hinge roots.  
**Aperture:** open lattice (not a continuous occlusive sheet) so CSF and vessels are not blanketed. Fill factor of solid material ≤ 35%.

### 4.2 Penetrating filament (the forest)

Cross-section, outside → in:

1. Exposed N-UNCD or BDD window (electrode), 14 × 24 µm or 20 µm disc  
2. 200–600 nm conformal N-UNCD / BDD sheath  
3. Optional 20–40 nm adhesion / carbide interlayer  
4. 5–7 µm carbon-fiber core  
5. Between sites: i-NCD or diamond-like carbon overcoat as dielectric  

**Filament width:** 12–20 µm at the electrode belt, tapering to 8–10 µm at the tip.  
**Thickness / effective diameter:** ~8–15 µm (still hair-scale, stiffer than Neuralink polyimide thread, softer than silicon Utah shanks).  
**Site pitch along filament:** 180–220 µm, 16 sites over ~3.2 mm.  
**Tip:** chisel or bullet UNCD, optional UNCD T-beam stiffener only in the proximal 400 µm to survive dura punch, then flex.

### 4.3 Hermetic feedthrough

- 64–96 UNCD or BDD vias through an i-NCD or glass-ceramic plate.
- Carbon-fiber or doped-diamond plugs, helium-leak qualified.
- ASIC side: standard Au/Cu bump to Neuralink-class custom amp/stim chip.
- Tissue side: traces fan into the veil and filament roots.

This is the one place diamond’s hermetic reputation is load-bearing. The can wall can remain PCTFE or ceramic; the *electrical skin* crossing into the body is carbon.

---

## 5. Electrical / electrochemical targets

These are *design targets* synthesized from published N-UNCD, BDD, and graphene-BCI numbers — not measured ADAMAS hardware.

| Parameter | Filament N-UNCD site | Filament BDD site | Graphene veil dot (25 µm) |
|---|---|---|---|
| Geometric area | ~300–500 µm² | ~300–500 µm² | ~500 µm² |
| 1 kHz impedance goal | < 50 kΩ | < 80 kΩ | < 30 kΩ |
| Charge injection capacity | ≥ 1.0 mC/cm² (O₂-activated N-UNCD) | 0.2–0.5 mC/cm² class | high; InBrain-class claims ≫ metal |
| Water window | wide | very wide | non-Faradaic-dominant |
| Stim use | primary IC stim | stim + FSCV | surface stim / mapping |
| Sensing | spikes, LFP | spikes + dopamine | LFP, high-gamma, mapping |
| Chronic Faradaic stability | high | highest | high (no metal oxide cycle) |

ASIC assumptions (Link-class):
- 1,024–3,072 rec channels, spike detect on-implant
- Independent stim current sources on a subset (256 stim-capable)
- 32 analog mux paths reserved for BDD voltammetry (slower than spike band)
- BLE or equivalent out; inductive recharge; ferrite thermal budget unchanged

---

## 6. Mesh geometry and surgical concept

### 6.1 Why “mesh” not “threads only”

A thread bundle records depth but is blind to the cortical surface sheet. A graphene veil records the sheet but not layer V output neurons. ADAMAS-1 is a **laminated lattice**:

- Veil sits on pia after a small durotomy (or through a dural slit if the hinge tabs are thin enough).
- Filaments deploy *through* registered holes in the veil so the veil acts as a strain-relief grommet and a surface electrode at the same time.
- Open-cell mesh geometry (hex or stretched-hex) with 250–400 µm windows keeps pial vessels visible to the insertion robot and reduces CSF trapping.

### 6.2 Insertion

Two-pass robot sequence:

1. **Seat the veil** — wet-conform the 8–12 µm carbon sheet; optical fiducials in the graphene (it is semi-transparent) let the vision system map vessels.
2. **Sew the forest** — same class of sewing robot as Neuralink R1, but the needle engages a UNCD-reinforced loop or a carbon-fiber eye at each filament tip. Insertion force is expected to be closer to carbon-fiber literature (low) than to silicon. Optional UNCD T-beam shuttle on the first 0.4 mm only, then released.

Avoidance map is vessel-first, same philosophy as Neuralink. The veil’s transparency is an advantage the opaque polyimide thread cartridge does not have.

### 6.3 Mechanical mismatch strategy

Diamond is stiff. The mesh must not be a diamond plate.

- Crystal carbon is used as *films and coatings* (100 nm–1 µm), not as 50 µm diamond beams (except optional proximal shuttle).
- Bending compliance lives in the polyimide/LCP carrier and in the carbon-fiber cores.
- Filament flexural rigidity target: high enough to insert, low enough to ride micromotion after the shuttle (if any) is withdrawn.
- Veil tensile islands of graphene take strain; i-NCD is patterned as islands, not a continuous brittle sheet.

---

## 7. Fabrication pathway (high level)

This is a process *map*, not a shop traveler.

**A. Filaments**
1. Tension-mount carbon-fiber tow; isolate singles.
2. Seed with nanodiamond; optional Mo/Nb interlayer.
3. MWCVD growth of N-UNCD or BDD to target thickness.
4. Mask electrode windows; grow or leave i-NCD dielectric between sites.
5. O₂-plasma activate N-UNCD sites (capacitance step).
6. Terminate proximal end in a UNCD/BDD via slug for the feedthrough plate.

**B. Veil**
1. Carrier PI/LCP on handle wafer.
2. Deposit / transfer graphene or rGO; pattern 25/80 µm dots and traces.
3. i-NCD dielectric by MWCVD or a diamond-in-PI process.
4. Open electrode and filament-through vias.
5. Backside barrier; release; cut hex lattice.

**C. Integration**
1. Pop-in filaments through veil vias; laser or thermosonic carbon-to-carbon / carbon-to-TiN bond at the hinge.
2. Bond hinge bundle to diamond feedthrough plate.
3. Helium leak + soak + accelerated aging.
4. Flip onto Link-class ASIC / battery / coil can.
5. Sterile cartridge for the sewing robot.

Yield killers to budget for: graphene transfer tears, CVD temperature vs PI budget (hence diamond-in-PI and handle-wafer sequences), fiber-to-via hermeticity, plasma activation uniformity.

---

## 8. Biological and chronic rationale

| Failure mode Neuralink-class devices already know | Carbon-mesh bet |
|---|---|
| Metal Faradaic wear under stim | Graphene + diamond have no metal-oxide charge cycle at the tissue face |
| PEDOT delamination / over-ox | Not the chronic stim film |
| Glial encapsulation on stiff silicon | Fiber-scale tips + open mesh + documented diamond cytocompatibility |
| Thread retraction | Veil grommet + hinge is an *anchor plane* the free thread lacks |
| Moisture ingress at feedthrough | Diamond via plate |
| No chemical closed loop | BDD FSCV channels |

None of this deletes immune response. Geometry still dominates scarring. The claim is *better electrochemistry and a second mechanical story*, not magic biocompatibility.

Neuron-retention target to beat in animal histology: Neuralink-reported ~98% local neuron presence around polymer threads. ADAMAS must match or beat that at 6 and 26 weeks, plus show stable BDD voltammograms.

---

## 9. Comparison snapshot

| | Neuralink N1-class (public) | InBrain-class graphene sheet | ADAMAS-1 mesh |
|---|---|---|---|
| Tissue face | Au/Pt + PEDOT / IrOx | Graphene / rGO | Graphene + N-UNCD + BDD |
| Form | 64 flexible threads | Epicortical film | Veil + 64 diamond-coated filaments |
| Depth access | Yes (3–5 mm) | No (surface) | Yes |
| Surface mapping | Weak | Strong | Strong |
| Chemical sensing | No | No | BDD subset |
| Hermetic strategy | Polymer / glass-ceramic | Conventional | Diamond vias |
| Insertion | Sewing robot | Lay-on | Lay-on + sew |
| Maturity | Human implants | First-in-human surface | Concept |

---

## 10. Risks, unknowns, kill criteria

1. **CVD vs flexibility.** If i-NCD films crack at physiological bend radii, fall back to diamond-in-PI and keep crystal carbon only at electrodes and vias.
2. **Insertion stiffness.** If coated fibers buckle or lacerate vessels more than polyimide threads, shorten the UNCD sheath to the windows only.
3. **Graphene chronic debris.** rGO flake release is a regulatory issue. Prefer continuous CVD graphene with sealed edges over loosely stacked oxide.
4. **Plasma-activated N-UNCD drift.** Capacitance gains must survive 10⁷ stim pulses and protein adsorption, not just PBS.
5. **ASIC thermal + FSCV.** Voltammetry waveforms are hostile neighbors to spike amps; isolate the 32 chemical paths.
6. **Robot cartridge rewrite.** A new end-effector is a program, not a material swap.
7. **Kill the program if** 12-week large-animal impedance rise > 3× *and* neuron loss exceeds polymer-thread controls *and* BDD sensing dies. Materials romance is not a clinical endpoint.

---

## 11. Development sequence

- **P0 (bench):** 16-site coated fibers + 64-dot graphene coupon; EIS, CIC, soak, Flex-cycle.
- **P1 (rodent):** 8-filament mini-mesh over motor cortex; 8-week histology + spike yield vs polyimide control.
- **P2 (sheep / NHP):** full 64-filament + veil, robot insertion, 6-month wireless.
- **P3:** hermetic via plate + chemical channels on.
- **P4:** human feasibility only after P2 histology and stim-safety pack match or beat the polymer baseline.

---

## 12. One-sentence thesis

**ADAMAS-1 is a Neuralink-shaped implant whose tissue face is a graphene mesh and whose depth electrodes are plasma-activated N-UNCD / BDD on carbon-fiber cores, with intrinsic diamond doing insulation and hermetic work that metals and polymers do poorly over a decade.**

---

*End of specification — ADAMAS-1 rev 0.1*