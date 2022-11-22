# Linux Kernel in a Nutshell

Das Linux Betriebssystem wie es typischerweise mit einer Linux Distribution wie RHEL verteilt wird besteht aus vielen Hundert Paketen. Die konkrete Ausprägung eines damit installierten Servers kann sehr unterschiedlich sein. Zum Beispiel ein einfacher Webserver, ein Datenbankserver, ein Build-Host zum erzeugen neuer Programmpakete oder ein Container-Host zur orchestrierung von Microservices.
All diesen Systemen gemeinsam ist der Betriebssystemkern, Linux.

## init=/bin/sh

Um ein Gefühl dafür zu bekommen, was dieser Kernel eigentlich ist, empfehle ich den Start eines auf die minimale Funktionalität beschränkten Systems. Mit RHEL-7 können wir den Bootloader so verändern, dass anstelle von `init` oder `systemd` einfach nur eine Shell gestartet wird.

Mit `dmesg | less` kann ich mir dir Meldungen des Kernels während und seit dem Bootvorgang anzeigen lassen. Auch hier gibt es wieder eine Masse von neuen Akronymen:

**cgroup** steht für Control Group und ist ein Mechanismus im Kernel um die Ressourcen zu kontingentieren.

**BIOS** ist das Basic Input Output System mit dem die Computerhardware das Betriebssystem lädt.

**DMI** ist das Desktop Management Interface. Mit `/sbin/dmidecode | less` kann ich mir eine Aufstellung der vom Bios erkannten Hardware anzeigen lassen.

**KVM** ist die Kernel Virtual Machine, der Hypervisor im Linux Kernel

**e820** ist der Aufruf mit dem das BIOS dem startenden Kernel die verfügbaren Speicherbereiche mitteilt.

**MTRR** steht für Memory Type Range Register.

**PAT** steht für Page Attribute Table.

**SMP** steht für Symmetric Multi Processing

**ACPI** steht für das Advanced Configuration and Power Interface

**RSDP** steht für Root System Description Pointer

**RSDT** setht für Root System Description Table

**FACP** steht für Fixed ACPI Control Pointer

