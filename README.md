# tīngshuō

Flashcards for the 1000 most common words in spoken Mandarin. Pinyin and audio only, no characters.

- **Mixed card directions.** Listening cards play a word and you say what it means. Speaking cards show the English and you say it out loud.
- **Spaced repetition, Anki-style.** New words come back after 1 minute, then 10, then the next day, with intervals growing from there. Grade each card Again / Hard / Good / Easy.
- **Pitch contours.** A small melody line over each syllable shows how the word is actually said, including tone changes (你好 is drawn as "ní hǎo").
- **Example sentence and usage note for every word.** Tap any pinyin in a note to hear it.
- **Works offline** and can be installed to your phone's home screen.

## Put it on GitHub Pages

1. Create a new repository on GitHub (for example `tingshuo`).
2. Upload everything in this folder to the root of the repo. Keep the `fonts/` and `icons/` folders.
   With git:
   ```
   git init
   git add .
   git commit -m "tīngshuō"
   git branch -M main
   git remote add origin https://github.com/YOUR-USERNAME/tingshuo.git
   git push -u origin main
   ```
3. In the repo, go to **Settings → Pages**. Under "Build and deployment", set **Source** to *Deploy from a branch*, then pick **main** and **/ (root)**, and save.
4. Wait a minute, then open `https://YOUR-USERNAME.github.io/tingshuo/`.

All paths are relative, so it also works from a subfolder like `/docs` (pick that folder in step 3 instead).

To try it locally first, run `python3 -m http.server` in this folder and open http://localhost:8000. Opening `index.html` directly from disk works too, but offline mode needs a server.

## Audio

Audio uses your device's built-in text-to-speech, so you need a Mandarin voice installed. Most phones and Macs have one available; the app's Settings page explains how to add one. Microsoft Edge's online "Natural" voices sound the best. Chrome on a desktop includes a Google Mandarin voice that works when you're online.

## Your progress

Progress is saved in the browser you study in (localStorage). It doesn't sync between devices. To move it, use **Settings → Export progress** on one device and **Import progress** on the other. Clearing your browser data erases it, so export a backup now and then.

## Files

| File | What it is |
| --- | --- |
| `index.html` | Page shell |
| `style.css` | All styling. Tone colors are the `--t1`…`--t4` variables at the top. |
| `app.js` | Everything else: scheduling, audio, the pitch contours, the four screens |
| `words.js` | The 1000 words, in study order |
| `sw.js` | Offline support. Bump `VERSION` after editing files if you want returning visitors to get a clean cache. |
| `manifest.webmanifest`, `icons/` | Home-screen install |
| `fonts/` | Gentium Book Plus and Andika (SIL Open Font License, see the license files) |

### Editing words

Each line in `words.js` is one word:

```
["知道","zhī|dào","to know (a fact)","我知道了。","Wǒ zhī|dào le.","Got it.","note"]
```

The fields are: characters (used only for audio, never shown), pinyin, English, example in characters (audio only), example pinyin, example English, and a note. The `|` marks syllable breaks inside a word so the app can color each tone. In notes, `{{我的|wǒ de}}` shows as tappable pinyin that plays the characters.

## Where the words come from

The ranking is from SUBTLEX-CH (Cai & Brysbaert, 2010), word frequencies from 33.5 million words of Mandarin film and TV subtitles. It's a better match for everyday speech than counts based on books or news. Subtitles skew toward crime and cop shows, so genre words like "corpse," "vampire" and "jury" were cut, along with name fragments and slurs. A few essentials that subtitles undercount (numbers, "hello," "how much is it," "tea") were added and scheduled early. Pinyin for every word and example was checked syllable by syllable against a pinyin dictionary.

> Cai, Q., & Brysbaert, M. (2010). SUBTLEX-CH: Chinese word and character frequencies based on film subtitles. *PLoS ONE, 5*(6), e10729.
