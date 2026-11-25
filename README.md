# DeutschFlow — Royal Blue edition (A1–C2)

An installable progressive web app (PWA), combining SatzWerk v3 with reading and listening comprehension. English instructions, meanings and explanations. No mandatory paid API, accounts or backend.

## Actual content
- 13,000 distinct German model sentences retained from SatzWerk (reviewed bilingual templates, not independently proofread by a native speaker). 1,000 / 1,500 / 2,000 / 2,500 / 3,000 / 3,000 by level.
- Six sentence practice modes: build, translate, correct, free writing, listen/repeat, speak from English. 78,000 possible sentence-mode combinations; free writing is self-review.
- Two more sentence modes: reading (choose English meaning) and listening dictation, using the same 13,000 model sentences. 26,000 additional possible activities, not unique passages.
- 30 original short bilingual passages (five per level), two questions per passage, usable in reading and listening: 60 reading and 60 listening comprehension questions. Total: 104,120 potential mode/question combinations, not unique learning texts.
- Reading and listening question options, answer explanations/evidence, transcript reveal, German voice selection, adjustable playback speed, pause/resume and stop. Listening uses device TTS, not native-speaker recordings.
- One dashboard: daily history, four skill scores, weekly change, 7/30/90-day charts, goals, streak, mistake review (written and comprehension), CSV export, JSON backup/restore. Guided comprehension excluded from accuracy; speaking scores are recognized word-match, not accent assessment.

## Deploy on Cloudflare Pages
1. Extract this ZIP. Upload all files in this folder to the root of a new GitHub repository (e.g. `deutschflow-app`). Keep `index.html` at repository root.
2. Cloudflare dashboard > Workers & Pages > create a Pages project > connect Git repository. Select the new repository and main branch.
3. Framework: None. Build command: leave blank if permitted, otherwise `exit 0`. Build output directory: `.`. No environment variables needed. Deploy.
4. Open the HTTPS pages.dev link supplied by Cloudflare. Install from the browser, not the preview HTML.
5. Android Chrome: browser menu > Install app or Add to Home screen. iPhone Safari: Share > Add to Home Screen. Chrome/Edge desktop: install icon/menu when available. The in-app install button also provides instructions.
6. Grant microphone permission when using speaking mode. Availability depends on browser/device and speech service. German voice must be installed/available. Browser speech service may process audio remotely; the app does not store audio recordings.

## Keep your existing SatzWerk progress
Before updating, open SatzWerk v3 > My progress > Download backup (JSON). After installing DeutschFlow, open My progress > Restore backup and select that file. Import replaces current progress, so export any new progress first. The app uses the same local storage key as v3 on the same origin, but separate sites have separate browser storage. There is no automatic cross-device sync. Export regularly. Do not clear browser data if you want to keep progress.

## Offline and limitations
The service worker precaches the app and learning data after successful first online load. Offline text exercises should then be available; the hosted offline path and installation have not been verified here because browser URL navigation is blocked in the test environment. Speech recognition often needs internet and device audio support; TTS may also need network. No APK, native iOS binary or app-store publication is provided. This is an independent CEFR-inspired trainer, not Goethe certification or an official/mock exam suite. The larger proposed mock exam, full dictionary, adaptive spaced repetition and 26,000 distinct long passages have not been implemented. Answers are based on fixed models; open-ended alternatives may not be recognized.

## Verification
Isolated Chromium: loaded all 60 level/mode combinations; graded 24 comprehension samples, verified four-skill scoring, guided exclusion, mistakes, JSON/CSV export and restore, simulated storage, mobile layout and no page errors. Counted 13,000 unique sentence models and 30 passages. Actual audio, microphone, installed PWA, live hosting and offline behavior require real-device testing. German content has not received professional line-by-line review.

