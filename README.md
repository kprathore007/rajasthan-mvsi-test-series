# MVSI Abhyas — Rajasthan Test Series MVP

A personal, bilingual (English/Hindi), installable PWA for Rajasthan MVSI Paper III practice.

## Included in this MVP
- Responsive phone-first dashboard and one-question-per-screen exam UI
- English/Hindi interface and bilingual question/option fields
- Question palette, previous/next, answer selection, review marking, countdown timer
- Configurable question count and duration
- MVSI marking: +4/3 correct, -4/9 incorrect, 0 unanswered; alternate marking modes
- Result summary, answer explanations and JSON result export
- Import/export question bank in JSON; import CSV; downloadable CSV template
- Browser local storage; service-worker caching for offline use after first visit
- Five bilingual demo questions to test the app

## Run locally
For a quick preview, open `index.html` in a browser. Test-taking and local question import work, but install/offline service-worker features require serving over `localhost` or HTTPS.

If Python is installed, from this folder run:

```bash
python -m http.server 8000
```

Then open `http://localhost:8000` in your browser. For a phone, deploy the folder to an HTTPS static host (for example GitHub Pages or Netlify), open the URL on Android Chrome, then choose **Install app** / **Add to Home screen**. Visit once while online so the service worker can cache the app; then test airplane mode.

## Importing a question bank
1. Click **Get template** in the app and fill one row per question, or create a JSON array.
2. Required CSV headers: `question_en` (or `question`), `A_en`, `B_en`, `C_en`, `D_en`, `correct`.
3. Optional fields: `question_hi`, `A_hi`, `B_hi`, `C_hi`, `D_hi`, `section`, `explanation_en`, `explanation_hi`.
4. `correct` must be `A`, `B`, `C`, or `D` (or 1–4).
5. Import replaces the current bank. Export your bank first if you need a backup.

JSON can use this shape:

```json
[
  {
    "section": "Basics",
    "question_en": "Question text",
    "question_hi": "प्रश्न",
    "options": [
      {"en":"Option A", "hi":"विकल्प A"},
      {"en":"Option B", "hi":"विकल्प B"},
      {"en":"Option C", "hi":"विकल्प C"},
      {"en":"Option D", "hi":"विकल्प D"}
    ],
    "correct": "B",
    "explanation_en": "Why B is correct",
    "explanation_hi": "B सही क्यों है"
  }
]
```

## Current limitations
- The current starter bank contains five sample questions, not a full 150-question set. Import your source bank with its verified answer key to use your own questions.
- PDF extraction is not built in; convert a PDF question bank to CSV/JSON first. Questions without reliable answer keys should be checked before importing.
- Data is local to the browser/device. Clearing browser storage or switching devices can remove or strand data; use Export bank for backups.
- This is a front-end personal-use MVP; it has no account, cloud sync, admin portal, or payment system.
