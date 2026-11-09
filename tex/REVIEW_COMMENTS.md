# Review comments on `tex/main.tex`

Exported from the Overleaf project on 2026-10-10, right after the "Sync edits from Overleaf" push. 59 open comment threads (none resolved), plus 62 tracked changes that have not been accepted or rejected.

**Revision status (updated 2026-11-09):** every thread below is addressed in `tex/main.tex`. The note after each checkbox says how, and describes the text as of 2026-11-09. That is after a second revision pass that, among other things, names EAMxx once and calls it the host model thereafter, folds the old Sect. 3.1 (verification and cost) into the preamble of Sect. 3, condenses Table 2 and moves the grammar to Appendix A. Once the revision is synced, resolve the threads and accept the tracked changes in Overleaf.

Line numbers refer to `tex/main.tex` as pushed in that commit. Overleaf pushes tracked insertions as plain text and leaves tracked deletions out, so the file here reads as if every tracked change were accepted. Line numbers will drift as the file is edited; the quoted anchor text is the reliable locator.

Authors are the Overleaf display names, or the email handle mapped to a name where the account has none.

## Comments by reviewer

- Andrew Gettelman: 45 (C05, C07, C08, C09, C11, C12, C13, C15, C16, C18, C19, C20, C22, C23, C24, C25, C26, C27, C28, C31, C32, C33, C34, C35, C36, C37, C38, C40, C41, C42, C43, C44, C45, C46, C47, C48, C49, C50, C51, C52, C53, C54, C55, C58, C59)
- Adam Varble: 8 (C03, C04, C06, C17, C21, C30, C39, C56)
- Peter Caldwell: 3 (C01, C02, C57)
- Robert Jacob: 3 (C10, C14, C29)

## Comments, in document order

### Abstract

#### C01 · line 78

- [x] addressed — Changed to "turns".

> accepts a string containing a mathematical expression into a syntax tree

- **Peter Caldwell** (2026-09-14): this seems grammatically incorrect. Maybe "turns" instead of "accepts"?

#### C02 · line 79

- [x] addressed — EAMxx is named where the implementation is introduced (Contributions), and called the *host model* thereafter, because any E3SM component can host the same system. The abstract says "the C++ atmosphere component of E3SM". The title does not yet name the model; GMD asks for the model name and version there, which is still open.

> the C++ atmosphere component of the Energy Exascale Earth System Model

- **Peter Caldwell** (2026-09-14): It feels a bit weird to not describe this as EAMxx here and elsewhere.

### 1 Introduction

#### C03 · line 90

- [x] addressed — Gave the resolution (nominal 1°, about 100 km). Added the 3.25 km global storm-resolving case: about 25 million columns × 128 levels, about 13 GB per 3-D field per sample, nearly 2000× the 1° figure.

> the latest release of the Energy Exascale Earth System Model (E3SM) has an atmosphere component with 21\,600 columns

- **Adam Varble** (2026-09-16): What spatial resolution is this? It would be useful to know for context to the later statement on cubic growth of data volume, so one can do the calculation for current global storm-resolving models that are en vogue.

#### C04 · line 97

- [x] addressed — Added a sentence: the usual workaround is to write every input and compute the quantity in post-processing, which adds to output volume and write time.

> adding a new variable  cannot be done without modifying the source code, and oftentimes changes are needed as part of community-driven model intercomparison projects or for specific scientific questions.

- **Adam Varble** (2026-09-16): Or, people choose to output variables needed to compute diagnostics in postprocessing, again amplifying the size of output and slowdown of runtime due to writing a lot of output.

#### C05 · line 99

- [x] addressed — The Discussion names spatial sampling (output at fixed sites, or along the track of an aircraft or a satellite) as future vocabulary, and Contributions says the current operators do not yet cover it. An intro sentence calling such sampling an observation operator applied in space was added in the first revision and later cut.

> The output list acts as an observation operator applied to the simulated trajectory, and it fixes a priori the set of questions the model output dataset can answer.

