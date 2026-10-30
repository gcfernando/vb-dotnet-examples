# VB.NET Windows Forms binary clock

Explore timer events, binary conversion and mouse interaction in a small legacy Visual Basic desktop application.

[![Repository standards](https://github.com/gcfernando/vb-dotnet-examples/actions/workflows/repository-standards.yml/badge.svg)](https://github.com/gcfernando/vb-dotnet-examples/actions/workflows/repository-standards.yml) [![Read the documentation](https://img.shields.io/badge/Read-the_documentation-2563eb?style=flat-square)](https://gcfernando.github.io/vb-dotnet-examples/)

The single project in `Observer Pattern/` displays local hours, minutes and seconds as colored blocks alongside a text clock. Its folder name is historical: the implementation uses Windows Forms events and a timer, without a separate subject/observer abstraction.

## Quick start and requirements

On Windows, open [Observer Pattern.sln](Observer%20Pattern/Observer%20Pattern.sln) in Visual Studio/MSBuild tooling capable of building the project's **.NET Framework 2.0** target. Build the solution, then press **F5** to start the clock. No compiled download or third-party packages are committed.

The [project file](Observer%20Pattern/Observer%20UI/Observer%20UI.vbproj) uses classic Visual Basic MSBuild targets and Windows Forms references. It is not an SDK-style `dotnet run` project. Modern tooling may need a separately reviewed retargeting change.

Both solution configurations, **Debug** and **Release**, select the project's **Release** build. Check Configuration Manager before expecting Debug behavior while stepping through code.

## Read and control the clock

Hours use five red blocks; minutes use six yellow blocks; seconds use six green blocks. From left to right, the weights are **1, 2, 4, 8, 16**, with **32** added at the right for minutes and seconds. Add the lit values: 45 seconds lights 1, 4, 8 and 32.

The timer interval is one second and reads the computer's local `Date.Now`. There is no time-zone setting or remote time service. Drag the form background with the left mouse button; double-click the background to exit.

## Explore the implementation

| Source | Responsibility |
| --- | --- |
| [Observer.vb](Observer%20Pattern/Observer%20UI/Observer.vb) | Timer, binary decomposition, block colors, dragging and exit. |
| [Observer.Designer.vb](Observer%20Pattern/Observer%20UI/Observer.Designer.vb) | Generated form layout and timer configuration. |
| [Observer UI.vbproj](Observer%20Pattern/Observer%20UI/Observer%20UI.vbproj) | Framework target, references and output paths; the application is named `Observer`. |

`SetColourIndex` decomposes time values using powers of two. `SetBackColour` clears and lights the corresponding labels. The [source reference](documentation.md) gives further navigation.

## Development and known limitations

There is no application test project or application CI build; the Repository standards workflow checks metadata only. In compatible legacy tooling, manually check time changes, second/minute/hour rollover, dragging and exit. Source inspection does not establish that this legacy toolchain builds successfully on a particular machine.

- **Stale blocks at zero:** `_thr`, `_tmt` and `_tsc` start at zero and are never updated. Repainting is skipped when a time component equals zero, so blocks can retain a previous nonzero value even though the text refreshes.
- **Mixed boundary values:** text, hours, minutes and seconds read `Date.Now` separately. A tick crossing a boundary can briefly combine different instants.
- **Fixed layout:** display scaling and accessibility have not been verified.
- **Missing build target:** use compatible tooling and reference assemblies, or propose framework retargeting as a separate code change.

## Contributing, support and license

Report reproducible defects through [repository issues](https://github.com/gcfernando/vb-dotnet-examples/issues). Include Windows version, display scaling, toolchain and manual checks for UI changes. Preserve generated designer structure and describe framework changes explicitly; follow [CONTRIBUTING.md](CONTRIBUTING.md) and the [repository standards](REPOSITORY_STANDARDS.md).

Use the [security policy](SECURITY.md) for sensitive findings. No license file is present in this checkout; confirm permission before reuse or redistribution. See the related [C# Windows Forms example](https://github.com/gcfernando/csharp-dotnet-examples/tree/main/FourKWinForm) for another desktop sample.

<!-- Preserve links to earlier README sections. -->
<a id="-architecture"></a>
<a id="-contributing"></a>
<a id="-development-and-testing"></a>
<a id="-features"></a>
<a id="-overview"></a>
<a id="-prerequisites-and-installation"></a>
<a id="-quick-start"></a>
<a id="-security"></a>
<a id="-support-and-license"></a>
<a id="-troubleshooting-and-limitations"></a>
<a id="-usage"></a>
<a id="core-idea"></a>
<a id="documentation-links"></a>
<a id="featured-project-binary-clock-observer-pattern"></a>
<a id="future-ideas"></a>
<a id="guide-architecture"></a>
<a id="guide-quick-start"></a>
<a id="guide-troubleshooting-and-limitations"></a>
<a id="guide-usage"></a>
<a id="how-the-binary-conversion-works"></a>
<a id="how-to-run-it"></a>
<a id="learning-value"></a>
<a id="overview"></a>
<a id="project-details"></a>
<a id="related-projects"></a>
<a id="repository-maintenance"></a>
<a id="repository-structure"></a>
<a id="technologies-used"></a>
<a id="vbnet-binary-clock--windows-forms-example"></a>
<a id="visual-behavior"></a>
<a id="visual-studio"></a>
<a id="what-it-does"></a>
