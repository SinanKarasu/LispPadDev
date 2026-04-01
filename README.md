# LispPadDev

`LispPadDev` is the standalone app shell for the LispPad work. It builds as a SwiftUI app for macOS, iPadOS, and visionOS while depending on GitHub-hosted Swift packages for the shared Lisp runtime and the SCMUtils staging bundle.

## Package Sources

The app project resolves its direct packages from GitHub:

- `https://github.com/SinanKarasu/LispPadCore.git`
- `https://github.com/SinanKarasu/SCMUtilsBundle.git`

`LispPadCore` in turn resolves the LispKit fork from:

- `https://github.com/SinanKarasu/swift-lispkit.git`

## Build

From this repository root:

```bash
xcodebuild -project LispPadDev.xcodeproj -scheme LispPadDevMac -destination 'platform=macOS' build
xcodebuild -project LispPadDev.xcodeproj -scheme LispPadDev -destination 'generic/platform=iOS Simulator' build
xcodebuild -project LispPadDev.xcodeproj -scheme LispPadDev -destination 'generic/platform=visionOS Simulator' build
```

## SCMUtils

`LispPadDev` stages SCMUtils through the bundled `SCMUtilsBundleSupport` package resources, so the app no longer depends on machine-specific sibling folder layout.

## Distribution

This repository is distributed under GPLv3. In its current form, it is intended for source distribution and self-managed/internal builds, not standard App Store distribution.
