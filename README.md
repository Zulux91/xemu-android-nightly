# X1 BOX Android Builder

[![GitHub Release](https://img.shields.io/github/v/release/Zulux91/xemu-android-nightly?label=Current%20Release)](https://github.com/Zulux91/xemu-android-nightly/releases/latest)
[![GitHub Downloads](https://img.shields.io/github/downloads/Zulux91/xemu-android-nightly/total?logo=github&label=GitHub%20Downloads)](https://github.com/Zulux91/xemu-android-nightly/releases/latest)
[![CI Build](https://img.shields.io/github/actions/workflow/status/Zulux91/xemu-android-nightly/build-xemu.yml/badge.svg)](https://github.com/Zulux91/xemu-android-nightly/releases/latest)


Automated build pipeline for [X1 BOX](https://github.com/izzy2lost/xemu) — an Original Xbox emulator for Android based on [xemu](https://xemu.app).

This repository contains no source code. It exists solely to build and release APKs from the upstream source via GitHub Actions.

---

## How it works

Triggering the workflow will:

1. Clone [izzy2lost/xemu](https://github.com/izzy2lost/xemu) with all submodules
2. Set up the Android SDK, NDK, CMake, Meson and Rust toolchain
3. Compile the native Xbox emulation core for `arm64-v8a`
4. Package and sign the APK with a debug key
5. Publish the APK as a GitHub Release

## Usage

1. Go to the **Actions** tab
2. Select **Build X1 BOX**
3. Click **Run workflow**
4. Optionally specify a branch or tag (defaults to `master`)
5. Once the build finishes, the APK will be available under [Releases](../../releases)

## Device Requirements

| Requirement | Minimum |
|---|---|
| Android version | 8.0 (API 26) |
| Architecture | 64-bit ARM (`arm64-v8a`) |
| GPU | Vulkan-capable |
| RAM | 8 GB recommended |

## Notes

- APKs produced here are signed with a **debug key** and intended for testing only
- This repo is not affiliated with Microsoft, xemu-project, or izzy2lost
- You must provide your own legally obtained Xbox BIOS and game files to use the emulator
- Compatibility and performance vary by device and game

> **⚠️ For forks:** Keep the repository name as short as possible. The native build
> system (CMake) has a maximum object file path length of 180 characters. GitHub Actions
> constructs the working directory as:
> `/home/runner/work/{repo-name}/{repo-name}/xemu/android/app/.cxx/...`
> A long repository name will eat into that limit and may cause build failures.
> A name under 20 characters is recommended.

## Credits

- Emulator core: [xemu-project/xemu](https://github.com/xemu-project/xemu)
- Android port: [izzy2lost/xemu](https://github.com/izzy2lost/xemu)