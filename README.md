[![crates.io](https://img.shields.io/crates/v/egui-screensaver-fractal-clock.svg)](https://crates.io/crates/egui-screensaver-fractal-clock)
[![docs.rs](https://docs.rs/egui-screensaver-fractal-clock/badge.svg)](https://docs.rs/egui-screensaver-fractal-clock)
[![Rust version](https://img.shields.io/badge/rust-1.85%2B-orange.svg)](https://www.rust-lang.org)
[![License: MIT OR Apache-2.0](https://img.shields.io/badge/license-MIT%20OR%20Apache--2.0-blue.svg)](LICENSE-MIT)
[![dependency status](https://deps.rs/repo/github/cecton/egui-screensaver-fractal-clock/status.svg)](https://deps.rs/repo/github/cecton/egui-screensaver-fractal-clock)
[![CI](https://github.com/cecton/egui-screensaver-fractal-clock/actions/workflows/ci.yml/badge.svg)](https://github.com/cecton/egui-screensaver-fractal-clock/actions/workflows/ci.yml)
[![demo](https://img.shields.io/badge/demo-live-blue)](https://cecton.github.io/egui-screensaver-fractal-clock/)

# egui-screensaver-fractal-clock

Fractal clock screensaver for [egui](https://github.com/emilk/egui).

Draws three clock hands (seconds, minutes, hours) from the centre of the
screen.  Each frame the tips of the seconds and minutes hands recursively
sprout two child branches, rotated by the angular difference between those
hands and the hour hand.  The result is a continuously-morphing fractal tree
whose shape encodes the current time.

Rendering is skipped while the window is not focused, so no CPU is wasted
when the tab is in the background.

## Usage

Add the crate to your `Cargo.toml`:

```toml
[dependencies]
egui-screensaver-fractal-clock = "0.1"
```

Then call `paint` every frame from your `eframe::App::update` implementation,
before drawing any UI windows:

```rust
use egui_screensaver_fractal_clock::FractalClockBackground;

struct MyApp {
    fractal_clock: FractalClockBackground,
}

impl eframe::App for MyApp {
    fn update(&mut self, ctx: &egui::Context, _frame: &mut eframe::Frame) {
        self.fractal_clock.paint(ctx);
        // … rest of your UI …
    }
}
```

## License

Licensed under either of

- Apache License, Version 2.0 ([LICENSE-APACHE](LICENSE-APACHE))
- MIT License ([LICENSE-MIT](LICENSE-MIT))

at your option.