- **Andrew Gettelman** (2026-09-10): What about the use case where output is only desired in a particular region or for particular columns (a fixed site or an aircraft or satellite observational sampling 'mask'? This is implied below (moving masks). 

#### C06 · line 105

- [x] addressed — Changed to "at every model time step".

> frequency

- **Adam Varble** (2026-09-16): What is this referring to?

#### C07 · line 111

- [x] addressed — Rewritten: training sets need a *different* selection. An emulator may use far fewer variables at higher frequency, and process emulators need quantities that are rarely written. Dropped "a great deal of it".

> and they want a great deal of it.

- **Andrew Gettelman** (2026-09-10): Actually they don't. They often want LESS. Think of what limited set of prognostic variables ACE2 has v. full E3SM....

#### C08 · line 115

- [x] addressed — Answered in the last intro paragraph and in Fig. 1b: values go into the stream's in-memory accumulator every step and are written at the stream's output frequency.

> evaluated by the model at runtime while the full state is still in memory.

- **Andrew Gettelman** (2026-09-10): Maybe answered later, but is it the diagnostic then held in memory as well for a time, with the write decoupled from the sampling time?

### 1 Introduction › Related works

#### C09 · line 121

- [x] addressed — Now "reduce data volume before it is written".

> reduce

- **Andrew Gettelman** (2026-09-10): reduce what?

#### C10 · line 122

- [x] addressed — Removed the LHCb example, as Rob suggested.

> LHCb experiment

- **Robert Jacob** (2026-09-10): I'd stick with examples from other scientific applications.  The data reduction done from sensor to disk is very different.

#### C11 · line 122

- [x] addressed — Moot: the LHCb sentence is gone.

> LHCb

- **Andrew Gettelman** (2026-09-10): Spell out acronym

#### C12 · line 125

- [x] addressed — Explained: a derived field is a formula over other fields, which may themselves be derived, and units carry through automatically.

> units through recursively defined derived fields

- **Andrew Gettelman** (2026-09-10): This might need some more explanation, I don't fully understand what this is.

#### C13 · line 126

- [x] addressed — Defined just-in-time compilation in the text, following Jeff's reply.

> just-in-time-compiled derived fields

- **Andrew Gettelman** (2026-09-10): is it 'compiled' or 'calculated'?
- **Jeffrey Johnson** (2026-09-10): Just-in-Time (JIT) compilation is the run-time compilation of a scripting language to machine code, just in advance of evaluating it. So: both!

#### C14 · line 129

- [x] addressed — The four placements are now labeled paragraphs (1)–(4).

> four

- **Robert Jacob** (2026-09-10): Make it more clear when you're moving from one to the other in what follows.
- **Andrew Gettelman** (2026-09-10): Agreed.

#### C15 · line 132

- [x] addressed — Spelled out XIOS (and ADIOS2).

> XIOS

- **Andrew Gettelman** (2026-09-10): Acronym

#### C16 · line 136

- [x] addressed — Now reads "Post-processing, however, sees only what was written, not the full model state", and the streaming placement is described as handing model state to consumers while the simulation runs.

> What post-processing does not have is the full model state.

- **Andrew Gettelman** (2026-09-10): The streaming model has the model state.

#### C17 · line 137

- [x] addressed — Adopted: exact only when the written fields fully determine the quantity. A process rate usually doesn't qualify, because of process ordering and limiters or fixers.

> It reproduces a quantity exactly whenever that quantity is determined by what is already written

- **Adam Varble** (2026-09-21): This depends. If you want a process rate, computing it from state output does not necessarily reproduce the rate during runtime in the model because there is an order of operations, conservation checks, etc.

#### C18 · line 138

- [x] addressed — Persistence boundary is now defined where it is introduced (Related works), in Table 1 and in Fig. 1.

> The persistence boundary

- **Andrew Gettelman** (2026-09-10): What does that mean?

#### C19 · line 138

- [x] addressed — Defined "write path" (middleware transforming fields on the way to the file) and "publish" (handing state to consumers outside the model).

> I/O middleware still acts on the write path before anything is published

- **Andrew Gettelman** (2026-09-10): what do 'write' and 'published' mean in this context?

#### C20 · line 139

- [x] addressed — Rewritten: time averaging and the choice of snapshots are established forms of reduction before persistence and part of every output configuration. In global km-scale modeling, more elaborate reductions (conditional statistics, moments, distributions) are now moving before the persistence boundary too.

> Reduction before persistence is the direction the field is moving.

- **Andrew Gettelman** (2026-09-10): This has always been the model right? The reduction is usually in time (Averaging or snapshots) and part of the state output. So how is this different?

#### C21 · line 139

- [x] addressed — Scoped to global km-scale modeling. Added that object tracking and observation simulators still write more output than ever.

> field

- **Adam Varble** (2026-09-21): What field specifically? Because I don't know if this is generally true. For some applications, we write out more than ever before, e.g., thermal tracking, observational simulators, etc. that may require high spatial and temporal resolution related to objects or specific spatial directions. There may be a bit of movement to move such tasks online, but not a lot. It really depends on how big your output is and what you can handle. It seems like you are thinking about global, km-scale modeling rather than modeling in general.

#### C22 · line 141

- [x] addressed — "Thesis" is gone. The three elements of the proposed approach are listed as (i)–(iii) at the end of the intro, as Jeff suggested, and Related works refers back to them as "the three elements of our proposed approach".

> thesis

- **Andrew Gettelman** (2026-09-10): What thesis? (the word doesn't appear before this). 
- **Jeffrey Johnson** (2026-09-10): Maybe "proposed approach" is more what we say in the intro?
- **Naser Mahfouz** (2026-09-11): The last paragraph in the intro preamble (bottom of page 1 currently) is a classic statement of thesis... 

#### C23 · line 141

- [x] addressed — Resolved by the same change: "its" now refers to the explicitly listed three elements.

> its

- **Andrew Gettelman** (2026-09-10): What is 'it'?
- **Jeffrey Johnson** (2026-09-10): The approach, I think. But this would hit better if we called out the three elements of the approach in the intro and then mention that all three elements are used in other communities, and that two are commonly used together. (Right?)
- **Naser Mahfouz** (2026-09-11): it goes back to "thesis of Sect 1" 

#### C24 · line 144

- [x] addressed — Now names them: "I/O middleware and streaming architectures".

> several of these systems

- **Andrew Gettelman** (2026-09-10): What systems? 

#### C25 · line 144

- [x] addressed — Rewritten: the distinction drawn is between whose code computes the diagnostic and on which representation of the state, explicitly not between online and offline analysis.

> online against offline

- **Andrew Gettelman** (2026-09-10): seems pretty online to me. 

#### C26 · line 145

- [x] addressed — Paragraph rewritten in plain terms with an example (mass-weighted vertical integral, mean over valid cells). Added Table 1 (terms) and the new Fig. 1 so the terminology is fixed early.

> It is which representation of the state the operator receives, and therefore which code implements the operator: for a quantity whose definition depends on the component's own conventions, its vertical coordinate, its area weights, its masking and renormalization rule, the implementation is part of the definition.
> For that reason we follow \citet{childs_terminology_2020} in avoiding ``in situ,'' whose established usage covers analysis over a published mesh representation, and we write ``model-integrated'' or ``in-model'' throughout.

- **Andrew Gettelman** (2026-09-10): I'm pretty confused by all this. Maybe you need a diagram here to label everything consistently and get the reader on the same page. I think terms keep changing.
- **Jeffrey Johnson** (2026-09-10): I *think* the point of this paragraph is that every component in an ESM has e.g. its own spatial discretization and therefore its own representation, and that "in situ" are often interpreted in terms of externally-imposed representations. But I agree that we could clean up the terminology. 

### 1 Introduction › Contributions

#### C27 · line 151

- [x] addressed — Now points to Fig. 1 (new schematic) and Table 1.

> the system

- **Andrew Gettelman** (2026-09-10): What system? A diagram would help here. It's not clear what you really mean by this (A diagnostic language?) Several 'systems' are described above, and of different types. 

#### C28 · line 152

- [x] addressed — Verbs replaced with plain ones: the host model "checks every name and operation in the tree against a list of operations it supports, and translates the tree into a graph of its existing compiled diagnostics, i.e., C++ routines already in the model that compute derived fields from other fields".

> syntax tree, and the host model validates it against a vocabulary it owns and lowers it onto its existing compiled diagnostics.

- **Andrew Gettelman** (2026-09-10): strange verbs are being used here, I think first the first time. 'Validates', 'lowers'? what are 'existing compiled diagnostics'?

#### C29 · line 152

- [x] addressed — "Lower" is removed throughout and replaced with "translate"; "lowered graph" is now "diagnostic graph".

> lowers

- **Robert Jacob** (2026-09-10): This verb is doing a lot throughout this paper and its not clear what process its representing.
- **Naser Mahfouz** (2026-09-10): good point; lowering is going from higher level (parsed strings) to lower level (compiled diags), but it may be a confusing term to use (we do use it in the code fwiw) so I will try to find a better verb or describe it better in the next draft
- **Jeffrey Johnson** (2026-09-10): We could say that the parser turns the expression string into a graph representing the expression, which is then "interpreted" and "evaluated" by a component. Just one idea.
- **Robert Jacob** (2026-09-11): That would be better for a climate modeling readership.

#### C30 · line 153

- [x] addressed — Clarified: level selection and vertical interpolation are expression operators. Horizontal regridding is not, because it is already a stream setting.

> vertical

- **Adam Varble** (2026-09-21): not horizontal?
- **Adam Varble** (2026-09-21): Is this because the calculations are node by node?

#### C31 · line 157

- [x] addressed — Added a scope paragraph to Contributions. Expressions can see every field registered with the field manager: the prognostic state, inter-process fields, and other diagnostics and expressions. They cannot see quantities local to a parameterization (e.g. a single microphysics rate, or a rate before a fixer); exposing one means registering it as a field, a source change made once per input. Andrew's point (hard-coded output-ready fields, configurable operators) is now stated explicitly.

> not require a review and a merge

- **Andrew Gettelman** (2026-09-10): This only works if you are operating on fields which are available at a level the system can see. Lots of work happens in the model in places where variables are calculated and operated on, but if never requested for output are simply then immediately thrown out. Would the system enable you to find something you wanted not in the model state? Like part of a microphysical process rate calculation, or a process rate that is immediately modified by a conservation check. How would you find the right variable in memory at the right time in the iteration loop? This is why we 'hard code' diagnostic/output ready fields. The operators on those fields can be flexible and configurable as you suggest. 

#### C32 · line 158

- [x] addressed — Same scope paragraph as C31: expressions see what is registered with the field manager at the end of the step, not values local to a parameterization, which need a one-time source change to register. The Discussion repeats this for users.

> at the end of the step 

- **Andrew Gettelman** (2026-09-10): See previous comment: what about non-state variables that don't exist at the end of a step. 
- **Adam Varble** (2026-09-21): I have the same question.

#### C33 · line 158

- [x] addressed — Now "the model's in-memory fields". Field is defined in Sect. 2 and Table 1.

> live \texttt{Field} objects

- **Andrew Gettelman** (2026-09-10): Again, a different term. 

### 2 Design and implementation

#### C34 · line 190

- [x] addressed — Every symbol in Eq. 2 is now defined right after the equation.

>  Y = \mathcal{A}_t\,\mathcal{R}_\text{h}\,\mathcal{R}_\text{v}\,\mathcal{D}_\text{e}[X(t)],

- **Andrew Gettelman** (2026-09-10): You start using these terms below without defining them. 

#### C35 · line 194

- [x] addressed — Defined: the diagnostic stage that evaluates the requested expressions.

>  $\mathcal{D}_\text{e}$

- **Andrew Gettelman** (2026-09-10): What is this?

#### C36 · line 197

- [x] addressed — Both terms defined (persistence boundary in Sect. 1; "lowering" replaced by "translation" and explained).

> persistence boundary and names, at the lowering stage

- **Andrew Gettelman** (2026-09-10): persistence boundary and lowering stage are not clearly defined.

#### C37 · line 199

- [x] addressed — The three sentences are deleted. Fig. 1 is redrawn to separate one-time setup from per-step evaluation, as Luca suggested.

> I'm not sure the last 3 sentences make a lot of sense

- **Andrew Gettelman** (2026-09-10): Agreed. They do not. 

#### C38 · line 227

- [x] addressed — Explained: the only difference is whether the result is written. warm_T could go under field_names, and conditionals don't need an alias.

>  aliases:

- **Andrew Gettelman** (2026-09-10): what is the difference between an alias and a field name? Could warm_T be a field name also? or conditionals require it to be an alias?

#### C39 · line 230

- [x] addressed — It wasn't a flux. The example is now `rho_air := p_mid/(Rair*T_mid)` (ideal-gas density). The constants list was also fixed: `Rgas` in EAMxx is the universal gas constant per kmol, so `Rair` and `gravit` are named instead.

> q_flux         := (qc+qv)*p_mid

- **Adam Varble** (2026-09-21): Is this meant to be an accurate flux expression? If so, and if p_mid is pressure, then shouldn't p_mid be a velocity?

#### C40 · line 249

- [x] addressed — Added: every field (model variable, alias or written expression) has a name, used to look it up, and a contract, used to check operations on it.

> contract $\sigma$

- **Andrew Gettelman** (2026-09-10): how is the contract related to the alias/field name?

#### C41 · line 289

- [x] addressed — Paragraph rewritten step by step, with AST and tokenizing defined, and pointed at Figs. 1 and 2.

> A request reaches the output manager as a string, and the manager splits an optional \texttt{name :=} prefix, tries the remainder through \dexpr, which tokenizes and parses it; the AST is then validated against the model's registry.

- **Andrew Gettelman** (2026-09-10): I don't really know what this means. Diagram please?  What is AST? Is the request an alias above? I still don't know what \dexpr is. A piece of code? What does 'tokenize' mean here?

#### C42 · line 290

- [x] addressed — Defined ("the outermost operation"), also in Table 1.

> root node 

- **Andrew Gettelman** (2026-09-10): What is this? Only place it appears in this document. No idea. 

#### C43 · line 290

- [x] addressed — Explained as "the routine that builds a diagnostic from its name".

> factory

- **Andrew Gettelman** (2026-09-10): Again, what is a factory?

#### C44 · line 291

- [x] addressed — Removed; the sentence now says the graph is built by resolving names.

> graph object

- **Andrew Gettelman** (2026-09-10): Also a unique term.

#### C45 · line 295

- [x] addressed — Changed to "layer".

> phase

- **Andrew Gettelman** (2026-09-10): What is a phase? Also unique word here. Maybe 'layer'?

### 3 Demonstrations › Verification and computational cost

#### C46 · line 322

- [x] addressed — The separate verification subsection is gone. Its checks are summarized in the preamble of Sect. 3 and in each demonstration, `shift` and `tend` are defined in Table 2 before they are used, and the restart behavior of `shift` is stated in Table 2 (invalid until its input is first computed, also after a restart).

> identical \texttt{shift} and \texttt{tend} output over all eight common windows

- **Andrew Gettelman** (2026-09-10): Again, you just introduced a bunch of terms. 

#### C47 · line 323

- [x] addressed — Diagnostic graph is defined in Table 1 and used consistently.

> diagnostic graph

- **Andrew Gettelman** (2026-09-10): First use of this term. 

### 3 Demonstrations › Doubly periodic profile and moments

#### C48 · line 330

- [x] addressed — Panels are labeled (a)–(c) by experiment. Fig. 3 was regenerated on 2026-10-11 from `fig/make_fig11_demonstrations.py` without the machinery row, which Fig. 1 now covers: three columns, one per experiment.

> \begin{figure*}[t]

- **Andrew Gettelman** (2026-09-10): The figure represents all three experiments right? Label them as such. Maybe move the machinery column to a different figure (schematic). then you have 3 columns, one fore each experiment....

#### C49 · line 335

- [x] addressed — Alias is now defined in Table 1 and Sect. 2, before the figure.

> An alias --- built, usable by name, never written

- **Andrew Gettelman** (2026-09-10): now you explain what an alias is!

#### C50 · line 335

- [x] addressed — Fig. 3 regenerated on 2026-10-11. Nothing is colour-coded any more: aliases are boxed (Luca's suggestion), all card text is one ink, both doubly periodic profiles are one colour on separate axes, and the cloudy/all-sky pair differs in line style as well as hue. Axis labels use overbar notation instead of `Tcolmean_sq`-style names (Luca).

> a written field is set in the color of what it produced, so no panel needs a separate legend.

- **Andrew Gettelman** (2026-09-10): The blues are similar. 

### 3 Demonstrations › Conditional high-cloud products

#### C51 · line 359

- [x] addressed — The text now defines the configuration: a one-day global atmosphere-only simulation with prescribed sea surface temperature and sea ice on the ne4pg2 grid (384 columns), 128 levels, one-hour step, 12 h averages. The Fig. 3 caption says panel (b) is the first 12 h of a run from the model's default initial condition. (Run record: rev3 `E18.cess2`, `F2010-SCREAMv1`.)

> The second experiment is a one-day instance of the conditional high-cloud workflow 

- **Andrew Gettelman** (2026-09-10): This is not DPSCREAM anymore right? So define what model configuration it is.

### 3 Demonstrations › Surface-oscillation temporal composition

#### C52 · line 371

- [x] addressed — Defined b_t = f_t − f_{t−1} and wrote the product out in terms of f_t, f_{t−1} and f_{t−2} (Eq. 6), with the second difference b_t − b_{t−1} in the text. The text says what a negative product means and how the fraction of negative steps measures reversals.

> exercise temporal composition

- **Andrew Gettelman** (2026-09-10): I'm very confused by your notation here and the multiple levels. Can you write it out in terms of f _t - f_(t+1) and show how the product works in the text? 

#### C53 · line 379

- [x] addressed — Names now match Fig. 3c: bt1 and bt_sign_reversal, used consistently.

> bt := f - f.shift(time=1)

- **Andrew Gettelman** (2026-09-10): you use b not bt in the text

#### C54 · line 386

- [x] addressed — The text now says "purpose-built C++ kernels", and kernel is defined in Table 1.

> compiled kernels

- **Andrew Gettelman** (2026-09-10): what is a compiled kernel?

#### C55 · line 388

- [x] addressed — One step per `shift`. The text now explains that `bt1.shift(time=1)` reaches f_{t-2} because each shift stores its own operand. This relies on diagnostics being evaluated every step (averaged streams).

> one-step history

- **Andrew Gettelman** (2026-09-10): How many steps are available?

### 4 Summary and discussion

#### C56 · line 399

- [x] addressed — Both points added to the Discussion: (1) a process rate not already a field still needs a source change to register it; (2) an expression is written at the frequency of its own stream, so it can be written every step while other output is daily or monthly.

> expressions are evaluated at the end of the time step and inside the output path, so they reach model state before the reductions that would destroy it but not between two parameterizations.

- **Adam Varble** (2026-09-21): This is a key point for a user such as myself. You can reduce output for calculations using current output, but if you want to use a variable (e.g., a process rate from a parameterization) not possible in current output, you still need to change the source code to make sure you can grab it for calculations at the end of the time step.
- **Adam Varble** (2026-09-21): Also, it wasn't clear to me whether diagnostics can be saved for output at time step frequency even if traditional output isn't saved and outputted that frequently. That would be useful.

#### C57 · line 401

- [x] addressed — Sentence removed, as Peter suggested. Sect. 3 says each experiment is cut down to the duration and resolution its operators need, and that each is checked against an every-step reconstruction from the same run.

> they reproduce neither the integrations nor the conclusions of the studies they are drawn from.

- **Peter Caldwell** (2026-09-14): I don't understand what this means - aren't the inline vs offline results statistically identical? If your test cases aren't from production runs just because you didn't bother to do bigger runs, I don't think this sentence is worth including.

#### C58 · line 404

- [x] addressed — "Kernelizer" replaced by "kernel fusion", with an explanation.

> kernelizer

- **Andrew Gettelman** (2026-09-10): what is a kernelizer? Sounds like something from ACME to vaporize a road runner. 

#### C59 · line 404

- [x] addressed — Now "diagnostic graph", which is defined in Table 1.

> lowered graph

- **Andrew Gettelman** (2026-09-10): As Rob said: strange usage here of 'lower'. And graph is never defined. 

## Appendix: unresolved tracked changes

Grouped by line and author. `+` is an insertion (already present in the pushed text), `−` a deletion (already absent from it). Accept or reject them in Overleaf's review panel; if rejected there, the next sync will undo them in the repo.

| line | section | author | date | changes |
|---|---|---|---|---|
| 78 | Abstract | Xylar Asay-Davis | 2026-09-13 | +“expression” −“express” |
| 97 | 1 Introduction | Robert Jacob | 2026-09-10 | +“possible” −“available” +“are” −“is” +“ and” +“which ones are output is determined at runtime. But adding a new variable ” −“and” +“done” −“changed” +“needed” −“inspired” +“as part of” −“by” +“for” −“by” |
| 98 | 1 Introduction | Robert Jacob | 2026-09-10 | +“The final output set” −“It” |
| 101 | 1 Introduction | Adam Varble | 2026-09-16 | +“s” |
| 102 | 1 Introduction | Adam Varble | 2026-09-16 | +“global ” +“typically ” |
| 103 | 1 Introduction | Adam Varble | 2026-09-16 | +“s” +“evolution” −“structure” |
| 105 | 1 Introduction | Adam Varble | 2026-09-16 | +“se requirements” −“y” +“is ” |
| 106 | 1 Introduction | Adam Varble | 2026-09-16 | +“differs ” −“that for which ” −“is ” |
| 107 | 1 Introduction | Adam Varble | 2026-09-16 | +“the” −“when it is computed: in what” +“ing of” −“relative to ” −“,” −“must also ” |
| 109 | 1 Introduction | Adam Varble | 2026-09-17 | +“as ” |
| 109 | 1 Introduction | Robert Jacob | 2026-09-10 | −“reads” |
| 130 | Related works | Robert Jacob | 2026-09-10 | +“D” −“Model-integrated d” +“ integrated into source code” |
| 130 | Related works | Adam Varble | 2026-09-21 | −“ with” |
| 131 | Related works | Adam Varble | 2026-09-21 | −“ what” −“ is” −“ somebody” +“d” −“s” |
| 133 | Related works | Adam Varble | 2026-09-21 | −“multi-model ” +“ grid ” −“-” +“multi-model ” |
| 135 | Related works | Adam Varble | 2026-09-21 | +“ given sufficient output” |
| 136 | Related works | Adam Varble | 2026-09-21 | +“full ” |
| 153 | Contributions | Adam Varble | 2026-09-21 | +“vertical ” |
| 198 | 2 Design and implementation | Adam Varble | 2026-09-21 | +“the” −“which” |
| 199 | 2 Design and implementation | Adam Varble | 2026-09-21 | +“those worked from in” −“what” −“ then works from” |
| 218 | 2 Design and implementation | Adam Varble | 2026-09-21 | +“and ” |
| 363 | Conditional high-cloud products | Adam Varble | 2026-09-21 | +“ly resolved” |
