---
"tray-icon": patch
---

On Windows, stop the timer that detects the cursor leaving the tray icon once it has left. The timer took the last cursor position on its first tick, so when the cursor was still on the icon then, later ticks found no position and never stopped it, and the app's main thread woke every 15 ms for as long as it ran. A cursor position or icon rect that can't be read (a locked screen, the icon in a closed overflow area) now also counts as having left.
