## Version 1.0
**version 1.0 (alpha)** is released. This is just an alpha version so please don't redistribute generated AI scripts yet. There are still bugs and features that don't work, though many features do work. Some of the documentation is outdated and everything is subject to change at this stage.

## Quick-start guide
- Install Microsoft Visual C++ Redistributable (Latest Supported) from the microsoft website 
  *https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist*
- Download the latest release of this tool and extract the files
- Open 'data/setup.ini' and change the values, such as output paths
- Read the example build orders in 'data/build-orders/'
- Read documentation.md and best-practices.md
- Edit the existing build orders or replace with your own (don't touch 'generic.xlsx')
- Go to the root folder; right-click and click on 'Open in Terminal'. Then run '.\bin\AiCompilerDE.exe' to generate the AI script.
- Fix any errors reported by the program
- Test and update the build-order as required

# AOEII AI Strategy Builder

### A simple & flexible tool for generating AI scripts with your own custom strategies

![Project Image](MiniAiPlayer.png)

## How?
- It uses a simple but flexible spreadsheet format to define the strategies
- The provided exe then compiles the strategies into a complete working AI
- It uses the Immortal AI script as a base; designed with flexibility in mind
- Despite being generated, the strategies can still be well optimized

## Compatible Game versions
- Age of Empires II (Definitive Edition)
- Age of Empires II (CD version) + UserPatch 1.5
- Age of Empires II (CD version) + UserPatch 1.5 + Wololo Kingdoms

## Compatible Settings
- Map: any (including arabia, rivers, nomad, islands, migration, etc)
- Civ: any (except custom civs, future expansions & civ changes)
- Game mode: conquest; low to high resources; non-turbo

## Rules for releasing your AI
- properly tested & optimized (it does not float resources; or fail to get build-order items)
    - *you AI does not have to be strong; just optimized*
- cannot remove chats that were added automatically
- must specify that is was created using the AI Strategy Builder and provide a link to this page
