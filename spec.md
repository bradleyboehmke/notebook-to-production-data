# DataOps Pipeline Workshop – Presentation Spec

This document defines the specification for building a **Quarto/RevealJS** slide deck titled *“From Notebook to Production: Building Reliable Data Pipelines.”*  The goal of the presentation is to introduce undergraduate and graduate students to DataOps principles and illustrate how a simple Jupyter notebook evolves into a robust, production‑ready pipeline using the Rossmann forecasting project as an example.

## Overview

1. **File Structure**
   - The slide deck should be implemented in a Quarto file located at `slides/dataops-pipeline.qmd`.
   - A directory `assets/` should store any custom images used in the presentation.
   - Ensure that the directory structure follows that of the *portfolio‑via‑github* workshop slides for consistency.

2. **Theme & Configuration**
   - Use the **simple** RevealJS theme as in the portfolio slides.
   - Enable slide numbers (`slide-number: true`) and set transition to **fade**.
   - Include plugins `appearance` and `highlight-text` for callouts and text emphasis.
   - Define YAML front‑matter with the title, subtitle, author, and theme settings:

     ```yaml
     ---
     title: "From Notebook to Production: Building Reliable Data Pipelines"
     subtitle: "A practical introduction to DataOps and pipeline design"
     author: "Your Name"
     format:
       revealjs:
         theme: simple
         slide-number: true
         transition: fade
         code-line-numbers: false
         preview-links: auto
         revealjs-plugins:
           - appearance
           - highlight-text
     footer: '[DataOps Resources](https://github.com/bradleyboehmke/rossmann-forecasting)'
     execute:
       echo: false
     ---
     ```

3. **Content and Structure**
   - Structure the deck according to the workshop outline. Each major section should correspond to a top‑level slide (`#` heading), with subpoints or details as nested headings or bullets. Use callouts and columns to visually organize information.
   - Include presenter notes using `::: {.notes}` blocks beneath slides where additional context or speaking guidance is needed.

## Slide Layout and Content

The following sections outline the sequence of slides along with key content elements. Citations refer to the Rossmann DataOps documentation and should be included as footnotes where appropriate.

### 1. Welcome / Title
   - Title, subtitle, and optional tagline (“Applied Workshops Series”). Use a dark background similar to the portfolio slides.
   - Presenter notes introducing the instructor and workshop purpose.

### 2. Agenda / Objectives
   - List the main topics: the notebook demonstration, DataOps overview, pipeline walk‑through, hands‑on exercise, and wrap‑up.
   - Include a callout box highlighting the primary workshop goal.

### 3. Simple Notebook Demo
   - Summarize typical notebook workflow (loading, merging, and analyzing data). Discuss limitations of this approach.
   - Provide a hyperlink to the baseline notebook in the `1-initial-exploration` branch (Rossmann repository) for students to explore.
   - Include a callout question prompting students to think about production concerns.

### 4. What Is DataOps?
   - Define DataOps and list its core principles: automation, quality assurance, reproducibility, collaboration, continuous improvement.
   - Highlight the importance of modularity and separating code into a `src/` directory.
   - Use callouts to emphasize key points.

### 5. High‑Level Pipeline Flow
   - Embed a Mermaid diagram showing the DataOps flow (validation gates, processing, feature engineering, versioning, and model retraining).
   - Summarize the purpose of each stage beneath the diagram.

### 6. DataOps Pipeline Steps
   - Create a series of bullet lists or subslides describing each pipeline step:
     1. **Validate Raw Data**: verify schema, types, ranges, and nulls.
     2. **Process Raw Data**: merge datasets, convert types, handle missing values, save as Parquet.
     3. **Validate Processed Data**: ensure processing didn’t introduce errors.
     4. **Build Standard Features**: generate calendar, promo, competition, lag and rolling features.
     5. **Validate Features**: catch NaNs, infinite values, and leakage.
     6. **Version Control with DVC**: track data separately from code; enable reproducibility.
   - Use callouts to explain why each step is critical.

### 7. From Notebook to Modular Code
   - Describe moving code from the notebook into `src/data/` and `src/features/` modules. Mention that the script `scripts/dataops_workflow.sh` automates the entire pipeline.
   - Optionally include a code snippet showing how to run the workflow script.

### 8. Student Exercise & Discussion
   - Prompt students to brainstorm their own mini pipeline projects (e.g., ingesting CSVs and API data). Encourage them to apply validation, processing, feature engineering, and versioning.
   - Highlight Jeff Whitcomb’s example project (“Yahoo Finance Data Pipeline”) as a portfolio piece.
   - Use callouts to inspire experimentation and ongoing practice.

### 9. Wrap‑Up & Takeaways
   - Summarize DataOps benefits: reliable data quality, reproducibility, modularity, version control, and automation.
   - Provide suggestions for next steps (e.g., exploring DVC, Great Expectations, or building a personal project pipeline).
   - End with an encouraging note on incremental improvement.

### 10. References
   - List citations and resources, including links to the Rossmann DataOps documentation and any supplementary materials. Use footnotes to cite the lines referenced in the slides.

## Style and Formatting Notes

1. **Callouts**: Use Quarto callout boxes (`::: {.callout-tip}`, `.callout-warning`, etc.) to emphasize tips, warnings, and important information.
2. **Notes**: Place presenter notes in `::: {.notes}` blocks underneath each slide. These will not be visible in the final output but provide guidance for delivery.
3. **Diagrams**: Prefer Mermaid diagrams for pipeline flows; embed them directly in the `.qmd` file for clarity.
4. **Consistency**: Follow the visual style of the portfolio workshop slides, using dark backgrounds (`#43464B`) for main slides and brighter accent colors for emphasis.

## Compilation

Render the slides with:

```bash
quarto render slides/dataops-pipeline.qmd
```

This will produce `dataops-pipeline.html`. Review the output in a browser and adjust styling or content as needed. If additional styling is required, add a `styles.css` file referenced in the front‑matter (`css: styles.css`).