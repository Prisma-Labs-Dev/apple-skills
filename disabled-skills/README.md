# Disabled Skills

These skills are kept in the repo but intentionally NOT loaded by agents (only `skills/` is scanned). They impose a specific taste or architecture rather than documenting facts — aesthetic manifestos, MV-over-MVVM mandates, "Apple-approved" design gatekeeping. The model should express its own design judgment and use the reference skills for API facts.

| Skill | Why disabled |
|-------|--------------|
| `ios-ui-craft` | Aesthetic manifesto: anti-pattern tables, "design dark first", font/color mandates |
| `ios-design-consultant` | "Apple-approved" / Design Award framing forces HIG conformity |
| `guide-swiftui-view-refactor` | Mandates MV over MVVM and strict view property ordering |

To re-enable one, move its directory back into `skills/` and bump the plugin version.
