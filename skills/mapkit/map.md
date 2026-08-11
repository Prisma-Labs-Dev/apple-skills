---
title: Map
description: A view that displays an embedded map interface.
source: https://developer.apple.com/documentation/mapkit/map
source_kind: apple-docc
source_json: https://developer.apple.com/tutorials/data/documentation/mapkit/map.json
timestamp: 2026-08-11T06:08:56.000Z
---

**Navigation:** [MapKit](/documentation/mapkit)

**Structure**

# Map

**Available on:** iOS 14.0+, iPadOS 14.0+, Mac Catalyst 14.0+, macOS 11.0+, tvOS 14.0+, visionOS, watchOS 7.0+

> A view that displays an embedded map interface.

```swift
@MainActor @preconcurrency struct Map<Content> where Content : View
```

## Overview

Use this SwiftUI view to display a `Map` with markers, annotations, and custom content you provide. You can configure the `Map` to optionally display the user’s location, track a location, and display various controls to allow them to interact with and control the map’s display. The following example displays a map of downtown San Francisco that shows different markers, and an annotation with custom view content at specific locations:

```swift
    struct ContentView: View {
        var body: some View {
            Map {
                Marker("San Francisco City Hall", coordinate: cityHallLocation)
                    .tint(.orange)
                Marker("San Francisco Public Library", coordinate: publicLibraryLocation)
                    .tint(.blue)
                Annotation("Diller Civic Center Playground", coordinate: playgroundLocation) {
                    ZStack {
                        RoundedRectangle(cornerRadius: 5)
                            .fill(Color.yellow)
                        Text("🛝")
                            .padding(5)
                    }
                }
            }
            .mapControlVisibility(.hidden)
        }
    }
```

You create markers, annotations, and overlays using [MapContentBuilder](/documentation/mapkit/mapcontentbuilder) with any of several [MapContent](/documentation/mapkit/mapcontent) types including:

- [Annotation](/documentation/mapkit/annotation)
- [UserAnnotation](/documentation/mapkit/userannotation)
- [Marker](/documentation/mapkit/marker)
- [MapCircle](/documentation/mapkit/mapcircle)
- [MapPolygon](/documentation/mapkit/mappolygon)
- [MapPolyline](/documentation/mapkit/mappolyline)

You can also add a variety of controls to allow a person to interact with the map to change the map’s scale, display or hide the device’s current location, and so on:

- [MapCompass](/documentation/mapkit/mapcompass)
- [MapPitchToggle](/documentation/mapkit/mappitchtoggle)
- [MapPitchSlider](/documentation/mapkit/mappitchslider)
- [MapScaleView](/documentation/mapkit/mapscaleview)
- [MapUserLocationButton](/documentation/mapkit/mapuserlocationbutton)
- [MapZoomStepper](/documentation/mapkit/mapzoomstepper)

## Conforms To

- [Sendable](/documentation/Swift/Sendable)
- [SendableMetatype](/documentation/Swift/SendableMetatype)
- [View](/documentation/SwiftUI/View)

## Creating a map

- [init(bounds:interactionModes:scope:)](/documentation/mapkit/map/init(bounds:interactionmodes:scope:)) Creates a new, empty map with the bounds, interaction modes, and scope you provide.
- [init(bounds:interactionModes:scope:content:)](/documentation/mapkit/map/init(bounds:interactionmodes:scope:content:)) Creates a new map with the bounds, interaction modes, scope, and content you provide.
- [init(bounds:interactionModes:selection:scope:)](/documentation/mapkit/map/init(bounds:interactionmodes:selection:scope:)-11lec) Creates a new, empty map with the bounds, interaction modes, a binding to a map feature, and scope you provide.
- [init(bounds:interactionModes:selection:scope:)](/documentation/mapkit/map/init(bounds:interactionmodes:selection:scope:)-236di) Creates a new, empty map with the bounds, interaction modes, the selected map feature, and scope you provide.
- [init(bounds:interactionModes:selection:scope:content:)](/documentation/mapkit/map/init(bounds:interactionmodes:selection:scope:content:)-28wns) Creates a new map with the bounds, interaction modes, selected map feature, scope, and map content you provide.
- [init(bounds:interactionModes:selection:scope:content:)](/documentation/mapkit/map/init(bounds:interactionmodes:selection:scope:content:)-2tdbr) Creates a new map with the bounds, interaction modes, selected value, scope, and map content you provide.
- [init(initialPosition:bounds:interactionModes:scope:)](/documentation/mapkit/map/init(initialposition:bounds:interactionmodes:scope:)) Creates a new, empty map with the initial camera position, bounds, interaction modes, and scope you provide.
- [init(initialPosition:bounds:interactionModes:scope:content:)](/documentation/mapkit/map/init(initialposition:bounds:interactionmodes:scope:content:)) Creates a new map with the initial camera position, bounds, interaction modes, scope, and map content you provide.
- [init(initialPosition:bounds:interactionModes:selection:scope:)](/documentation/mapkit/map/init(initialposition:bounds:interactionmodes:selection:scope:)) Creates a new, empty map with the initial camera position, bounds, interaction modes, selected map feature, and scope you provide.
- [init(initialPosition:bounds:interactionModes:selection:scope:content:)](/documentation/mapkit/map/init(initialposition:bounds:interactionmodes:selection:scope:content:)-9feos) Creates a new map with the initial camera position, bounds, interaction modes, selected map feature, scope, and content you provide.
- [init(initialPosition:bounds:interactionModes:selection:scope:content:)](/documentation/mapkit/map/init(initialposition:bounds:interactionmodes:selection:scope:content:)-451vp) Creates a new map with the initial camera position, bounds, interaction modes, selected map feature, scope, and content you provide.
- [init(position:bounds:interactionModes:scope:)](/documentation/mapkit/map/init(position:bounds:interactionmodes:scope:)) Creates a new, empty map with the initial camera position, bounds, interaction modes, and scope you provide.
- [init(position:bounds:interactionModes:scope:content:)](/documentation/mapkit/map/init(position:bounds:interactionmodes:scope:content:)) Creates a new map with the initial camera position, bounds, interaction modes, scope, and content you provide.
- [init(position:bounds:interactionModes:selection:scope:)](/documentation/mapkit/map/init(position:bounds:interactionmodes:selection:scope:)) Creates a new map with the initial camera position, bounds, interaction modes, scope, and content you provide.
- [init(position:bounds:interactionModes:selection:scope:content:)](/documentation/mapkit/map/init(position:bounds:interactionmodes:selection:scope:content:)-47y4p) Creates a new map with the initial camera position, bounds, interaction modes, selected feature, scope, and content you provide.
- [init(position:bounds:interactionModes:selection:scope:content:)](/documentation/mapkit/map/init(position:bounds:interactionmodes:selection:scope:content:)-9xq1q) Creates a new map with the initial camera position, bounds, interaction modes, selected feature, scope, and content you provide.
- [MapInteractionModes](/documentation/mapkit/mapinteractionmodes) Options that indicate the user interactions that the map responds to.

