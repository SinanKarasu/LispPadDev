# LispPadDev

`LispPadDev` is the standalone app shell for the LispPad work. It builds as a SwiftUI app for macOS, iPadOS, and visionOS while depending on sibling package checkouts for the shared Lisp runtime and the optional SCMUtils staging bundle.

## Workspace Layout

This repo expects the surrounding checkout to look like this:

```text
<workspace>/
  Packages/
    swift-lispkit/
    LispPadCore/
    SCMUtilsBundle/
  Projects/
    LispPadDev/
```

The app project resolves `LispPadCore` via `../../Packages/LispPadCore`, and `LispPadCore` resolves the local `swift-lispkit` fork via `../swift-lispkit`.

## Build

From this repository root:

```bash
xcodebuild -project LispPadDev.xcodeproj -scheme LispPadDevMac -destination 'platform=macOS' build
xcodebuild -project LispPadDev.xcodeproj -scheme LispPadDev -destination 'generic/platform=iOS Simulator' build
xcodebuild -project LispPadDev.xcodeproj -scheme LispPadDev -destination 'generic/platform=visionOS Simulator' build
```

## SCMUtils

`LispPadDev` can stage the SCMUtils bootstrap when a sibling `Packages/SCMUtilsBundle` checkout is present. The app now resolves that bundle and the local probe script through relative workspace discovery instead of machine-specific paths.

## Distribution

This repository is distributed under GPLv3. In its current form, it is intended for source distribution and self-managed/internal builds, not standard App Store distribution.

