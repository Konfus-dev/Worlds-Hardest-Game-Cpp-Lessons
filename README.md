# World's Hardest Game C++ Tutorial (raylib + CMake)

This repository is a hands-on C++ tutorial that builds a small game inspired by [The World's Hardest Game](https://www.crazygames.com/game/worlds-hardest-game). Play it for a minute before starting so the goals and feel make sense.

The tutorial teaches C++ fundamentals in a game context:
- lesson 1: project structure and basic movement
- lesson 2: pointers/references and manual memory management (including an intentional leak and fix)
- lesson 3: refactoring manual ownership to smart pointers
- lesson 4 and beyond: TBD...

We use [CMake](https://cmake.org/) so one build configuration works across Windows, macOS, and Linux, and so we can generate both Visual Studio solutions and terminal builds from the same project setup.

After you successfully set up the project following the steps below and get things building, make a fork of the repo and start here: [Lesson 1](Lessons/Lesson1.md)

## Project layout (and why)

```text
.
├── CMakeLists.txt
├── README.md
├── .clang-format
├── .clang-tidy
├── generate_project.sh
├── generate_vs2022.bat
├── Lessons/
│   ├── Lesson1.md
│   ├── Lesson2.md
│   └── Lesson3.md
├── include/
│   └── App.h
└── src/
    ├── App.cpp
    └── main.cpp
```

- `Lessons/`: step-by-step tutorial path. Keep lesson content separate from runtime code so learners can follow in order.
- `CMakeLists.txt`: the build recipe for the project. It tells CMake how to configure the project, fetch/find dependencies like raylib, and generate IDE project files (such as Visual Studio solutions) or command-line build files. Learn more: [YouTube: CMake tutorial for beginners](https://www.youtube.com/results?search_query=cmake+tutorial+for+beginners).
- `include/` + `src/`: common C++ project layout that clearly splits declarations (`.h`) and implementation (`.cpp`), which keeps compile boundaries and file responsibilities clear. Learn more: [YouTube: C++ headers and source files for beginners](https://www.youtube.com/results?search_query=c%2B%2B+header+files+and+source+files+for+beginners).
- `main.cpp` + `App` class: `main` is the automatic C++ entry point the OS/runtime calls when your executable starts, so we keep it tiny and move game behavior into `App`. Learn more: [YouTube: C++ main function explained for beginners](https://www.youtube.com/results?search_query=c%2B%2B+main+function+explained+for+beginners).
- generator scripts: quick setup for Visual Studio and cross-platform terminals.
- `.clang-format` and `.clang-tidy`: enforces consistent style and static analysis.

## Setup

Requirements:
- [CMake 3.20+](https://cmake.org/cmake/help/latest/guide/tutorial/index.html)
- C++17 compiler
- [raylib](https://www.raylib.com/) (the project fetches it automatically if not found locally)
- [Git](https://git-scm.com/install/) (needed when raylib is fetched from source)

Suggested:
- [Clang For Visual Studio](https://learn.microsoft.com/en-us/cpp/code-quality/clang-tidy?view=msvc-170) with format on save enabled.

Generate and build:

1. Visual Studio 2022 solution:
```bat
generate_vs2022.bat
```
Then open `build\WorldsHardestGameTutorial.sln`.

2. Cross-platform (Linux/macOS/Windows terminal or VS Code terminal):
```bash
./generate_project.sh
cmake --build build
```

Run:
- Linux/macOS: `./build/bin/WorldsHardestGameTutorial`
- Windows PowerShell: `.\build\bin\WorldsHardestGameTutorial.exe`

Without helper scripts:
```bash
cmake -S . -B build
cmake --build build
```

Feedback and TODOs:
- Put generation before clang stuff
- Make the not on windows stuff not feel like a required second step
- Make a lesson that focuses on lifetime (constructor and destructor)
- Explain how to run the application.
- Link to following tutorial at the end of a tutorial.
- Be explicit about public/private and explain how that works in C++
- We should also explain header vs source files in detail.
- We should have a tutorial that explains how things are compiled and linked and how to output intermediate and inspect it.
- Explain copies and stack vs heap memory and how pointers refs value types deal with that.
- Make users make a copy of player and then observe that when they modify the player isn't actually affected.
- Also explain derefs.
- Be sure to regularly test your changes tip!
- (Add random tips throughout and gotchas and such)
- The death count overlaps more UI.
- Explain what RAII stands for and how to make something RAII (how shared pointers work under the hood).
- Replace lesson 3 with creating our own smart pointer, this will teach all sorts of things! Copy constructors and assignment operators and how RAII works and all that!
- Need to specify where things go.
- Have users use std strings instaed of const char explain why.
- Explain the different types of casting and when to use them.
- Link to docs explaining all the things we use. (smart pointers, strings, etc..)
- At the end of the tutorial encorage folk to go crazy and make something cool now :)
