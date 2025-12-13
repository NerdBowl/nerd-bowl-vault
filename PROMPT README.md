
This is a guide to quickly create MOCs for new fields, based on a collection of sources that cover a big part of that field. 

**Prerequisites:** NotebookLM Plus & Gemini 3.0 Pro (or variants of better or equal quality)

### Overview of Steps
1. **Create overview of high level concepts** (NotebookLM)
   Create an overview of high level concepts / clusters that fully divide the sources/field in around 10-20 clusters.
2. **Extract Atomic Concepts** (NotebookLM)
   For each of the given High Level Concepts, extract all smaller atomic concepts within those clusters. Do this one-by-one.
3. **Atomic Concept Refactoring** (Gemini Thinking)
   Given a full list of all of the atomic concepts for all clusters, refactor them using Gemini. Prompt 1 and 2 lead to a very big list of atomic concepts that are very specific to clusters, with a lot of duplicates. These can be filtered, refactored, combined, grouped and discarded effectively by gemini. The resulting list should be used in step 4, concept by concept. 
4. **Atomic Writing** (Gemini Thinking)
   Write all of the atomic concepts, concept by concept. 


### Prompt 1
Replace:
- **`{FIELD_OF_STUDY}`**: e.g., "Machine Learning"
- **`{BROAD_FIELD}`**: e.g., "Computer Science"
- **`{ATOMIC_CONCEPT}`**: e.g., "Gradient Descent" (A specific Truth)
- **`{CLUSTER_EXAMPLE}`**: e.g., "Optimization Algorithms" (A Container/MOC)
- **`{FOUNDATION_CLUSTER}`**: Give an example of where to start. E.g., "Linear Algebra" or "Basic Syntax."
```
Act as a Professor in {FIELD_OF_STUDY}. Map the provided sources into a structured curriculum.

**Task:**
Identify 10-20 "Concept Clusters" (MOCs) and order them **Topologically**.
* **Topological Order:** Sequence the clusters by *pedagogical dependency*. Cluster 1 must contain the foundational knowledge required to understand Cluster 2, and so on. Start with axioms/basics; end with complex applications.

**Constraints:**
1.  **Ignore Context:** Remove all "Lecture" numbers, dates, and syllabus logistics. Extract only the *topic topology*.
2.  **Granularity:**
    * Too Broad: "{BROAD_FIELD}"
    * Too Narrow: "{ATOMIC_CONCEPT}" (Specific definition/theorem)
    * **Target:** "{CLUSTER_EXAMPLE}" (Thematic grouping of 5-20 concepts)
3.  **Field Standards:** Use standard {FIELD_OF_STUDY} terminology.

**Output:**
A Markdown table sorted by topological order:
| Sequence | Cluster Name | Logic/Prerequisites | Child Atomic Concepts (Examples) |
| :--- | :--- | :--- | :--- |
| 01 | **{FOUNDATION_CLUSTER}** | *Foundational logic needed for all subsequent topics.* | *{CONCEPT_A}, {CONCEPT_B}* |
| ... | ... | ... | ... |
| 20 | **{ADVANCED_CLUSTER}** | *Requires knowledge of [Cluster 05] and [Cluster XX].* | *{CONCEPT_X}, {CONCEPT_Y}* |
```

### Prompt 2
Replace:
- {CLUSTER_NAME}
- 
```
Act as a Data Architect. We are cataloging the **{CLUSTER_NAME}** domain.

**Goal:**
Identify every distinct **Atomic Concept** within this cluster and provide the metadata required to initialize my Obsidian notes.

**Constraints:**
1.  **Scope:** Extract ONLY concepts strictly belonging to **{CLUSTER_NAME}**.
2.  **Granularity:** Each item must be an "Atomic Truth" (a specific definition, theorem, formula, or entity).
    * *Bad:* "Basics of Probability" (Too broad)
    * *Good:* "Law of Total Probability" (Atomic)
3.  **Tags:** Assign 2-3 hierarchical tags.
    * Format: `#field/subfield/topic` (e.g., `#math/probability/theorems`).
