# Second Tidal Cycles Patch
```haskell
-- MELODY
d1 $ slow 24 $ n "[b3@2 d4] [a3@2 [g3 a3]] [b3@2 d4] [a3] [b3@2 d4] [a4@2 g4] [d4@2 [c4 b3]] [a3] [b3@2 d4] [a3@2 [g3 a3]] [b3@2 d4] [a3] [b3@2 d4] [a4@2 g4] d5@2 [d5@2 [c5 b4]] [[c5 b4] g4@2] [c5@2 [b4 a4]] [[b4 a4] e4@2] [d5@2 [c5 b4]] [[c5 b4] g4 c5] [g5] [~ ~ b3]"
# s "supervibe"
# room 0.8 # sz 0.9
# gain 0.4
# detune 4
# velocity 5
# lpf 1600

-- BASS
d2 $ slow 24 $ n "[[c2 g2] e3@2] [[c2 g2] fs3@2] [[c2 g2] e3@2] [[c2 g2] fs3@2][[b1 d3] g3@2] [[b1 d3] g3@2] [[a1 c3] g3@2] [[d2 c3] fs3@2][[c2 g2] e3@2] [[c2 g2] fs3@2] [[c2 g2] e3@2] [[c2 g2] fs3@2][[b1 d3] g3@2] [[b1 d3] g3@2] [[a1 c3] g3@2] [[d2 c3] fs3@2][[f2 c3] e3@2] [[e2 b2] d3@2] [[d2 a2] c3@2] [[c2 g2] b2@2][[f2 c3] e3@2] [[e2 b2] d3@2] [[ef2 bf2] df3@2] [[d2 a2] c3 [f3,g2]]"
# s "supervibe"
# room 1 # sz 0.9
# delay 0.3
# gain 0.6
```

I was a bit short on time for this patch and a bit stressed with some major project deadlines for other classes, haha, so I thought it'd be a good idea to use this assignment to do something fun. I decided to attempt a cover of ***Zelda's Lullaby*** to help me get more familiar with **TidalCycles** (which I've been kind of struggling to learn for some reason). 

I started first with just laying out the melody and bass line notes, taking a bit of time to noodle it out by ear and fine tune the durations and structure. I had still not quite understood how to use nested brackets `[[c5 b4] g4 c5]`, or the lengthen feature `@` when we were still working in **Strudel,** so this was a good opportunity for me to finally use those. 

Once I had the lines written, it was just a matter of playing around with sounds and parameters. I started first by digging through the [Synthesizers Documentation](https://tidalcycles.org/docs/reference/synthesizers/#supersaw). I was hoping to find some kind of triangle wave, to emmulate the NES sound, but didn't have any luck looking through the documentation. I ended up really liking `supervibe`, though! Koyo was in the living room as I was working on it and said it made the track sound like it was playing over the speakers of the ***Animal Crossing: New Horizons*** museum, haha. 

After I had my synth picked, I just messed around with some of the parameters listed in the documentation. I wanted to add reverb with `# room` and `# sz` to make it feel very spacey, and also made use of some slight `# delay`. For the melody in particular, I wanted the vibraphone to sound a bit brighter, so I upped the `# velocity`. This however, sent some of the harmonics into hyperdrive, so I tempered them back down with a `# lpf`. Lastly, I just wanted to introduce a very subtle detuning to give the melody a bit more character. 

As usual, I also did some minor mixing with `# gain` just to bring the levels to somewhere I would be happy with.

One issue I couldn't resolve however, is I couldn't find any way to wrap the melodies to the next line. I'm pretty sure there would be a way to do it, since it's possible in **Strudel,** but I wasn't able to find anything on it online. It would always give me an error when executing as soon as I broke the line within the quotes `""`.