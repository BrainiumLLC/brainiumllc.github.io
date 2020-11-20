---
layout: post
title:  "cargo-mobile: Rust on mobile made easy!"
date:   2020-11-20 10:00:00 -0800
author: Francesca Lovebloom
author-link: https://github.com/francesca64
---

**THIS IS A DRAFT - REMEMBER TO OPTIMIZE ASSETS BEFORE POSTING**

***The answer to "how do I use Rust on iOS and Android?"***

For nearly 2 years, we've been perfecting a tool called [cargo-mobile]. It's a framework-agnostic tool that generates all the boilerplate of a Rust mobile project, and is packed full of handy commands for building and running on mobile devices.

If you'd like to follow along, installation is easy:

```shell
cargo install --git https://github.com/BrainiumLLC/cargo-mobile
```

Note that cargo-mobile currently only works on macOS! If you shoot us a PR that adds support for Linux or Windows, we'll shower you in heart emoji. Feel free to ask us for guidance if you're interested!

Additionally, until Rust 1.49.0 is released, you can't build for iOS unless you're using [either Rust 1.45.2 or a recent nightly](https://github.com/BrainiumLLC/cargo-mobile#status).

To start a new project, you just need to run `cargo mobile init`:

{% include terminal.html alt="`cargo mobile init` demo" src="/assets/cargo-mobile/init.svg" %}

Just like that, you have a version of [Bevy](https://bevyengine.org/)'s [Breakout example](https://github.com/bevyengine/bevy/blob/master/examples/game/breakout.rs) that can run out of the box on desktop, iOS, and Android!

As usual, you can use `cargo run` to run on desktop:

{% include lightbox.html alt="`cargo run` demo" src="/assets/cargo-mobile/desktop.png" %}

More excitingly, it's easy to run on iOS and Android!

## [iOS](#ios)

We provide a convenience command for opening your project in Xcode:

```shell
cargo apple open
```

From there, you can build your project like you normally would in Xcode! Just hit that Play button. It'll work on Simulator, too.

{% include lightbox.html alt="Xcode project" src="/assets/cargo-mobile/xcode.png" %}

You can even set breakpoints!

{% include lightbox.html alt="Xcode breakpoints" src="/assets/cargo-mobile/breakpoints.png" %}

If you're not a fan of opening Xcode, you can also run directly from the command line. Be warned that the output might contain some spurious errors; we're still improving that! Also, you can't currently use Simulator unless you're running from Xcode.

```shell
cargo apple run
```

Whether you run from Xcode or the command line, you should ultimately be greeted by Breakout:

{% include lightbox.html alt="Running on an iPhone XR" src="/assets/cargo-mobile/iphone.jpg" %}

We provide several other helpful iOS commands, which are listed in our help info:

```shell
cargo apple
```

## [Android](#android)

Naturally, we also provide a convenience command for opening your project in Android Studio:

```shell
cargo android open
```

Once again, you just need to hit the Run button like you normally would.

{% include lightbox.html alt="Android Studio project" src="/assets/cargo-mobile/android-studio.png" %}

Alternatively, you can skip Android Studio and run directly from the command line:

```shell
cargo android run
```

Either way, it should pop up on your connected device:

{% include lightbox.html alt="Running on a Pixel 4" src="/assets/cargo-mobile/pixel.jpg" %}

You can find more Android commands in our help info:

```shell
cargo android
```

## [Going forward](#going-forward)

Be advised that Bevy's mobile support is still [very new](https://bevyengine.org/news/bevy-0-3/), so the Breakout demo doesn't work perfectly yet. They're doing an amazing job nonetheless! We've been following their progress, and a lot of contributors worked very hard to make it happen.

We'd love to see PRs that add template packs for other engines and frameworks, so that cargo-mobile is convenient for anyone and everyone to use. We'd also love to show you a demo using Brainstorm, our own internal mobile-first game engine, but we're not ready to open source it just yet!

If you have any questions, issues, or ideas, feel free to [open an issue](https://github.com/BrainiumLLC/cargo-mobile/issues)!

[cargo-mobile]: https://github.com/BrainiumLLC/cargo-mobile