4.  **Aliases:** crucial for linking. Include abbreviations (e.g., "CLT") and alternate names.

**Output:**
Provide a list of concepts. For each, use this exact format:

---
**Concept:** {Concept Name}
**Tags:** #{FIELD_OF_STUDY}/{CLUSTER_TAG}/{SUB_TOPIC}
**Aliases:** [{Alias 1}, {Alias 2}, {Abbreviation}]
**Description:** *A 1-sentence definition identifying exactly what this object is (e.g. "A theorem stating that...", "A variable representing...").*

---
```

### Prompt 3A
```
Act as a Senior Ontology Engineer and Domain Expert in {FIELD_OF_STUDY}.

I am providing a "Raw Inventory" of Atomic Concepts generated for an Obsidian Knowledge Graph.
**Current State:** The list contains duplicates, synonyms, overlapping concepts, and "fragments" (definitions that are too small to stand alone).
**Goal:** Refactor this list into a "Golden Set" of distinct, substantial Atomic Concepts.

**Input Data:**
You are given an attached document with a long list of concepts. 

---

**Task: Perform a 3-Pass Refactoring Analysis thorughly for all concepts in the given list.**

**Pass 1: Deduplication (Synonym Merger)**
Identify concepts that are effectively synonyms or identical entities with different names (e.g., "Cost Function" vs "Loss Function").
* *Action:* Pick the standard industry term as the "Primary," make the others "Aliases."

**Pass 2: Molecular Merger (Up-scoping)**
Identify "Fragment Concepts" that are too granular and should be merged into a parent concept.
* *Heuristic:* If Concept A is merely a component of Concept B and has no utility without B, merge A into B.
* *Example:* Merge "Numerator of Bayes" and "Denominator of Bayes" INTO "Bayes' Theorem."
* *Constraint:* Do NOT merge distinct sibling concepts (e.g., Keep "L1 Regularization" and "L2 Regularization" separate; do not merge them into "Regularization").

**Pass 3: Relevance Filtering**
Identify concepts that are too generic (e.g., "Mathematics") or outlier concepts. Mark them for deletion.

---

**Output Requirement:**
Produce a **Refactoring Table** representing your decisions. Do not generate the full descriptions yet.

| Current Concept Name | Action | Target Concept Name | Reasoning |
| :--- | :--- | :--- | :--- |
| Concept A | **KEEP** | Concept A | Unique, valid atomic concept. |
| Concept B | **MERGE** | Concept A | Concept B is just a sub-property of A. |
| Concept C | **RENAME** | Concept D | Standard industry term is Concept D. |
| Concept E | **DELETE** | N/A | Too generic/out of scope. |

**Wait for my approval of this table before generating the final list.**
```

### Prompt 3B
```
The Refactoring Table is approved.

**Task:**
Generate the **Final "Golden Set" of Concepts** based strictly on the decisions in the table above.

**Constraints for Final Output:**
1.  **Consolidated Content:** When merging concepts, ensure the `Description` and `Aliases` of the child concepts are integrated into the Target Concept.
2.  **Strict Formatting:** Use the exact format below for every item.
3.  **Tags:** Ensure tags are clean and consistent (max 3 tags per item).

**Output Format:**

---
**Concept:** {Refined Concept Name}
**Tags:** #{FIELD_OF_STUDY}/{CLUSTER}/{SUB_TOPIC}
**Aliases:** [{Alias 1}, {Alias 2}, {Merged Concept Name}]
**Description:** {A robust definition. If this is a merged concept, mention the components briefly.}
---
```

### Prompt 4
Replace:
- \[LIST OF CONCEPTS TO GENERATE\]
```
### Role
You are an expert Knowledge Architect and Polymath Data Scientist managing a high-integrity Obsidian knowledge vault. Your goal is to transform raw information into **Atomic Concepts**—universal truths that exist independently of a specific textbook or course.

