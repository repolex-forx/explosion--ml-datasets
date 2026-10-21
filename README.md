# Repolex Knowledge Graph of explosion/ml-datasets

RDF knowledge graph data for [explosion/ml-datasets](https://github.com/explosion/ml-datasets), parsed by [repolex](https://repolex.ai).

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
rlex download explosion/ml-datasets
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── ccdea9532caa119a8703e4853f3b73f9f37af5eb
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── ccdea9532caa119a8703e4853f3b73f9f37af5eb
│           └── chunk-001.nq.gz
├── blob
│   ├── 0288a4ca574c11eeb08bc1ef2b2f0d6e897203a8.nq.gz
│   ├── 07add6b2555c8ce38ddbd9a156ea61f7077c9663.nq.gz
│   ├── 0ac975684bfce509cfaa5e65b17b815269cfa0d3.nq.gz
│   ├── 0c0a3d876e7199edfb8703294a93c4e4a2aa9a26.nq.gz
│   ├── 12e22983f35dbb900597cddc3f610c4eb5c50ac5.nq.gz
│   ├── 15d6da08c351287e0a3ae564470174f9250b0cfa.nq.gz
│   ├── 16c25c97db983f8cbcb9e789b661ea32f260eea5.nq.gz
│   ├── 1cfa797205dac64d0e73acadc6332398e02ee941.nq.gz
│   ├── 20428efa0ef36d662d01f7f06839096cefdac270.nq.gz
│   ├── 2e9c8039e0ecb078a7a39349697d071bf8e8ee45.nq.gz
│   ├── 2f901eb42b23c452e727290d3aa09bc7cbfd2244.nq.gz
│   ├── 30ea6a7799e39ae7cea8a1d94e7c9afda2ee9282.nq.gz
│   ├── 37f77c60f9236be556499225f09cb67c00eb4795.nq.gz
│   ├── 3be8060d4a5178363a0386647f5d1d0b545ec01b.nq.gz
│   ├── 463b4924d7de8898db7a7e767142005e19cb92e1.nq.gz
│   ├── 500a54bb5f91472f885dca6152566bc4a2c7d445.nq.gz
│   ├── 52afd6478cdfd47c583bb99c7d56dc82c8ff411e.nq.gz
│   ├── 56fe96505e9e1d9bb0a952fbb1377cfaf2f828e1.nq.gz
│   ├── 592a708f93dcb082cf09fb2b12e3cb1ab8748d79.nq.gz
│   ├── 760a6521c767922b8d90d52b557fbb060bf2c4d5.nq.gz
│   ├── 77984176f1aa0b80ef9be5190a8315744f1fceb7.nq.gz
│   ├── 798e972ba731995ec17df4147e09f918458a8f4b.nq.gz
│   ├── a27dbc05037dc936d817a0d9531c99e9ff2dd2ae.nq.gz
│   ├── aff4f6c52f61ec4b44647e1c98730da2629473ee.nq.gz
│   ├── bc6f6c8e3d692d7bc70d219cd38567b949e9ce3c.nq.gz
│   ├── d37826bb78aaeb8245390b4226c927a50b403d59.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── ebd42575505a0ca1e6cd91e60efcb3669549d537.nq.gz
│   ├── f570a48ada824ae71187ca3bdc292ecaacd522ba.nq.gz
│   └── fa5571294e2239375f175ab413cbbc428498f2d8.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── ccdea9532caa119a8703e4853f3b73f9f37af5eb.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 37 files
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

[explosion/ml-datasets](https://github.com/explosion/ml-datasets)

---
*Parsed on 2026-10-21 by [repolex](https://repolex.ai)*
