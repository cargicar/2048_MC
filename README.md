# 2048_MC

A Reinforcement Learning Monte Carlo agent that solve the popular 2048 game in less than a minute without even training requiered.

 ![Alt Text](https://github.com/cargicar/2048_MC/blob/main/2048_short.gif)

# Game description

2048 is a single-player board game popularized on its cell phone version in recent years. The game mechanics is as follows: It start with a 4x4 almost empty board, with two random positions on the board being occupied each by the number 2 (or with a smaller probability by a number 4). The gamer can slide a tile in four directions (up, down, left, right) and in doing so will slide the whole board to that side. If two slides containing the same number collide, they can merge into one containing the sum of them both. The name of the name implies that a gamer wins when it reach a merger equal to 2048. In reality, you can keep merging even after getting 2048 and I am unaware of what of an upper limit number for the game, but I guess will be very large, if any. The game ends when there are not allowed slides, which means that there is neither, empty tiles (or zero value) neither near-neighbors with the same value.

# Reinforcement Learning Method of Choice

At first I tried to solve the game by using a deep-Q learning architecture, similar to the one employed by deepmind to solve the atari games. But on one hand, it was very hard to tune, because it requires at least four hyperparameters (the epsilon for the epsilon-greedy policy, batch size for the replay buffer, the number of frames for updating the policy, the number of frames to increase greedines). On the other hand, it takes a long time to train (each single experiment I did took at least one hour using a Tesla GPU from google computing cloud) and lastly, requires some Reward Engineering, which is perhaps the hardest part and the results are greatly dependent (and in my opinion fairly inconsisten) on the reward choice. 

## Monte Carlo Tree Search

Then I decided to try a very simple Monte Carlo Tree Search (with just one level, very simple), which consist only of 30 lines of code, with almost not additional package needed other that numpy (if any). 

Due to speed concerns, I coded the environment and the MC-tree in fortran, and used the method numpy.f2py to create a corresponding module in python, which I added here already (the module can be used as any regular module in python, just print environment_2048.__doc__ to see the methods in the module). 

A jupyter notebook is added which use the above mentioned environment and let us see the game in real time. If you don't care about speed, use the function 'render(state,timestep)',  otherwise, instead just print the raw matrix print(state).

Have fun learning to play 2048 from a machine :P (At least it plays way better than me ).



