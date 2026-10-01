# flash-to-pim

![Course](https://img.shields.io/badge/course-NCKU%20Emerging%20Memory%20Techniques-555)
![Topics](https://img.shields.io/badge/topics-NAND%20Flash%20%C2%B7%20PCM%20%C2%B7%20PIM%20%C2%B7%20SMR%20%C2%B7%20KV%20stores-1F6FEB)
![License: MIT](https://img.shields.io/badge/license-MIT-yellow)

Paper critiques and labs on emerging memory and storage systems, from NAND Flash to Processing-in-Memory.

Coursework for *Introduction to Emerging Memory Techniques* at National Cheng Kung University (NCKU), Department of Computer Science and Information Engineering, Fall 2026 (115-1).

The course covers NAND Flash and SSDs (FTL, garbage collection, wear-leveling, 3D NAND), phase-change memory, processing-in-memory, shingled magnetic recording disks, and SSD-conscious key-value stores such as LSM-trees.

## What's here

- Critiques of the eight papers on the reading list.
- Six labs, three on SSDs and three on PIM. I'll add them under `labs/` as I finish them.
- Materials for the 20-minute in-class paper presentation, once a paper is assigned.

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

Each critique has five sections: Overview, Contributions, Room for Improvement, Possible Future Work, Overall Assessment.

## PC1: Design Tradeoffs for SSD Performance

Agrawal et al., *2008 USENIX Annual Technical Conference*. [Full critique](paper-critiques/01-design-tradeoffs-for-ssd-performance.md)

- The paper is an early taxonomy of SSD design trade-offs (logical page size, allocation pool, over-provisioning, command interleaving, ganging, cleaning). It uses a DiskSim-based simulator driven by real enterprise traces.
- The simulator is closed-source and not validated against real hardware. It has no DRAM write cache, which probably inflates random-write latency and garbage collection. The wear-leveling experiment scales block endurance from 100,000 down to 50 cycles.
- It anticipated the host-to-drive "unused space" hint that became TRIM, and described write amplification without naming it.
- Future work I suggest: open-source and validate the simulator, extend it to MLC flash, and measure the controller-memory cost of page-level mapping tables at terabyte scale.

## Layout

```
flash-to-pim/
├── README.md
└── paper-critiques/
    └── 01-design-tradeoffs-for-ssd-performance.md
```

Critiques are named `NN-paper-title.md`, matching their number on the reading list.

## Sources

Everything here is my own writing. The papers and course slides belong to their authors, publishers and instructor and are not included. Critiques are my own opinions as a student reader.

## License

[MIT](LICENSE) © 2026 Adam Fan. This covers my own writing and code, not the papers or course materials referenced here.

Adam Fan, [@Adam010341](https://github.com/Adam010341)
