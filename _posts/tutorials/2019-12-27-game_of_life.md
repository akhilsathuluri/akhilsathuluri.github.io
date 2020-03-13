---
layout: tutorial
title: "Simulating the game of life in C++"
date: 2019-12-27
category: tutorials
summary: The game of life is an example of how complex behaviour can emerge from a simple set of rules.
notempty: "True"
image: /images/display_images/game_of_life.gif
---

All the codes are available in [this](https://github.com/akhilsathuluri/game_of_life) repository. 

The Eigen package is used to create a 2D array which is the game of life universe. The trick is to use the command "system("clear")" in the code to reprint at the same place by clearing the screen. Further, the print rate can be controlled using the "usleep(100000)" command to generate pleasing prints in the terminal. This is my first code written exploring [cellular automata](https://en.wikipedia.org/wiki/Cellular_automaton) systems.

Wikipedia interestingly describes it as a [zero-player](https://en.wikipedia.org/wiki/Zero-player_game) game. It was first proposed by John Horton Conway in 1970. You can see the game explained by himself in this [Numberphile](https://www.youtube.com/watch?v=E8kUJL04ELA) video.


