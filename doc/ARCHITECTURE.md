CloseCombatFree (CCF) Architecture Documentation
================================================

Welcome to the comprehensive architecture documentation for CloseCombatFree (CCF), a free and open-source real-time tactical wargame. This documentation provides an in-depth exploration of the game's codebase, design patterns, and implementation details.

**Project Information**
- **Name**: CloseCombatFree (CCF)
- **Version**: 0.0.5 (Early Development)
- **Author**: Tomasz 'sierdzio' Siekierda
- **License**: GNU GPLv3
- **Repository**: [Project repository location]

-------------------------------------------------------------------------------

Table of Contents
-----------------

1.  [Project Overview](#project-overview)
2.  [Architecture Documentation Chapters](#architecture-documentation-chapters)
3.  [Supplementary Documentation](#supplementary-documentation)
4.  [Reading Guide](#reading-guide)
5.  [Quick Start](#quick-start)
6.  [Project Statistics](#project-statistics)

-------------------------------------------------------------------------------

Project Overview
----------------

CloseCombatFree (CCF) is a free, open-source alternative to the classic Close Combat real-time tactical wargame series. The project was born from the need for a modern, cross-platform implementation that can run natively on contemporary operating systems without compatibility issues. While the original Close Combat series is now dated and difficult to run on modern Windows systems or through Wine on Linux, CCF leverages modern technology to provide a smooth gaming experience across multiple platforms.

The game is built using a hybrid technology stack that combines the performance of C++ with the flexibility of declarative UI development. The core game engine and logic are implemented in C++17, providing high performance for real-time tactical simulations, complex pathfinding calculations, and physics-based interactions. The user interface and game scenarios utilize QML (QtQuick 2.1), enabling rapid UI development, dynamic scenario scripting, and easy modding capabilities. This architecture allows CCF to target Linux, Windows, macOS, Android, iOS, and other platforms supported by the Qt5 framework. The build system uses qmake, which is standard for Qt projects and provides good cross-platform build support.

-------------------------------------------------------------------------------

Architecture Documentation Chapters
-----------------------------------

This comprehensive architecture documentation is organized into ten detailed chapters, each focusing on a specific aspect of the CCF codebase. Each chapter provides detailed explanations, code examples, diagrams (where applicable), and best practices for understanding and working with that part of the system.

### Chapter 1: Overview and High-Level Architecture
**File**: [chapters/01-overview.md](chapters/01-overview.md) (1,189 lines)

This chapter introduces the fundamental architecture of CCF, including:
- System architecture overview and component interaction diagrams
- Core design patterns used throughout the codebase (State, Observer, Command patterns)
- Main entry points and application lifecycle management
- Threading model and concurrency considerations
- Communication mechanisms between C++ backend and QML frontend
- Data flow architecture and event handling systems
- High-level module organization and dependency structure

**Recommended for**: All developers, especially those new to the project.

---

### Chapter 2: Object System
**File**: [chapters/02-object-system.md](chapters/02-object-system.md) (1,387 lines)

This chapter details the object-oriented foundation of CCF:
- Base object classes (CcfObjectBase) and inheritance hierarchy
- Unit system architecture (soldiers, vehicles, equipment)
- Object properties, metadata, and reflection system
- Memory management and object lifecycle
- Factory patterns for object creation
- Type system and dynamic casting considerations
- Object serialization and persistence mechanisms
- Component-based design for extensible unit types

**Recommended for**: Game logic developers, unit system implementers.

---

### Chapter 3: State Machine and Action System
**File**: [chapters/03-state-machine.md](chapters/03-state-machine.md) (1,484 lines)

This chapter explores the state management infrastructure:
- CcfScenarioState: Central state management class
- Unit states and state transitions (READY, MOVING, FIRING, etc.)
- State machine implementation patterns
- Action queue system and execution flow
- Real-time state synchronization between simulation and UI
- State persistence for save/load functionality
- Handling concurrent state changes and race conditions
- Event-driven state updates and callbacks

**Recommended for**: Gameplay programmers, AI developers.

---

### Chapter 4: Order System and AI Pathfinding
**File**: [chapters/04-orders-pathfinding.md](chapters/04-orders-pathfinding.md) (1,326 lines)

This chapter covers command execution and navigation:
- Order types: Move, Attack, Defend, Ambush, Sneak, etc.
- Order queue system and prioritization
- Pathfinding algorithms and terrain analysis
- Line of Sight (LOS) calculations and detection
- AI decision-making framework
- Unit formations and group movement
- Obstacle avoidance and dynamic path recalculation
- Waypoint system and advanced movement orders

**Recommended for**: AI programmers, gameplay developers.

---

### Chapter 5: Graphics and Rendering System
**File**: [chapters/05-graphics.md](chapters/05-graphics.md) (1,546 lines)

This chapter documents the visual presentation layer:
- QtQuick 2.1 scene graph architecture
- Custom QML components for game entities
- Sprite and animation systems
- Particle system implementation (redesigned in v0.0.5)
- Camera controls and viewport management
- Zoom and pan implementation with dimension preservation
- Rendering optimization techniques
- Graphics asset pipeline and loading
- Visual effects and post-processing

**Recommended for**: Graphics programmers, UI/UX developers.

---

### Chapter 6: World, Map, and Terrain System
**File**: [chapters/06-world-terrain.md](chapters/06-world-terrain.md) (1,206 lines)

This chapter describes the game world infrastructure:
- Map coordinate systems and coordinate transformations
- Terrain types and their properties (cover, movement cost, visibility)
- Map cluster system for modularity
- Obstacle and prop management
- Terrain generation and map editor integration
- Scenario loading and world initialization
- Dynamic terrain modification during gameplay
- Terrain information display system

**Recommended for**: Level designers, world system developers.

---

### Chapter 7: Configuration Files and Data Schemas
**File**: [chapters/07-configuration.md](chapters/07-configuration.md) (1,352 lines)

This chapter explains data-driven design:
- Configuration file formats (JSON, XML, QML)
- Unit definition schemas and validation
- Weapon and equipment data structures
- Game balance parameters and tuning
- Localization and internationalization support
- Preferences and settings system
- Mod configuration and metadata
- Data schema versioning and migration

**Recommended for**: Modders, game designers, technical writers.

---

### Chapter 8: Asset Structure and File Formats
**File**: [chapters/08-assets.md](chapters/08-assets.md) (1,227 lines)

This chapter covers the asset pipeline:
- Directory structure and organization
- Image formats and requirements (sprites, textures, backgrounds)
- Audio asset management
- Resource compilation with Qt Resource System (QRC)
- Non-QRC file loading support (added in v0.0.4)
- Asset naming conventions and versioning
- Dynamic asset loading and caching
- Public domain asset sources (NASA imagery, etc.)
- Asset validation and integrity checking

**Recommended for**: Artists, asset managers, modders.

---

### Chapter 9: UI System and Combat Module
**File**: [chapters/09-ui-combat.md](chapters/09-ui-combat.md) (1,567 lines)

This chapter details user interface implementation:
- Menu system architecture (OptionsMenu, PreferencesMenu, ScenarioMenu)
- TopMenu and BottomMenu with flickability support
- Dynamic menu parameterization for responsive design
- Order interface and command input handling
- Group selection and unit grouping UI
- Combat visualization (shot trajectories, hit effects)
- Status indicators and unit markers
- Side marker sets and customization
- Touch and mouse input handling
- Mobile UI adaptations (terrainInfoMode)

**Recommended for**: UI developers, frontend programmers.

---

### Chapter 10: Build System and Dependencies
**File**: [chapters/10-build-system.md](chapters/10-build-system.md) (1,184 lines)

This chapter provides build and deployment information:
- qmake project structure (.pro and .pri files)
- Dependency requirements (Qt5, QtQuick 2.1)
- Cross-platform build configuration
- Documentation generation with Doxygen
- doxyqml for QML documentation
- makedocs automation tool
- Project archiving with archiveProject tool
- QML 1.x to 2.0 conversion tool
- Installation and packaging procedures
- Development environment setup

**Recommended for**: Build engineers, release managers, new contributors.

-------------------------------------------------------------------------------

Supplementary Documentation
---------------------------

In addition to this comprehensive architecture documentation, CCF includes several other documentation resources:

### User Documentation
Located in `doc/user/`, this documentation is designed for players and end-users:
- Game manuals and tutorials
- Control reference guides
- How-to-play guides
- Tips and strategies

### Developer Documentation
Located in `doc/developer/`, this documentation is for contributors:
- API reference documentation
- Coding standards and guidelines
- Contribution procedures
- Testing procedures

### Quick Reference
- **Keyboard Reference**: `doc/KEYBOARD_reference` - Complete list of keyboard shortcuts and controls
- **README**: Project overview and basic information at repository root
- **CHANGELOG**: Version history and changes between releases

### Generated Documentation
CCF uses Doxygen for API documentation generation:
- Run `doxygen user.docconf` to generate user documentation (HTML and QCH)
- Run `doxygen developer.docconf` to generate developer documentation
- Requires Doxygen and optionally KDE's doxyqml for QML support

-------------------------------------------------------------------------------

Reading Guide
-------------

This architecture documentation is designed to serve different audiences. Follow the recommended paths below based on your role and interests:

### New Developers
**Start here**: [Chapter 1: Overview](chapters/01-overview.md)

As a new developer, begin with the high-level architecture to understand how components interact. Then dive into the object system to understand the fundamental building blocks.

**Reading Path**:
1. Chapter 1: Overview and High-Level Architecture
2. Chapter 2: Object System
3. Chapter 3: State Machine and Action System
4. Chapter 10: Build System (to set up your environment)
5. Other chapters as needed for your specific tasks

**Prerequisites**:
- C++17 knowledge
- Qt5/QML familiarity
- Game development concepts

### Modders
**Start here**: [Chapter 7: Configuration](chapters/07-configuration.md)

If you're interested in creating new units, maps, scenarios, or total conversions, focus on the data and asset chapters.

**Reading Path**:
1. Chapter 7: Configuration Files and Data Schemas
2. Chapter 8: Asset Structure and File Formats
3. Chapter 6: World, Map, and Terrain System
4. Chapter 2: Object System (for understanding unit structures)

**Note**: The modding API is currently alpha-quality (targeting stability by v0.1.0). Expect some changes until v1.0.0.

### UI Developers
**Start here**: [Chapter 5: Graphics](chapters/05-graphics.md)

For developers working on the user interface, visual effects, or input handling.

**Reading Path**:
1. Chapter 5: Graphics and Rendering System
2. Chapter 9: UI System and Combat Module
3. Chapter 1: Overview (for understanding C++/QML communication)
4. Chapter 3: State Machine (for UI state synchronization)

### Build Engineers
**Start here**: [Chapter 10: Build System](chapters/10-build-system.md)

For those setting up build infrastructure, CI/CD pipelines, or release processes.

**Reading Path**:
1. Chapter 10: Build System and Dependencies
2. Chapter 8: Asset Structure (for asset pipeline integration)
3. Other chapters for understanding what gets built

### Researchers and Academics
**Read all chapters in order**

For those studying the codebase for research, education, or comprehensive understanding.

**Reading Path**:
1. Chapter 1: Overview and High-Level Architecture
2. Chapter 2: Object System
3. Chapter 3: State Machine and Action System
4. Chapter 4: Order System and AI Pathfinding
5. Chapter 5: Graphics and Rendering System
6. Chapter 6: World, Map, and Terrain System
7. Chapter 7: Configuration Files and Data Schemas
8. Chapter 8: Asset Structure and File Formats
9. Chapter 9: UI System and Combat Module
10. Chapter 10: Build System and Dependencies

-------------------------------------------------------------------------------

Quick Start
-----------

### Prerequisites

Before building CCF, ensure you have the following installed:

**Required**:
- Qt5 (5.x or later)
- QtQuick 2.1 or later
- qmake
- C++17 compatible compiler (GCC, Clang, MSVC)

**Optional** (for documentation generation):
- Doxygen
- doxyqml (KDE project for QML documentation)

### Building CCF

1. **Clone the repository** (if not already done):
   ```bash
   git clone <repository-url>
   cd closecombatfree
   ```

2. **Generate Makefiles with qmake**:
   ```bash
   qmake CloseCombatFree.pro
   ```

3. **Build the project**:
   ```bash
   make
   ```
   Or on Windows with MSVC:
   ```bash
   nmake
   ```

4. **Run the game**:
   ```bash
   ./CloseCombatFree
   ```

### Building Documentation

To generate the complete documentation suite:

```bash
# Generate user documentation (HTML and QCH)
doxygen user.docconf

# Generate developer documentation (HTML and QCH)
doxygen developer.docconf

# Or use the automated tool
tools/makedocs
```

Generated documentation will be available in the `doc/html/` and `doc/qch/` directories.

### Development Tips

- **Enable frame rate display**: Set `QML_SHOW_FRAMERATE=1` environment variable to see render timing
- **Debug mode**: Build with `CONFIG+=debug` for debugging symbols
- **Parallel builds**: Use `make -j$(nproc)` on Linux for faster compilation

-------------------------------------------------------------------------------

Project Statistics
------------------

The following statistics provide an overview of the CCF codebase scope:

### File Counts

| Category | File Count | Description |
|----------|------------|-------------|
| **Total Source Files** | ~258 files | All project files including code, assets, and documentation |
| **C++ Source Files** | ~122 files | Implementation files (.cpp) and headers (.h) |
| **QML Files** | ~50+ files | UI components and game scenarios |
| **Documentation Files** | 10 chapters | Architecture documentation (this suite) |
| **Configuration Files** | Multiple | .pro, .pri, JSON, XML configuration files |

### Documentation Statistics

| Chapter | Lines | Focus Area |
|---------|-------|------------|
| Chapter 1: Overview | 1,189 | High-level architecture |
| Chapter 2: Object System | 1,387 | Core object model |
| Chapter 3: State Machine | 1,484 | State management |
| Chapter 4: Orders & Pathfinding | 1,326 | AI and navigation |
| Chapter 5: Graphics | 1,546 | Rendering system |
| Chapter 6: World & Terrain | 1,206 | Environment system |
| Chapter 7: Configuration | 1,352 | Data schemas |
| Chapter 8: Assets | 1,227 | Asset pipeline |
| Chapter 9: UI & Combat | 1,567 | Interface system |
| Chapter 10: Build System | 1,184 | Build infrastructure |
| **Total Documentation** | **~12,500 lines** | Comprehensive coverage |

### Version History

| Version | Date | Major Features |
|---------|------|----------------|
| v0.0.5 | 2012.xx.xx | Qt5 port, expanded docs, particle redesign, LOS detection, side markers |
| v0.0.4 | 2012.02.10 | Save/load, LOS detection, QML 2.0, doxygen docs |
| v0.0.3 | 2011.12.20 | Scripting, waypoints, preferences, zooming |

### Unit Statuses Implemented

The game implements the following unit states:
- **Movement**: READY, MOVING, MOVING FAST, SNEAKING
- **Combat**: AMBUSHING, DEFENDING, AIMING, FIRING, LOADING, COVERING
- **Condition**: KIA, DAMAGED, WOUNDED, INCAPACITATED, BROKEN, BERSERK
- **Actions**: FIXING, ROTATING

-------------------------------------------------------------------------------

Additional Resources
--------------------

### External Dependencies and Tools

- **Qt Project**: https://www.qt.io/ - Cross-platform framework
- **Doxygen**: https://www.doxygen.nl/ - Documentation generator
- **doxyqml**: http://agateau.com/projects/doxyqml/ - QML support for Doxygen

### Asset Sources

Some images used in development are from public domain sources:
- NASA imagery (Haiti Deforestation photographs)
- Creative Commons licensed aerial photographs

### License Information

CCF is distributed under the GNU General Public License v3 (GPLv3). This means:
- You are free to use, modify, and distribute the software
- Source code must be made available for distributed binaries
- Modifications must be under the same license

Artwork may be licensed separately (check individual asset licenses).

-------------------------------------------------------------------------------

Contributing
------------

We welcome contributions to CCF! Whether you're a developer, artist, designer, or documentation writer, there's a way to contribute:

1. **Code Contributions**: Follow the coding standards in doc/developer/
2. **Documentation**: Help improve this architecture documentation
3. **Art Assets**: Create new units, maps, or UI elements
4. **Testing**: Report bugs and test new features
5. **Modding**: Create mods and provide feedback on the modding API

For contribution guidelines, see the developer documentation in `doc/developer/`.

-------------------------------------------------------------------------------

Contact and Support
-------------------

- **Author**: Tomasz 'sierdzio' Siekierda
- **Project Status**: Early development (v0.0.5)
- **License**: GNU GPLv3

For questions, bug reports, or feature requests, please refer to the project repository.

-------------------------------------------------------------------------------

**Last Updated**: 2012

**Document Version**: 1.0 (Architecture Documentation Suite)

-------------------------------------------------------------------------------

*End of Architecture Documentation Index*
