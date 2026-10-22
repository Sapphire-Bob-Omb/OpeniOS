# OpeniOS

OpeniOS is a free, local, IPSW-driven iOS emulation project built for experimentation, diagnostics, and learning. The goal is simple: let users import an IPSW, define a compatible device profile, and explore early iPhone/iOS behavior without needing a physical device.

This project is not meant to be a perfect iPhone replacement. Instead, it aims to be a practical, transparent, and research-friendly emulator for older iOS profiles and developer workflows.

Still, OpeniOS is not open-source, so if you’re looking at the repository’s source, you might only see the README. Go to Releases to get OpeniOS.

Suggestions or bugs will be read in Issues.

Think:
- “I have an IPSW, I want to inspect it”
- “I want to boot a supported early iOS profile”
- “I want to test device behavior without buying hardware”
- “I want a local emulator that doesn't require expensive paid tooling”

If you’re here for full modern iOS parity, this is not that. If you’re here for a local, customizable iOS playground with honest limitations, welcome.

You can still use OpeniOS for personal use, but emulation is not as perfect as actual hardware.

---

## Important notice

OpeniOS is an independent, community-driven project and is not affiliated with, endorsed by, sponsored by, or connected to Apple Inc., iPhone, iOS, or any Apple product or service.

OpeniOS is intended to emulate iOS devices only. It does not emulate iPodOS or macOS.

If you want to emulate iPodOS or macOS, you should use an emulator designed specifically for those platforms instead. Even if you want to emulate an iPod in iPhone 3G mode because they share the same chip family, OpeniOS does not currently distinguish between iPodOS and iOS based on their header or code differences, so the project is intentionally scoped to iOS device emulation only.

---

## Why OpeniOS?

There’s a gap between:
- expensive, enterprise-grade device emulation products
- abandoned or dead projects with little maintenance
- and the need for a free, local, user-controlled emulator

OpeniOS tries to sit in that middle lane:
- local-first
- IPSW-driven
- user-controlled
- experimental but useful
- honest about what works and what doesn’t

This isn’t trying to be “the perfect iPhone in a VM.” It’s trying to be a serious, usable tool for people who actually want to experiment with iOS profiles and firmware behavior.

---

## Features

### Current / planned core features
- IPSW import and profile selection
- Device model and firmware profile management
- Host/guest architecture handling for ARM-based iOS profiles
- Settings panel for device, CPU, memory, firmware, and networking
- Wi‑Fi emulation with safe default behavior
- Optional virtual carrier profile emulation
- Bluetooth emulation support (experimental)
- JIT / interpreter / hybrid execution modes
- Diagnostics and verbose logging
- Experimental and Fun settings categories
- Power impact indicators for heavier toggles

### Settings categories
OpeniOS will organize settings into categories like:
- General
- Device
- CPU / Execution
- Memory
- Firmware
- Graphics
- Networking
- Bluetooth
- Diagnostics
- Experimental
- Fun

This keeps the normal experience stable while leaving room for research features.

---

## Default networking model

OpeniOS has a safe default networking mode:

- Default Wi‑Fi network: OpeniOS Wi‑Fi
- Guest sees a Wi‑Fi profile even if the host PC is not connected
- Guest can use host Wi‑Fi metadata (signal strength, standards, etc.) for realism
- Host network bridging is optional and explicit
- If the host has no network connection, OpeniOS can surface a “No internet connection” state instead of falsely reporting a valid connection

This is safer than forcing the guest to share the host’s real network connection without permission.

---

## Device / firmware compatibility

OpeniOS is meant to be flexible, but it is not magical.

### Supported direction
OpeniOS is most likely to work best with:
- older iPhoneOS / early iOS firmware
- simpler boot stages
- supported device profiles
- custom firmware sets with known architecture and board metadata

### Experimental direction
Some features are intentionally designed for:
- mismatched region / carrier testing
- firmware diagnostics
- unsupported board profiles
- custom boot configuration
- dev/debug workflows

These features may be unstable, require manual configuration, or have known compatibility edge cases.

---

## Experimental features

Some features will live in Experimental until they’re mature:
- Allow region mismatch
- Allow board mismatch
- Force JIT / interpreter / hybrid execution
- Unsafe boot options
- Unsupported device profile loading
- Custom carrier profile emulation
- Bluetooth emulation
- SIM/eSIM simulation
- Verbose kernel and boot tracing
- Debug-only memory and CPU logging

These settings should be clearly labeled as risky and may be disabled while emulation is running.

---

## Fun features

There will also be a Fun tab for harmless, cosmetic, non-critical settings like:
- invert display colors
- CRT / scanline effects
- retro UI skins
- custom boot splash effects
- silly wallpaper themes
- alternate visual behaviors

Fun features are not supposed to break emulation. They are just there for vibe, testing, and visual experimentation.

---

## Verbose logging

OpeniOS includes support for verbose logging modes:

