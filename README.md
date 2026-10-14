# CangJie 仓颉

A Swift (SwiftUI) app for iPad and iPhone that teaches Chinese characters by tracing them back to their oldest form — **oracle-bone script** (甲骨文), carved on bones and shells over 3,000 years ago.

Each level picks one character and lets you *see* how a picture became writing: the sun 日, the moon 月, a person 人, a tree 木. Instead of memorizing strokes, you watch, trace, shake, tap and draw your way from pictograph to modern glyph.

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

A built-in voice guide narrates every level, and the whole app works with VoiceOver.

## Tech

- SwiftUI, Swift Playgrounds app package (`Package.swift`, iOS 18.1+)
- Hand-encoded oracle-bone stroke paths (`OracleStrokePaths.swift`) animated into modern glyphs
- Touch-based tracing canvas with stroke matching (`TraceCanvasView`, `DrawView`)
- On-device speech narration (`VoiceGuidePlayer`) and accessibility narrator (`A11yNarrator`)

## Run it

Open the folder in **Swift Playgrounds** (iPad or Mac) or **Xcode 16+**, then run the app target (its bundle is still named *Bone to Brush*).

## Project layout

```
LevelData/      level sequence — characters, titles, interactions
Models/         game state and level types
Components/     one SwiftUI view per interaction type
OracleStrokePaths.swift   stroke data for each oracle-bone character
Assets.xcassets           pictograph artwork and textures
```
