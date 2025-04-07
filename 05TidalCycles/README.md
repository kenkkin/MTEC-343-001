# First Tidal Cycles Patch
```
-- MELODY
d1 $ slow 2 $ n (scale "minor" (run 8 + 11)) # s "superpiano" # legato 1.5 # gain 0.5 # room 0.8 # sz 0.9 # delay 0.3 # delaytime 0.25 # delayfeedback 0.4

-- HARMONY
d2 $ slow 4 $ n "bf4'min9 gf4'maj7 ef4'min11 bf4'min9" # s "superpiano" # sustain 4 # legato 2 # gain 0.5 # room 0.8 # sz 0.9 # lpf 1000

-- PERCUSSION
d3 $ s "drumtraks:snare" # gain 0.3 # room 0.5 # sz 0.6
```

My biggest focus for this patch was to just experiment and get familiar with different ways to generate sound. I first started with my melody, where I tried playing around with writing a minor melody without outright specifying notes. I ran into this interesting `run` function, which generates a pattern representing a cycle of numbers. I set my cycle to `8` and then transposed it up to **Bb minor.**

I prioritised getting something functional before playing with the quality, effects, and mix, so then I moved onto playing with **harmony.** I decided to make a simple minor progression, using the TidalCycles documentation to figure out proper notation for root note qualities (`f` = flat and `s` = sharp) and for octave voicings. At this point I also started playing with tempo, adding `slow 4` here and bringing the melody to a slower tempo with `slow 2`.

I spent less time experimenting with percussion, and just made a simple repeating loop to mark the downbeat, but I'd like to experiment with this more for the next assignment.

From here, I want back and played around with effects. I wanted this to be semi-ambient so I made use of things like `legato`, `sustain`, and `room`/`sz` to add reverb and expressive performance. I also introduced a **LPF** to the harmony to add some subtlety to the chord pads and added a `delay` to the melody to push that ambient effect a bit more. The last thing that I did was some minor mixing of each section using `gain`.