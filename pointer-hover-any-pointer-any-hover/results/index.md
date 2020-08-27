---
title: "pointer/hover/any-pointer/any-hover test results"
---

Results from manually verifying the reported values of the [`pointer` / `hover` / `any-pointer` / `any-hover` test](../) on different browsers/devices with additional input mechanisms.

| Browser | `pointer:none` | `pointer:coarse` | `pointer:fine` | `hover:none` | `hover:hover` | `any-pointer:none` | `any-pointer:coarse` | `any-pointer:fine` | `any-hover:none` | `any-hover:hover` | Notes |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Windows 10 / mouse / Chrome 81 | false | false | true | false | true | false | false | true | false | true | |
| Windows 10 / mouse / Firefox 75.0 | false | false | true | false | true | false | false | true | false | true | |
| Windows 10 / mouse / Edge 81 | false | false | true | false | true | false | false | true | false | true | |
| iOS 13.4 / touch / Safari | false | true | false | true | false | false | true | false | true | false | |
| iOS 13.4 / iPad / touch + mouse / Safari | false | true | false | true | false | false | true | ![Bug](warn.svg){:.icon} ***false*** | ![Bug](warn.svg){:.icon} ***true*** | ![Bug](warn.svg){:.icon} ***false*** | Presence of mouse not reflected (see `any-pointer:fine` / `any-hover:none` / `any-hover:hover`) - see [bug 209292](https://bugs.webkit.org/show_bug.cgi?id=209292) |
| iOS 13.5 / iPad / touch + Pencil / Safari | false | true | false | true | false | false | true | ![Bug](warn.svg){:.icon} ***false*** | true | false | Does not consider Pencil (see `any-pointer:fine`) - see [bug 212580](https://bugs.webkit.org/show_bug.cgi?id=212580) |
| macOS / Safari | false | false | true | false | true | false | false | true | false | true | |
| Windows 10 / Surface + type cover / Chrome 81 | false | false | true | false | true | false | true | true | false | true | |
| Windos 10 / Surface (tablet mode) / Chrome 81 | false | true | false | true | false | false | true | ![Bug](warn.svg){:.icon} ***false*** | ![Bug](warn.svg){:.icon} ***true*** | ![Bug](warn.svg){:.icon} ***false*** | Does not consider stylus (see `any-pointer:fine` / `any-hover:none` / `any-hover:hover`) <br> Note that the Surface stylus is hover-capable |
| Windows 10 / Surface (tablet mode) + mouse / Chrome 81 | false | true | false | true | false | false | true | ![Bug](warn.svg){:.icon} ***false*** | ![Bug](warn.svg){:.icon} ***true*** | ![Bug](warn.svg){:.icon} ***false*** | Does not consider stylus nor mouse at all (see `any-pointer:fine` / `any-hover:none` / `any-hover:hover`) - see [bug 1088262](https://bugs.chromium.org/p/chromium/issues/detail?id=1088262)|
| Windows 10 / Surface + type cover / Firefox 75.0 | false | false | true | false | true | false | true | true | false | true | |
| Windows 10 / Surface (tablet mode) / Firefox 75.0 | false | true | false | true | false | false | true | ![Bug](warn.svg){:.icon} ***false*** | ![Bug](warn.svg){:.icon} ***true*** | ![Bug](warn.svg){:.icon} ***false*** | Does not consider stylus (see `any-pointer:fine` / `any-hover:none` / `any-hover:hover`) <br> Note that the Surface stylus is hover-capable |
| Windows 10 / Surface (tablet mode) + mouse / Firefox 75.0 | false | true | false | true | false | false | true | true | false | true | Does not consider stylus, but *does* consider mouse as secondary input (see `any-pointer:fine` / `any-hover:none` / `any-hover:hover`) |
| Windows 10 / Surface + type cover / Edge 81 | false | false | true | false | true | false | true | true | false | true | |
| Windows 10 / Surface (tablet mode) / Edge 81 | false | true | false | true | false | false | true | ![Bug](warn.svg){:.icon} ***false*** | ![Bug](warn.svg){:.icon} ***true*** | ![Bug](warn.svg){:.icon} ***false*** | Does not consider stylus (see `any-pointer:fine` / `any-hover:none` / `any-hover:hover`) <br> Note that the Surface stylus is hover-capable|
| Windows 10 / Surface (tablet mode) + mouse / Edge 81 | false | true | false | true | false | false | true | ![Bug](warn.svg){:.icon} ***false*** | ![Bug](warn.svg){:.icon} ***true*** | ![Bug](warn.svg){:.icon} ***false*** | Does not consider stylus nor mouse at all (see `any-pointer:fine` / `any-hover:none` / `any-hover:hover`)|
| Android 10 / touch / Chrome 81 | false | true | false | true | false | false | true | false | true | false | |
| Android 10 / touch + mouse / Chrome 81 | false | true | false | ![Bug](warn.svg){:.icon} ***false*** | ![Bug](warn.svg){:.icon} ***true*** | false | true | true | false | true | When mouse present, incorrectly reports `hover:hover` - if the primary input is still touch (i.e. `pointer:coarse`), it shouldn't - see [bug 1028118](https://bugs.chromium.org/p/chromium/issues/detail?id=1028118)|
| Android 10 / touch / Firefox 68 | false | true | false | true | false | false | true | false | true | false | |
| Android 10 / touch + mouse / Firefox 68 | false | true | false | true | false | false | true | true | false | true | Most correct implementation - still treating touch as primary but setting all the correct `any-*` as well |
| Android 10 / touch / Puffin | false | ![Bug](warn.svg){:.icon} ***false*** | ![Bug](warn.svg){:.icon} ***true*** | false | ![Bug](warn.svg){:.icon} ***true*** | false | ![Bug](warn.svg){:.icon} ***false*** | ![Bug](warn.svg){:.icon} ***true*** | ![Bug](warn.svg){:.icon} ***false*** | ![Bug](warn.svg){:.icon} ***true*** | Utterly broken |
| Android 10 / touch + mouse / Puffin | false | false | true | false | true | false | ![Bug](warn.svg){:.icon} ***false*** | true | false | true | No change from the "without mouse" scenario. Paradoxically, could be deemed ok if it treated mouse as primary (but still doesn't aknowledge `any-pointer:coarse` even in this case) |
| Android 10 / touch / UC Browser 13.12.1293 | false | true | false | ![Bug](warn.svg){:.icon} ***false*** | false | false | true | false | false | false | No `hover:none` for touch for the primary touch input |
| Android 10 / touch + mouse / UC Browser 13.12.1293 | false | true | false | ![Bug](warn.svg){:.icon} ***false*** | false | false | true | true | false | true | No `hover:none` for touch for the primary touch input |
| Android 6.0.1 / Galaxy note 4 (touch + stylus) / Chrome 81 | false | true | false | true | false | false | true | true | ![Bug](warn.svg){:.icon} ***true*** | ![Bug](warn.svg){:.icon} ***false*** | Knows there's a pen/stylus (`any-pointer:fine`) but does not consider it a hovering input (despite the stylus being hover-capable on the Galaxy Note) (see `any-hover:none` / `any-hover:hover`) - see [bug 1028118](https://bugs.chromium.org/p/chromium/issues/detail?id=1028118)|
| Android 6.0.1 / Galaxy note 4 (touch + stylus + mouse) / Chrome 81 | false | true | false | ![Bug](warn.svg){:.icon} ***false*** | ![Bug](warn.svg){:.icon} ***true*** | false | true | true | false | true | When mouse present, incorrectly reports `hover:hover` - if the primary input is still touch (i.e. `pointer:coarse`), it shouldn't - see [bug 1028118](https://bugs.chromium.org/p/chromium/issues/detail?id=1028118)|
| Android 6.0.1 / Galaxy note 4 (touch + stylus) / Samsung Internet 11.12.2 | false | true | false | true | false | false | true | true | ![Bug](warn.svg){:.icon} ***true*** | ![Bug](warn.svg){:.icon} ***false*** | Knows there's a pen/stylus (`any-pointer:fine`) but does not consider it a hovering input (despite the stylus being hover-capable on the Galaxy Note) (see `any-hover:none` / `any-hover:hover`) |
| Android 6.0.1 / Galaxy note 4 (touch + stylus + mouse) / Samsung Internet 11.12.2 | false | true | false | ![Bug](warn.svg){:.icon} ***false*** | ![Bug](warn.svg){:.icon} ***true*** | false | true | true | false | true | When mouse present, incorrectly reports `hover:hover` - if the primary input is still touch (i.e. `pointer:coarse`), it shouldn't |
| Android 6.0.1 / Galaxy Note 4 (touch + stylus) / Firefox 68.7.0 | false | true | false | true | false | false | true | ![Bug](warn.svg){:.icon} ***false*** | ![Bug](warn.svg){:.icon} ***true*** | ![Bug](warn.svg){:.icon} ***false*** | Does *not* consider the pen/stylus |
| Android 6.0.1 / Galaxy note 4 (touch + stylus + mouse) / Firefox 68.7.0 | false | true | false | true | false | false | true | true | false | true | Most correct implementation? |