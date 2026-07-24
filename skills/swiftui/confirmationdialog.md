---
title: confirmationDialog(_:isPresented:titleVisibility:actions:)
description: Presents a confirmation dialog when a given condition is true, using a localized string resource for the title.
source: https://developer.apple.com/documentation/swiftui/view/confirmationdialog(_:ispresented:titlevisibility:actions:)
source_kind: apple-docc
source_json: https://developer.apple.com/tutorials/data/documentation/swiftui/view/confirmationdialog(_:ispresented:titlevisibility:actions:).json
timestamp: 2026-07-24T07:42:58.868Z
---

**Navigation:** [SwiftUI](/documentation/swiftui) › [View](/documentation/swiftui/view)

**Instance Method**

# confirmationDialog(_:isPresented:titleVisibility:actions:)

**Available on:** iOS 16.0+, iPadOS 16.0+, Mac Catalyst 16.0+, macOS 13.0+, tvOS 16.0+, visionOS 1.0+, watchOS 9.0+

> Presents a confirmation dialog when a given condition is true, using a localized string resource for the title.

```swift
@export(implementation) nonisolated func confirmationDialog<A>(_ titleResource: LocalizedStringResource, isPresented: Binding<Bool>, titleVisibility: Visibility = .automatic, @ContentBuilder actions: () -> A) -> some View where A : View
```

## Parameters

**titleResource**

Text resource for the localized string that describes the title of the dialog.

**isPresented**

A binding to a Boolean value that determines whether to present the dialog. When the user presses or taps the dialog’s default action button, the system sets this value to `false`, dismissing the dialog.

**titleVisibility**

The visibility of the dialog’s title. The default value is [Visibility.automatic](/documentation/swiftui/visibility/automatic).

**actions**

A [ContentBuilder](/documentation/swiftui/contentbuilder) returning the dialog’s actions.

## Discussion

In the example below, a button conditionally presents a confirmation dialog depending upon the value of a bound Boolean variable. When the Boolean value is set to `true`, the system displays a confirmation dialog with a cancel action and a destructive action.

```swift
struct ConfirmEraseItems: View {
    @State private var isShowingDialog = false
    var body: some View {
        Button("Empty Trash") {
            isShowingDialog = true
        }
        .confirmationDialog(
            "Permanently erase the items in the Trash?",
            isPresented: $isShowingDialog
        ) {
            Button("Empty Trash", role: .destructive) {
                // Handle empty trash action.
            }
        }
    }
}
```

All actions in a confirmation dialog will dismiss the dialog after the action runs. The default button will be shown with greater prominence. You can influence the default button by assigning it the [defaultAction](/documentation/swiftui/keyboardshortcut/defaultaction) keyboard shortcut.

The system may reorder the buttons based on their role and prominence.

Dialogs include a standard dismiss action by default. If you provide a button with a role of [cancel](/documentation/swiftui/buttonrole/cancel), that button takes the place of the default dismiss action. You don’t have to dismiss the presentation with the cancel button’s action.

> **Note:** In regular size classes in iOS, the system renders confirmation dialogs as a popover that the user dismisses by tapping anywhere outside the popover, rather than displaying the standard dismiss action.

On iOS, tvOS, and watchOS, confirmation dialogs only support controls with labels that are [Text](/documentation/swiftui/text). Passing any other type of view results in the content being omitted.

This modifier creates a [Text](/documentation/swiftui/text) view for the title on your behalf. See [Text](/documentation/swiftui/text) for more information about localizing strings.

## Getting confirmation for an action

- [confirmationDialog(_:isPresented:titleVisibility:presenting:actions:)](/documentation/swiftui/view/confirmationdialog(_:ispresented:titlevisibility:presenting:actions:)) Presents a confirmation dialog using data to produce the dialog’s content and a localized string resource for the title.
- [dismissalConfirmationDialog(_:shouldPresent:actions:)](/documentation/swiftui/view/dismissalconfirmationdialog(_:shouldpresent:actions:)) Presents a confirmation dialog when a dismiss action has been triggered.

---

*Extracted from Apple DocC JSON by apple-skills tooling.*
*This is unofficial content. All documentation belongs to Apple Inc.*
