# claude-test
Testing Claude Environments

## Tiny Taps: toddler touchscreen games for the Tesla browser

Self-contained web pages built for an ~18-month-old to play with on a car touchscreen. There's nothing
to install and no external files, and after a page loads it works with no internet. Every sound is made
in the browser (Web Audio) and the artwork is embedded in the pages.

| Page | What it is |
| --- | --- |
| [`index.html`](index.html) | **Home page:** two big picture cards that open the games. |
| [`party.html`](party.html) | **Tap Tap Party:** tap, swipe and multi-finger sparkle/music toy. |
| [`animals.html`](animals.html) | **Animal Sounds:** tap animals to hear and learn the sounds they make. |

Every game has a **Home** link on its start screen and a **Home** button in its grown-up panel.

---

### Animal Sounds (`animals.html`)

33 animals in four scenes. Switch scenes with the big round buttons at the bottom:

| Scene | Animals |
| --- | --- |
| Farm (tractor) | cow, pig, horse, sheep, goat, duck, chicken, rooster, chick, turkey, donkey, goose |
| Home & Garden (house) | dog, cat, mouse, parrot, bird, bee, cricket, frog |
| Wild (palm tree) | lion, tiger, bear, wolf, monkey, elephant, gorilla, snake, owl |
| Ocean (wave) | whale, dolphin, seal, penguin |

| Action | What happens |
| --- | --- |
| **Tap an animal** | It bounces and wiggles and makes its sound, with glowing "sound waves" around it. A speech bubble pops up with the sound word in big rainbow letters (**MOO!**, **QUACK QUACK!**, **ROAR!**), and its name grows bigger. |
| **Tap several animals at once** | Each one sings at the same time. Multi-touch is fully supported. |
| **Drag an animal** | Pick it up and move it around. Let go and it bounces back home. |
| **Four or more fingers at once** | **Chorus:** every animal in the scene sings in turn. |
| **Tap or swipe the background** | Ripples, rainbow sparkles and soft musical notes. |
| **Nobody touching** | Animals hop now and then to invite a tap. |

**Talking:** if the browser has a text-to-speech voice, it also says "The cow says moo!" after each
sound. The car's browser may not have a voice; if so, only the animal sounds play.

**About the sounds:** the animal sounds are synthesized cartoon voices (shaped like real moos, barks,
roars and so on), not recordings. To use real recordings instead, add audio files to the repo and list
them in the `RECORDINGS` object near the top of the script in `animals.html`, e.g.
`const RECORDINGS = { cow: 'sounds/cow.mp3' };`. Any animal without a recording keeps its synthesized sound.

**Grown-up settings:** hold the lock (top-right) for 2 seconds to get Sound (Off/Low/Medium/High),
Talking (On/Off), Show animal names (On/Off), Home, Start screen, and Done.

---

### Tap Tap Party (`party.html`)

| Action | What happens |
| --- | --- |
| **Tap anywhere** | A smiling star, heart, flower, sun or ball pops up with sparkles and a bell note. The screen works like a rainbow piano: low notes and red on the left, high notes and violet on the right. |
| **Swipe / drag** | A glowing rainbow ribbon follows the finger with a "slide whistle" sound. Higher on the screen gives a higher note. |
| **Fast flick** | Launches a shooting star that bounces off the edges, chiming on each bounce. |
| **Press and hold** | Blows up a balloon (with a squeaky sound). Let go and it floats away; hold too long and it **POPS** into confetti. Tap a floating balloon to pop it. |
| **Bubbles** | Bubbles drift up from the bottom. Tap them or swipe through them to pop them. |
| **The three buddies** | Tap a buddy to make it jump, spin and giggle. Grab one to drag it around, and fling it to throw it. Their eyes follow the child's finger. |
| **2 fingers** | A sparkly lightning zap links the fingers, with a shimmer sound. |
| **3–4 fingers** | Fireworks! |
| **Whole hand (5+ fingers)** | A big rainbow party: fireworks, confetti rain, a fanfare, and all the buddies jump. |
| **Nobody touching** | Soft glowing rings appear to invite a tap, and bubbles come more often. |

All melodic sounds use a pentatonic scale, so any mash of fingers sounds musical. A compressor
and a voice limit keep many simultaneous touches from getting harsh or too loud.

**Grown-up settings:** hold the lock (top-right) for 2 seconds to get Sound (Off/Low/Medium/High),
Calm mode (softer sound, no screen flashes, fewer bubbles), Home, Start screen, and Done.

---

### Built for a toddler and a car screen
- Big touch targets, full multi-touch, and no menus a toddler can get stuck in.
- Scrolling, pinch-zoom, double-tap zoom, long-press menus and text selection are blocked in the games.
- The grown-up panels sit behind a 2-second hold, so a quick toddler tap won't open them, and they
  close on their own after 30 seconds. Settings are remembered in that browser.
- Each game starts with a big play button, because browsers only allow sound to start after a tap.
  Audio starts when the finger lifts, which is what Chromium-based browsers (like the Tesla's) need
  on touchscreens.

### Using it in a Tesla
1. Host the pages somewhere the car can reach (see below), then open the home page URL in the Tesla
   browser. The browser only works while the car is in **Park**.
2. Pick a game, then tap the big play button.
3. Hand over the screen. A determined toddler can still tap the car's own controls around the browser
   window, so stay nearby.

### Hosting (GitHub Pages)
Turn on **Settings → Pages → Deploy from a branch** for this repository and choose `main` and `/ (root)`.
The home page will then be at `https://<user>.github.io/<repo>/`. (GitHub Pages on a private repo needs
a paid GitHub plan. Any static host works, since these are plain HTML files.)

To try it locally, open `index.html` in any modern browser. A mouse works for single-finger play.

### Credits
Animal and icon artwork: [Twemoji](https://github.com/jdecked/twemoji) by Twitter, Inc. and other
contributors, licensed under [CC-BY 4.0](https://creativecommons.org/licenses/by/4.0/).
All sounds are synthesized in code.
