# Melanocyte Regeneration in Vitiligo

### Why does repigmentation remain incomplete even when autoimmune inflammation is being treated?

**Primary focus:** Incomplete repigmentation, melanocyte precursor biology, inflammatory signalling, and the skin microenvironment

---

## 1. Project overview

Vitiligo is an acquired depigmenting skin disorder in which pigment-producing cells called **melanocytes** are lost from areas of skin, producing white patches. Autoimmune mechanisms are central to disease activity, but reducing inflammation does not necessarily guarantee complete or durable repigmentation. Successful repigmentation also requires a source of melanocytes, their activation and migration into the epidermis, their survival and differentiation, and a tissue environment that supports pigment production.

This project will use a small, carefully selected set of public human transcriptomic datasets to investigate the relationship between immune activity and regenerative biology in vitiligo. Rather than merging every dataset into one expression matrix, results will be connected through shared genes, pathway-level signatures, and-where single-cell data are used-cell-type-specific patterns.

## 2. Main research question

**Which molecular and cellular features are associated with successful versus incomplete repigmentation in vitiligo, and do the data point more strongly to persistent inflammatory pressure, impaired melanocyte regeneration, an unfavourable skin-cell environment, or an interaction between them?**

### Objectives

1. Identify genes and pathways associated with responding and non-responding vitiligo lesions.
2. Derive a melanocyte-precursor regeneration signature and a separate keratinocyte-support signature.
3. Test whether these signatures are associated with response status in the primary lesion dataset.
4. Use single-cell RNA-seq to determine which cell populations express the key inflammatory and regenerative signals.

### Working hypothesis

Incomplete repigmentation may reflect a combination of **ongoing immune pressure**, **limited availability or activity of melanocyte precursors**, and **a tissue niche that does not adequately support melanocyte migration, survival, differentiation, or melanogenesis**. This is a hypothesis to test—not a predetermined result.

---

## 3. Biological background: what is vitiligo?

Melanocytes produce melanin, the pigment that contributes to skin colour. In vitiligo, immune-mediated damage and loss of melanocytes lead to depigmented patches. The disease is often described as autoimmune, but the persistence of depigmented skin also raises a regenerative question: after melanocytes have been lost, can enough new melanocytes repopulate the epidermis?

### Mechanisms relevant to this project

#### 3.1 Immune-mediated melanocyte damage

Autoreactive CD8+ T cells can recognise melanocyte-associated antigens and contribute to melanocyte injury. **Interferon-gamma (IFN-γ)** is an important inflammatory signal in this process.

#### 3.2 IFN-γ–CXCL9/CXCL10–CXCR3 signalling

IFN-γ can stimulate skin cells, including keratinocytes, to express chemokines such as **CXCL9** and **CXCL10**. These signals help recruit CXCR3-expressing T cells into skin and can reinforce local inflammation. This pathway will be used as an inflammatory signature to investigate—not as proof on its own that a lesion is actively destroying melanocytes.

#### 3.3 Melanocyte precursor reservoir and migration

Melanocyte precursors in the hair-follicle bulge can contribute to epidermal repigmentation. They must become activated, proliferate where appropriate, migrate towards depigmented epidermis, survive, differentiate, and produce melanin. Differences in these steps may help explain why lesions do not respond equally to treatment.

#### 3.4 Regeneration and tissue-niche signalling

Several pathways are relevant to melanocyte precursor behaviour and pigmentation:

- **WNT/β-catenin signalling**, including CTNNB1-related biology, is implicated in precursor activity and repigmentation.
- **RHO-GTPase signalling** is relevant to cell migration and melanocyte responses.
- **cAMP signalling and PDE4B** may be associated with differences between responding and non-responding lesions.
- **Keratinocyte state and senescence** may influence whether the surrounding epidermis supports regeneration.
- Signals from keratinocytes and other niche-associated cells may support or constrain melanocyte precursor activity.

These mechanisms are supported to different degrees by prior studies. Their contribution will be assessed using the selected datasets rather than assuming that all mechanisms are present in every sample.

---

## 4. Selected datasets

The project is intentionally restricted to **two core datasets**, with a third dataset for cell-type context if resources allow. A fourth dataset is listed as an optional extension. These datasets are free to access; the practical costs are storage, computing, and time.

