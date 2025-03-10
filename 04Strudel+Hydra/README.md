# Strudel + Hydra 

```javascript
// "undersurface" - wondrid
// https://wondrid.com

// original visuals by Olivia Jack (with personal modifications)
// https://ojack.github.io

// OSTINATO
$: n("[0 1 ~ -1] [0 4] [~] [~ ~ 5 6] [7 ~ ~ 4][~ 5][~ 3 4 ~][2 1]")
  .scale("Bb:phrygian").s("gm_shamisen")
  .cpm(90/4).slow(2).delay(0) // => 0.5 => 1
  .room(2).roomsize("3")
  .lpf(slider(200,0,2100,10)) 
  ._punchcard()

// PADS
_$: gain(0.1).chord("<Bbm Cbadd9>").voicing()
  .s("gm_synth_strings_2").cpm(90/4)
  .room(2).roomsize("3")
  ._pitchwheel()

_$: n("[4][~][~][~][5][~][7][6]")
  .scale("Bb:phrygian").s("gm_epiano2").gain(0.4)
  .cpm(90/4).slow(2)
  .room(2).roomsize("3")
  // .mask("<1 1 1 [0]>")
  .pan("<-1 1>") 


// LEAD IN
_$: n("[~]!2[~ 3][~ 5 ~ ~][4][~]!3")
  .scale("Bb:phrygian").s("gm_glockenspiel")
  .cpm(90/4).slow(2)
  .room(2).roomsize("3")


// BASS
_$: note("Bb1 B1".sub(12)).struct("x x")
// $: note("[Bb1] [B1@3 [Db2 B1]]".sub(12))
  .sound("gm_synth_bass_2:1").attack("0.03")
  .slow(2).cpm(90/4).gain(1.5)


// PERCUSSION
_$: s("hh:4!32")
  .slow(2).cpm(90/4).gain(0.1)

_$: s("[bossdr110_bd][~ bossdr110_bd][bossdr110_sd][~ bossdr110_bd]")
  .cpm(90/4).gain(0.5)
// variation
_$: s("[bossdr110_bd][~ bossdr110_bd][bossdr110_bd bossdr110_sd@2 bossdr110_sd][bossdr110_sd bossdr110_sd]")
  .cpm(90/4).gain(0.5)

// SECOND PATTERN
// $: s("[bossdr110_bd]").struct("[x x][~ x][[~ x] x][~]")
//   .cpm(90/4).gain(0.5)

// $: s("[tr626_rim]").struct("[~][x][~][x]")
//   .cpm(90/4).gain(0.4)

all(x=>x.color('cyan'))

await initHydra()

osc(6, 0, 0.8)
  .color(1.14, 0.6,.80)
  .rotate(0.92, 0.3)
  .pixelate(20, 10)
  .mult(osc(40, 0.03).thresh(0.4).rotate(0, -0.02))
  .modulateRotate(osc(50, 0).thresh(0.3, 0.8), () => 0.6 + Math.sin(time) * 0.25)
  .out(o0)
```

### Process
***Disclaimer:** It's going to be a bit difficult for me to document this as this ended up being pretty stream of consciousness and I got way too invested in the creation aspect to remember I should be writing things down, haha. So I'm just going to do my best to trace back my steps!*

For starters, I wanted to talk about my inspiration going into this assignment. A lot of the stuff that I compose for my major (GAIMS) is either very orchestral or ambient and almost always narrative driven. Songwriting and beat making have always been much less familiar to me, so I wanted to challenge myself to use the pattern schemes to write something that felt a bit more contemporary and vibey. 

I thought a good start would be to build off of an ostinato, so I wrote that first, going for a nice dark and moody feel by writing in Phrygian.

```javascript
// OSTINATO
$: n("[0 1 ~ -1] [0 4] [~] [~ ~ 5 6] [7 ~ ~ 4][~ 5][~ 3 4 ~][2 1]")
  .scale("Bb:phrygian").s("gm_shamisen")
  .cpm(90/4).slow(2).delay(0) // => 0.5 => 1
  .room(2).roomsize("3")
  .lpf(slider(200,0,2100,10)) 
  ._punchcard()
```

