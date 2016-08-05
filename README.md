.WALDIO
================================
    * Maintainer : Dam Quang Tuan (damquangtuan1985@gmail.com)
    * Contributor : Lee Wongun (inamind@gmail.com)

### Reference:
    * Wongun Lee, Keonwoo Lee, Hankeun Son, Wook-Hee Kim, Beomseok Nam, Youjip Won, “WALDIO: Eliminating the Filesystem Journaling in Resolving the Journaling of Journal Anomaly”,  In Proceedings of  USENIX ATC(Annual Technical Conference), Santa Clara, CA, July 8 – 10, 2015
    * http://esos.hanyang.ac.kr/files/publication/conferences/international/waldio.pdf

### Acknowledgement:
    * This work is sponsored by IT R&D program from MKE/KEIT (No. 10041608, Embedded system Software for New-memory based Smart Device) and by ICT R&D program of MSIP/IITP (No.1I2221-14-1005)

WALDIO
-----------------------------------
This work is dedicated to resolve the Journaling of Journal Anomaly in Android IO stack. We orchestrate SQLite and EXT4 filesystem so that SQLite’s file-backed journaling activity can dispense with the expensive filesystem intervention, the journaling, without compromising the file integrity under unexpected filesystem failure. In storing the logs, we exploit the direct IO to suppress the filesystem interference. This work consists of three key ingredients: (i) Preallocation with Explicit Journaling, (ii) Header Embedding, and (iii) Group Synchronization. Preallocation with Explicit Journaling eliminates the filesystem journaling properly protecting the file metadata against the unexpected system crash. We redesign the SQLite B-tree structure with Header Embedding to make it direct IO compatible and block IO friendly. With Group Synch, we minimize the synchronization overhead of direct IO and make the SQLite operation NAND Flash friendly. Combining the three technical ingredients, we develop a new journal mode in SQLite, the WALDIO. We implement it on the commercially available smartphone.
WALDIO mode achieves 5.1× performance (insert/sec) against WAL mode which is the fastest journaling mode in SQLite. It yields 2.7× performance (inserts/sec) against the LS-MVBT, the fastest SQLite journaling mode known to public. WALDIO mode achieves
7.4× performance (insert/sec) against WAL mode when it is relieved from the overhead of explicitly synchronizing individual log-commit operations. WALDIO mode reduces the IO volume to 1/6 compared against the WAL mode.