### Inputs
1.  **Source Material:** Attached pdfs are given explaining (at least) the target concepts
2.  **Target Concepts:** [LIST OF CONCEPTS TO GENERATE]

### Vault Philosophy (Strict Adherence Required)
1.  **Universal Truth vs. Narrative Context:** You must decouple the *concept* from the *source*.
    * *Bad:* "Prof. Smith says gradients are like hills."
    * *Good:* "The gradient is a vector operator $\nabla$ representing the direction of steepest ascent."
    * *Context Storage:* Specific examples or metaphors used in the source text must be placed in a separate "Illustrative Examples" section, not in the definition.
2.  **Atomic Design:** Each note must be self-contained. A user should be able to understand the concept without reading the original source.

### Task
For **each** concept listed in the "Target Concepts" input, generate a comprehensive Markdown note. You must use your internal knowledge base to ensure completeness, filling in gaps if the source material is shallow, while prioritizing academic precision.

### Content Guidelines

#### 1. Metadata (YAML Frontmatter)
* **Tags:** Assign 3-5 tags.
    * *Constraint:* Think cross-disciplinarily. If the concept is "Entropy," tags should cover `#physics/thermodynamics` AND `#information-theory` if applicable.
    * *Format:* `#field/subfield/topic`
* **Aliases:** Provide a comprehensive list of synonyms, acronyms, and common naming variations (e.g., "Gaussian Distribution", "Bell Curve", "Normal Distribution").

#### 2. The "Universal Truth" (The Body)
* **Definition:** Provide the rigorous, academic definition. List necessary axioms or assumptions.
* **Completeness Check:** If the provided source is missing standard properties, edge cases, or derivations known to general theory, **add them**. You are creating the *definitive* note, not just a summary of the file.
* **Math & Notation:**
    * Use LaTeX for all math.
    * Inline math: `$x$`
    * Block math: `$$` (MUST be on its own line).
    * *Variable Definitions:* Immediately after *any* formula, you must define every variable (e.g., "Where $\alpha$ represents...").

#### 3. Properties & Dynamics
* Explain *why* this concept matters.
* List key properties (e.g., "Convexity," "Linearity") and their implications.
* Detail the "Intuition" — how should a human think about this conceptually?

#### 4. Source Context
* Create a section called `### Illustrative Examples (Source Context)`.
* Place specific examples, case studies, or unique metaphors found in the **Source Material** here. This separates the "Universal Truth" from the "Book's Narrative."

#### 5. Style & Density 
* **Prioritize High Information Density:** Ensure every sentence conveys a specific fact, relationship, or constraint.
* **Do not simplify** complex ideas for the sake of brevity; explain them with extreme precision. 
* **Zero Fluff:** Avoid conversational filler (e.g., remove "It is important to note that...", "Basically,", "In this section we see...").

### Output Structure
For each concept, output the following Markdown format exactly:

---
tags:
  - [Tag 1]
  - [Tag 2]
aliases: [[Alias 1], [Alias 2]]
status: good_enough
---

### Concept Name
*The rigorous academic definition. Axioms, theorems, and fundamental logic.*

*If applicable. Derivations, formulas, and strict variable definitions.*
$$ 
FORMULA 
$$
*Where:*
* $\alpha$: Definition...
* $\beta$: Definition...
  
#### Properties & Intuition
* **Property 1:** Explanation...
* **Property 2:** Explanation...
* **Intuition:** Deep dive into the "why".

### This is a sub-part
This is a sub-part, a slightly distinct version of the main Concept, a specific applicaiton in a field, or a slight variation. 

### Illustrative Examples (Source Context)
*Specific scenarios or narrative examples derived strictly from the provided source text.*

### Related Concepts
* [[Related Concept A]]
* [[Related Concept B]]

---
```

