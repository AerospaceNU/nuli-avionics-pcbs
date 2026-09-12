# Avionics PCBs

This repository contains NULI-Avionics PCB designs and reusable hardware components created with [KiCad](https://www.kicad.org/).

The repository is organized around individual PCB projects. Each PCB contains its own source files, documentation, 3D models, and fabrication outputs. Reusable components are maintained separately under `common-components/`.

**Any naming examples used below are just to show repo structure and are not indicative of good naming practices**.

## Repository Structure

```text
.
├── README.md
├── LICENSE
│
└── hardware/
    ├── boards/
    │   ├── <board-name>/
    │   │   ├── README.md
    │   │   ├── <board-name>.kicad_pro
    │   │   ├── <board-name>.kicad_sch
    │   │   ├── <board-name>.kicad_pcb
    │   │   ├── 3d-models/
    │   │   └── fabrication/
    │   │
    │   └── <another-board>/
    │       └── ...
    │
    └── common-components/
        ├── <component-name>/
        │   ├── <component-name>.kicad_sym
        │   ├── <component-name>.kicad_mod
        │   └── <component-name>.step
        │
        └── <another-component>/
            └── ...
```

## Boards

All PCB projects are located under:

```text
hardware/boards/
```

Each PCB has its own directory containing everything specific to that board.

A typical board directory has the following structure:

```text
hardware/boards/usb-c-breakout/
├── README.md
├── usb-c-breakout.kicad_pro
├── usb-c-breakout.kicad_sch
├── usb-c-breakout.kicad_pcb
├── 3d-models/
└── fabrication/
```
It will also typically have its own symbol and footprint library including any combination of both external and common components.
### KiCad Project Files

| File         | Description        |
| ------------ | ------------------ |
| `.kicad_pro` | KiCad project file |
| `.kicad_sch` | Schematic          |
| `.kicad_pcb` | PCB layout         |

The KiCad source files are the digital representation of the PCB design.

### 3D Models

Board-specific 3D models are stored in the board's `3d-models/` directory.

```text
3d-models/
├── enclosure.step
├── connector.step
├── mounting-bracket.step
└── <board-name>.step
```

Reusable component 3D models should instead be stored with their corresponding component under `common-components/`.

### Fabrication Files

Manufacturing outputs are stored in the board's `fabrication/` directory.

Typical contents include (basically whatever the program outputs + the BOM):

```text
fabrication/
├── gerbers/
├── drill/
├── bom/
├── pick-and-place/
└── assembly/
```

Fabrication files should correspond to a specific PCB revision/release.

## Common Components

Reusable components are stored under:

```text
hardware/common-components/
```

Each component gets its own directory containing all of the resources required to use that component.

For example:

```text
hardware/common-components/
└── usb-c-receptacle/
    ├── usb-c-receptacle.kicad_sym
    ├── usb-c-receptacle.kicad_mod
    └── usb-c-receptacle.step
```

Keeping the symbol, footprint, and 3D model together makes components easy to find, copy, reuse, and version.

### Component Guidelines

A component should be placed in `common-components/` when it is intended to be reused by multiple PCB projects.

Components that are unique to a single PCB should generally remain with that PCB project (this will likely be very few components).

Each component should use a descriptive directory name and consistent filenames:

```text
<component-name>/
├── <component-name>.kicad_sym
├── <component-name>.kicad_mod
└── <component-name>.step
```

Not every component necessarily requires all three files. For example, a component may just use a standard 0603 footprint.

## Versions and Revision History

PCB revisions are versioned independently for each board.

The repository does **not** use a single repository-wide hardware version. Each PCB project maintains its own revision history, allowing individual boards to be developed and released independently.

For example:

```text
hardware/boards/
├── usb-c-breakout/
├── power-board/
└── sensor-board/
```

Each board may have its own revision sequence:

```text
usb-c-breakout:
    v1.0.0
    v1.1.0
    v1.2.0

power-board:
    v1.0.0
    v2.0.0

sensor-board:
    v1.0.0
    v1.1.0
```

### Git History

Git commits provide the complete historical record of every PCB project.

Changes to a board should be committed with the board name and revision in the commit message.

For example:

```bash
git add hardware/boards/usb-c-breakout/
git commit -m "usb-c-breakout: Rev 1.2.0"
```

The history for an individual board can be viewed with:

```bash
git log -- hardware/boards/usb-c-breakout/
```

This shows only commits that affected that PCB.

### Board Revision Tags

When a PCB revision is considered complete, a Git tag may be created for that specific board revision.

Board tags should use the board name as a prefix:

```text
usb-c-breakout/v1.0.0
usb-c-breakout/v1.1.0
usb-c-breakout/v1.2.0

power-board/v1.0.0
power-board/v2.0.0
```

These tags are **board revision references**, not repository-wide releases.

A board revision tag identifies the exact Git commit from which that PCB revision was produced. This makes it possible to return to a known historical version of a board at any time.

### Viewing an Older Board Revision

To inspect a specific revision of a board, first identify its revision tag:

```bash
git tag --list "usb-c-breakout/*"
```

For example:

```text
usb-c-breakout/v1.0.0
usb-c-breakout/v1.1.0
usb-c-breakout/v1.2.0
```

The complete repository can be checked out at a particular board revision:

```bash
git checkout usb-c-breakout/v1.2.0
```

The `hardware/boards/usb-c-breakout/` directory will then contain the exact KiCad source files associated with that revision.

The repository does not need separate directories for historical revisions.

For example, the repository should **not** contain:

```text
usb-c-breakout-v1/
usb-c-breakout-v2/
usb-c-breakout-v3/
```

Instead, it contains one board directory whose history is maintained by Git.

### Viewing a Historical Board Without Changing the Current Checkout

A historical file can also be retrieved directly from Git:

```bash
git show usb-c-breakout/v1.2.0:hardware/boards/usb-c-breakout/usb-c-breakout.kicad_pcb
```

For more extensive work with an older revision, a separate Git worktree can be created so that the historical board can be opened in KiCad without changing the main working directory.

### Fabrication Outputs

Fabrication outputs should be associated with the board revision from which they were generated.

For example:

```text
hardware/boards/usb-c-breakout/
└── fabrication/
    ├── gerbers/
    ├── drill/
    ├── bom/
    └── assembly/
```

When a revision is finalized, the fabrication outputs should be generated from the exact source revision represented by the corresponding Git tag.

This ensures that:

```text
usb-c-breakout/v1.2.0
```

always identifies the KiCad source used to produce the Rev 1.2.0 manufacturing files.

### Revision History

Each board can maintain a revision history in its own `README.md`.

For example:

```markdown
## Revision History

| Version | Date | Changes |
|---|---|---|
| v1.0.0 | YYYY-MM-DD | Initial prototype |
| v1.1.0 | YYYY-MM-DD | Updated USB-C connector |
| v1.2.0 | YYYY-MM-DD | Changed ESD protection |
```



### Release Contents

A PCB release should include:

* KiCad schematic
* KiCad PCB layout
* KiCad project
* Board-specific 3D models
* Fabrication outputs
* BOM, when applicable
* Assembly files, when applicable
* Relevant documentation

Fabrication outputs should be generated from the same source revision represented by the release.

## PCB Documentation

Every PCB should contain its own `README.md`.

The PCB README should document:

* Authors / Contributors
* Purpose of the board
* Current revision/version
* Current development status
* Important design notes
* Manufacturing information
* Known issues
* Revision history

A PCB README can use the following template:

```markdown
# <PCB Name>

Short description of the board.

## Contributors
Authors / Contributors
## Status

**Version:** v1.0.0  
**Status:** Prototype

## Description

Describe the purpose of the board and what it is intended to do.

## Manufacturing

- Layers: ...
- Thickness: ...
- Surface finish: ...
- Minimum trace/space: ...
- Manufacturer: ...
(Basically all relavent stackup information)

## Known Issues

- Issue 1
- Issue 2

## Revision History

| Version | Date | Changes |
|---|---|---|
| v1.0.0 | YYYY-MM-DD | Initial release |

```

## Design Guidelines

### Keep Boards Self-Contained

Each board should contain the resources that are specific to that board.

```text
boards/my-board/
├── README.md
├── my-board.kicad_pro
├── my-board.kicad_sch
├── my-board.kicad_pcb
├── 3d-models/
└── fabrication/
```

Avoid putting board-specific files into `common-components/`.

### Reuse Common Components

If a component is likely to be used by multiple boards, place its KiCad resources in:

```text
hardware/common-components/<component-name>/
```

### Generated Files

Fabrication outputs are generated from the KiCad source files.

When possible, generated files should be associated with a specific release so that it is clear which source revision they were generated from.

## KiCad Version

The repository should document the KiCad version used to create or modify the projects when compatibility is important.

Projects should ideally be maintained using the same major KiCad version (Though its likely fine to update them, just document the new Kicad version).

## Adding a New PCB

When adding a new PCB:

1. Create a directory under `hardware/boards/`.
2. Give the directory a descriptive name.
3. Add the KiCad project, schematic, and PCB files.
4. Add a PCB-specific `README.md`.
5. Add board-specific 3D models under `3d-models/`.
6. Add fabrication outputs under `fabrication/` when appropriate.
7. Place reusable components in `common-components/`.
8. Run electrical rules checks and design-rule checks.
9. Update the board documentation and revision information.

## Licensing

See `LICENSE` for information about the licensing of the hardware designs, documentation, and associated files.
