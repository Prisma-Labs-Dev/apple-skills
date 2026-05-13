---
title: GraphicsContext
description: An immediate mode drawing destination, and its current state.
source: https://developer.apple.com/documentation/swiftui/graphicscontext
source_kind: apple-docc
source_json: https://developer.apple.com/tutorials/data/documentation/swiftui/graphicscontext.json
timestamp: 2026-05-13T20:40:21.095Z
---

**Navigation:** [SwiftUI](/documentation/swiftui)

**Structure**

# GraphicsContext

**Available on:** iOS 15.0+, iPadOS 15.0+, Mac Catalyst 15.0+, macOS 12.0+, tvOS 15.0+, visionOS 1.0+, watchOS 8.0+

> An immediate mode drawing destination, and its current state.

```swift
@frozen struct GraphicsContext
```

## Overview

Use a context to execute 2D drawing primitives. For example, you can draw filled shapes using the [fill(_:with:style:)](/documentation/swiftui/graphicscontext/fill(_:with:style:)) method inside a [Canvas](/documentation/swiftui/canvas) view:

```swift
Canvas { context, size in
    context.fill(
        Path(ellipseIn: CGRect(origin: .zero, size: size)),
        with: .color(.green))
}
.frame(width: 300, height: 200)
```

The example above draws an ellipse that just fits inside a canvas that’s constrained to 300 points wide and 200 points tall:

