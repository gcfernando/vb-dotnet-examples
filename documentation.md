---
layout: default
title: "VB.NET Windows Forms Examples — Documentation and Guides"
description: "Visual Basic desktop examples, including a binary clock built with Windows Forms."
permalink: /documentation/
---

Browse the published guides, examples and reference pages for **VB.NET Windows Forms Examples**. Each guide has a readable web page; the Markdown sources remain available on GitHub.

## 🔎 Source reference

The [README](README.md) explains setup, reading the binary clock and known limitations. There is one application, not a library of separate guides.

| Source | What it defines |
|---|---|
| [Solution](https://github.com/gcfernando/vb-dotnet-examples/blob/main/Observer%20Pattern/Observer%20Pattern.sln) | The Observer UI project; both solution configurations select the project's Release build |
| [Project](https://github.com/gcfernando/vb-dotnet-examples/blob/main/Observer%20Pattern/Observer%20UI/Observer%20UI.vbproj) | .NET Framework 2.0, Windows Forms and output paths |
| [Form logic](https://github.com/gcfernando/vb-dotnet-examples/blob/main/Observer%20Pattern/Observer%20UI/Observer.vb) | Timer, powers-of-two decomposition and mouse events |
| [Form designer](https://github.com/gcfernando/vb-dotnet-examples/blob/main/Observer%20Pattern/Observer%20UI/Observer.Designer.vb) | Label placement, color defaults and one-second timer |

## 🧪 Manual verification reference

Build in a compatible legacy Windows toolchain, then check a nonzero time, second/minute rollover, the midnight hour, dragging and exit. In the current code, cached time fields remain zero, so the repaint conditions skip values equal to zero. This explains the stale-block issue recorded in the README.

No automated tests or successful build result are supplied by this documentation review. The generated page/source navigation below belongs to the documentation site.

## Read online

<table>
<thead><tr><th>Guide</th><th>Markdown or HTML source</th></tr></thead>
<tbody>
{% assign guides = site.html_pages | sort: 'url' %}
{% for guide in guides %}{% if guide.sitemap != false and guide.url != page.url and guide.url != '/404.html' %}
<tr><td><a href="{{ guide.url | absolute_url }}">{{ guide.title | default: guide.name | escape }}</a></td><td><a href="https://github.com/{{ site.repository }}/blob/main/{{ guide.path | uri_escape }}">View source</a></td></tr>
{% endif %}{% endfor %}
{% for guide in site.static_files %}{% if guide.extname == '.html' and guide.sitemap != false %}
<tr><td><a href="{{ guide.path | uri_escape | absolute_url }}">{% if guide.path == '/Linux_Commands/index.html' %}Linux Command Reference{% elsif guide.path contains 'AI-Learning-Atlas' %}AI Learning Atlas{% elsif guide.path contains 'ai_coding_plugins_beginners_guide' %}AI Coding Add-ons: Beginner’s Guide{% elsif guide.path contains 'Wifi Radar' %}WiFi Radar — static interface preview{% else %}{{ guide.name | escape }} — {{ guide.path | escape }}{% endif %}</a></td><td><code>{{ guide.path | escape }}</code></td></tr>
{% endif %}{% endfor %}
</tbody>
</table>

## Markdown source library

[View this documentation index source](https://github.com/{{ site.repository }}/blob/main/documentation.md). These are the authored Markdown files. Some are package-specific documents or alternate source formats of the same guide.

{% assign sources = site.static_files | sort: 'path' %}
{% for source in sources %}{% if source.extname == '.md' %}
- [{{ source.path | escape }}](https://github.com/{{ site.repository }}/blob/main{{ source.path | uri_escape }})
{% endif %}{% endfor %}

## Explore more

[All developer projects](https://gcfernando.github.io/gcfernando/projects/) · [Repository on GitHub](https://github.com/gcfernando/vb-dotnet-examples) · [XML sitemap](https://gcfernando.github.io/vb-dotnet-examples/sitemap.xml)
