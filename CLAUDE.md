# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a LaTeX CV/Resume repository based on the Awesome-CV template. It supports three document types: full CV, resume, and cover letter. The project uses XeLaTeX for compilation and custom fonts (Roboto, FontAwesome).

## Building Documents

Compile documents using XeLaTeX (required for custom fonts and Unicode support):

```bash
# Compile the full CV
xelatex cv.tex

# Compile the resume
xelatex resume.tex

# Compile the cover letter
xelatex coverletter.tex
```

The compilation will generate PDF files with the same base name (cv.pdf, resume.pdf, coverletter.pdf).

## Architecture

The repository follows a modular structure where content is separated from document structure:

### Document Types

1. **cv.tex** - Full CV format with comprehensive sections
   - Includes: education, skills, projects, experience, certificates, honors, extracurricular
   - Uses sections from `cv/` directory
   - A4 paper with tight margins (1.2cm)
   - Uses awesome-darknight color scheme

2. **resume.tex** - Concise resume format
   - Includes: summary, education, projects, skills, extracurricular
   - Uses sections from `resume/` directory
   - A4 paper with standard margins (1.5cm)
   - Uses custom blue color scheme (#0D47A1)

3. **coverletter.tex** - Professional cover letter
   - Standalone document with recipient and letter information
   - Includes letter opening, body, and closing

### Section Organization

Content is organized in modular `.tex` files within subdirectories:

- `cv/` - Contains section files for the full CV (education.tex, skills.tex, projects.tex, experience.tex, certificates.tex, honors.tex, extracurricular.tex, etc.)
- `resume/` - Contains section files for the resume (summary.tex, education.tex, projects.tex, skills.tex, extracurricular.tex, etc.)

Each section file uses Awesome-CV environments:
- `\cvsection{}` - Section headers
- `\begin{cventries}...\end{cventries}` - Container for entries
- `\cventry{}{}{}{}{}` - Individual entries with 5 parameters: organization, title, location, dates, description
- `\begin{cvitems}...\end{cvitems}` - Bullet point lists within entries

### Configuration Files

- **awesome-cv.cls** - The document class defining all styles and commands. Do not modify unless changing fundamental styling.
- **fonts/** - Custom font files (Roboto family and FontAwesome). Required for compilation.

### Personal Information

Personal details are defined at the top of each main document file (cv.tex, resume.tex, coverletter.tex) using commands like:
- `\name{}{}`
- `\position{}`
- `\address{}`
- `\mobile{}`
- `\email{}`
- `\github{}`
- `\homepage{}`
- `\linkedin{}`

## Working with Sections

To add or modify content:

1. Identify which document type needs updating (CV or resume)
2. Navigate to the appropriate subdirectory (`cv/` or `resume/`)
3. Edit the relevant section file (e.g., `cv/experience.tex` for work experience)
4. Each section follows the same structure with `\cventry` commands
5. To add a new section, create a new `.tex` file and add `\input{path/to/file.tex}` in the main document

To enable/disable sections: Comment or uncomment the `\input{}` lines in the main document files.

## Color Customization

Colors are configured in each main document:
- Use predefined colors: awesome-emerald, awesome-skyblue, awesome-red, awesome-pink, awesome-orange, awesome-nephritis, awesome-concrete, awesome-darknight
- Or define custom colors: `\definecolor{awesome}{HTML}{HEXCODE}`
- Section highlighting: `\setbool{acvSectionColorHighlight}{true/false}`
