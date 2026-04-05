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
You can use the fact that your speed is maintained if you jump on the exact tick you land on to chain perfs together for even more distance. That is an MBH.

You are likely to reach the limit of how much speed you can maintain after just two perfs. Your speed will be reduced to 120% of your maximum walking speed if it is faster than that when you hit a perf. With a single bhop, this is only a concern on Heavy.  

Doing the first perf uncrouched and the second perf as a crouch-jump gives you more height than you would get doing both perfs crouched or uncrouched. You can bind scrolling up or down to jumping to make timing uncrouched perfs more consistent. For example:  
```
bind MWHEELDOWN +jump;
```
Binding scroll to crouch-jump is not useful. You must time your key press.  

For a good MBH, run at full speed, jump, strafe for speed, do an uncrouched perf, strafe to max out speed, do a crouched perf, strafe back and forth to build speed, and land crouched. Even though pre is going to be the same regardless of the height you jump from, the stat only records if all three jumps and the landing are from the same height.  

### WeirdJump/WJ  
A WJ is a jump from a perf hit after falling (not jumping) from at most 64 hu.

You can find 64 hu tall platforms on kz_baxter_tf2.

### Jumpbug/JB  
At a specific height above a platform, you can uncrouch while airborne and jump on the exact same tick. That is a JB.  

Most players choose to use a bind to make the tick-perfect timing easier. There are several different versions of JB binds. This is one of them:  
```
alias jumpbug "+duck; bind space +jumpbugjump";
alias +jumpbugjump "-duck; +jump;";
alias -jumpbugjump "-jump; bind space +jump";
bind MOUSE2 jumpbug;
```

For a good JB with this bind, run at full speed, tap a key bound to crouch-jump, right-click once while strafing to gain speed, press space on the right tick, begin holding crouch, strafe back and forth to gain speed, and land crouched.  

Jumpbugs are only possible from certain heights. For the stat, the first jump, the tick-perfect jump, and the landing all have to be on platforms of the same height.  

## Jumpstat Information
After performing a jumpstat, you will see information about your jump in chat. Only you and people spectating you can see information about your jump. For example:  

```
climb.tf | LJ: 309.9 | 4 Strafes (81%) | 320 / 351 Speed | 34.8 Edge | +1 W
```

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

### Jumpstat Information Explained  

Numbers are sometimes rounded down to the nearest whole unit or tenth of a unit in some outputs. Sometimes numbers are inacurrate.  

The number labeled with the type of jump is the displacement (usually imprecisely called "**distance**").  
**Strafes** is defined differently by the climb plugin and distbug. In the climb plugin, it is the number of horizontal mouse movements. In distbug, it is the number of strafe key presses.  
**Sync** refers to the percentage of the time mouse movements and strafe key presses were synchronized throughout the jump.  
Two numbers may be displayed for speed. The first is **pre**, and the second is **max speed**.  
**Edge** refers to the distance between where the jump started (when jump was pressed) and the edge of the LJ block.  
**W**, or **Fwd**, refers to the number of ticks in the air before W was released.  
**Block** refers to the length between LJ blocks jumped across.  
**OL** stands for overlap. It is the number of ticks both strafe keys were pressed or held during.  
**DA** stands for dead air. It is the number of ticks where a strafe key was not pressed or held.  
**Deviation**, or **Veer**, refers to the component of displacement along (and not across) LJ blocks.  
**Width** refers to the mean angle (in degrees) of the jump's strafes.  
**Height** refers to the maximum distance from the ground the collision hull was.  
**Airtime** refers to the number of ticks the jump took.  
**Offset** refers to the height jumped up onto.  
**Crouched** refers to the number of ticks spent crouched in the air.  
**Gain** is the amount of speed gained during a strafe.  
**Loss** is the amount of speed lost during a strafe.  
**Land Edge** refers to how far (in hu) from the very edge of your landing block you were when you landed.  
**Jumpoff Angle** refers to how much you turned counter-clockwise (in degrees) throughout your jump (the view angle at the start of your jump compared to the angle of your airpath).  
**Airpath** refers to distance traveled (in the precise sense of the term) divided by displacement. The closer to 1, the better (though reducing airpath may require you to sacrifice on other aspects of the jump).  
**Jump Direction** can be forwards, sideways, or backwards.  
**Efficiency** refers to mouse movement speed, which can vary throughout your jump. A higher percentage is faster. 100% is optimal for gain.  
There is also a breakdown of your key presses and mouse movement over time. It is read from left to right. Each column of characters represents 1 tick.  

You can use all of this information to improve your jumpstats.
