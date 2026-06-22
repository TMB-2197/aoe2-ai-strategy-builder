**This tool is still not ready. This is just a preview of the documentation**

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

## Quick-start guide
- Open 'data/setup.ini' and change the values, such as output paths
- Read the example build orders in 'data/build-orders/'
- Read documentation.md and best-practices.md
- Remove the existing build orders and replace with your own
- Run 'bin/strategy_xx.exe' to generate your AI script
- Fix any errors reported by the program
- Test and update the build-order as required

## Rules for releasing your AI
- properly tested & optimized (it doesn't float resources; or fail to get build-order items)
    - *you AI doens't have to be strong; just optimized*
- cannot remove chats that were added automatically
- must specify that is was created using the AI Strategy Builder and provide a link to this page
- you cannot include any strategies that were released as part of any other AI

