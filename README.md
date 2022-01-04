# 2048_MC

A Reinforcement Learning Monte Carlo agent that solve the popular 2048 game in less than a minute without even training requiered.

<p align = "center">
  https://github.com/cargicar/2048_MC/blob/main/2048.mp4
</p>

# Game description

2048 is a single-player board game popularized on cell phone in recent years. The game mechanics is as follows: Start with an 4x4 almost empty board, with two random positions on the board being occupied each by the number 2 (or with a smaller porbability a number 4). The gamer can slide a tile in four directions (up, down, left, right) and doing so will slide the whole board to that side. If the two slides containing the same number collide, they can merge into one containing the sum of them both. The name of the name implies that a gamer wins when it reach a merger equal to 2048. In reality, you can keep merging even after getting 2048 and I am unaware of what is the upper limit number for the game, but I guess will be very large, if any. The game ends when there are not allowed slides, which means that there is neither, empty tiles (or with zero value) neither near-neighbors with the same value.

# Reinforcement Learning Method of Choice

At first I tried to solve the game by using a deep-Q learning architecture, similar to the one employed by deepmind to solve the atari games. But first, it was very hard to tune, because it requires at least four hyperparameters (the epsilon for the epsilon-greedy policy, batch size for the replay buffer, the number of frames for updating the policy, the number of frame to increase greedines). Second it takes a long time to train (each single experiment I did took at leat one hour using a Tesla GPU from google computing cloud). Third it requires some Reward Enginering, which is perhaps the hardest part and the results are greatly dependent (and in my opinon fairly inconsisten) on the reward choice. 

Then I decided to try a very simple Monte Carlo Tree Search, with just one level, which consist of approximately only 30 lines of code, with almost not additional package needed other that numpy (if any). 

Due to speed concerns, I coded the enviroment and the MC-tree in fortran, and used the method numpy.f2py to create a corresponding module in python, which I added here already.

