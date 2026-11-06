# Repolex Knowledge Graph of sphinx-contrib/gnuplot

RDF knowledge graph data for [sphinx-contrib/gnuplot](https://github.com/sphinx-contrib/gnuplot), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download sphinx-contrib/gnuplot
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 0375f74b5d315ce3aa5fa0fdcbe2ad1ec56b8af6
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 0375f74b5d315ce3aa5fa0fdcbe2ad1ec56b8af6
│           └── chunk-001.nq.gz
├── blob
│   ├── 0083945baf6ef97f8cb9d0ac4d8417bc8aff3c4d.nq.gz
│   ├── 092ff21583d38363377a0847d01de1db801de1e6.nq.gz
│   ├── 2d74c58f248790e34e482eb07e20ec6c753c9d2d.nq.gz
│   ├── 2eba9160d403563d8b100534a4d950281de057e6.nq.gz
│   ├── 451a0e58b7e4dedc216956bee3f249fed5c117ca.nq.gz
│   ├── 45dd5f5b51e10661a6b6699e050c4ab23d721804.nq.gz
│   ├── 54c4bd0b35d11f9fd1d8a64a7dd8f598b5999dc3.nq.gz
│   ├── 8039d47c7fdedff04f6e1fe48d66558f67f7147e.nq.gz
│   ├── a54e0ce4e3210920322fe21d2421b146b5fe0ca1.nq.gz
│   └── b5a7dc29ef0f7f3593b1c61cfc5dfe8a17d3918c.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 0375f74b5d315ce3aa5fa0fdcbe2ad1ec56b8af6.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 18 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[sphinx-contrib/gnuplot](https://github.com/sphinx-contrib/gnuplot)

---
*Parsed on 2026-11-06 by [repolex](https://repolex.ai)*
