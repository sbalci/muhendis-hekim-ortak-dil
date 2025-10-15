# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Quarto presentation project titled "Mühendisler ve Hekimler Ortak Bir Dili Nasıl Kurar?" (How Do Engineers and Physicians Establish a Common Language?). The presentation is created for a Memorial Hospital event about breast cancer research on October 18, 2025, focusing on pathology workflows and collaboration between medical professionals and engineers.

## Build System: Quarto

This project uses Quarto to create a reveal.js presentation from `.qmd` (Quarto Markdown) files.

### Building the Presentation

```bash
quarto render
```

This renders the presentation and outputs to the `docs/` directory (configured in `_quarto.yml`).

### Preview During Development

```bash
quarto preview
```

This starts a local server with live reload for development.

### Render Specific File

```bash
quarto render index.qmd
```

## Project Architecture

### Main Entry Point

- **`index.qmd`**: The main presentation file that includes all section files via `{{< include >}}` directives
  - Configured as a reveal.js presentation with custom theme (`slides.scss`)
  - Uses fullscreen plugin for embedded content
  - Has custom JavaScript to hide slide menu on title slide

### Content Organization

The presentation is modular, with each section in a separate file prefixed with underscore:

- `_is_akisi.qmd`: Pathology workflow and software needs
- `_amac_etik.qmd`: Purpose and ethics
- `_temel_histopatoloji.qmd`: Basic histopathology
- `_kohort_metin.qmd`: Cohort text data
- `_kohort_klinik.qmd`: Cohort clinical data
- `_kohort_goruntu.qmd`: Cohort image data
- `_anonimlestirme.qmd`: Anonymization
- `_annotasyon.qmd`: Annotation/labeling (references external GitHub project)
- `_arayuz.qmd`: Interface/UI
- `_yorumlama.qmd`: Interpretation
- `_tesekkur.qmd`: Acknowledgments

### Diagrams

The `diagram/` directory contains Mermaid diagrams (`.mmd` files):
- `patoloji-is-akisi.mmd`: Pathology workflow diagram used in the presentation

**Mermaid Syntax Notes:**
- All node definitions must be consistent (diamond `{}`, square brackets `[]`, rounded `()`)
- When referencing a node defined as a diamond (e.g., `PATOLOG{Patolog}`), use the same diamond syntax in subsequent references
- Avoid chaining multiple arrows on a single line; split into separate lines for better maintainability
- Turkish special characters (İ, ı, ö, Ş, ğ) are supported in node labels

### Assets

- `media/`: Images and graphics for the presentation
- `qrcodes/`: QR code images
- `slides.scss`: Custom reveal.js theme styling

### Output

- `docs/`: Generated presentation files (configured as output directory)
- `index_cache/`: Quarto cache directory

## Language

All content is in Turkish. The presentation focuses on pathology workflow, medical imaging, data annotation, and collaboration between pathologists and engineers for AI/ML research in medical contexts.

## Reveal.js Configuration

The presentation uses several reveal.js features:
- Scrollable slides
- Custom theme
- Speaker notes (`::: notes`)
- Fullscreen plugin for embedded iframes
- Chalkboard (disabled buttons)
- Custom slide menu behavior (hidden on title slide)
- Background images/videos on title slide
- Fragment animations
- Panel tabsets for organizing content