![A screenshot of a view that shows a green ellipse.](https://docs-assets.developer.apple.com/published/d7362dca562c6e165da941bc85ce0ff7/GraphicsContext-1%402x.png)

In addition to outlining or filling paths, you can draw images, text, and SwiftUI views. You can also use the context to perform many common graphical operations, like adding masks, applying filters and transforms, and setting a blend mode. For example you can add a mask using the [clip(to:style:options:)](/documentation/swiftui/graphicscontext/clip(to:style:options:)) method:

```swift
let halfSize = size.applying(CGAffineTransform(scaleX: 0.5, y: 0.5))
context.clip(to: Path(CGRect(origin: .zero, size: halfSize)))
context.fill(
    Path(ellipseIn: CGRect(origin: .zero, size: size)),
    with: .color(.green))
```

The rectangular mask hides all but one quadrant of the ellipse:

![A screenshot of a view that shows the upper left quarter of a green](https://docs-assets.developer.apple.com/published/dffe890532ee24aa3b6ec04abdab4ca2/GraphicsContext-2%402x.png)

The order of operations matters. Changes that you make to the state of the context, like adding a mask or a filter, apply to later drawing operations. If you reverse the fill and clip operations in the example above, so that the fill comes first, the mask doesn’t affect the ellipse.

Each context references a particular layer in a tree of transparency layers, and also contains a full copy of the drawing state. You can modify the state of one context without affecting the state of any other, even if they refer to the same layer. For example you can draw the masked ellipse from the previous example into a copy of the main context, and then add a rectangle into the main context:

```swift
// Create a copy of the context to draw a clipped ellipse.
var maskedContext = context
let halfSize = size.applying(CGAffineTransform(scaleX: 0.5, y: 0.5))
maskedContext.clip(to: Path(CGRect(origin: .zero, size: halfSize)))
maskedContext.fill(
    Path(ellipseIn: CGRect(origin: .zero, size: size)),
    with: .color(.green))

// Go back to the original context to draw the rectangle.
let origin = CGPoint(x: size.width / 4, y: size.height / 4)
context.fill(
    Path(CGRect(origin: origin, size: halfSize)),
    with: .color(.blue))
```

The mask doesn’t clip the rectangle because the mask isn’t part of the main context. However, both contexts draw into the same view because you created one context as a copy of the other:

![A screenshot of a view that shows the upper left quarter of a green](https://docs-assets.developer.apple.com/published/44b9540bfd44ed50b730bc8dff67b39b/GraphicsContext-3%402x.png)

The context has access to an [EnvironmentValues](/documentation/swiftui/environmentvalues) instance called [environment](/documentation/swiftui/graphicscontext/environment) that’s initially copied from the environment of its enclosing view. SwiftUI uses environment values — like the display resolution and color scheme — to resolve types like [Image](/documentation/swiftui/image) and [Color](/documentation/swiftui/color) that appear in the context. You can also access values stored in the environment for your own purposes.

## Drawing a path

- [stroke(_:with:lineWidth:)](/documentation/swiftui/graphicscontext/stroke(_:with:linewidth:)) Draws a path into the context with a specified line width.
- [stroke(_:with:style:)](/documentation/swiftui/graphicscontext/stroke(_:with:style:)) Draws a path into the context with a specified stroke style.
- [fill(_:with:style:)](/documentation/swiftui/graphicscontext/fill(_:with:style:)) Draws a path into the context and fills the outlined region.
- [GraphicsContext.Shading](/documentation/swiftui/graphicscontext/shading) A color or pattern that you can use to outline or fill a path.
- [GraphicsContext.GradientOptions](/documentation/swiftui/graphicscontext/gradientoptions) Options that affect the rendering of color gradients.

## Drawing images, text, and views

- [draw(_:in:)](/documentation/swiftui/graphicscontext/draw(_:in:)) Draws a resolved symbol into the context, using the specified rectangle as a layout frame.
- [draw(_:in:style:)](/documentation/swiftui/graphicscontext/draw(_:in:style:)) Draws a resolved image into the context, using the specified rectangle as a layout frame.
- [draw(_:at:anchor:)](/documentation/swiftui/graphicscontext/draw(_:at:anchor:)) Draws a resolved image into the context, aligning an anchor within the image to a point in the context.

## Drawing into a new layer

- [drawLayer(content:)](/documentation/swiftui/graphicscontext/drawlayer(content:)) Draws a new layer, created by drawing code that you provide, into the context.

## Resolving a drawn entity

- [resolve(_:)](/documentation/swiftui/graphicscontext/resolve(_:)) Gets a version of an image that’s fixed with the current values of the graphics context’s environment.
- [resolveSymbol(id:)](/documentation/swiftui/graphicscontext/resolvesymbol(id:)) Gets the identified child view as a resolved symbol, if the view exists.
- [GraphicsContext.ResolvedSymbol](/documentation/swiftui/graphicscontext/resolvedsymbol) A static sequence of drawing operations that may be drawn multiple times, preserving their resolution independence.
- [GraphicsContext.ResolvedImage](/documentation/swiftui/graphicscontext/resolvedimage) An image resolved to a particular environment.
- [GraphicsContext.ResolvedText](/documentation/swiftui/graphicscontext/resolvedtext) A text view resolved to a particular environment.

## Masking

- [clip(to:style:options:)](/documentation/swiftui/graphicscontext/clip(to:style:options:)) Adds a path to the context’s array of clip shapes.
- [clipToLayer(opacity:options:content:)](/documentation/swiftui/graphicscontext/cliptolayer(opacity:options:content:)) Adds a clip shape that you define in a new layer to the context’s array of clip shapes.
- [clipBoundingRect](/documentation/swiftui/graphicscontext/clipboundingrect) The bounding rectangle of the intersection of all current clip shapes in the current user space.
- [GraphicsContext.ClipOptions](/documentation/swiftui/graphicscontext/clipoptions) Options that affect the use of clip shapes.

## Setting opacity and the blend mode

- [opacity](/documentation/swiftui/graphicscontext/opacity) The opacity of drawing operations in the context.
- [blendMode](/documentation/swiftui/graphicscontext/blendmode-swift.property) The blend mode used by drawing operations in the context.
- [GraphicsContext.BlendMode](/documentation/swiftui/graphicscontext/blendmode-swift.struct) The ways that a graphics context combines new content with background content.

## Filtering

- [addFilter(_:options:)](/documentation/swiftui/graphicscontext/addfilter(_:options:)) Adds a filter that applies to subsequent drawing operations.
- [GraphicsContext.Filter](/documentation/swiftui/graphicscontext/filter) A type that applies image processing operations to rendered content.
- [GraphicsContext.FilterOptions](/documentation/swiftui/graphicscontext/filteroptions) Options that configure a filter that you add to a graphics context.
- [GraphicsContext.BlurOptions](/documentation/swiftui/graphicscontext/bluroptions) Options that configure the graphics context filter that creates blur.
- [GraphicsContext.ShadowOptions](/documentation/swiftui/graphicscontext/shadowoptions) Options that configure the graphics context filter that creates shadows.

## Applying transforms

- [scaleBy(x:y:)](/documentation/swiftui/graphicscontext/scaleby(x:y:)) Scales subsequent drawing operations by an amount in each dimension.
- [rotate(by:)](/documentation/swiftui/graphicscontext/rotate(by:)) Rotates subsequent drawing operations by an angle.
- [translateBy(x:y:)](/documentation/swiftui/graphicscontext/translateby(x:y:)) Moves subsequent drawing operations by an amount in each dimension.
- [concatenate(_:)](/documentation/swiftui/graphicscontext/concatenate(_:)) Appends the given transform to the context’s existing transform.
- [transform](/documentation/swiftui/graphicscontext/transform) The current transform matrix, defining user space coordinates.

## Drawing with a core graphics context

- [withCGContext(content:)](/documentation/swiftui/graphicscontext/withcgcontext(content:)) Provides a Core Graphics context that you can use as a proxy to draw into this context.

## Accessing the environment

- [environment](/documentation/swiftui/graphicscontext/environment) The environment associated with the graphics context.

## Instance Methods

- [draw(_:options:)](/documentation/swiftui/graphicscontext/draw(_:options:)) Draws `line` into the graphics context.

## Immediate mode drawing

- [Add rich graphics to your SwiftUI app](/documentation/swiftui/add-rich-graphics-to-your-swiftui-app) Make your apps stand out by adding background materials, vibrancy, custom graphics, and animations.
- [Canvas](/documentation/swiftui/canvas) A view type that supports immediate mode drawing.

---

*Extracted from Apple DocC JSON by apple-skills tooling.*
*This is unofficial content. All documentation belongs to Apple Inc.*