## Managing feature selection

- [mapFeatureSelectionContent(content:)](/documentation/SwiftUI/View/mapFeatureSelectionContent(content:)) Specifies a custom presentation for the currently selected feature.
- [mapFeatureSelectionDisabled(_:)](/documentation/SwiftUI/View/mapFeatureSelectionDisabled(_:)) Specifies which map features should have selection disabled.

## Managing Look Around view presentation

- [lookAroundViewer(isPresented:initialScene:allowsNavigation:showsRoadLabels:pointsOfInterest:onDismiss:)](/documentation/SwiftUI/View/lookAroundViewer(isPresented:initialScene:allowsNavigation:showsRoadLabels:pointsOfInterest:onDismiss:))
- [lookAroundViewer(isPresented:scene:allowsNavigation:showsRoadLabels:pointsOfInterest:onDismiss:)](/documentation/SwiftUI/View/lookAroundViewer(isPresented:scene:allowsNavigation:showsRoadLabels:pointsOfInterest:onDismiss:))

## Managing map control sizing and visibility

- [mapControlVisibility(_:)](/documentation/SwiftUI/View/mapControlVisibility(_:)) Configures all Map controls in the environment to have the specified visibility
- [mapControls(_:)](/documentation/SwiftUI/View/mapControls(_:)) Configures all `Map` views in the associated environment to have standard size and position controls

## Managing the camera

- [mapCameraKeyframeAnimator(trigger:keyframes:)](/documentation/SwiftUI/View/mapCameraKeyframeAnimator(trigger:keyframes:)) Uses the given keyframes to animate the camera of a `Map` when the given trigger value changes.
- [onMapCameraChange(frequency:_:)](/documentation/SwiftUI/View/onMapCameraChange(frequency:_:)-2pcga) Performs an action when Map camera framing changes
- [onMapCameraChange(frequency:_:)](/documentation/SwiftUI/View/onMapCameraChange(frequency:_:)) Performs an action when Map camera framing changes

## Setting the namespace Identifier

- [mapScope(_:)](/documentation/SwiftUI/View/mapScope(_:)) Creates a mapScope that SwiftUI uses to connect map controls to an associated map.

## Setting the map style

- [mapStyle(_:)](/documentation/SwiftUI/View/mapStyle(_:)) Specifies the map style to be used.

## Deprecated

- [Deprecated Symbols](/documentation/mapkit/deprecated-symbols) Map protocols and view modifiers that are no longer supported.

## Displaying place information

- [mapFeatureSelectionAccessory(_:)](/documentation/SwiftUI/View/mapFeatureSelectionAccessory(_:)) Specifies the selection accessory to display for a `MapFeature`
- [mapItemDetailSelectionAccessory(_:)](/documentation/mapkit/mapcontent/mapitemdetailselectionaccessory(_:)) Specifies the selection accessory to display for the selected map item content.

## Initializers

- [init(bounds:interactionModes:selection:scope:content:)](/documentation/mapkit/map/init(bounds:interactionmodes:selection:scope:content:)-335qt)
- [init(initialPosition:bounds:interactionModes:selection:scope:content:)](/documentation/mapkit/map/init(initialposition:bounds:interactionmodes:selection:scope:content:)-2u4ry)
- [init(position:bounds:interactionModes:selection:scope:content:)](/documentation/mapkit/map/init(position:bounds:interactionmodes:selection:scope:content:)-96bhq)

## Essentials

- [MapStyle](/documentation/mapkit/mapstyle) A style that you can apply to a map.

---

*Extracted from Apple DocC JSON by apple-skills tooling.*
*This is unofficial content. All documentation belongs to Apple Inc.*
