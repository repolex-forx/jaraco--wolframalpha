# Repolex Knowledge Graph of jaraco/wolframalpha

RDF knowledge graph data for [jaraco/wolframalpha](https://github.com/jaraco/wolframalpha), parsed by [repolex](https://repolex.ai).

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
rlex download jaraco/wolframalpha
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 1b0207fdd14c48ee7b2cb4b8a9815bc89d3915a6
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 1b0207fdd14c48ee7b2cb4b8a9815bc89d3915a6
│           └── chunk-001.nq.gz
├── blob
│   ├── 128c54d0edf005a2e46f4aa363d5f810869c898b.nq.gz
│   ├── 1f2aa7533b0423a8eb943f6f4ec02498e39581a0.nq.gz
│   ├── 240329c3604d8ead4c10aa8c88352caa8e4ce7b2.nq.gz
│   ├── 2e3f4dd791a6372b427d618eb0baa8c4dc58e5f0.nq.gz
│   ├── 304196f81e11a168c9894f966e4a617ebf4ed53c.nq.gz
│   ├── 30c39ff8d776dd6032b061732d98818f889139d3.nq.gz
│   ├── 37df1d920f05c184b040a7f2caebca7fa9365bbd.nq.gz
│   ├── 49ab471bc61d3b6713f539132d98b1add4b6a341.nq.gz
│   ├── 4dd53b92a9b8c23d730dc6df9d3d915f3ccf242c.nq.gz
│   ├── 5367688cc0bdc1318a0b179775367549794ee407.nq.gz
│   ├── 54c9000ec94341dd65c2053251b85b124017b9b5.nq.gz
│   ├── 54cc8303b22089e12053e552d4e6cb852a865b8a.nq.gz
│   ├── 577e87a793a20e413f7321f4f17ec1eba2ea1962.nq.gz
│   ├── 5bdc232005af9be104a00437ae9bc64417a4c1cc.nq.gz
│   ├── 700235be57c1b2872455c0be5333f59cf568e252.nq.gz
│   ├── 724370638fc188317bbc7dc868f1a571995fd796.nq.gz
│   ├── 9a0f3bce1395ae3819030b822e5d9076c85068ea.nq.gz
│   ├── b404267659315f82cb6afcb5c4fd3557af9e849b.nq.gz
│   ├── c6fc197e4674f73b881419f8a2e977b3404844f7.nq.gz
│   ├── ccb9ded59dffeadb1bae6185b748447007d17652.nq.gz
│   ├── e49a6b43de5a5f7bd45e6939e75cf231eb286652.nq.gz
│   ├── f2d8643957863e332528301f693d9a11ad18b0af.nq.gz
│   └── f5e4977e1cbf7e5dbad77da562f2a0970db72a06.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 1b0207fdd14c48ee7b2cb4b8a9815bc89d3915a6.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 31 files
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

[jaraco/wolframalpha](https://github.com/jaraco/wolframalpha)

---
*Parsed on 2026-10-20 by [repolex](https://repolex.ai)*
