<!---Documatic-section-fixed: top1-start--->
# Showdown  ![umbreon](https://play.pokemonshowdown.com/sprites/xyani/umbreon.gif)
A Pokémon battle-bot that can play battles on [Pokemon Showdown](https://pokemonshowdown.com/).

The bot can play single battles in generations 3 through 8 however some of the battle mechanics assume it is gen8.

<!---Documatic-section-fixed: top1-end--->

**Last updated:** 2022-01-14\
_Document generation aided by **Documatic**_

## Getting started

* python 3.6 or greater
* Install requirements with `pip install -r requirements.txt`
* Codebase is not installable as a python package 

### Config

This project uses `environs` to load environment variable from a `.env` file.
**Do not add the .env to source control.**
The following environment variables are accepted

```
BATTLE_BOT              default = safest
SAVE_REPLAY
USE_RELATIVE_WEIGHTS
GAMBIT_PATH
MAX_SEARCH_DEPTH
DYNAMIC_SEARCH_DEPTH
GREETING_MESSAGE
WEBSOCKET_URI           sim.smogon.com:8000
PS_USERNAME
BOT_MODE
TEAM_NAME               None
POKEMON_MODE
RUN_COUNT               1
ROOM_NAME
```

### Docker

The project uses Docker to build a maintainable environment for the project, using python:3.6-slim as a base image.
The container uses ENV variables `PYTHONIOENCODING=utf-8`, `GAMBIT_PATH=gambit-enummixed`.
The entrypoint to the Docker container is `run.py`:

It runs an asynchronous function `run.showdown`:
It creates a configuration file from system environment variables.
It runs a loop which challenges a user or accepts a match
and runs a pokemon battle.
The loop tracks the number of wins, losses, and battles run.
The loop breaks if more battles are run than the config value.
Raises a ValueError if the bot mode is invalid.

### Developers

* Unit tests are stored in `tests/` (uses unittest)
* There are no specific developer requirements
* The project uses GitHub Actions for CI/CD.

| CI File | Purpose |
|:--------|:--------|
| `.github/workflows/pythonapp.yml` | Runs unit tests. Executes on push to branch `master` and pull request to branch `master` |


## Code Overview

### Entrypoints

There are 0 source code entrypoints in top-level `__main__`/`__init__` files.
The codebase has a flat structure with no central package.
Source code is in:
`data/`,
`showdown/`,
`teams/`.

### Class structure

#### showdown.battle.Battle

The `showdown.battle.Battle` base class has 4 child classes:
* `showdown.battle_bots.most_damage.main.BattleBot`
* `showdown.battle_bots.nash_equilibrium.main.BattleBot`
* `showdown.battle_bots.ou_scraped_teams.main.BattleBot`
* `showdown.battle_bots.safest.main.BattleBot`

```python
class showdown.battle.Battle(self, battle_tag)
```

```python
    def prepare_battles(self, guess_mega_evo_opponent=True, join_moves_together=False)
```

Returns a list of battles based on this one
The battles have the opponent's reserve pokemon's unknowns filled in
The opponent's active pokemon in each of the battles has a different set.

#### showdown.battle_bots.most_damage.main.BattleBot

```python
class showdown.battle_bots.most_damage.main.BattleBot(*args, **kwargs)
```

```python
    def find_best_moves(self)
```

It loops through


## API

### **showdown/**

#### tests/

<!---Documatic-section-file: tests/test_instruction_generator.py--->

##### test_instruction_generator.py


File has 52 lines added and 26 lines removed
                in the past 4 weeks. pmariglia <mariglia4423@gmail.com> is the inferred code owner.


<!---Documatic-section-file: tests/test_battle_modifiers.py--->

##### test_battle_modifiers.py


File has 474 lines added and 0 lines removed
                in the past 4 weeks. pmariglia <mariglia4423@gmail.com> is the inferred code owner.


<!---Documatic-section-file: tests/test_battle_mechanics.py--->

##### test_battle_mechanics.py


File has 260 lines added and 6 lines removed
                in the past 4 weeks. pmariglia <mariglia4423@gmail.com> is the inferred code owner.


#### showdown/

##### engine/

###### special_effects/

###### abilities/

<!---Documatic-section-file: showdown/engine/special_effects/abilities/modify_attack_against.py--->

###### modify_attack_against.py


File has 38 lines added and 33 lines removed
                in the past 4 weeks. pmariglia <mariglia4423@gmail.com> is the inferred code owner.


###### moves/

<!---Documatic-section-file: showdown/engine/special_effects/moves/move_special_effect.py--->

###### move_special_effect.py


File has 15 lines added and 8 lines removed
                in the past 4 weeks. pmariglia <mariglia4423@gmail.com> is the inferred code owner.


<!---Documatic-section-file: showdown/engine/objects.py--->

###### objects.py


File has 29 lines added and 4 lines removed
                in the past 4 weeks. pmariglia <mariglia4423@gmail.com> is the inferred code owner.


<!---Documatic-section-file: showdown/engine/instruction_generator.py--->

###### instruction_generator.py


File has 29 lines added and 3 lines removed
                in the past 4 weeks. pmariglia <mariglia4423@gmail.com> is the inferred code owner.


<!---Documatic-section-file: showdown/engine/damage_calculator.py--->

###### damage_calculator.py


File has 53 lines added and 7 lines removed
                in the past 4 weeks. pmariglia <mariglia4423@gmail.com> is the inferred code owner.


<!---Documatic-section-file: showdown/engine/evaluate.py--->

###### evaluate.py


File has 14 lines added and 14 lines removed
                in the past 4 weeks. pmariglia <mariglia4423@gmail.com> is the inferred code owner.


##### battle_bots/

###### safest/

<!---Documatic-section-file: showdown/battle_bots/safest/main.py--->

###### main.py


File has 2 lines added and 38 lines removed
                in the past 4 weeks. pmariglia <mariglia4423@gmail.com> is the inferred code owner.


###### ou_scraped_teams/

<!---Documatic-section-file: showdown/battle_bots/ou_scraped_teams/main.py--->

###### main.py


File has 191 lines added and 0 lines removed
                in the past 4 weeks. pmariglia <mariglia4423@gmail.com> is the inferred code owner.


<!---Documatic-section-file: showdown/battle_bots/helpers.py--->

###### helpers.py


File has 97 lines added and 0 lines removed
                in the past 4 weeks. pmariglia <mariglia4423@gmail.com> is the inferred code owner.


<!---Documatic-section-file: showdown/battle_modifier.py--->

##### battle_modifier.py


File has 164 lines added and 34 lines removed
                in the past 4 weeks. pmariglia <mariglia4423@gmail.com> is the inferred code owner.


<!---Documatic-section-file: showdown/battle.py--->

##### battle.py


File has 27 lines added and 3 lines removed
                in the past 4 weeks. pmariglia <mariglia4423@gmail.com> is the inferred code owner.


<!---Documatic-section-file: showdown/run_battle.py--->

##### run_battle.py


File has 23 lines added and 1 lines removed
                in the past 4 weeks. pmariglia <mariglia4423@gmail.com> is the inferred code owner.

<!---Documatic-section-fixed: bottom1-start--->
## Questions? Wanna Chat?
Send me a message on discord: pmariglia#5568
<!---Documatic-section-fixed: bottom1-end--->
