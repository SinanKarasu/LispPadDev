# LispPad Portable Import Audit

This folder vendors source copied from `swift-lisppad-ios` for evaluation inside `LispPadDev`.

## Imported into the repo

All 43 source files currently judged free of direct `UIKit` usage were copied into:

- `Upstream/LispPadPortable`

The previously adapted navigation shell remains local to `LispPadDev/Navigation` and is not duplicated here.

## Compiled in `LispPadDev` today

These files were typechecked together, mirrored into the shared local Swift package
`LispPadCore`, and now build from that package instead of the app target:

- `Editor/LispPadDocument.swift`
- `Files/DirectoryTracker.swift`
- `Files/FileExtensions.swift`
- `Files/FileObserver.swift`
- `Generic Views/IntField.swift`
- `Generic Views/OptionalScrollView.swift`
- `Preferences/Appearance.swift`
- `Util/AsyncResult.swift`
- `Util/Characters.swift`
- `Util/TaskSerializer.swift`
- `Util/ThreadUtil.swift`
- `Util/Zoomable.swift`

## Vendored but parked for later wiring

These files are present in the project tree but are not yet compiled because they still depend on other local app infrastructure, `LispKit`, `MarkdownKit`, richer document/view helpers, or file abstractions that have not been brought over yet:

- `Canvas/*`
- `Files/FileHierarchy.swift`
- `Files/Move.swift`
- `Files/NamedRef.swift`
- `Files/Open.swift`
- `Files/Organizer.swift`
- `Files/SaveAs.swift`
- `Generic Views/DocumentView.swift`
- `Generic Views/MarkdownViewer.swift`
- `Generic Views/RTFTextView.swift`
- `Generic Views/ScrollSheet.swift`
- `Libraries/*`
- `Library Browser/*`
- `LispPadApp.swift`
- `LispPadGlobals.swift`
- `Log/SessionLog.swift`
- `Preferences/HistoryManager.swift`
- `Session/*`
- `Util/Mutable.swift`

## Next likely unlocks

- Bring in `PortableURL` and related file abstractions.
- Decide whether to vendor `MarkdownKit` as a package dependency or replace those views.
- Bring in `LispKit` only after the app shell is stable enough to absorb the interpreter/runtime graph.
