# flash-to-pim

![Course](https://img.shields.io/badge/course-NCKU%20Emerging%20Memory%20Techniques-555)
![Topics](https://img.shields.io/badge/topics-NAND%20Flash%20%C2%B7%20PCM%20%C2%B7%20PIM%20%C2%B7%20SMR%20%C2%B7%20KV%20stores-1F6FEB)
![License: MIT](https://img.shields.io/badge/license-MIT-yellow)

**Paper critiques and labs on emerging memory & storage systems — from NAND Flash to Processing-in-Memory.**

Coursework for *Introduction to Emerging Memory Techniques* at National Cheng Kung University (NCKU), Department of Computer Science and Information Engineering — Fall 2026 (115-1).

---

## Why "flash-to-pim"?

The course follows a single thread: it starts with the memory technology inside every SSD and ends by moving computation *into* the memory itself. On the way it visits phase-change memory, shingled magnetic recording disks, and key-value stores designed around flash. This repository mirrors that arc, so the notes read as one story rather than a pile of assignments.

| Area | The question it asks |
|---|---|
| **NAND Flash & SSDs** | How do you build fast, durable storage from a medium that cannot overwrite in place and wears out? (FTL, garbage collection, wear-leveling, parallelism, 3D NAND scaling) |
| **Phase-Change Memory (PCM)** | What changes when memory is non-volatile and byte-addressable, but writes are slower, costlier and wear the cell? |
| **Processing-in-Memory (PIM)** | If moving data is the bottleneck, what happens when compute lives next to the data? |
| **Shingled Magnetic Recording (SMR)** | How do hard disks keep growing in capacity when tracks overlap and must be written sequentially? |
| **SSD-conscious key-value stores** | How should software such as LSM-trees be redesigned to fit the strengths of flash? |

## What's in this repository

- **Paper critiques** — written critiques of the eight papers on the course reading list.
- **Labs** — six labs: three SSD-related and three PIM-related. *Added under `labs/` as they are completed.*
- **Paper presentation** — materials for the 20-minute in-class paper presentation. *Added once a paper is assigned.*

### Paper critiques

| # | Paper | Area | Critique |
|:-:|---|---|---|
| 1 | Design Tradeoffs for SSD Performance | SSD architecture | [Read](paper-critiques/01-design-tradeoffs-for-ssd-performance.md) |
| 2 | Recent Progress on 3D NAND Flash Technologies | 3D NAND | Upcoming |
| 3 | Accelerating Write by Exploiting PCM Asymmetries | PCM | Upcoming |
| 4 | Improving Phase Change Memory Performance with Data Content Aware Access | PCM | Upcoming |
| 5 | Benchmarking a New Paradigm: Experimental Analysis and Characterization of a Real Processing-in-Memory System | PIM | Upcoming |
| 6 | Skylight — A Window on Shingled Disk Operation | SMR | Upcoming |
| 7 | Performance Evaluation of Host Aware Shingled Magnetic Recording (HA-SMR) Drives | SMR | Upcoming |
| 8 | WiscKey: Separating Keys from Values in SSD-conscious Storage | Key-value stores | Upcoming |

### How I critique a paper

Every critique uses the same five sections, so they are easy to compare:

1. **Overview** — the background the paper was written into, and what it found.
2. **Contributions** — what is genuinely new, and how it was demonstrated.
3. **Room for Improvement** — methodology, rigor, reproducibility, and how well the experiments support the claims. Where relevant, a look back at what the paper got right (or missed) with today's hindsight.
4. **Possible Future Work** — concrete follow-ups a researcher could pick up at the time of publication.
5. **Overall Assessment** — a short verdict.

### Featured: PC1 — *Design Tradeoffs for SSD Performance*

Agrawal et al., *2008 USENIX Annual Technical Conference*. [Full critique →](paper-critiques/01-design-tradeoffs-for-ssd-performance.md)

- **The paper.** One of the first systematic taxonomies of SSD internal design trade-offs (logical page size, allocation pool, over-provisioning, command interleaving, ganging, cleaning), evaluated on a DiskSim-based simulator driven by real enterprise traces.
- **What worked.** Realistic workloads exposed details that theory alone would miss — for example, database workloads could not benefit from interleaving because their request queues were almost always empty.
- **Where I push back.** The simulator is closed-source and not validated against real hardware; it has no DRAM write cache, which likely exaggerates random-write latency and garbage collection; the wear-leveling experiment scales block endurance from 100,000 down to 50 cycles; and the benchmarks cover only part of the taxonomy.
- **Hindsight.** The paper anticipated the host-to-drive "unused space" hint that became the TRIM command, and captured the mechanics of write amplification without naming or formalizing it.
- **Future work I propose.** Open-source and validate the simulator, extend the study to MLC flash, and quantify the controller-memory cost of page-level mapping tables at terabyte scale.

## Repository layout

```
flash-to-pim/
├── README.md
├── paper-critiques/
│   └── 01-design-tradeoffs-for-ssd-performance.md
└── labs/                 # coming: one folder per lab
```

Conventions: critiques are named `NN-paper-title.md`, matching their number on the reading list, and open with a citation table. Each lab gets its own folder with a README covering the goal, how to run it, and the results.

## A note on sources

Everything in this repository is my own writing. The papers and course slides belong to their authors, publishers and instructor, and are deliberately **not** included — please read the originals from the publishers. Critiques express my own opinions as a student reader.

## License

[MIT](LICENSE) © 2026 Adam Fan. This covers my own writing and code in this repository, not the papers or course materials referenced here.

## Author

**Adam Fan** — [@Adam010341](https://github.com/Adam010341)
