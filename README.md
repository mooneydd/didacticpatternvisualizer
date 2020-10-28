[Versión en español](README-ESP.md) 

# Didactic pattern visualizer for Tidal Cycles 

Sound pattern visualizer programmed in Processing by the artist Ivan Abreu to study the potential and complexity of the syntax of the pattern system for sequencing <b>Tida Cycles</b> sounds, it is also a useful tool for composing having visual feedback of ordering and sound intentions and can be a fun visual software during the live act to unfold the musical composition and with them emphasize and direct attention to the subtleties that are semi-hidden in the multiple layers created by the artist.

#

Musical pattern example:

[![SC2 Video](https://ivanabreu.net/github/videoivan.jpg)](https://ivanabreu.net/github/soundpatternbyivanabreu01.mp4 "Click to play >")

```haskell

do
  asap $ connectionMax 3 # speedSequenser 4
  d5 $ grid "1 0!15"
  d1 $ s "bd(3,8)" # connectionN 1
  d2 $ s "hh(6,8)" # connectionN 2
  d3 $ every 3 ( density 8 ) $ density 2 $ n "<[d4,e2,g2] [d4,e4,g2]?>" 
     # s "superfork"  # connectionN 3

```


Musical pattern created by electronic musician and digital artist <b>CNDSD</b>:


[![SC2 Video](https://ivanabreu.net/github/videomali.jpg)](https://ivanabreu.net/github/soundpatternbycndsd.mp4 "Click to play >")

Code from previous video by <b>CNDSD</b>, using only defaults samples of TidalCycles:

```haskell
do
 asap $ connectionMax 5 # speedSequenser 2
 d5 $ slow 0.75 $ grid "1 0!8"
 d1 $ qtrigger 1 $ seqPLoop [
    (0,8, slow 0.75 $ cat [
    sometimesBy 0.15 (#crush 6)$ s "[bd(5,9),[superhat(2,9)]/2]"
    # n "[[2 4],[g5 ,b6 ,a3]]"  # accelerate 0.8 # note "[f5] g2" # gain (slow 2 $ range 0.9 1.2 $ sine) #connectionN 1,
    sometimesBy 0.25 (# speed "[[1 0.8],[1.5 2]*2]") $ s "[yeah(3,9),notes(7,9)]" # n "[[2][a4 ,d7 g6]b3]" # gain "1.2" #connectionN 2,
    sound "[print(2,9)]/4" # n "3" # gain "1.2" #room 0.1 #connectionN 3,
    sound " ~ ~ [sax]/12" # n "2" # gain "1.2" # legato 3 #room 0.5 #connectionN 4,
    sound "{super808 ~ ~ ~ ~ ~}%1.5" # n "g2" # gain "1.5" # legato 4 #room 1 #connectionN 5] ),
    (8,24, slow 0.75 $ stack [
    sometimesBy 0.15 (#crush 6)$ s "[bd(5,9),[superhat(2,9)]/2]"
    # n "[[2 4],[g5 ,b6 ,a3]]"  # accelerate 0.8 # note "[f5] g2" # gain (slow 2 $ range 0.9 1.2 $ sine) #connectionN 1,
    sometimesBy 0.25 (# speed "[[1 0.8],[1.5 2]*2]") $ s "[yeah(3,9),notes(7,9)]" # n "[[2][a4 ,d7 g6]b3]" # gain "1.2" #connectionN 2,
    sound "[print(2,9)]/4" # n "3" # gain "1.2" #room 0.1 #connectionN 3,
    sound " ~ ~ [sax]/12" # n "2" # gain "1.2" # legato 3 #room 0.5 #connectionN 4,
    sound "{super808 ~ ~ ~ ~ ~}%1.5" # n "g2" # gain "1.5" # legato 4 #room 1 #connectionN 5] )
    ] 
    
```
#
[Sending OSC messages to Processing (Getting started)](GETTING-STARTED.md)
#


### Visualize grids and time division 

Examples to set pattern in Tidal to view grid and time division<br>
#### <b>1 creates a thicker line.<br>0 creates a thinner line.</b>

Grid with <b>four times</b>

<img width="700px" src="https://ivanabreu.net/github/4t.jpg">

```haskell

s4 $ grid "1 0 0 0"

-- or

s4 $ grid "1 0!4"

```

Grid with <b>eight times</b>

<img width="700px" src="https://ivanabreu.net/github/8t.jpg">

```haskell

s4 $ grid "1 0 0 0 0 0 0 0"

-- or

s4 $ grid "1 0!7"

```

### Visualize sound pattern 

Examples to set pattern in Tidal to view <b>sound pattern</b><br>
You'll need put the function <b># connectionN n</b>, where <b>n</b> is the number of layer playing ("s" or "d")

Example 1:<br>
<img width="700px" src="https://ivanabreu.net/github/pattern1_1x4.jpg">

```haskell

do
  d1 $ s "bd cp" # connectionN 1
  d4 $ grid "1 0 0 0"

```

Example 2:<br>
<img width="700px" src="https://ivanabreu.net/github/pattern1_3x4.jpg">

```haskell

do
   d1 $ s "bd cp*3" # connectionN 1
   d4 $ grid "1 0 0 0"

```

Example 3:<br>
<img width="700px" src="https://ivanabreu.net/github/patternd1d2.jpg">

```haskell

do
   d1 $ s "bd(3,8)" # connectionN 1
   d2 $ s "hh(6,8)" # connectionN 2
   d4 $ grid "1 0 0 0 0 0 0 0"

```

Example 4:<br>
[![SC2 Video](https://ivanabreu.net/github/patternd1d2d3.jpg)](https://ivanabreu.net/videos/CNDSD_Ivan_Abreu-CODING_IN_ATYPICAL_PLACES.mp4 "Click to Watch >")

```haskell

do
  d1 $ s "bd(3,8)" # connectionN 1
  d2 $ s "hh(6,8)" # connectionN 2
  d3 $ s "supermandolin" # n "<[d4,e2,g2] [d4,e4,g2]?>" # connectionN 3
  d4 $ grid "1 0 0 0 0 0 0 0"

  -- In d3, notes are used in a transversal way (such as chords [d4,e2,g2]) 
  -- which appear in the same vertical line in the grid.
  -- Randomness is also used with the "?" Sign, so sometimes empty times appear.
  
```



### Contact or reports

Please share reports of success / failure with Ivan Abreu via email: data@ivanabreu.net or ivanabreuochoa@gmail.com
