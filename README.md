# Countryside Sunday School Games

A small set of review games for a Sunday school class, built to run on a
projector. Each game is a single HTML file with no build step and no server
requirements, so the site can be hosted anywhere static files are served,
including GitHub Pages. Open `index.html` to see the list of pages.

The games share one idea: the teacher asks a review question, kids answer by
physically moving to a spot in the room, and the page decides what happens
next. Everything is random each round so kids cannot learn a "safe" spot.

## Pages

| File | What it is |
| --- | --- |
| `index.html` | Landing page that links to every game |
| `cardflip.html` | Card Flip review game (see below) |
| `bingo.html` | Bingo card creator and printer |
| `sundayschool_colorpicker.html` | Color Picker game with four colors |
| `sundayschool_colorpicker6.html` | Color Picker game with six colors |
| `ding.mp3`, `jeopardy.mp3` | Sounds used by the games |

Settings for each game are saved in the browser with `localStorage`, so they
survive a page reload on the same computer. Nothing is sent anywhere.

## Card Flip

Kids stand by the card they want, and the teacher flips a card to reveal what
it was worth. Cards are shuffled every round, so the value under each card
changes every time.

### Playing a round

1. Ask a question and let the kids pick a card to stand by.
2. Optionally start the timer so they have a fixed time to choose.
3. Click the card the group picked, or press its number key (1 to 4).
   With letter labels, the A to D keys also work.
4. The card flips and shows its value. The other cards flip dimmed so
   everyone sees what they would have been.
5. Click **Next round** or press N or Enter. The cards shuffle and go face
   down again.

**Flip all** (or the F key) turns every card over at once instead of picking
one. Nothing is scored automatically in that case.

### Setup options

Click **Setup** in the top bar.

- **Teams.** Turn on "Play with two teams and keep score" to show a scoreboard
  with two named, colored teams. Each card then belongs to a team, and
  flipping it adds the card's points to that team. The plus and minus buttons
  on the scoreboard adjust scores by hand. With teams off there is no
  scoreboard and each card simply shows how many points it is worth.
- **Cards.** Presets depend on whether teams are on.
  - Without teams: 4 cards worth 0, 1, 2 and 3 points (the default), or
    3 cards worth 1, 2 and 3.
  - With teams: 2 cards worth 1 point each, or 4 cards worth 1 and 2 points
    per team.
  - **Custom** lets you choose 2 to 4 cards and set each card's points
    (0 to 3) and, with teams on, which team it belongs to.
- **Card labels.** Cards are either named colors or gray letters A to D.
  The default colors are yellow, blue, red and green. Click a swatch to change
  a card's color. Picking a color another card already uses swaps the two, so
  no two cards share a color.
- **Sounds.** Turn the ding that plays on every flip on or off.
- **Timer.** An optional countdown shown over the cards while kids walk to
  their spot. You can set the length in seconds, the sound when time runs out
  (buzzer, ding, chime or none), and music during the countdown (Jeopardy
  theme, ticking clock, heartbeat that speeds up, or a game show tune).
  "Cards stay locked until the timer ends" prevents any flip while the
  countdown is running. With it off, flipping a card stops the timer early.
  The space bar starts and stops the timer during the game.

**Reset game** clears both scores and deals a new round. It needs two clicks
within a few seconds so a stray click cannot wipe a game.

The ▲ button at the right of the top bar hides the bar so only the cards
show on the projector. A small **Menu** tab in the top-right corner brings
it back, and the H key toggles it. The choice is remembered.

## Bingo Card Creator

Build 5×5 or 6×6 bingo cards from words or images and print as many unique
cards as you need.

- Create a named set, then fill the squares by typing, pasting a list of
  words one per line, or adding images with captions.
- Sets are saved in the browser. **Export file** downloads a set, images
  included, as a `.bingo.json` file you can back up or import on another
  computer with **Import file**.
- **Shuffle card** previews a random layout. **Print cards** prints the
  number of cards you ask for, each with its own random layout, one per page.

## Color Picker

The screen is split into colored sections (four or six, depending on the
page). Kids stand by a color, the teacher presses **Start**, and the page
flashes through the colors while a countdown runs with music. The flashing
slows down toward the end, then one color is picked at random and a ding
plays. Set the countdown length in the box before pressing Start.

## Hosting and limits

The pages are served from a hosted site, so there is no way to add files
next to them after the fact. Everything a game needs, including sounds, is
either in this repo or generated in the browser. Dark mode follows the
system setting.

## Development

There is nothing to install. Edit the HTML file, open it in a browser, and
reload. To test over HTTP instead of a `file://` URL, any static server works,
for example:

```
python3 -m http.server 8000
```

Then open `http://localhost:8000/`.

## License

See `LICENSE`.
