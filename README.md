# My Word Cards

A personal vocabulary website inspired by Quizlet, with additional review scheduling based on a memory curve. The entire website is contained in one HTML file and does not require a server or account.

## Features

- **Review**: Uses a simplified SM-2 memory curve algorithm to schedule reviews. Each word is rated as "Forgot / Unsure / Remembered / Familiar," and stronger recall increases the interval until the word appears again. You can study at most 15 new words per day and see the number of reviews scheduled for each of the next 7 days.
- **Cards**: Flip cards by clicking, mark words as "Known / Still Learning," shuffle the deck, and use browser speech to read words aloud.
- **Quiz**: Multiple-choice questions with either English-to-Chinese or Chinese-to-English translations. Afterward, you can practice only the questions you got wrong.
- **Word List**: View, edit, and delete words, and filter them by word set or mastery level.
- **Add Words**: Add one word at a time or paste multiple words in bulk (one word per line, separated with tabs, ` - `, or commas). Quizlet export format is also supported.
- **Backup**: Export and import JSON backup files to move data between devices.

Keyboard shortcuts: During review, press Space to reveal the answer and `1` `2` `3` `4` to rate it. When viewing cards, press Space to flip a card and ← / → to move to the previous or next card.

## Local Use

Open `index.html` directly in a browser.

## Where Data Is Stored

Words and review progress are stored in the browser's `localStorage` and are visible only in that browser. Keep the following in mind:

- Switching computers or browsers does not carry over your existing words. Export a backup from the old browser via "Add → Export Backup," then import it in the new browser.
- Clearing browser data or using private/incognito mode can remove your words, so export backups regularly.

## Example Word Set

`data/sample-words.js` contains 49 words and example sentences from Chapter 1 of _Invisible Women_ by Caroline Criado Perez. If the word library is empty, click "Load Example Word Set" to import them. To use a custom word set, edit this file using the existing format:

```js
window.SAMPLE_SETS = [
  {
    "set": "Word Set Name",
    "words": [
      { "term": "laudable", "meaning": "值得称赞的", "example": "Original sentence from the book (optional)" }
    ]
  }
];
```

`data/sample-words.json` is the JSON version of the same word set and can be imported directly via "Import Backup."

## File Structure

```
index.html              The complete website (HTML, CSS, and JavaScript in one file)
data/sample-words.js    Example word set, loaded when the page starts
data/sample-words.json  JSON version of the example word set
```

## License

MIT
