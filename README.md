# ksTFL Binaries

Pre-built binaries for the ksTFL package.

[Package documentation](https://crow16384.github.io/ksTFL-release/)
# ksTFL: Clinical Tables, Figures, and Listings Framework

[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](LICENSE)

<img src="man/figures/ksTFL-logo.svg" alt="ksTFL logo" width="700" />

## Overview

**ksTFL** is a professional R package designed to fill a long-standing gap in the R ecosystem: the lack of a dedicated, end-to-end solution for producing well-formatted, regulatory-compliant clinical Tables, Figures, and Listings (TFLs). While R excels at statistical analysis, generating submission-quality DOCX outputs that meet pharmaceutical industry standards has traditionally required fragile workarounds or external tooling. ksTFL solves this by distilling the best ideas from existing reporting solutions into a simple, minimalistic, yet highly flexible declarative language — a compact set of composable functions whose combinations can produce virtually any clinical output format.

The core philosophy is **data–presentation separation**: input data stays clean and planar, free of reporting artefacts such as merged cells, indentation columns, or display-only rows. Formatting, pagination, grouping, and styling are declared independently and applied at render time. This keeps datasets maintainable, traceable, and validation-ready — exactly what regulated environments demand.

Under the hood, a built-in **rendering engine** with text shaping converts declarative specs into styled DOCX documents with deterministic, pixel-perfect pagination. Rendering is extremely fast even on large datasets, making ksTFL practical for batch production of hundreds of outputs in a single pipeline run.

### Key Design Principles

- **Separation of Concerns**: Metadata generation (R) is decoupled from document rendering; input data remain clean and analysis-ready
- **Declarative Syntax**: Users describe *what* to render, not *how* to render it — a small function vocabulary covers the full range of clinical outputs
- **Deterministic Pagination**: font shaping guarantees pixel-perfect, reproducible layouts and pagination
- **High Performance**: C++ engine renders large multi-spec reports in seconds
- **Type Safety**: Comprehensive input validation with informative error messages
- **Reproducibility**: Specifications are serializable. That allows to store the metadata for replay without re-runnig of the whole code

---

## Installation

ksTFL is distributed as **pre-compiled binaries** for R 4.4 and R 4.5 on Windows, Ubuntu/Debian, and Fedora/RHEL.

### Windows

```r
install.packages("ksTFL",
                 repos = "https://crow16384.github.io/ksTFL-release",
                 type  = "binary")
```

### Linux — Ubuntu / Debian

```r
install.packages("ksTFL",
                 repos = "https://crow16384.github.io/ksTFL-release/bin/linux/ubuntu-noble")
```

Before installing, make sure system libraries are available (required at runtime):

```bash
sudo apt-get install -y libharfbuzz0b libfreetype6 libminizip1
```

### Linux — Fedora / RHEL

```r
install.packages("ksTFL",
                 repos = "https://crow16384.github.io/ksTFL-release/bin/linux/fedora")
```

Before installing, make sure system libraries are available (required at runtime):

```bash
sudo dnf install -y harfbuzz freetype minizip-ng-compat
```

### macOS

macOS binaries are published as GitHub Release assets and can be installed from a downloaded `.tgz` file:

```r
install.packages("ksTFL_<version>.tgz", repos = NULL)
```

When a macOS binary is available in the CRAN-like repo, you can also use:

```r
install.packages("ksTFL",
                 repos = "https://crow16384.github.io/ksTFL-release",
                 type  = "binary")
```

### From a downloaded file

Pre-built packages can be downloaded from the
[Releases](https://github.com/crow16384/ksTFL-release/releases) page and
installed directly:

```r
# Linux (.tar.gz binary)
install.packages("ksTFL_<version>_R_x86_64-pc-linux-gnu.tar.gz", repos = NULL)

# Windows (.zip)
install.packages("ksTFL_<version>.zip", repos = NULL)

# macOS (.tgz)
install.packages("ksTFL_<version>.tgz", repos = NULL)
```

Release repository: <https://github.com/crow16384/ksTFL-release>

### Fonts note

Proprietary Microsoft fonts (Arial, Times New Roman, etc.) are **not bundled** due to licensing restrictions; open-source Liberation fonts are included as metrically compatible fallbacks. Windows and macOS systems with Microsoft Office installed typically have the original fonts already available. On Linux, additional steps may be required — see [Package documentation](https://crow16384.github.io/ksTFL-release/index.html#id_7-font-management) for details.

---
