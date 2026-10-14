# CangJie 仓颉

A Swift (SwiftUI) app for iPad and iPhone that teaches Chinese characters by tracing them back to their oldest form — **oracle-bone script** (甲骨文), carved on bones and shells over 3,000 years ago.

Each level picks one character and lets you *see* how a picture became writing: the sun 日, the moon 月, a person 人, a tree 木. Instead of memorizing strokes, you watch, trace, shake, tap and draw your way from pictograph to modern glyph.

Built for the Apple Swift Student Challenge 2026.

## Why I built it

I've practised calligraphy since first grade, and the more I wrote, the more I felt that Chinese characters weren't designed as symbols. They grew out of everyday life and imagination. I still remember the first time I saw an oracle-bone character turn, step by step, into the character I knew.

Now, watching my younger cousins learn to read, I notice they memorise stroke order but rarely see what a character first looked like. My mom works in international trade, and whenever she explains to foreign clients what a character depicts, they are instantly drawn in.

CangJie tries to keep that "so that's where it comes from" moment, for children and for people who don't read Chinese at all.

## How it plays

**Learn — 9 characters, 9 different interactions**

| # | Character | Interaction |
|---|---|---|
| 1 | 日 Sun | Observe the pictograph morph into the modern glyph |
| 2 | 月 Moon | Trace the ancient strokes with your finger |
| 3 | 人 Person | Glimpse it once, then draw from memory |
| 4 | 木 Tree | Tap to crack the tree open and reveal the oracle form |
| 5 | 口 Mouth | Tap to reveal strokes one by one |
| 6 | 心 Heart | Strokes appear to a heartbeat rhythm |
| 7 | 女 Woman | Pick the matching silhouette |
| 8 | 子 Child | Show, hide, redraw |
| 9 | 一 One | A single swipe |

**Combine** — drag 木 + 木 together to make 林 (woods); guess what 女 + 子 = 好 means.

**Create** — combine what you've learned on your own: 人 + 木 = 休 (rest), 日 + 月 = 明 (bright), 木 + 木 = 林, 女 + 子 = 好.

Combinations follow the traditional compound-ideograph (会意) readings used in teaching; some etymologies are debated among scholars.

See [Accessibility](#accessibility) for how every level works with VoiceOver.

## Design choices

- **Every level asks for a different action** (watch, trace, draw from memory, tap, swipe, match, drag, guess), so it feels like a series of discoveries rather than a set of tasks.
- **The player moves from guided to independent**: early levels show the way; the last levels ask them to combine characters on their own.
- **Each oracle-to-modern morph pauses for 2.5 seconds** before moving on, leaving time for the "aha" to land.
- **Successful combinations are marked with haptic feedback**, so creating a character is felt as well as seen.

## Accessibility

CangJie asks players to trace characters and drag components together. Both are gesture-based, and neither works with VoiceOver. That was the biggest accessibility challenge I faced.

- **Tracing**: the canvas is an adjustable element. VoiceOver users swipe up or down to move along the guide strokes, and an auto-trace button lets them complete the stroke without drawing at all.
- **Drag-and-combine**: draggable tiles switch to tappable buttons when VoiceOver is active. Users tap to place pieces, then use layout and swap controls to arrange them, since direction matters when forming the correct character.
- **Voice guide**: built with AVSpeechSynthesizer, it narrates each level's context and instructions aloud, with adjustable speed. It pauses automatically when system VoiceOver is active to avoid conflict.
- **Basics**: decorative images are hidden from VoiceOver, all buttons meet the 44-point minimum, and interactive elements have clear labels and hints.

Before this project, I never thought about how someone who cannot see would use an app. Now I think about it every time I add a new screen.

## Tech

- SwiftUI, Swift Playgrounds app package (`Package.swift`, iOS 18.1+)
- Hand-encoded oracle-bone stroke paths (`OracleStrokePaths.swift`) animated into modern glyphs
- Touch-based tracing canvas with stroke matching (`TraceCanvasView`, `DrawView`)
- On-device speech narration (`VoiceGuidePlayer`) and accessibility narrator (`A11yNarrator`)

## Run it

Open the folder in **Swift Playgrounds** (iPad or Mac) or **Xcode 16+**, then run the app target.

## Project layout

```
LevelData/      level sequence — characters, titles, interactions
Models/         game state and level types
Components/     one SwiftUI view per interaction type
OracleStrokePaths.swift   stroke data for each oracle-bone character
Assets.xcassets           background texture
```
