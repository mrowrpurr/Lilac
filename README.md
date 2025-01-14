> _This fork updates `Lilac` to:_
> - _Print test output to the Skyrim ~ console_
> - _Show the test summary as a notification (top-left of screen)_
>
> _This requires \*either\* [PapyrusUtil][] or [ConsoleUtil][]_
> _(to print to the console)_
>
> _There are 2 releases available, 1 for [PapyrusUtil][] and another for [ConsoleUtil][]._
>
> _**Download this fork in the [Releases][] section of the GitHub page (to the right)**_
>
> _~_ _@mrowrpurr_

[PapyrusUtil]: https://www.nexusmods.com/skyrimspecialedition/mods/13048
[ConsoleUtil]: https://www.nexusmods.com/skyrimspecialedition/mods/24858
[Releases]: https://github.com/mrowrpurr/Lilac/releases

---

- **[Download Fork (requires PapyrusUtil)](https://github.com/mrowrpurr/Lilac/releases/download/v1.2c/Console_Lilac_PapyrusUtil.7z)** `<---` **recommended version**
- **[Download Fork (requires ConsoleUtil)](https://github.com/mrowrpurr/Lilac/releases/download/v1.2c/Console_Lilac_ConsoleUtil.7z)** `<---` _difficult to use, don't use this_

![Screenshot](https://user-images.githubusercontent.com/87039589/130496507-1607079a-3b0f-4ccf-a952-40e9fcfd2c89.png)

---

![Lilac](http://i.imgur.com/YzpYlCG.png "Lilac")
### A Papyrus Testing Framework

Lilac is a unit testing framework for Papyrus. It has a simple and direct syntax so that you can easily write tests to increase the quality of your mods.

It is inspired by [Jasmine](http://jasmine.github.io) for Javascript. It is currently available for **Skyrim** and **[Fallout 4](https://github.com/chesko256/LilacFO4)**.

Lilac can be built into your mod and distributed with it. Your tests will only run when you decide to run them; your users will most likely never know they exist.

### Documentation

Documentation can be found on the Lilac GitHub Wiki: https://github.com/chesko256/Lilac/wiki

### Requirements

Lilac does not have any extra requirements or dependencies, just the Skyrim base game.

### Installation
All of Lilac is contained in a single script file, **Lilac.psc**. There is no complex set-up or installation.

Download and install the [latest release](https://github.com/chesko256/Lilac/releases) using a mod manager, or just drop Lilac.psc into your `Scripts/Source` directory. Then, create a new script that extends Lilac and away you go:

    scriptname MyTests extends Lilac

### Writing Tests
Lilac allows you to write tests in a clear and expressive syntax.

    function MonsterSpawnerSuite()

        it ( "should spawn monsters", MonsterSpawnerTest() )

    endFunction


    function MonsterSpawnerTest()

        spawner.SpawnMonsters()
        expectInt ( spawner.SpawnedMonsterCount, to, beEqualTo, 20 )
        expectRef ( spawner.LastSpawnedMonster, notTo, beNone )
        expectForm ( spawner.LastSpawnedMonsterType, to, beEqualTo, MegaDragon )

    endFunction

### Running Tests
Lilac test scripts are attached to quests. To run your tests, just start the quest:
    
    startquest MyTestQuest

The results will be printed to your Papyrus log.

### Version History

v1.2: Added spec expectation number to test runner output in order to assist debugging. Added 'enabled' flag in order to help prevent unwanted accidental execution by users at runtime. Removed the 'contain' matcher in order to remove the SKSE dependency.

v1.1: Fixed bugs related to reports being wrong when the Actual was a blank string.

v1.0: Initial Release

### License
Lilac is released under the [MIT License](https://github.com/chesko256/Lilac/blob/master/MIT.LICENSE).

### Contact
Contact Chesko at chesko.tesmod@gmail.com
