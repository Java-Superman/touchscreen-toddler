# claude-test
Testing Claude Environments

## Tiny Taps: toddler touchscreen games for the Tesla browser

Self-contained web pages built for an ~18-month-old to play with on a car touchscreen. There's nothing
to install, and after a page loads it works with no internet. The animal sounds are real recordings in
the [`sounds/`](sounds) folder; every other sound is made in the browser (Web Audio), and the artwork is
embedded in the pages.

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

**About the sounds:** each animal plays a short real recording of that animal (see
[Sound credits](#sound-credits)). The clips are trimmed, small mono MP3s in `sounds/<animal>.mp3`, listed
in the `RECORDINGS` array near the top of the script in `animals.html`. The page downloads all of them
as soon as it opens, so after that it keeps working with no internet, and evens out their volume.
The snake plays a rattlesnake's rattle, the nearest real recording to a hiss that's freely licensed.
If an animal has no recording, or its file can't be loaded, the game falls back to that animal's
synthesized cartoon voice, which is still in the code. To swap a sound, replace its MP3 (keep it short).

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
a paid GitHub plan. Any static host works, since these are plain HTML files; upload the `sounds/` folder
alongside the pages.)

To try it locally, serve the folder with any web server, e.g. `python3 -m http.server` and then open
`http://localhost:8000/`. A mouse works for single-finger play. (Opening `index.html` straight from disk
also works, but browsers block loading the sound files that way, so Animal Sounds falls back to its
synthesized voices.)

### Credits
Animal and icon artwork: [Twemoji](https://github.com/jdecked/twemoji) by Twitter, Inc. and other
contributors, licensed under [CC-BY 4.0](https://creativecommons.org/licenses/by/4.0/).
Animal sound recordings: see [Sound credits](#sound-credits) below. All other sounds are synthesized in code.

#### Sound credits
The animal recordings come from [SoundBible](https://soundbible.com), [Freesound](https://freesound.org),
[NOAA Fisheries](https://www.fisheries.noaa.gov/national/science-data/sounds-ocean-mammals) and
[Wikimedia Commons](https://commons.wikimedia.org). Each one is public domain or under the Creative
Commons license shown. They were trimmed, mixed down to mono, faded in and out, and re-encoded as MP3.

<!-- sound-credits:start -->
| Animal | Recording | By | License |
| --- | --- | --- | --- |
| Cow | [Cow Moo](https://soundbible.com/1778-Cow-Moo.html) (SoundBible) | Mike Koenig | [CC BY 3.0](https://creativecommons.org/licenses/by/3.0/) |
| Pig | [Pig Oinking](https://soundbible.com/1220-Pig-Oinking.html) (SoundBible) | Mike Koenig | [CC BY 3.0](https://creativecommons.org/licenses/by/3.0/) |
| Horse | [Horse Neigh](https://soundbible.com/1296-Horse-Neigh.html) (SoundBible) | Mike Koenig | [CC BY 3.0](https://creativecommons.org/licenses/by/3.0/) |
| Sheep | [Sheep Bleating](https://soundbible.com/520-Sheep-Bleating.html) (SoundBible) | Mike Koenig | [CC BY 3.0](https://creativecommons.org/licenses/by/3.0/) |
| Goat | [Goat Bah](https://soundbible.com/619-Goat-Bah.html) (SoundBible) | BlastwaveFx.com | [CC BY 3.0](https://creativecommons.org/licenses/by/3.0/) |
| Duck | [Mallard Duck Quacking](https://soundbible.com/1862-Mallard-Duck-Quacking.html) (SoundBible) | Mike Koenig | [CC BY 3.0](https://creativecommons.org/licenses/by/3.0/) |
| Chicken | [Hen Chicken](https://soundbible.com/1022-Hen-Chicken.html) (SoundBible) | Caroline Ford | [CC BY 3.0](https://creativecommons.org/licenses/by/3.0/) |
| Rooster | [Rooster Crowing](https://soundbible.com/1134-Rooster-Crowing.html) (SoundBible) | Mike Koenig | [CC BY 3.0](https://creativecommons.org/licenses/by/3.0/) |
| Chick | [Chicks very young](https://freesound.org/people/AGFX/sounds/43380/) (Freesound) | AGFX | [CC0](https://creativecommons.org/publicdomain/zero/1.0/) |
| Turkey | [Turkey Gobble](https://soundbible.com/1737-Turkey-Gobble.html) (SoundBible) | bod | Public domain |
| Donkey | [Donkey braying close to the market, in Morocco](https://freesound.org/people/felix.blume/sounds/152907/) (Freesound) | felix.blume | [CC0](https://creativecommons.org/publicdomain/zero/1.0/) |
| Goose | [Canadian Geese Honk](https://soundbible.com/1202-Canadian-Geese-Honk.html) (SoundBible) | Tony Phillips | [CC BY 3.0](https://creativecommons.org/licenses/by/3.0/) |
| Dog | [Labrador Barking Dog](https://soundbible.com/2215-Labrador-Barking-Dog.html) (SoundBible) | Daniel Simion | [CC BY 3.0](https://creativecommons.org/licenses/by/3.0/) |
| Cat | [Cat Meowing](https://soundbible.com/1290-Cat-Meowing.html) (SoundBible) | Mike Koenig | [CC BY 3.0](https://creativecommons.org/licenses/by/3.0/) |
| Mouse | [Mice Squeaks](https://freesound.org/people/berboberbo/sounds/727114/) (Freesound) | berboberbo | [CC0](https://creativecommons.org/publicdomain/zero/1.0/) |
| Parrot | [Macaw Parrot screaming in a park](https://freesound.org/people/felix.blume/sounds/504988/) (Freesound) | felix.blume | [CC0](https://creativecommons.org/publicdomain/zero/1.0/) |
| Bird | [Birds After Rain](https://soundbible.com/1827-Birds-After-Rain.html) (SoundBible) | Mike Koenig | [CC BY 3.0](https://creativecommons.org/licenses/by/3.0/) |
| Bee | [Bee buzzing sound (animal noises).opus](https://commons.wikimedia.org/wiki/File:Bee_buzzing_sound_(animal_noises).opus) (Wikimedia Commons) | Free Sounds Library User Spanac | [CC BY 3.0](https://creativecommons.org/licenses/by/3.0/) |
| Cricket | [Crickets Chirping At Night](https://soundbible.com/2083-Crickets-Chirping-At-Night.html) (SoundBible) | Lisa Redfern | Public domain |
| Frog | [Croaking 2x](https://soundbible.com/1340-Croaking-2x.html) (SoundBible) | snottyboy | [CC BY 3.0](https://creativecommons.org/licenses/by/3.0/) |
| Lion | [Lion Roar](https://soundbible.com/1282-Lion-Roar.html) (SoundBible) | Mike Koenig | [CC BY 3.0](https://creativecommons.org/licenses/by/3.0/) |
| Tiger | [Tiger Growling](https://soundbible.com/1485-Tiger-Growling.html) (SoundBible) | Mike Koenig | [CC BY 3.0](https://creativecommons.org/licenses/by/3.0/) |
| Bear | [Bear](https://soundbible.com/1142-Bear.html) (SoundBible) | Mike Koenig | [CC BY 3.0](https://creativecommons.org/licenses/by/3.0/) |
| Wolf | [Wolf Howling Yipping](https://soundbible.com/2132-Wolf-Howling-Yipping.html) (SoundBible) | Daniel Simon | [CC BY 3.0](https://creativecommons.org/licenses/by/3.0/) |
| Monkey | [Chimpanzee](https://soundbible.com/1188-Chimpanzee.html) (SoundBible) | Mike Koenig | [CC BY 3.0](https://creativecommons.org/licenses/by/3.0/) |
| Elephant | [Elephant](https://soundbible.com/1140-Elephant.html) (SoundBible) | Mike Koenig | [CC BY 3.0](https://creativecommons.org/licenses/by/3.0/) |
| Gorilla | [Gorilla](https://soundbible.com/1149-Gorilla.html) (SoundBible) | unknown | Public domain |
| Snake | [Rattlesnake Rattle](https://soundbible.com/237-Rattlesnake-Rattle.html) (SoundBible) | U.S. Fish & Wildlife Service (fws.gov) | Public domain |
| Owl | [Spotted Owl Call](https://soundbible.com/1010-Spotted-Owl-Call.html) (SoundBible) | nps.gov | Public domain |
| Whale | [Humpback whale song](https://www.fisheries.noaa.gov/national/science-data/sounds-ocean-mammals) (NOAA Fisheries) | NOAA Fisheries Passive Acoustics Group | Public domain |
| Dolphin | [Common bottlenose dolphin whistles](https://www.fisheries.noaa.gov/national/science-data/sounds-ocean-mammals) (NOAA Fisheries) | NOAA Fisheries Passive Acoustics Group | Public domain |
| Seal | [Seal Call Zoo](https://soundbible.com/142-Seal-Call-Zoo.html) (SoundBible) | Mike Koenig | [CC BY 3.0](https://creativecommons.org/licenses/by/3.0/) |
| Penguin | [African penguins at Boulders Beach](https://freesound.org/people/Vortichez/sounds/545415/) (Freesound) | Vortichez | [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) |
<!-- sound-credits:end -->