| Planned use | Accession and link | Samples | Assay / material | Approximate processed download size | Role in this project |
|---|---|---:|---|---:|---|
| **Core 1 - primary response comparison** | [GSE256271](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE256271) | 8 samples from 4 paired patients: responding and non-responding lesions | Whole-transcriptome TempO-Seq from FFPE epidermal scrapes | ~994 KB for the listed compressed expression table | Identify molecular features associated with response versus non-response; score inflammatory and regenerative pathways |
| **Core 2 - regeneration signature** | [GSE150954](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE150954) | 24 samples: 12 melanocyte precursor samples and 12 keratinocyte precursor samples | Bulk RNA-seq of laser-captured hair-follicle-bulge precursor populations, treated vs untreated | ~3.9 MB across two listed compressed comparison tables | Derive a melanocyte-precursor regeneration signature and separately assess keratinocyte-support signals |
| **Optional core extension - cell-type context** | [GSE203262](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE203262) | 12 samples from 6 analyzable patients, matched lesional and non-lesional skin; one of seven original patient pairs was excluded due to insufficient cells | 10x single-cell RNA-seq | ~94.6 MB across the six listed processed archives (download sizes may change) | Attribute relevant signals to cell types; examine cellular states and potential cell–cell communication |
| **Optional extension - direct IFN-γ response** | [GSE129921](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE129921) | 12 samples | RNA-seq of cultured human melanocytes exposed to PBS, DMSO, or IFN-γ | - | Derive or inspect an IFN-γ response signature if a more specific inflammatory comparison is needed |

**Note:** Sizes above refer to selected processed supplementary files as listed on GEO, not to all files associated with an accession. Raw sequencing files are not needed for the initial analysis. GSE256271 uses TempO-Seq and should not be described as conventional bulk RNA-seq. GSE129921 is described in its GEO design as RNA-seq on cultured melanocytes; despite the series title, it is not the single-cell dataset planned for cell-type analysis.

### Why these datasets?

- **GSE256271** directly matches the key outcome of interest: repigmentation response versus non-response after NB-UVB treatment.
- **GSE150954** focuses on melanocyte and keratinocyte precursors in the hair-follicle bulge, making it useful for constructing regeneration-related signatures.
- **GSE203262** can provide cell-type-level context, but it needs more memory and analysis effort; it will be added after the two core analyses.
- **GSE129921** is optional and will be used only if the first analyses show that a separate IFN-γ signature would improve interpretation.

---

## 5. Analysis plan: how the datasets will be connected

### Step 1 - Metadata and file inspection

For each selected accession, record sample identifiers, tissue/material, treatment or response group, patient pairing, assay type, file format, and processing status. Inspect the columns and contents of the processed files before selecting statistical methods.

### Step 2 - Primary response analysis: GSE256271

- Compare responding and non-responding lesions while preserving the four-patient pairing wherever the available data support it.
- Inspect the supplied normalized expression table and existing differential-expression results.
- Rank genes and assess relevant pathways, including IFN-γ/inflammatory signalling, WNT/β-catenin, cAMP/PDE4B, senescence, melanocyte markers, and melanogenesis.
- Because there are only four patient pairs, report effect sizes, direction of change, and uncertainty. Treat findings as exploratory and hypothesis-generating.

### Step 3 - Regeneration signature: GSE150954

- Analyze the melanocyte-precursor (MCBG) comparison separately from the keratinocyte-precursor (KCBG) comparison.
- Identify genes and pathways associated with treated versus untreated precursor samples, guided by the original study design and the contents of the processed tables.
- Create two conceptually distinct gene sets: (1) melanocyte regeneration/pigmentation and (2) keratinocyte support/niche signalling.
- Check the direction and meaning of the comparison before assigning a gene to a “higher in treated” or “higher in untreated” group.

### Step 4 - Signature integration between GSE150954 and GSE256271

- Score or compare the regeneration and keratinocyte-support signatures in the primary response dataset.
- Ask whether the signatures are stronger or weaker in responding versus non-responding lesions.
- Compare these results with inflammation, senescence, WNT/β-catenin, and cAMP pathway signals.
- Interpret associations cautiously: the datasets differ in sample type and assay, so pathway-level or gene-signature integration is more appropriate than merging their expression matrices.

### Step 5 - Optional single-cell analysis: GSE203262

- Load the processed single-cell files rather than starting with raw FASTQ files.
- Perform quality checks, use or verify cell annotations, and summarise gene expression by cell type.
- Use patient-aware pseudobulk or other appropriate patient-level methods for group comparisons; individual cells are not independent biological replicates.
- Map the candidate genes and signatures from Steps 2–4 to cell types such as keratinocytes, immune populations, fibroblasts, and melanocyte-lineage cells where present and adequately represented.
- Explore cell–cell communication only after the cell annotations and candidate signals are credible.

### Step 6 - Optional IFN-γ signature: GSE129921

If needed, compare IFN-γ-exposed cultured melanocytes with suitable controls, taking account of the study's treatment groups and sample design. Use the resulting signature as a targeted comparison against the lesion-level and cell-type-level findings. This dataset is an in-vitro response model, not a substitute for patient-skin evidence.

### Integration principle

**We will not concatenate all datasets into one matrix.** They differ in assay, sample type, tissue context, and experimental design. We will integrate evidence through shared gene identities, pathway enrichment, gene-set scores, cell-type attribution, and consistency of effect direction. Additional datasets will be selected only if they answer a specific unresolved question.

---

## 6. Planned outputs

1. A sample-metadata sheet and data provenance log for every dataset used.
2. A ranked list of response-associated genes and pathways from GSE256271.
3. A melanocyte-regeneration signature and a separate keratinocyte-support signature from GSE150954.
4. A comparison showing whether these signatures differ between responding and non-responding lesions.
5. If GSE203262 is analyzed, a cell-type summary of where the key signals are observed.
6. Clear figures and tables showing effect direction, uncertainty, and agreement or disagreement across datasets.

