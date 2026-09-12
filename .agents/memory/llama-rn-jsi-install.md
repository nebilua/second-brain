---
name: llama.rn JSI initialization
description: Version-specific initialization required by llama.rn 0.13.
---

Call llama.rn's exported installJsi function before the first initLlama call in the Android app.

**Why:** llama.rn 0.13 does not bind its global JSI functions during module import. initLlama throws “JSI bindings not installed” until installJsi has installed and captured those bindings.

**How to apply:** Keep the explicit installJsi call in the native model-loading path and rebuild the Android release APK after changing it; web preview and an already-installed APK cannot validate this native initialization.