- Off
- Show in terminal
- Show as pop-up
- Write to file

File output may impact performance depending on the kind of trace you enable. Terminal mode is typically the best tradeoff for debugging without making the UI annoying.

Example output files:
- iOS6Verbose.txt
- iOS10Verbose.txt
- device-specific verbose logs if desired

---

## Power impact indicators

Because this is an emulator, power matters.

Several settings will include a small “power impact” label such as:
- No impact
- Very low
- Low
- Medium
- High
- Very high
- Seriously high
- Host battery heavy
- Guest CPU heavy
- Host CPU heavy
- Host GPU heavy
- Guest GPU heavy

This is especially useful for:
- JIT and hybrid execution
- dual-core / multi-core guest scheduling
- logging to file
- Bluetooth / carrier emulation
- graphics scaling
- heavy debug traces

This is meant to help laptop users avoid turning their battery into a smoke test.

I don’t recommend using features marked as “Seriously high” unless you’re on AC power.

---

## Current status / known limitations

OpeniOS is a work in progress. It is not a finished product and it will not magically do everything.

Known limitations:
- not all IPSWs are supported
- not all device profiles are compatible
- modern iOS is much harder to emulate than early iOS
- some features are deliberately experimental
- full app compatibility is not guaranteed
- some options require a supported host environment
- some settings are intentionally disabled until the architecture is stable

Important:
OpeniOS is not a full replacement for a real iPhone, and it is not intended to be marketed as one.

This project is best understood as:
- a local iOS research tool
- a diagnostic platform
- an experimentation environment
- a free alternative for users who want to explore firmware without a device

---

## Supported use cases

OpeniOS is meant to be useful for:
- IPSW inspection
- early iOS profile boot experiments
- device profile testing
- firmware diagnostics
- learning how iOS boots and behaves
- exploring older iPhone device logic
- local emulator experimentation

This is the target lane. Not “perfect iPhone emulation,” but real utility.

---

## Requirements

### Minimum
- Windows 10 or 11 x64
- Modern CPU with multiple cores
- 8 GB RAM
- SSD recommended
- .NET runtime / SDK support for the app project

### Recommended
- Windows 11 x64
- 6+ cores / 12+ threads
- 16 GB RAM
- NVMe SSD
- decent cooling
- enough headroom for diagnostics and logs

These numbers will vary depending on which iOS version and profile you are targeting.

---

## Architecture direction

OpeniOS is designed around a layered model:
- Firmware parsing / manifest handling
- Device profile definition
- Execution engine (interpreter / JIT / hybrid)
- Memory and board model
- Boot stage control
- Graphics / UI / display layer
- Networking / carrier / Wi‑Fi / Bluetooth
- Diagnostics and logging

This keeps the codebase easier to reason about and avoids turning the project into one giant monolith.

---

## Development philosophy

OpeniOS aims to be:
- free
- transparent
- local
- user-driven
- realistic about limitations
- useful for learning and research

It is not meant to be:
- an opaque commercial platform
- a fake “works on everything” project
- a promise of perfect device parity
- a replacement for actual hardware

If you’re building with this project, keep the scope honest and keep the architecture clean.

---

## Contributing

Contributions are welcome if they help the project move forward in a sane way.

Good starting points:
- device profile work
- firmware parsing
- architectural cleanup
- settings system improvements
- emulator safety and guardrails
- networking and Wi‑Fi simulation
- diagnostics and logging
- documentation

Bad fit:
- “make it magically run everything with no work”
- “add half-baked unsafe toggles with no warnings”
- “turn the emulator into a fake Apple product without telling anyone”

Please keep it practical and well-documented.

Suggestions or bugs will be read in Issues.

---

## License

This project is currently intended to be used as a local, user-driven emulator/tooling project. License details should be added as the project matures.

---

## A note

OpeniOS is not trying to be a fake iPhone that tricks everyone. It’s trying to be a usable, local, IPSW-based iOS experimentation environment that people can actually run on their own machine.

That’s the vibe.

---

## Disclaimer

OpeniOS is a research and experimentation tool. It is not a substitute for a real device, and it does not provide official Apple support or official Apple compatibility guarantees. Use it responsibly and be aware of the real technical limitations of emulation.

This project does not emulate iPodOS or macOS. It is developed for iOS device emulation only.

If you want more apps from me, check out my work at:
https://iphoneplay-website.web.app/

---

## Legal usage

Before you use OpeniOS for commercial purposes, do not:

- advertise OpeniOS as a misleading product
- try to claim ownership of OpeniOS
- advertise OpeniOS as “made by Apple”

---

## Last disclaimer

OpeniOS is not open-source.

I use the word “Open” to mean free-to-use, not that the project is open-source or officially affiliated with Apple.

Thank you for reading this. I know some people may not respect the legal usage shown above, but as long as they don’t cause trouble, I’m fine with it.