Potential figures include: (i) paired response comparison, (ii) pathway/signature score comparison, (iii) regeneration-signature overlap, and (iv) cell-type attribution if the single-cell analysis is completed.

---

## 7. Methods and tools under consideration

Final tool choice will depend on the format of each GEO file and whether it contains raw counts, normalized expression, or already-computed differential-expression statistics.

- **R:** `limma`, `edgeR` or `DESeq2` where their input assumptions are met; `fgsea` or `clusterProfiler` for pathway analysis.
- **Single-cell:** `Seurat` in R or `Scanpy` in Python, with patient-aware pseudobulk or other appropriate sample-level comparisons.
- **Visualisation and reporting:** `ggplot2` in R or `pandas`/`matplotlib` in Python.
- **Execution environment:** begin with compact processed files and a notebook-based workflow; use Google Colab or another suitable cloud notebook if local storage or memory is insufficient. GPU acceleration is not expected to be necessary for the core analyses.

These are planned tools, not a claim that the analyses have already been run. The repository will record final software choices and versions once the workflow is implemented.

---

## 8. Limitations and interpretation

- GSE256271 has only four paired patients. It is suitable for exploratory comparisons and hypothesis generation, not for building or validating a reliable machine-learning predictor.
- GSE150954 compares precursor populations from treated and untreated vitiligo skin; its design should not be treated as identical to a within-patient responder/non-responder experiment.
- GSE203262 is a small single-cell cohort. Cell counts do not replace the number of independent patients.
- Different platforms and sample types introduce technical and biological differences. Pathway-level triangulation is more defensible than direct merging of expression values.
- A gene signature is evidence of an expression pattern, not proof of a causal mechanism or clinical response.
- The project will distinguish previously reported findings, results reproduced from public data, and new exploratory observations.

---

## 9. Suggested repository structure

As the project develops, files may be organised as follows:

```text
.
├── README.md
├── data/
│   └── README.md              # accession metadata and download instructions; no large raw files
├── notebooks/
│   ├── 01_gse256271_response_analysis.ipynb
│   ├── 02_gse150954_regeneration_signature.ipynb
│   └── 03_gse203262_cell_type_analysis.ipynb  # optional
├── scripts/                   # reusable analysis scripts
├── results/
│   ├── tables/
│   └── figures/
├── references.bib
├── environment.yml            # or renv.lock for an R-first workflow
└── .gitignore
```

---

## 10. Data sources

- [GSE256271 - Vitiligo non-responding lesions after NB-UVB](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE256271)
- [GSE150954 - Melanocyte precursors and RHO-GTPase, KCTD10, and CTNNB1 signalling](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE150954)
- [GSE203262 - Single-cell RNA-seq of matched lesional and non-lesional skin](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE203262)
- [GSE129921 - RNA-seq of cultured melanocytes exposed to IFN-γ and controls](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE129921) *(optional)*

Data remain attributed to their original submitters and publications. This repository documents a secondary analysis of public data and is not affiliated with the original study authors unless explicitly stated.

---

## 11. Key references

1. Goldstein NB, et al. **Vitiligo non-responding lesions to narrow band UVB have intriguing cellular and molecular abnormalities that may prevent epidermal repigmentation.** *Pigment Cell & Melanoma Research*. 2024;37(3):378–390. [https://doi.org/10.1111/pcmr.13160](https://doi.org/10.1111/pcmr.13160) 
2. Goldstein NB, et al. **Melanocyte Precursors in the Hair Follicle Bulge of Repigmented Vitiligo Skin Are Controlled by RHO-GTPase, KCTD10, and CTNNB1 Signaling.** *Journal of Investigative Dermatology*. 2021;141(3):638–647.e13. [https://doi.org/10.1016/j.jid.2020.07.016](https://doi.org/10.1016/j.jid.2020.07.016) 
3. Shiu J, et al. **Multimodal analyses of vitiligo skin identify tissue characteristics of stable disease.** *JCI Insight*. 2022;7(13):e154585. [https://doi.org/10.1172/jci.insight.154585](https://doi.org/10.1172/jci.insight.154585) 
4. Frisoli ML, Essien K, Harris JE. **Vitiligo: Mechanisms of Pathogenesis and Treatment.** *Annual Review of Immunology*. 2020;38:621–648. [https://doi.org/10.1146/annurev-immunol-100919-023531](https://doi.org/10.1146/annurev-immunol-100919-023531) 
5. Liu L, et al. **The IFN-γ–CXCL9/CXCL10–CXCR3 axis in vitiligo: Pathological mechanism and treatment.** *European Journal of Immunology*. 2024;54(4):2250281. [https://doi.org/10.1002/eji.202250281](https://doi.org/10.1002/eji.202250281) 

---

## Project status

**Current stage:** Planning and dataset prioritisation.
