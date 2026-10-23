# Your TV, Your Way

*How I turned a stock Android TV into a home screen that feels like mine.*

## Overview

This guide covers the whole journey: the debloat, a clean base, my own dock, a favourites lineup, and a deck of mood cards for nights I can't pick what to watch.

One prompt won't do all of it. Each part below is a short guide (**what to collect, what to prepare**) followed by the **prompt to paste**.

<img width="800" height="283" alt="Before and after: stock TV home screen vs the finished home screen" src="https://github.com/user-attachments/assets/754c4f0a-6e60-47cd-bd03-f2b31dd396d0" />

> **Left:** the TV as it came from the brand. **Right:** the home screen at the end of this guide.

---

## Table of Contents

- [Overview](#overview)
- [1. Before You Start](#1-before-you-start)
- [2. Debloat with CleanYourTV](#2-debloat-with-cleanyourtv)
- [3. Clean Up the Home Screen](#3-clean-up-the-home-screen)
- [4. Gather Your Assets](#4-gather-your-assets)
- [5. Make the Home Screen Yours](#5-make-the-home-screen-yours)
- [6. Build My Favourites](#6-build-my-favourites)
- [7. Add "Don't Have Time to Browse?" Mood Cards](#7-add-dont-have-time-to-browse-mood-cards)
- [8. Finish Up](#8-finish-up)

---

## 1. Before You Start

What you need:

- **An Android TV or Google TV.** CleanYourTV lists which sets and brands work.
- **A computer on the same Wi-Fi as the TV**, with Claude Code installed.
- **Developer mode on the TV.**
  1. Go to **Settings → Device Preferences → About**.
  2. Press **OK** on "Build" seven times.
  3. Go back to **Developer options** and turn on **USB debugging** (and **Network/ADB debugging** if your TV shows it).
  4. When your computer first connects, the TV asks "Allow USB debugging?". Say yes.
- **An image editor with layers and background removal** for the favourites lineup. I used Photoshop; [Photopea](https://www.photopea.com/) is free and opens PSD files.
- **Time.** The prompts are quick. Finding good images is the slow part, so give yourself an evening for the favourites and the cards.

---

## 2. Debloat with CleanYourTV

This is the open-source project that started it all. Over Wi-Fi, with no root, it switches off the ads, tracking and promoted rows and replaces the home screen with a clean Apple TV–style one. It's fully reversible.

- **Website:** [cleanyour.tv](https://cleanyour.tv)
- **GitHub:** [github.com/Gathin23/cleanyourtv](https://github.com/Gathin23/cleanyourtv)
- **The prompt:** `PROMPT.md` (in the repository)

### Steps

1. Clone the repository and open Claude Code inside its folder.
2. Copy the whole prompt from `PROMPT.md`, type in your TV model where it asks, and paste it. Mention that you cloned the repo, so Claude reuses its tools and launcher instead of writing them from scratch.
3. Keep the TV on and stay close. Claude asks before anything that depends on your preferences, and you'll accept the debugging prompt on the TV.

> When it's done you'll have a clean TV and a new home screen. That's the base everything below builds on. **Keep working in the same folder.**

<img width="800" height="450" alt="What the CleanYourTV prompt built: a greeting, the time and apps as tiles" src="https://github.com/user-attachments/assets/84aa95b9-673b-4b91-8b6b-03346fa56a53" />

> What the CleanYourTV prompt built on my TV: a greeting, the time, and my apps as tiles. Clean, but not yet mine.

---

## 3. Clean Up the Home Screen

The launcher you get is already a big step up. Before adding anything personal, strip it down to a quiet base: no greeting, no boxes, no extra rows.

Fill in the highlighted parts in **[brackets]** and paste.

```text
PROMPT · CLEAN-UP

My TV is already debloated and running the home screen launcher from this repo. Before I make it my own, strip the home screen down to a clean, quiet base. Work on the real TV: rebuild and install after each change, and check every change with a screenshot pulled from the TV.

- Remove the greeting and the date. Keep only the time, top left.
- Top right: Wi-Fi, Inputs and Settings as bare icons in one row. No labels, no Wi-Fi network name, no pills or circles behind them.
- Remove every highlight box, ring and glass panel. When something is focused it only grows slightly, with a short, smooth ease. That is the only focus state anywhere.
- Keep a single row of my main apps: [Netflix, Prime Video, YouTube, …]. Remove every other row (the extra apps row, recommendations, anything else).
- Under it, one centred "More apps" button that opens a full-screen grid of every other installed app on the same background. Back returns home. Put these first: [your other streaming apps].
- Screensaver: when the TV goes idle, fade the home screen away and leave only the wallpaper. Any button brings it back.
- Keep it light for the TV: no blur, no video, nothing running in the background.

Ask me before anything that depends on my taste.
```

---

## 4. Gather Your Assets

This is where your TV stops looking like mine. Make one folder (I used `~/Downloads/tv-assets`) and collect everything **before** you prompt.

> **Naming:** name every file after its app or title, in lowercase with dashes: `the-office.jpg`, `netflix.png`.

| Asset | Used for | Size and format | Where to find it, how to prepare it |
|---|---|---|---|
| **Wallpaper** | Home screen | 1920×1080 or higher, PNG | Choose character artwork or a 4K wallpaper. A dark lower third works best behind the app row. Export as an sRGB PNG for smoother dark gradients. |
| **App logos** | Dock | White, transparent PNG, about 600 px wide | Find each app's logo on its official brand page or search for `app name logo PNG`. Trim empty space; Claude can help make coloured logos white. |
| **Character cut-outs** | My Favourites | Transparent PNG, at least 1500 px tall | Use high-resolution promotional images or posters with full-body or waist-up characters. Keep angles and lighting consistent. See [My Favourites](#6-build-my-favourites). |
| **Lineup PSD** | My Favourites | 1920×1080 canvas | Create a PSD with each character cut-out on a separate layer, arranged as a group. See [My Favourites](#6-build-my-favourites). |
| **One scene per favourite** | Background behind My Favourites | 16:9, at least 1920 px wide | Choose an empty scene, street, room, or set without logos or watermarks. Find images under [TMDB](https://www.themoviedb.org/) → title → Media → Backdrops. |
| **Posters** | Content cards | 2:3, around 600×900 px or larger | Download one poster per title from [TMDB](https://www.themoviedb.org/) → title → Media → Posters. |
| **Backdrops** | Background behind content cards | 16:9, at least 1920 px wide | Download backdrops from [TMDB](https://www.themoviedb.org/) → title → Media → Backdrops. Prefer text-free images. |
| **Streaming links** | Favourites and content cards | One valid URL per title | Use [JustWatch](https://www.justwatch.com/) to find streaming availability in your country. Copy the direct streaming link and ask Claude to verify it. Omit titles without working links. |

---

## 5. Make the Home Screen Yours

The top of the screen is the time and weather, a few icons and one row of white logos floating on your wallpaper. When you move along the row:

- the focused logo grows,
- its name appears,
- a one-liner shows above it,
- and a soft glow in that app's colour moves with you.

<img width="800" height="405" alt="The finished home screen, broken down: sizes, type and motion for each part" src="https://github.com/user-attachments/assets/e1d441b2-e18e-41b2-b22a-dc8618b03062" />

> The finished home screen, broken down: sizes, type and motion for each part.

### Steps

1. **Pick the wallpaper.** It sets the mood for everything else, so try a few. You can always ask Claude to swap it later.
2. **Get a white logo for each dock app** and save them in `tv-assets/logos/`.
3. **Write your taglines.** One line per app, ideally a quote from something you'd watch on it. They make the TV feel like yours more than anything else does.
4. **Paste the prompt** with your brackets filled in.
5. **Look at it on the TV and adjust in plain words:** "make the tagline a bit smaller", "move the weather closer to the clock", "the glow is too strong".

```text
PROMPT · HOME SCREEN

Now make the home screen mine. My files are in [~/Downloads/tv-assets]:
- wallpaper.png, my wallpaper
- logos/, white logo PNGs on transparent backgrounds, one per app, named after the app

Wallpaper
- Use wallpaper.png full screen behind everything. Load it in full 32-bit colour and treat it as plain sRGB so dark areas don't band.
- Add a soft black gradient across the bottom so the app row sits on dark, and darken the wallpaper a little more as I scroll down the page.

Top left
- The time in the Outfit typeface (free on Google Fonts; bundle it with the app). No date.
- Beside it, the weather: a small outline icon and the temperature in °C, from Open-Meteo (free, no key needed) for [your city]. Fetch it only while the home screen is showing, at most every 30 minutes. Never show the place name.

The dock
- One row of my white logos, in this order: [Netflix, Prime Video, …]. No boxes: the logos float on the wallpaper.
- Size them by visual weight, so a thin logo and a solid logo look equally big. Never stretch them.
- The focused logo grows a little and its name fades in underneath in small text.
- Above the row, a short tagline for the focused app, and a soft glow behind the dock in that app's brand colour. My taglines: [Netflix: "Bazinga." · Prime Video: "Run, Barry, run."]. If I give several lines for one app, rotate them each time I come home.
- [Optional: a PS5 item that switches the TV to HDMI 1 instead of opening an app.]

Navigation
- Up from the dock goes to the top-right icons. Left and Right stop at the ends. Home brings me back to the last thing I used.

Rebuild, install, and show me a screenshot with each dock app focused.
```

### How I did mine

A black-and-white **Doctor Doom** wallpaper. The dock: **Netflix, Prime Video, JioHotstar, PS5** (it switches the TV to the console's HDMI input), **YouTube** and **Apple TV**. The taglines are lines from my favourite shows: *"Bazinga."*, *"Run, Barry, run."*, *"Legen… wait for it… dary."*

---

## 6. Build My Favourites

A lineup of characters from the shows and films you love, standing over your wallpaper in black and white. Move to one and they turn to colour, step forward and glow in their own colour, the background fades into a scene from their show, and **OK** opens it.

This section is mostly design work you do yourself; the prompt comes last.

<img width="800" height="450" alt="My Favourites lineup on the TV" src="https://github.com/user-attachments/assets/318a74ba-4f47-46c7-b8e1-addb908f5bce" />

### Steps

1. **Pick five to seven favourites**, shows or films, and one character from each. Characters with a recognisable silhouette work best.
2. **Find a big, sharp image of each character**, waist-up or full body. Try to match the camera angle and lighting so the group looks like one photo.
3. **Cut each one out.** In Photoshop: *Select → Subject*, then *Select and Mask* to clean up hair and edges, and output as a layer mask. Check the edges against black: green-screen shots often leave a coloured fringe you need to paint out.
4. **Build the lineup.** New 1920×1080 file with your wallpaper as the bottom layer, just for reference. Drop each cut-out in as its own layer, named after the character. Arrange them in two rows: a back row and a front row that overlaps it. Let their legs run off the bottom; the TV fades them into black.
5. **Add little extras as their own layers:** a symbol, a prop, a mark. Set the blend mode you want. The TV shows each one only when its owner is selected.
6. **Find one scene per title:** a place, not people. Crop it to 16:9 with no logos or text.
7. **Find each title's link** (see [Gather Your Assets](#4-gather-your-assets)).
8. **Paste the prompt**, then add each character's little touch with the follow-ups, one at a time.

```text
PROMPT · MY FAVOURITES

Add a "My Favourites" section under the dock, built from my Photoshop file [~/Downloads/my-favourites.psd].

About the PSD
- One layer per character, cut out on a transparent background and named after the character.
- They're arranged in two rows. Back row: [Sheldon, Walter White, Spider-Man]. Front row: [Patrick Jane, JD, Reverse-Flash, Barney].
- [Extra layer: "Red John", blend mode Darken. It belongs to Patrick Jane.]

Export every layer at full resolution and keep the PSD's layout exactly: where each character stands, their size, their row, and who overlaps whom. Extra layers keep their position and blend mode and only appear while their owner is selected.

How it behaves
- Everyone is black and white. The selected character turns to colour and grows slightly.
- Front-row characters step in front of everyone when selected. Back-row characters grow but stay behind the front row.
- Above the group: the title and the logo of the app it streams on.
- Behind the group: a soft light in the selected character's own main colour.
- While a character is selected, crossfade the wallpaper into a darkened black-and-white scene from their title (my scenes are in [~/Downloads/tv-assets/scenes], named after the title). Moving away brings the wallpaper back. Prepare the scenes in advance so the switch is instant.
- The characters' legs fade into black so the section blends into the page below.
- Left and Right move along a row, Up and Down switch rows, OK opens the title in its app.

The titles (title | app | link)
- [The Big Bang Theory | Netflix | https://www.netflix.com/title/…]
- […]

Check that every link opens the right title on my TV. Rebuild, install, and show me a screenshot with each character selected.
```

### Character touches

Then give each character a small moment of their own. These are mine; write yours the same way: **who, what happens, how long, and that it plays once.**

```text
FOLLOW-UPS · CHARACTER TOUCHES

When [Reverse-Flash] is selected, give him a one-second sideways speedster shudder. Once per selection, not looping.

When [Spider-Man] is selected, add a single vertical thud and a burst of spider-sense lines around his head that looks a little different every time.

When [Patrick Jane] is selected, fade in the [Red John] layer exactly where it sits in the PSD, with its blend mode.
```

### How I did mine

- **Back row:** Sheldon (*The Big Bang Theory*), Walter White (*Breaking Bad*) and Spider-Man (*No Way Home*).
- **Front row:** Patrick Jane (*The Mentalist*), JD (*Master*), Reverse-Flash (*The Flash*) and Barney (*How I Met Your Mother*).
- **Scenes:** all places: Apartment 4A, the RV in the desert, Farhampton station under the yellow umbrella, and the CBI bullpen with Jane's couch.

---

## 7. Add "Don't Have Time to Browse?" Mood Cards

A deck of mood cards for when you can't decide.

- **Swipe left** to skip a mood.
- **Pick one** and its posters spin like a slot machine, land on a title, count down from three and open it in its app.
- **Behind the cards**, a darkened scene from one of the titles changes as you swipe.

<img width="800" height="450" alt="The mood card deck, broken down: card sizes, colours, the swipe, the reel and the countdown" src="https://github.com/user-attachments/assets/2ee22e79-7baa-4283-af65-ef66477fedcc" />

> The deck, broken down: card sizes, colours, the swipe, the reel and the countdown.

### Steps

1. **Choose five or six moods** that match how you actually decide what to watch: comfort, action, something dark, something clever. Then add **"Anything at all"**, which holds every title.
2. **List four to eight titles per mood.** A title can sit in more than one mood.
3. **For each title, find where it streams** in your country and its link.
4. **Download a poster (2:3) and a text-free backdrop (16:9)** for each title into `posters/` and `backdrops/`, named after the title.
5. **Give each mood a colour.** It tints the card, the glow and the countdown bar.
6. **Paste the prompt**, then try a few swipes with the remote.

```text
PROMPT · MOOD CARDS

Under My Favourites, add a section titled "Don't have time to browse?": a deck of mood cards for nights when I can't pick what to watch.

Moods, in deck order (name | colour)
- [Comfort sitcom | #F2B84B]
- [Capes and chaos | #E5484D]
- […]
- Anything at all | #B8C0CC (holds every title automatically)

Titles (title | app | link | moods)
- [The Office | Netflix | https://www.netflix.com/title/… | Comfort sitcom]
- […]

My posters (2:3) are in [~/Downloads/tv-assets/posters] and my backdrops (16:9, no text) in [~/Downloads/tv-assets/backdrops], each named after the title.

The deck
- One big card on top: the mood's colour fading to near-black, its first three posters fanned out, the mood name and "N titles" underneath. The next two moods peek out behind it.
- Left = nope: the card flies off to the left with a slight tilt and fades, and the next mood comes up.
- Right or OK = yes: the mood's posters spin past like a slot-machine reel, fast at first, then slowing down, and land on one random title. Then "Opening in 3…" with a progress bar in the mood's colour, and the title opens in its app. During the countdown, OK opens it now, Right spins again, Left or Back cancels.
- Behind the deck: a heavily darkened, vignetted black-and-white scene from one of the top card's titles. It changes with the card as I swipe, and when the reel lands it crossfades to the picked title's scene. A very soft glow in the mood's colour sits behind the cards.
- Skip any title whose app isn't installed.

Check that every link opens the right title on my TV. Rebuild, install, and show me screenshots of the deck, a swipe, the reel and the countdown.
```

<img width="800" height="450" alt="Mood cards running on the TV" src="https://github.com/user-attachments/assets/36df4680-91c2-4ec7-9114-b3c138e68acf" />

### How I did mine

Six moods: **Comfort sitcom, Capes and chaos, Gotham after dark, Thalapathy mass, Mind games** and **Anything at all**, with 29 titles across Netflix, Prime Video, JioHotstar, ZEE5 and Apple TV.

---

## 8. Finish Up

- **Turn USB debugging off when you're done.** While it's on, any computer on your Wi-Fi can ask to connect, and some TVs cut power to their USB ports. Switch it back on whenever you want to change something.
- **Everything can be undone.** Apps were disabled, not uninstalled. Ask Claude to re-enable an app or restore the stock home screen, or re-enable it on the TV under **Settings → Apps → Show system apps**.
- **Go one section at a time.** Prompt, check it on the TV, then adjust in plain words. Small, specific requests work better than one giant prompt.
- **Keep your assets folder.** Swapping a wallpaper, a character or a whole mood later is one short prompt.
- **Hands off the remote while Claude installs.** Each install restarts the home screen.

*Reference: [source document](https://docs.google.com/document/u/0/d/1JrGoSIpS25907k3UYvtLf_s34vReFVZV/mobilebasic).*