Eine vollständige Liste aller ACPI Objekte ist in der [Dokumentation zum Linux Kernel](200~https://www.kernel.org/doc/html/latest/arm64/acpi_object_usage.html) enthalten.

**NUMA** steht für Non Uniform Memory Access bei dem in einem Multiprozessorsystem der Arbeitsspeicher nicht einheitlich als Ganzes verwaltet wird sondern mit bestimmten den jeweiligen Prozessoren vorbehaltenen Speicherbereichen arbeitet.

**DMA** steht für Direct Memory Access

**SLUB** steht für Unqueued Slab Allocator

**DAC** steht für Discretionary Access Control, das ist ein Sicherheitskonzept bei dem die Zugriffsrechte auf Basis der Identität (UID/GID) des Benutzers getroffen werden.

**MAC** steht für Mandatory Access Control, das ist ein strengeres Sicherheitskonzept bei dem die Rechte durch ein Regelwerk bestimmt werden. Alles was nicht ausdrücklich durch diese Regeln erlaubt wird ist verboten.

**RBAC** steht für Role Based Access Control.

**Yama** ist das Subsystem im Linux Kernel mit dem DAC durchgesetzt wird

**SELinux** ist das Subsystem im Linux Kernel mit dem MAC durchgesetzt wird.

**SRBDS** steht für Special Register Buffer Data Sampling und weist auf einen möglichen Angriffsvektor in INTEL CPUs hin.

**MDS** steht für Microarchitectural Data Sampling und weist auf einen weiteren Angriffsvektor von CPUs hin.

**APIC** steht für Advanced Programmable Interrupt Controller

**TSC** steht für Time Stamp Counter

**PCI** steht für Peripheral Component Interconnect, ein Standard Bus-System zur Verbindung von PC Komponenten.

**acpiphp** steht für ACPI PCI Hot Plug

Mit `/sbin/lspci` kann ich eine Aufstellung aller erkannten PCI Geräte anzeigen lassen.

**SCSI** steht für Small Computer System Interface

**EDAC** steht für Error Detection and Correction

**RAPL** steht für Running Average Power Limit

**HugeTLB** steht für Huge Pages Table


Wenn wir uns mit `ps axf` die Liste aller auf dem Kernel laufenden Prozesse ansehen, finden wir als Prozess mit der Nummer 1 unsere Shell. Selbst wenn wir bisher noch gar kein Kommando eingegeben haben hat unser `ps` nicht die Prozessnummer 2. Stattdessen finden wir eine Mange seltsamer Prozesse deren Namen in eckigen Klammern angezeigt werden und die alle vom kthreadd abstammen. Hierbei handelt es sich um interne Prozesse im Linux Kernel.

Wir verwenden die Linux Toolbox um die Liste dieser Kernelprozesse zu sortieren: 
`ps axf | grep \\[ | grep -v grep | sort -k6`

Oder auch `ps --ppid 2 -fh | sort -k5`

Hier finden wir jede Menge Akronyme:

**ATA** ist das Advanced Technology Attachment, ein Standard für die Steuerung von Festplatten. SFF steht für Small Form Factor. Dieser Kernel Thread sorgt also dafür, dass solche Geräte auch von den modernen Hochleistungskerneln genutzt werden können, ohne dass der Kernel von deren langsamen Operationen ausgebremst wird.

**BIO** steht für Block IO und die biosets dienen dazu, die Details von geordneten Schreib/Lese Operationen auf Blockdevices von den schreibenden Kernelprozessen zu entkoppeln.

**EDAC** steht für Error Detection and Correction, der edac-poller behandelt solche Situationen.

**ALUA** steht für Asymmetric Logical Unit Access, eine Multipath Technologie für Storage Aread Networks.

**DM** steht für Device Mapper mit dem Schichten virtueller Blockdevices aufeinander aufgebaut werden.

Der kintegrityd kümmert sich nur um die Integrität bestimmter BIO Operationen indem die Integtity Metadata vom Gerät berücksichtigt wird.

**RDAC** steht für Redundant Disk Array Controller, eine andere Multipath Technologie für SAN.

**PS** steht für Personal System, eigentlich Personal System/2. psmouse ist also eine PS/2 Maus. Kennt heute ausser dem Linux Kernel keiner mehr.

**KSM** steht für Kernel Samepage Merging.

**IRQ** ist ein Interrupt Request. Typischerweise werden solche Requests von der Hardware erzeugt, zum Beispiel wenn neue Daten angekommen sind. Wie der Name schon andeutet unterbricht so ein Request den Kernel bei seiner regulären Arbeit und verlangt sofort eine Reaktion. Das kann zum Beispiel das Kopieren der Daten an einen sicheren Ort sein. Danach kann das Gerät weitere Daten empfangen, ohne dass dabei existierende Daten im Empfangspuffer überschrieben werden. Weil ein solcher Hardware Interrupt selbst nicht wieder unterbrochen werden darf, ist es gute Praxis die empfangenen Daten nicht direkt in diesem Interrupt weiter zu verarbeiten. Stattdessen wird ein softirq ausgelöst der dann zeitnah aber in einer kooperativen Weise mit den Daten verfährt.

**LRU** steht für Least Recently Used.

**MD** steht für Multipath Daemon.

**NS** steht für NameSpace.

**RCU** steht für Read, Copy, Update. Das ist ein Verfahren zur Synchronisation von Änderungen gemeinsam genutzter Datenstrukturen.

**BH** steht für Bottom Half, das ist zum Beispiel der softirq zum Hardware IRQ auf der Oberseite.

**SCSI** steht für Small Computer Systems Interface.

**TMF** steht für Task Mangement Function und **EH** für Error Handler.

**TTM** steht für Transition Table Maps, eine Technologie mit der Speicher von GPU Grafikkarten angesprochen wird.
## Hardware, Resources, Devices

Viele der Kernel-Threads dienen offenbar dazu, bestimmte Hardware und bestimmte Geräte zu steuern.

Die Kerneltreiber für solche Geräte werden in der Regel nicht fest in den Linux Kernel eingebaut. Stattdessen hat Linux einen Mechanismus, Treiber zur Laufzeit als Module nachzuladen. Mit `cat /proc/modules` sehen wir, welche Module aktuell geladen sind. 


Im Dateisystem Zweig /proc gibt es zu jedem laufenden Prozess und zu den Kernel Threads jeweils ein eigenes Verzeichnis, indem Statusinformationen und Steuerdateien für den jeweiligen Prozess zu finden sind.

Im Zweig /sys befinden sich analog Status und Steuerdateien für den Kernel und das gesamte System.


Eine detaillierte Betrachtung aller Daten in diesen beiden Zweigen sprengt den Rahmen dieser Übersicht.

Als Erkenntnis solltest du aber auf jeden Fall mitnehmen, dass das Linux System sämtliche Informationen und Parameter in dem Dateisystem transparent offen legt. Die technischen Details sind in den Kernel Sourcen Dokumentiert




