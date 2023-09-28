Se vengono rimossi i controller che permettono di utilizzare i classici filesystem a blocchi (es FAT, NTFS, ext) è necessario utilizzare filesystem spaciali come:

* **jffs**: "Log Structured Filesystem" che lavora con le NAND, ma necessita fasi di clean agni volta che viene montato.
* **yaffs**: Simile a jffs, utilizzato dai primi produttori Android
* **ubifs**: ottimizzazioni del "wear level" e minori tempi di accesso in fase di mount.