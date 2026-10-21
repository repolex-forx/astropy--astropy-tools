# Repolex Knowledge Graph of astropy/astropy-tools

RDF knowledge graph data for [astropy/astropy-tools](https://github.com/astropy/astropy-tools), parsed by [repolex](https://repolex.ai).

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
rlex download astropy/astropy-tools
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 73f458424a616c1ec9d5be5f1580b1d3ea146624
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 73f458424a616c1ec9d5be5f1580b1d3ea146624
│           └── chunk-001.nq.gz
├── blob
│   ├── 025d9b8da9ba04d9700a03badde24f5cdf72b877.nq.gz
│   ├── 097288963845a656a95b276e12104f2d368b1340.nq.gz
│   ├── 184c71747ec1fde05d3c52f56f6fdf89851f9900.nq.gz
│   ├── 1cb744407b10b2ac40d2be0cbaeb2cae5e78dc3a.nq.gz
│   ├── 20782707c729c3ac67691763c81ae2ef57343fee.nq.gz
│   ├── 20b70ea5c15cb259997defded23a71f92884dd9f.nq.gz
│   ├── 220dd57ec707a2f3b12193203793bd76050de942.nq.gz
│   ├── 2295da72377d4304d7840c6b870b739a23efd53e.nq.gz
│   ├── 2bae775c6c5f7bf4de64be3922a392876b46b084.nq.gz
│   ├── 325b8e3b2eaad277ff69837b30ef28a9c841c558.nq.gz
│   ├── 355b6a5944a0a566c8e42f666960b0dc38e9029a.nq.gz
│   ├── 3ef89d8469a7662de5b47d26184ff719a0a2106e.nq.gz
│   ├── 3fc065ffc9fe2cafb1c634b09b1032c7182d58ea.nq.gz
│   ├── 4e090782040c9266763dc5414dd12e53f129f90d.nq.gz
│   ├── 51464b25ba124d84e3c3216de8d6640e1108b2d8.nq.gz
│   ├── 53825d67b154a06126b70921dd9afee0fdcb746f.nq.gz
│   ├── 59073c2745d226c8ecfa7973703ca24f3d66cc3a.nq.gz
│   ├── 59e52ec9d40f5af349621c969454c164d42b883b.nq.gz
│   ├── 5e64d1f4f3affa4d7dc625531ba00775c4f111fe.nq.gz
│   ├── 6459331ecd5c61036ce9d52f8d04b01a41902d87.nq.gz
│   ├── 690980e47e1b1feda1aa2b79f3e27079b891ed05.nq.gz
│   ├── 7b7818960af00a951882aa67f6d961b7f0a837ce.nq.gz
│   ├── 856f59d4c101e6722c1503bd60a0db832248f240.nq.gz
│   ├── 876771a9b0c3de5b0084a166be306901c0aff27e.nq.gz
│   ├── 938fecf0f109008fecac0ce980bd47c18de7a51a.nq.gz
│   ├── 9c39a860a9d0ebe9a50f5d96bddb878a3f0b7881.nq.gz
│   ├── ab22d6bcf771849e80dac293061fb8a8f641463b.nq.gz
│   ├── ad97a2fb01095de3e6cd3407da2eecf1f77783a4.nq.gz
│   ├── b0a3737d6e8b637b769c26a14b4b1345bfcdf08d.nq.gz
│   ├── c1814b83158ab4c0fa82c691bc40b25a1d5a540b.nq.gz
│   ├── c417f7c0e78a1538431f413d3f936634cf6a9450.nq.gz
│   ├── d228e5b45286a9f674937e8e513f79db12f9447b.nq.gz
│   ├── e0b0b84796b3bfdd286928e2897ff578e2a6e3d0.nq.gz
│   ├── e8b0612164859d37912f3434fe6478b84c3e487f.nq.gz
│   ├── ecbe27ea7c70900af380953d930494c63bd30136.nq.gz
│   └── f1af0f723a02e43eec6157700a25292c6e396ebc.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 73f458424a616c1ec9d5be5f1580b1d3ea146624.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 44 files
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

[astropy/astropy-tools](https://github.com/astropy/astropy-tools)

---
*Parsed on 2026-10-21 by [repolex](https://repolex.ai)*
