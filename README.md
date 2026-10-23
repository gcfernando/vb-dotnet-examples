<a id="future-ideas"></a>
<a id="learning-value"></a>
<a id="overview"></a>

# VB.NET Binary Clock — Windows Forms Example

A small Visual Basic Windows Forms application that displays hours, minutes and seconds as colored binary blocks.

## 🔎 Overview

This repository contains one legacy desktop project in `Observer Pattern`. It is useful for studying Windows Forms timer events, binary conversion and mouse interaction. The folder name is historical: the implementation uses form events and a timer, without a separate subject/observer abstraction.

<a id="featured-project-binary-clock-observer-pattern"></a>
<a id="project-details"></a>
<a id="visual-behavior"></a>
<a id="what-it-does"></a>

## ✨ Features

- Hours use five red blocks; minutes use six yellow blocks; seconds use six green blocks.
- A text label displays local time alongside the binary representation.
- Drag the form background with the left mouse button; double-click the background to exit.

<a id="how-to-run-it"></a>
<a id="visual-studio"></a>

## 🚀 Quick start

On Windows, open [Observer Pattern.sln](Observer%20Pattern/Observer%20Pattern.sln) in a Visual Studio/MSBuild environment capable of building the legacy .NET Framework 2.0 target. Build the solution, then start it with **F5**. Modern tooling may require a separately reviewed retargeting change; this documentation does not change the target. The committed solution maps both its **Debug** and **Release** configurations to the project's **Release** configuration, so selecting Debug at solution level still selects the Release project build. Review Configuration Manager when stepping through the application.

<a id="technologies-used"></a>

## 📦 Prerequisites and installation

The [project file](Observer%20Pattern/Observer%20UI/Observer%20UI.vbproj) targets `.NET Framework v2.0`, uses the classic Visual Basic MSBuild targets and references Windows Forms. It is not an SDK-style `dotnet run` project. No third-party packages or compiled binaries are committed.

## 💡 Usage

Each illuminated block represents a power of two. From left to right, the hour row has weights **1, 2, 4, 8, 16**; minute and second rows add **32** at the right. Add the lit weights to read the value. For 45 seconds, the 1, 4, 8 and 32 blocks light up.

The timer is configured for a one-second interval. It uses `Date.Now` on the computer; there is no time-zone configuration or remote time service.

<a id="core-idea"></a>
<a id="how-the-binary-conversion-works"></a>
<a id="repository-structure"></a>

## 🏗️ Architecture

| File | Responsibility |
|---|---|
| [Observer.vb](Observer%20Pattern/Observer%20UI/Observer.vb) | Timer updates, binary decomposition, colors, dragging and exit |
| [Observer.Designer.vb](Observer%20Pattern/Observer%20UI/Observer.Designer.vb) | Generated form layout and timer configuration |
| [Observer UI.vbproj](Observer%20Pattern/Observer%20UI/Observer%20UI.vbproj) | Framework target, references and Debug/Release output paths |

`SetColourIndex` decomposes each value using powers of two; `SetBackColour` clears and lights the corresponding labels. The solution builds an application named `Observer`.

## 🧪 Development and testing

There is no automated test project or CI workflow in this checkout. After building in a compatible environment, manually check time changes, minute/hour rollover, dragging and exit. The documentation review inspected the project, designer and event handlers; it did not launch the application or verify the legacy build toolchain.

## 🛠️ Troubleshooting and limitations

- **Build target unavailable:** use tooling and reference assemblies supporting .NET Framework 2.0, or review retargeting as a separate code change.
- **Stale blocks at zero:** `_thr`, `_tmt` and `_tsc` are initialized to zero and never updated. The timer skips repainting when an hour, minute or second equals zero, so blocks can retain the previous nonzero value. The text label still refreshes. This existing code defect is documented, not fixed here.
- **Mixed boundary values:** the text, hour, minute and second values each read `Date.Now` separately. A tick crossing a time boundary can briefly combine values from different instants.
- **Fixed layout:** the form uses a small fixed label layout; display scaling and accessibility have not been tested.

## 🤝 Contributing

Keep examples reproducible and describe any framework/toolchain change explicitly. For UI changes, include the Windows version, display scaling and manual checks performed. Preserve generated designer structure. The existing `.gitignore` ignores the entire `Observer Pattern/Observer UI` directory; already tracked files remain versioned, but new source files there may be hidden from ordinary `git status`. Check ignore rules when adding files and review any rule change separately.

## 🔒 Security

Avoid putting sensitive information in public reports. Use a private reporting option if available, or contact the maintainer privately for sensitive findings. No dedicated security policy is committed.

<a id="documentation-links"></a>
<a id="related-projects"></a>

## 📄 Support and license

Use [repository issues](https://github.com/gcfernando/vb_codes/issues) for questions and defects. No license file is present in this checkout; confirm permission before reuse or redistribution.

[Source reference](documentation.md) · [C# Windows Forms example](https://github.com/gcfernando/csharp_codes/tree/main/FourKWinForm)
