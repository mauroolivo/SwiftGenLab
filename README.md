# SwiftGenLab

A production-minded iOS reference app exploring where SwiftGen adds value alongside native Xcode resource generation.

Read the article: [SwiftGen in a Production-Minded iOS App](https://uimatters.io/articles/swiftgen-production).

## What it demonstrates

- Typed assets and localization accessors alongside native APIs.
- English and Spanish localization, including formatted strings and plurals.
- Built-in and custom templates with explicit API visibility.
- A sandboxed Xcode build phase that lints configuration before generation.
- Package-owned resources and generated localization in the local `InboxFeature` package.

## Getting started

Use Xcode with Swift 6.4 support and the iOS 27 SDK. The app targets iOS 27.0; the reference setup uses SwiftGen 6.6.2.

1. Install SwiftGen (for example, `brew install swiftgen`) and check `swiftgen --version`.
2. Open `SwiftGenLab.xcodeproj`.
3. Select the `SwiftGenLab` scheme and a compatible simulator, then build and run.

The build phase runs SwiftGen automatically and fails explicitly if the tool is missing.

## Regenerate resources

From the repository root:

```sh
swiftgen config lint --config swiftgen.yml
swiftgen config run --config swiftgen.yml
```

For package resources and tests:

```sh
cd Packages
swiftgen config lint --config swiftgen.package.yml
swiftgen config run --config swiftgen.package.yml
swift test
```

Keep generated files reviewable and check for unexpected changes with `git diff --exit-code` after regeneration.

See the [full implementation walkthrough](https://uimatters.io/articles/swiftgen-production) for configuration decisions, build integration, failure cases, and CI guidance.