## Royal Blue update
This appearance-only update preserves the exercise databases, grading logic and storage keys. Replace the files in your existing repository and deploy to the same HTTPS URL to retain browser-local progress. Export a JSON backup first. The app manifest identity is unchanged; the service worker cache name is bumped so old green assets are replaced when the updated worker activates. If an old screen remains, close all app tabs/windows and reopen online. Do not clear site data. The installed home-screen icon may refresh on the browser’s own schedule. A separate origin requires importing a backup.

## Vocabulary Studio update

Open **Practice vocabulary** to study the built-in 579 distinct German entries. Estimated learning-level distribution: A1 166, A2 100, B1 89, B2 82, C1 69, C2 73. Levels are pedagogical estimates, not official word lists. The starter words and glosses were authored for this app; they have not undergone professional linguistic proofreading. The vocabulary starter collection is not a 16,000-word database. Example sentences appear only when an existing matching example or an authored/imported example is available; verb conjugations are supplied for selected verbs, not all verbs.

Four modes: flashcards (self-rated English recall), written German recall (strict spelling), listening dictation (German device voice), and speaking (browser-recognized word match, not pronunciation assessment). Review intervals for successive remembered answers: 1, 3, 7, 14, 30, 60 days; an incorrect answer resets the stage and is immediately due. Stage 4+ is labelled retained, not guaranteed mastery. Daily new-word goal defaults to 20. Browse all words bypasses the daily queue. Vocabulary from a current exercise is available after grading and matches exact dictionary/plural forms, not every inflection. Existing sentence bank and passages are unchanged.

### Expand the dictionary

Use the CSV template inside the vocabulary dialog. CSV header: `word,english,level,topic,pos,article,plural,conjugation,example_de,example_en`. Only word and English meaning are required; missing level defaults to B1. JSON imports are arrays of rows containing the same columns in that order. Imports deduplicate by exact NFC-normalized headword, validate fields, and skip bad rows. Maximum combined entries 16,000; actual capacity also depends on local browser storage (especially for long examples). No external dictionary was bundled because the download was unavailable in the build environment. For optional external data, use only appropriately licensed datasets; verify their translations and CEFR tags before relying on them. Imported data is not automatically linguistically verified.

The original local storage key (`satzwerk.v2`) and exercise identifiers are unchanged. Vocabulary data is added to the existing progress object; the main JSON backup includes imported entries and word-review history. Vocabulary CSV export contains per-word review statistics. Export your backup before replacing website files and use the same HTTPS origin/browser to preserve data. Upload all files to the existing GitHub repository root; Cloudflare Pages configuration stays unchanged. Service worker cache version has been incremented. Reopen online to pick up the update. Standalone HTML preview is for local testing, not PWA installation.

### Verification

Isolated Chromium tests cover all four original skills at each level, vocabulary modes at each level, flashcard and typed recall, review scheduling, import/deduplication, backup export and restore, mobile width, and simulated local storage. Actual speech/audio, service worker installation and live hosting are not tested on a real device. The full 16,000-word target has not been populated.


## Grammar Coach update
- After submitting any sentence-building, translation, error correction, free-writing, speaking, sentence-meaning or dictation exercise, a model-based grammar explanation appears whether or not the response was accepted.
- Includes sentence-part roles, finite verb and clause order, relevant cases and inflection, simplified terminology, a model/contrast example, English meaning and comparison hints for the submitted response.
- Covers all 13,000 sentence records using annotations for 72 original sentences and 31 generation templates; no changes to sentence IDs, original data, vocabulary, scoring or storage key. Passage questions retain their existing evidence explanations; the coach does not parse arbitrary passages.
- Word differences are comparison hints, not a full language diagnosis. Accepted alternatives refer to the annotated main model; speech recognition can introduce errors. No external API required.
- To update, back up progress and replace all files in your existing repository, including grammar.js and sw.js. Keep the existing website origin. Browser storage is local. Reopen the hosted PWA online to pick up the new service worker.
- Verification: automated role coverage across all 13,000 model sentences; isolated Chromium tests using simulated storage and speaking transcripts; actual hosted PWA updates, browser persistence and device audio/microphone require live testing.
