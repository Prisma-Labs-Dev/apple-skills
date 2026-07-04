# Changelog

## 2026-07-04

- `xcuitest`: restructured to match the collection's pattern — `SKILL.md` is now a short intro + table of contents (quick-reference snippet, topic guide table, downloaded-docs table, sources), with the bulk moved into topic files alongside the existing reference docs: `element-queries.md`, `interactions.md`, `waiting.md`, `swift6-concurrency.md`, `assertions.md`, `screenshots.md`, `launch-arguments.md`, `permissions.md`, `test-helpers.md`, and `troubleshooting.md`. No content was removed.

## 2026-07-04 (1.0.14)

- `ios-dev`: added the craft-bar operating rule — apps should feel current-generation (fluid, design-forward; custom components, novel interactions, and Metal shaders in-bounds), while the aesthetic direction itself stays the model's per-app judgment. High ambition, no prescribed style.

## 2026-07-04 (1.0.13)

De-opinionate the collection: reference docs stay, taste mandates go. The model should form its own design judgment; skills provide facts.

- Moved `ios-ui-craft`, `ios-design-consultant`, and `guide-swiftui-view-refactor` to `disabled-skills/` (kept in repo, not loaded by agents) — they impose aesthetic manifestos, "Apple-approved" gatekeeping, and MV-over-MVVM architecture mandates.
- `ios-dev`: UIKit is now first-class alongside SwiftUI (removed the no-bridging rule); removed the Liquid Glass default-design-system mandate; added an explicit rule against imposing a house style; removed routing to the disabled skills.
- `ios-liquid-glass`: stripped the design manifesto (anti-pattern tables, typography/color/dark-mode-first directives, "The Mandate"); now a pure API reference with Apple's stated principles noted as reference material.

## 2026-05-13

- Added the `core-animation` skill with the full QuartzCore framework index and per-symbol reference pages for `CALayer`, the animation classes (`CAAnimation`, `CABasicAnimation`, `CAKeyframeAnimation`, `CASpringAnimation`, `CAPropertyAnimation`, `CAAnimationGroup`, `CATransition`), `CATransaction`, `CAMediaTiming`, `CATransform3D`, common layer subclasses (`CAShapeLayer`, `CAGradientLayer`, `CAEmitterLayer`, `CAEmitterCell`, `CAReplicatorLayer`, `CAMetalLayer`, `CATextLayer`, `CATiledLayer`), and `CADisplayLink`.
- Added SwiftUI `Canvas` and `GraphicsContext` reference pages and surfaced them in the `swiftui` skill table.
- Listed Core Animation in the `apple-docs-index` framework table.

## 2026-04-10

- Added the `uikit` skill with a full UIKit framework index and focused core API pages fetched through the direct Apple DocC workflow.
- Updated skill fetch instructions to use `pnpm fetch-doc` instead of the old hosted proxy workflow.
- Replaced stale generated "Not Found" docs for SwiftUI inspector and TipKit popover tips, and removed an unreferenced Liquid Glass "Not Found" page.

## 2026-04-09

Refreshed all 179 skill docs from Apple's DocC JSON directly (replaced the hosted proxy path).

### What changed in the docs

- **App Intents** — Apple reorganized the overview significantly: new "System experiences" and "Domains" sections, new `IntentURLRepresentation` and `AppShortcutsContent` APIs, reworked Siri + Apple Intelligence hierarchy
- **SwiftUI** — overview trimmed by ~1400 lines (Apple removed duplicate/deprecated entries), new Articles section added
- **StoreKit, HealthKit, Combine, MapKit, SwiftData indexes** — large reshuffles as Apple reorganized their reference trees
- **HIG** — tables now render correctly (typography sizes, accessibility contrast ratios, button styles, etc. were previously blank rows); layout and color pages gained substantial new content
- **Liquid Glass** — all pages updated with refined API surface
- **Rendering fixes across all docs** — platform availability no longer shows `undefined`, WWDC session links now have proper titles, link text uses real names instead of raw identifiers, Apple images now stay in the main docs, and embedded Apple videos move into neighboring `*.videos.md` sidecars

### Tooling

- Fetch directly from `developer.apple.com` DocC JSON, drop the hosted proxy dependency
- Native Node TypeScript execution (25.2+), drop `tsx`
- Add GitHub Actions CI
