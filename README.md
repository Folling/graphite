# Overview
graphite is a semi-retained, semi-immediate GUI library that tries to combine the best of both worlds into a sophisticated product.
It is supposed to fill the existing gap between mature and cross-platform, performant and efficient and styleable GUI libraries.
graphite is part of a larger application development framework called [alloy](https://github.com/Folling/alloy).

This document is a WIP and will be expanded upon as the project progresses.

graphite uses [neon](https://github.com/Folling/neon) for 2D rendering, [ink](https://github.com/Folling/ink) for text-handling and [adhesive](https://github.com/Folling/adhesive) for the OS handling. Check out those libraries if you're interested in their respective feature sets.

This library has existed in multiple forms before. Two C++ versions and one previous rust version. 
You can find these projects (in ascending order of the creation date):
- [Original C++ version](https://memleak.eu/Folling/graphite)
- [Original Rust version](https://memleak.eu/Folling/graphite-rs)
- [Second C++ iteration](https://memleak.eu/Folling/graphite-CPP-v2)

# Features
- [ ] DOM
- [ ] Layouts (link will follow)
- [ ] Widgets (link will follow)
- [ ] right-to-left support
- [ ] Popups / Dialogs / Tooltips

It should be noted that popups/dialogs and tooltips don't use native windows.
This is done due to previous experiences. Adding these functions i a signficicant complication and not really necessary for a good UX.
Yes, it does pose some troubles on MacOS, but Electron is in the same boots and people don't seem to mind too much.

---

# Classification – IMGUI or Retained?
Neither! graphite combines immediate and retained aspects. 
Code Example (subject to change as the rust API isn't finalised yet):
```rust
let btn = window->set_root_item::<Button>();
btn.text = "Click Me!";
// executed once per frame
btn.update_function = |btn| {
    if btn.is_hovered() {
        btn.background.color = Color.red;
    }
}
```
You only add the button once and initialise its static state. For interaction and things that might change you can specify an update function that is called each frame.

# Contributing
alloy is open source and is supposed to benefit from the inclusion of other people. 
However I do reserve the rights to deny any feature requests or pull requests but am always open to discussion and having my mind changed. 
If you're uncertain whether or not a certain pull request would be appreciated and don't want to waste effort without knowing whether it's worth it, feel free to open an issue and ask. 
All code should be formatted using the same guideline. For this please use rustfmt. In the future a customised rustfmt stylisation might be used.
File and directory names are are to be formatted using snake_case. Excluded from this rule are files that have a certain convention such as .gitignore, LICENCE.txt and markdown files.

# Support
I have a fulltime job and can only afford so much time for alloy. If you would like to change that in the future consider donating to the project (note: Donating link will follow, alloy isn't worth donating yet). I also appreciate feedback (next to constructive criticism) so feel free to email me at coding@folling.de. 
