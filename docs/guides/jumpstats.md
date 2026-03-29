---
title: Jumpstats
layout: default
nav_order: 3
parent: Guides
---

# Jumpstats
This page is about the distant jumps recorded by the climb plugin.

## Types of Jumpstats

### LongJump/LJ  
An LJ is a jump done from a running start.

For a good LJ, run at full speed, crouch-jump, strafe back and forth to build speed, and land while crouched (on a platform the same height you jumped from). Crouching does not affect your air-acceleration in TF2, so feel free to hold crouch throughout your entire jump.

### Bhop/Bunnyhop/BH  
A bhop is a jump done immediately after landing another jump that starts and ends at the same height. You can bhop farther than you can LJ because your speed is maintained between the two jumps.

For a good bhop, run at full speed, crouch-jump, build speed by strafing, crouch-jump on the exact tick you land, strafe back and forth to build speed, and land while crouched.

### MultiBunnyhop/MBH  
You can use the fact that your speed is maintained if you jump on the exact tick you land on to chain bhops together for even more distance. That is an MBH.

You are likely to reach the limit of how much speed you can maintain after just two perfs. Your speed will be reduced to 120% of your maximum walking speed if it is faster than that when you hit a perf. With a single bhop, this is only a concern on Heavy.

### WeirdJump/WJ  
A WJ is a jump from a perf hit after falling (not jumping) from at most 64 hu.

You can find 64 hu tall platforms on kz_baxter_tf2.

### Jumpbug/JB  

## Jumpstat Information
After performing a jumpstat, you will see information about your jump in chat. Only you and people spectating you can see information about your jump. For example:  

```
climb.tf | LJ: 309.9 | 4 Strafes (81%) | 320 / 351 Speed | 34.8 Edge | +1 W
```

In this case, the jump was an LJ,  
the displacement (usually imprecisely called "distance") was 309.9 hu (rounded down to the nearest tenth of a hu),  
there were 4 strafes (mouse movements, not strafe key presses),  
keyboard and mouse inputs were synchronized 81% of the time,  
the pre was 320 hu/s,  
the greatest speed reached during the jump (rounded down to the nearest whole hu/s) was 351 hu/s,  
the jump started 34.8 hu (rounded down to the nearest tenth of a hu) from the edge of the platform,  
and W was released 1 tick too late.  

Opening the developer console reveals more information. For example:  

```
Indifferent jumped 309.9755 units with a Long Jump
 | 272 Block | 34.86 Edge | 4 Strafes | 81% Sync | 320.00 Pre | 351.89 Max | 1 W | 8 OL | 1 DA | 8.1 Deviation | 20.8° Width | 72.1 Height | 53 Airtime | 0.0 Offset | 53 Crouched
  #.  Sync      Gain      Loss      Airtime   Width     OL     DA     
  1.   84%      15.57      0.00     26       36.2°     3      1
  2.   90%       9.52      0.79     11       24.1°     1      0
  3.   77%       5.74      0.00      9       13.5°     2      0
  4.   57%       3.44      1.59      7        9.2°     2      0
```

Some numbers in the console are more precise than the numbers in chat.  
The console also tells you the length of the gap between the platforms you jumped between (272 hu in this case),  
overlap, the number of ticks you pressed your left and right strafe keys at the same time for (8 in this case),  
dead air, the number of ticks you weren't pressing any strafe keys for (1 in this case),  
the displacement along (not across) the blocks you were jumping across (8.1 hu in this case),  
the mean angle of your strafes (20.8 degrees in this case),  
the height of your jump (which almost always reads 72.1 hu),  
the number of ticks you were in the air for (which almost always reads 53),  
the height of the platform you jumped up onto (almost always 0.0 hu),  
and the number of ticks you spent crouched while in the air (which almost always reads 53).  

In addition to information about your entire jump, there is also information about each of your strafes. Gain refers to the amount of speed gained, in hu/s, during that strafe. Loss refers to the amount of speed lost, in hu/s, during that strafe.

You can view additional information if you enable distbug before jumping. To enable distbug, type !distbug in chat. You can type it again to toggle it off.

An example of console output with distbug enabled:  

```
[GC] LJ: 313.31350 [Block: 300 | Edge: 3.8168 | Veer: 9.6322 | Fwd: 0 | Sync: 86.79 | Max: 353.822]
[Land Edge: 9.3835 | Pre: 320.0000 | OL/DA: 0/2 | Jumpoff Angle: -18.522 | Airpath: 1.0121]
[Strafes: 6 | Airtime: 53 | Jump Direction: Forwards | Height: 72.1999]
 #.  Sync    Gain   Loss   Max  Air  OL  DA  AvgGain  Avg efficiency, (max efficiency)
 1.   0.0%   0.00   0.00  320.0   2   0   2  0.00       5% (  6%)
 2. 100.0%  12.30   0.00  332.3  20   0   0  0.61      63% (166%)
 3.  90.9%   9.79   0.10  341.9  11   0   0  0.89      53% ( 93%)
 4.  66.6%   5.63   0.00  347.6   9   0   0  0.62      39% ( 61%)
 5.  83.3%   4.63   0.59  351.6   6   0   0  0.77      35% ( 66%)
 6. 100.0%   2.15   0.00  353.8   5   0   0  0.43      22% ( 40%)

Strafe keys:
L: ......................███████████.........██████.....
R: ..████████████████████...........█████████......█████
Mouse movement:
L: .......................▄▄▄▄▄▄▄▄▄▄▄.........▄▄▄▄▄▄...▄
R: ▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄...........▄▄▄▄▄▄▄▄▄......▄▄▄.
```

The displacement reported with distbug enabled is higher than the displacement recorded by the climb plugin.  
Veer refers to deviation.  
Fwd refers to W release.  
Land Edge refers to how far (in hu) from the very edge of your landing block you were when you landed.  
Jumpoff Angle refers to how much you turned counter-clockwise (in degrees) throughout your jump (the view angle at the start of your jump compared to the angle of your airpath).  
Airpath refers to distance traveled (in the precise sense of the term) divided by displacement. The closer to 1, the better.  
You don't need to do jumpstats forward. You can also do them backwards or sideways. Jump direction says which.  
Efficiency refers to mouse movement speed, which can vary throughout your jump. A higher percentage is faster. 100% is optimal for gain.  

There is also a breakdown of your key presses and mouse movement over time. It is read from left to right. Each column of characters represents 1 tick.

You can use all of this information to improve your jumpstats.
