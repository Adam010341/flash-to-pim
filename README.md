# flash-to-pim

![Course](https://img.shields.io/badge/course-NCKU%20Emerging%20Memory%20Techniques-555)
![Topics](https://img.shields.io/badge/topics-NAND%20Flash%20%C2%B7%20PCM%20%C2%B7%20PIM%20%C2%B7%20SMR%20%C2%B7%20KV%20stores-1F6FEB)
![License: MIT](https://img.shields.io/badge/license-MIT-yellow)

**Paper critiques and labs on emerging memory & storage systems, from NAND Flash to Processing-in-Memory.**

Coursework for *Introduction to Emerging Memory Techniques* at National Cheng Kung University (NCKU), Department of Computer Science and Information Engineering, Fall 2026 (115-1).

## Topics

- **NAND Flash & SSDs**: FTL, garbage collection, wear-leveling, parallelism, 3D NAND scaling
- **Phase-Change Memory (PCM)**: non-volatile, byte-addressable memory with slower, costlier writes that wear the cell
- **Processing-in-Memory (PIM)**: putting compute next to the data
- **Shingled Magnetic Recording (SMR)**: growing disk capacity with overlapping tracks that must be written sequentially
- **SSD-conscious key-value stores**: redesigning software such as LSM-trees for flash

## Contents

- **Paper critiques**: critiques of the eight papers on the course reading list.
- **Labs**: six labs, three SSD-related and three PIM-related. Added under `labs/` as they are completed.
- **Paper presentation**: materials for the 20-minute in-class presentation. Added once a paper is assigned.

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

### Featured: PC1, *Design Tradeoffs for SSD Performance*

Agrawal et al., *2008 USENIX Annual Technical Conference*. [Full critique](paper-critiques/01-design-tradeoffs-for-ssd-performance.md)

- **The paper.** An early taxonomy of SSD internal design trade-offs (logical page size, allocation pool, over-provisioning, command interleaving, ganging, cleaning), evaluated on a DiskSim-based simulator with real enterprise traces.
- **Pushback.** The simulator is closed-source and not validated against real hardware. It has no DRAM write cache, which likely exaggerates random-write latency and garbage collection. The wear-leveling experiment scales block endurance from 100,000 down to 50 cycles.
- **Hindsight.** It anticipated the host-to-drive "unused space" hint that became TRIM, and captured write amplification without naming it.
- **Future work.** Open-source and validate the simulator, extend to MLC flash, and quantify the controller-memory cost of page-level mapping tables at terabyte scale.

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

## Author

**Adam Fan** — [@Adam010341](https://github.com/Adam010341)
