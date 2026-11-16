# typing-test-wordlists

Word lists and formulas for building a typing test. Free to use (MIT).

Made by the team behind [Typing Test](https://typingtest.network/), a free online typing speed test.

## What is inside

| Key in `wordlists.json` | Content |
|---|---|
| `common200` | About 200 of the most common English words, good for 1-minute tests |
| `punctuation` | Short sentences with capitals, commas, quotes and symbols |
| `numberRow` | Number and symbol drills |
| `formulas` | WPM, CPM, KPH and accuracy formulas in plain words |

## The formulas

A typing word is 5 characters, including spaces.

- Gross WPM = (all typed characters / 5) / minutes
- Net WPM = ((all typed characters / 5) - uncorrected errors) / minutes
- CPM = typed characters / minutes
- KPH = CPM x 60
- Accuracy = correct characters / all typed characters x 100

## Example (JavaScript)

```js
import lists from "./wordlists.json" with { type: "json" };

// build a random test text of n words
function makeText(n = 60) {
  const w = lists.common200;
  return Array.from({ length: n }, () => w[Math.floor(Math.random() * w.length)]).join(" ");
}

// score a finished test
function score(typedChars, correctChars, uncorrectedErrors, seconds) {
  const minutes = seconds / 60;
  const gross = typedChars / 5 / minutes;
  return {
    grossWpm: Math.round(gross),
    netWpm: Math.max(0, Math.round(gross - uncorrectedErrors / minutes)),
    cpm: Math.round(typedChars / minutes),
    accuracy: Math.round((correctChars / typedChars) * 1000) / 10,
  };
}
```

## Speed guide

| WPM | Level |
|---|---|
| Under 30 | Beginner |
| About 40 | Average adult |
| 50 | Above average, common job requirement |
| 60 to 70 | Good to very good |
| 80+ | Fast |
| 100+ | Very fast |

## Try it live

- [1-minute typing test](https://typingtest.network/1-minute-typing-test/)
- [5-minute typing test](https://typingtest.network/5-minute-typing-test/)
- [WPM calculator](https://typingtest.network/wpm-calculator/)
- [What is a good typing speed?](https://typingtest.network/what-is-a-good-typing-speed/)
- [How to type faster](https://typingtest.network/how-to-type-faster/)

## License

MIT. Use the lists in any project.
