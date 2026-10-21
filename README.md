# Repolex Knowledge Graph of pyca/infra

RDF knowledge graph data for [pyca/infra](https://github.com/pyca/infra), parsed by [repolex](https://repolex.ai).

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
rlex download pyca/infra
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 137aa2e2b9a7d4d9ec6d4cb755ddfcc15c2d2a9d
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 137aa2e2b9a7d4d9ec6d4cb755ddfcc15c2d2a9d
│           └── chunk-001.nq.gz
├── blob
│   ├── 0a76be69a7d1b39ebce28717db6d7d0cd8dc151c.nq.gz
│   ├── 178fa2fd9bf86ba8d9123c6c06bcecb67087088b.nq.gz
│   ├── 19f88e0fcc21b2d7fc49976bbd9e0ca9ca62ea85.nq.gz
│   ├── 321865cba705778fc10f29aeb42bf1fa3f2b20be.nq.gz
│   ├── 34390818a7f6f0f65412fa29a4c076609d5bcf56.nq.gz
│   ├── 37d44b2b05c055f5f4da322ca8775171a1f97113.nq.gz
│   ├── 5798ea3a0118a38c81a109983c6274ee22d80ba6.nq.gz
│   ├── 5a41bfac4feb747f1cfe2ee1e2aff88c7fb56278.nq.gz
│   ├── 5a6edff8da92b778381babbb810e1ddc3b0ad03c.nq.gz
│   ├── 5a87d7d258789ac8185e69c8dd3b942cda5f1be2.nq.gz
│   ├── 5e4251f206bc9cbe7c602962ce69f3e69ed8c431.nq.gz
│   ├── 5ec32e31f52cdfcbe74ed76158d80a542bc9a167.nq.gz
│   ├── 60692041809a1001f1d2d0db124f65f610d34583.nq.gz
│   ├── 62589edd12a37dd28b6b6fed1e2d728ac9f05c8d.nq.gz
│   ├── 79a4d7b39193166a7263e2541190a48ce82f7a5c.nq.gz
│   ├── 984d5fab3a02bf9ed07922e197511da48ac29a36.nq.gz
│   ├── 9a1c83b1f050232d03a8fec8c45085a39812f19b.nq.gz
│   ├── bb7fba6e6c58e51f953cf44b3e0342c7697dccbf.nq.gz
│   ├── c2357f806c37dd5999b3aec6e3184288e1724699.nq.gz
│   ├── c962a82847b14e72f25d4b1f948ecf657aeda2aa.nq.gz
│   ├── dc652bda07a2388db88ab20556d50988575c3ea4.nq.gz
│   ├── dd76d6529843135926b60d90d3a1da6114a558d4.nq.gz
│   └── e37208eb949ce444ca192c743b92e5d768d07a54.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 137aa2e2b9a7d4d9ec6d4cb755ddfcc15c2d2a9d.nq.gz
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

[pyca/infra](https://github.com/pyca/infra)

---
*Parsed on 2026-10-21 by [repolex](https://repolex.ai)*