I had initially set my low pass filter with this longgggg chain of incrementing values, but after taking a peak at some user demos, I found this nifty little slider mechanic that worked perfect for the LPF automation effect I was trying to achieve for my intro. Then from there, I just wanted to incorporate another visual element so I added the `punchcard()` function.

From here, I wrote out a simple pad vamp to accompany the ostinato and then gave that a nice `pitchwheel()` visualiser. I felt that the pads came in a bit abruptly no matter when I cued them, so I wrote an accompanying line, that when enabled at the right moment, would create a lead in of sorts.

```javascript
// PADS
_$: gain(0.1).chord("<Bbm Cbadd9>").voicing()
  .s("gm_synth_strings_2").cpm(90/4)
  .room(2).roomsize("3")
  ._pitchwheel()

_$: n("[4][~][~][~][5][~][7][6]")
  .scale("Bb:phrygian").s("gm_epiano2").gain(0.4)
  .cpm(90/4).slow(2)
  .room(2).roomsize("3")
  // .mask("<1 1 1 [0]>")
  .pan("<-1 1>") 
```

I also added some panning to that accompanying line and added a `mask()` function to create some variation as it played out. At this point, I also started mixing throughout the creative process- adjusting gain values with each section introduced.

I really enjoyed the little lead in line I added and ended up creating a second one for any moments I wanted to bring in some higher-register colors or introduce a new section:

```javascript
// LEAD IN
_$: n("[~]!2[~ 3][~ 5 ~ ~][4][~]!3")
  .scale("Bb:phrygian").s("gm_glockenspiel")
  .cpm(90/4).slow(2)
  .room(2).roomsize("3")
```

From here, I wanted to move onto the groove section, so I started first with a simple root motion bass line. I ended up really liking the sound of sub bass for this patch, so I just ran with it.

```javascript
// BASS
_$: note("Bb1 B1".sub(12)).struct("x x")
// $: note("[Bb1] [B1@3 [Db2 B1]]".sub(12))
  .sound("gm_synth_bass_2:1").attack("0.03")
  .slow(2).cpm(90/4).gain(1.5)
```

I included a variation on the bass line here as well, but wanted to reserve it as a development choice instead of leaving it to the `mask()` function to rotate between possibilities. 

From there I moved onto percussion. I knew I wanted a steady hi-hat pattern, but wanted to include two different intensity percussion patterns, so I started with the higher intensity one (also including a development-based variation):

```javascript
// PERCUSSION
_$: s("hh:4!32")
  .slow(2).cpm(90/4).gain(0.1)

_$: s("[bossdr110_bd][~ bossdr110_bd][bossdr110_sd][~ bossdr110_bd]")
  .cpm(90/4).gain(0.5)

// variation
_$: s("[bossdr110_bd][~ bossdr110_bd][bossdr110_bd bossdr110_sd@2 bossdr110_sd][bossdr110_sd bossdr110_sd]")
  .cpm(90/4).gain(0.5)
```

Then moved onto the calmer, second pattern:

```javascript
// SECOND PATTERN
$: s("[bossdr110_bd]").struct("[x x][~ x][[~ x] x][~]")
  .cpm(90/4).gain(0.5)

$: s("[tr626_rim]").struct("[~][x][~][x]")
  .cpm(90/4).gain(0.4)
```

After finishing the composition aspect, I just did a few practice runs of the performance to make sure I was reaching the time requirements and could get through the performance cleanly. Then, once I felt solid enough on that, I moved onto the visuals. 

Before even starting with Hydra, I first set the Strudel colors to match my in-browser theme:

```javascript
all(x=>x.color('cyan'))
```

Now moving onto Hydra, I started by looking through their demos for inspiration as I was a bit lost on how to even start approaching things. I stumbled upon a design I really liked by **Olivia Jack** so I just copied that over to my code and started tweaking a few parameters. Olivia's pattern was reliant on `mouse.x` movement to map the mod rotation, which I wanted to avoid as I felt my mouse movements would be too jarring for the vibe I was going for. To remedy this, I just edited the patch to modulate with `Math.sin(time)` instead. I then just tweaked some numbers until I got the effect I was going for. 