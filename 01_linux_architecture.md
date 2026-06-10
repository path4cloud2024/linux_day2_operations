## Linux Architecture

```mermaid
flowchart TD
  subgraph UserSpace["User Space (Applications & Libraries)"]
    A["User Applications (Web Browsers, Editors)"]
    B["System Libraries (glibc)"]
  end

  C{"System Calls (syscalls)"}

  subgraph KernelSpace["Kernel Space (Core OS)"]
    D["System Call Interface"]
    E["Memory Management"]
    F["Process Management"]
    G["File Systems"]
    H["Device Drivers"]
  end

  subgraph Hardware["Hardware"]
    I["CPU, RAM, Disks, Network Cards"]
  end

  A --> B --> C --> D
  D --> E
  D --> F
  D --> G
  D --> H
  E --> I
  F --> I
  G --> I
  H --> I

