# Final Performance Tidal Cycles Patch
```haskell
setcps(0.6)

-- [MELODY]
d1 $ note "e4 fs4 b4 cs5 d5 fs4 e4 cs5 b4 fs4 d5 cs5"
# room 1 # legato 1 # lpf 1200 -- # lpf "<2400 2300 2200 2100 2000 1900 1800 1700 1600>"
# s "superpiano" # velocity 0.7 # pan 0 # gain 0.8


-- FEZ SHIFT:
xfade 1 $ note "e4 fs4 b4 cs5 d5 fs4 e4 cs5 b4 fs4 d5 cs5"
# s "superchip" # velocity 0.5 # gain 0.7
# room 1 # legato 1 # lpf 1200

-- FADE OUT:
xfade 1 $ note "e3"
# silence


-- [PHASE]
d2 $ slow 1.01 $ note "e4 fs4 b4 cs5 d5 fs4 e4 cs5 b4 fs4 d5 cs5"
# room 1 # legato 1 # lpf 1200 -- # lpf "<1600 1700 1800 1900 2000 2100 2200 2300 2400>"
# s "superpiano" # velocity 0.7 # pan 1 # gain "<0.1 0.2 0.3 0.4 0.5 0.6 0.7 0.8 0.8@10>"

-- FEZ SHIFT:
xfade 2 $ slow 1.01 $ note "e4 fs4 b4 cs5 d5 fs4 e4 cs5 b4 fs4 d5 cs5"
# s "superchip" # velocity 0.5 # gain 0.7
# room 1 # legato 1 # lpf 1200
# silence -- MUTE WHEN READY

-- FADE OUT:
xfade 2 $ note "e3"
# silence


-- [BELLS]
d3 $ slow 2 $ note "<e3 <[b3|~|e4|d4]>>" -- slow (rand + 1.5)
# s "supervibe" # velocity 1
# room 1 # sz 0.9
# lpf 1600 # gain 0.6 -- REPLACE WITH NEXT LINE
-- # lpf 1600 # gain 0.7 # pan rand
-- FEZ SHIFT
-- # distort 0.1
-- # silence


-- [BASS DRONE]
d4 $ slow 4 $ note "e2"
# s "superpwm"
# room 0.5 # sustain 8 # gain 0.8
# velocity 0.3 # lpf 200
-- # silence
```

I wanted to try my hand at working with melodic phasing, and since the first thing that comes to mind for this practive is Steve Reich's "Piano Phase", I thought it'd be the perfect basis for this performance. I started by getting the melodic sequence set up with `superpiano` and then tackled the issue of phasing the phrases. Since `cps` is a strictly global paramter, I ended up using `slow` to augment the speed of the second pattern. `slow 1.01` seemed to be the best sweet spot to mimic the original recording.

From there I wanted to add some other melodic elements to my performance, so I made two more patterns. The first one I tried to incorporate was a bass drone. I had some difficulty at first making this sound constant, but after adding a long `sustain`, tweaking the `velocity`, throwing on some reverb with `room`, and setting a severe `lpf`, I ended up with something I was pretty happy with. Looking back, I think it would have been best to incorporate **AHDSR modulation** to also change the attack, sustain, etc... but this still got me the effect I was going for.

I had kind of been in a certain musical headspace after thinking of "Piano Phase" and started kind of vibing with idea of mimicking generative music. Inspired by that style, I decided to add another pattern that would sort of mimic the melodic pings used in the game *Mini Metro*. I added some bells using `supervibe` that had some randomisation to the melodic pattern. I also eventually added a random pan feature and random tempo alteration to that too. 

As per usual, at this point I just started playing with effects, adding `lpf`, reverb via `room` and `sz`, and `legato`. It was at this point that I also did some very light mixing using `gain`.

As I was playing around with effects, I got inspired to have an interesting tone shift in my performance. I added some slight distortion to the bells, and the timbre reminded me so much of the music in the video game *FEZ*, that I decided to adjust everything to fit that sound. The bass drone stayed the same, but I decided I wanted to switch the phasing melodic sequences to `superchip` to get that **Atari chiptune** sound.

To best fascilitate the transition, I looked into the [xfade documentation](https://tidalcycles.org/docs/reference/transitions/#xfade) and also made some careful use of the `silence` function. Once I had the first crossfade running, I set up a few more and some comments just to help me establish a **form** of sorts for my performance. 

At this point, I had everything I wanted to include in my performance coded, so I just sat down with my patch and practiced a few times to prepare for the final.

## Reflections

Looking back, there's a lot of things here I'd like to improve, especially regarding quality of life and simplification of syntax. One of the more obvious things I wish I had seen before setting up my whole form was the `fadeOut` function. I had manually made one by setting up an `xfade` to a silenced pattern, but this would be a much more straightforward way of making that happen. 

I also could not for the ***life*** of me get the `stacks` working and I'm still not quite sure why. I think it would've been super helpful for making sure the phasing melodies were triggered at the same time, but If I just play them fast enough I don't seem to really have any performance issues.

Another weird thing I ran into but couldn't find much info on was how the `superchip` synthesizer transposes the melody. I'm sure it's somehow related to accurate emulation of the Atari music system, but it was an unwanted change I didn't know how to overcome when adding it to my performane. The crossfade seemed to at least make it a little less offensive, but I definitely want to look into that more.