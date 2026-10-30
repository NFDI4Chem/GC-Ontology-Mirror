# Gainesville Core Ontology (GC) — NFDI4Chem Mirror

This repository contains a mirror of the Gainesville Core Ontology (GC), developed by Chemical Semantics, Inc. (published 2015, version 0.7.0). We created this repo to ingest the ontology for research purposes within the [NFDI4Chem Terminology Service](https://terminology.nfdi4chem.de/ts/ontologies/gc) and the TIB Terminology Service, since the original IRI (`http://purl.org/gc/`) does not resolve anymore.

Beyond mirroring the ontology source, this README documents the historical context we were able to reconstruct about GC — its provenance, creators, dependencies, and current state — to aid future preservation and reuse efforts.

---
## Provenance & Historical Context

### What is GC?

From the ontology's own metadata:

> **Title:** GNVC: Gainesville Core Ontology — standard for publishing results of computational chemistry.
>
> **Description:** This ontology aims at complete description of typical Computational Chemistry experiment. Gainesville Core describes:
> - Molecular Publications
> - Molecular Systems
> - Molecular Calculations
>
> Molecular Systems contains Molecules. The Molecules may have Residues (for biopolymers and polymers). Molecular Calculations contain Initial Data and Results. The Initial Data may have Methods, Basis Sets, Functionals, etc. The Results may have Energies, Wave Functions and Spectra, etc.

GC formalizes the meaning of terms used in the computational chemistry domain and provides human-readable definitions that disambiguate term usage, along with logical axioms that allow automated reasoning. It enables consistency checking, classification, and querying over the knowledge landscape of computational chemistry. It also serves as a cross-mapping hub for other chemistry ontologies such as ChEBI.

### Creators & Affiliation

- **Chemical Semantics, Inc.** (listed as `dcterms:creator` in the ontology metadata)
- **Mirek Sopek** — according to his [CV](https://sopek.net/mirek/Mirek%20BIO_en.pdf), president of Chemical Semantics, Inc. between 2013 and 2016.
- **Neil S. Ostlund** — co-author with Sopek on the below listed publications, both affiliated with Chemical Semantics Inc.

### PURL.org Registration

| Field | Value |
|-------|-------|
| Domain | `purl.org/gc` |
| Redirect type | partial |
| Target | `http://ontologies.makolab.com/gc/gc/` |
| Created | 2013-03-27 02:48:46 |
| Modified | 2013-04-03 09:20:50 |

The PURL redirect points to `ontologies.makolab.com`, which is no longer online.

### Relevant Publications

- **Wang et al. (2017)** — [*Computational Chemistry Data Management Platform Based on the Semantic Web*](https://doi.org/10.1021/acs.jpca.6b10489): Proposes the XML-based data publishing standard "Common Standard for eXchange (CSX)." Contains the most detailed documentation of GC available (beyond the source code itself). Key excerpt:

  > In the data publishing process, CSX serves as a structured data container. Data and metadata are annotated using the element definitions in the CSX schema. However, the XML encoded data in CSX does not have a semantic sense, since it has no connection with semantic meaning as defined in the Gainesville Core (GC) ontology. Therefore, we convert a CSX file into a JSON-LD file by the use of an XML Stylesheet Language Transformation file (XSLT). The transformation integrates the computational chemistry annotated in CSX with the semantic meanings described in the GC ontology.

  The paper also states: *"We will change the GC repository permission on our GitHub account so that the public users can submit their pull requests."* — This never appears to have happened; no such GitHub repository can be found.

- **Ostlund & Sopek (2013)** — SWAT4LS poster: [*Applying the Semantic Web to Computational Chemistry*](https://ceur-ws.org/Vol-1114/Poster_Ostlund.pdf): is about "a proto type test bed that enables computational chemists to publish the results of their computations (for example: structure, energies and wave functions of Ab Initio calculations) on servers (powered by semantic triple stores) holding RDF data." Key excerpt:

  > For the purpose of definition of shared type system across all published files on the portal we have created a new web ontology named Gainesville Core. The Gainesville Core ontology is identified by IRI: http://purl.org/gc
  > Gainesville Core defines the following types:
    >1. theoretical models (or experiment foundations) used in computations
    >2. molecular systems (as collections of atoms and molecules)
    >3. molecular arrangements which can describe molecular system subparts (like monomers) or system evolutions in time or in phase space (different configurations of the system)
    >4. types related to computations and specific features of the theoretical model of the system (such as computation method and technology)
    >5. types related to results of computations (like energies, orbitals etc.)
  >
  >The Gainesville Core ontology is currently undergoing thorough changes. There is a new update that will soon replace the current content of http://purl.org/gc.

### Current State of Availability

| Resource | Status |
|----------|--------|
| Original source (`ontologies.makolab.com`) | Offline |
| PURL (`http://purl.org/gc/`) | Non-resolving |
| Last available source code (Wayback Machine) | [gc07.owl snapshot (2022-10-05)](https://web.archive.org/web/20221005233201fw_/http://ontologies.makolab.com/gc/gc07.owl) |
| Last available documentation (Wayback Machine) | [gc.html snapshot (2022-05-31)](https://web.archive.org/web/20220531133239/http://ontologies.makolab.com/gc/gc.html) |
| GitHub repository (mentioned in paper) | Never made public |

---
## Ontology Metadata (from source)

```xml
<owl:Ontology rdf:about="http://purl.org/gc/">
  <owl:imports rdf:resource="http://data.qudt.org/qudt/owl/1.0.0/unit.owl"/>
  <owl:imports rdf:resource="http://www.daml.org/2003/01/periodictable/PeriodicTable.owl"/>
  <owl:imports rdf:resource="http://bfo.googlecode.com/svn/releases/2012-07-20-graz/owl-group/bfo.owl"/>
  <owl:versionInfo>0.7.0</owl:versionInfo>
  <rdfs:comment xml:lang="en">An ontology for publishing results of computational chemistry.</rdfs:comment>
  <dcterms:creator xml:lang="en">Chemical Semantics, Inc.</dcterms:creator>
  <cc:license rdf:resource="http://creativecommons.org/licenses/by/3.0/"/>
  <rdfs:isDefinedBy rdf:resource="http://chemicalsemantics.com/"/>
  <dcterms:title xml:lang="en">GNVC: Gainesville Core Ontology - standard for publishing results of computational chemistry.</dcterms:title>
  <dc:created>2015-03-04</dc:created>
  <rdfs:label xml:lang="en">Gainesville Core Ontology</rdfs:label>
</owl:Ontology>
```

---
## Import Dependencies & Resolution

GC declares three `owl:imports`. Their current resolvability:

| Import | Status | Notes |
|--------|--------|-------|
| `http://data.qudt.org/qudt/owl/1.0.0/unit.owl` | **404** | Outdated QUDT version; last working snapshot available via Wayback Machine |
| `http://bfo.googlecode.com/svn/releases/2012-07-20-graz/owl-group/bfo.owl` | **Dead** | Google Code is gone; version IRI still resolves via OBO Foundry |
| `http://www.daml.org/2003/01/periodictable/PeriodicTable.owl` | Resolves | Not commented out in this mirror |

### How we resolved the broken import statements

#### BFO

The GC references the "2012-07-20-graz" release of BFO using an unresolving URL. However, the correct version IRI `http://purl.obolibrary.org/obo/bfo/2012-07-20/bfo.owl` still resolves to the artifact on GitHub. To verify equivalence:

```shell
curl -o gc_reference_bfo_v2012-07-20-graz.owl https://web.archive.org/web/20150402100424/http://bfo.googlecode.com/svn/releases/2012-07-20-graz/owl-group/bfo.owl &&
curl -L -o github_bfo_v2012-07-20-graz.owl http://purl.obolibrary.org/obo/bfo/2012-07-20/bfo.owl &&
robot diff --left gc_reference_bfo_v2012-07-20-graz.owl \
           --right github_bfo_v2012-07-20-graz.owl \
           -f markdown -o bfo_in_gc_diff.md
```

The diff ([bfo_in_gc_diff.md](bfo_in_gc_diff.md)) shows only annotation property changes, no semantic differences. It is therefore safe to replace the IRI in the GC `owl:import` statement.

**Suggested fix:** Replace with `http://purl.obolibrary.org/obo/bfo/2012-07-20/bfo.owl`

#### QUDT

The PURL `http://data.qudt.org/qudt/owl/1.0.0/unit.owl` returns a 404. The last working snapshot is available via the Wayback Machine: https://web.archive.org/web/20220121082231/http://data.qudt.org/qudt/owl/1.0.0/unit.owl

**Suggested fix:** Replace with the Wayback Machine URL above, or mirror the QUDT module locally.

#### QUDT usage in GC

After inspecting GC with the QUDT import restored, we found that QUDT is used only minimally:
- To classify GC instances of units, e.g., `ClassAssertion(qudt:LengthUnit gc:angstrom)`
- To subclass QUDT unit kinds under `gc:AuxiliaryConcept`, e.g., `SubClassOf(qudt:LengthUnit gc:AuxiliaryConcept)`

---
## Changes Made in This Mirror

The file [`gc07_without_imports.owl`](https://github.com/NFDI4Chem/GC-Ontology-Mirror/blob/main/gc07_without_imports.owl) is identical to the [archived original](https://web.archive.org/web/20221005233201fw_/http://ontologies.makolab.com/gc/gc07.owl) except for commenting out the two `owl:imports` statements (BFO and QUDT) that caused crashes during NFDI4Chem TS indexing due to unresolvable URLs. See [lines 20–22](https://github.com/NFDI4Chem/GC-Ontology-Mirror/blob/main/gc07_without_imports.owl#L20-L22). This is the file currently used to index GC in the NFDI4Chem TS.

The fixes suggested to resolve GC's corrupt imports were implemented in [gc_v0.7.0_fixed_imports.owl](gc_v0.7.0_fixed_imports.owl). After discussing these with the community at the [5th Ontology4Chem Workshop 2026](https://doi.org/10.25798/g8yv-kf83), we might use it instead in the TS.

---
## Usage

This mirror is consumed by:
- [NFDI4Chem Terminology Service](https://terminology.nfdi4chem.de)
- [TIB Terminology Service](https://terminology.tib.eu/ts)

---
## Preservation Notes

This ontology is effectively abandoned by its creators. The original hosting infrastructure (`makolab.com`) is offline, the PURL is dead, and the promised public GitHub repository never materialized. This mirror and its documentation serve as a preservation effort for a domain ontology that represents a structured attempt at formalizing computational chemistry semantics.

