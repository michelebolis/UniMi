Se vengono rimossi i controller che permettono di utilizzare i classici filesystem a blocchi (es FAT, NTFS, ext) è necessario utilizzare filesystem spaciali come:

* **jffs**: "Log Structured Filesystem" che lavora con le NAND, ma necessita fasi di clean agni volta che viene montato.
* **yaffs**: Simile a jffs, è un file System progettato specificamente per le memoria flash NAND e NOR. È altamente ottimizzato per i dispositivi embedded ed utilizza la memoria flash come supporto di archiviazione.
* **ubifs**: ottimizzazioni del "wear level" e minori tempi di accesso in fase di mount.