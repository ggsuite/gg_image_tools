<!--
@license
Copyright (c) ggsuite

Use of this source code is governed by terms that can be
found in the LICENSE file in the root of this package.
-->

# Migrate to the latest Dart and Flutter SDK

## Motivation

- The package failed its checks on the latest SDK and with the latest DNA
- It now builds, analyzes and tests cleanly on Dart 3.14

## Strategy

- Raise the SDK constraint, then run `dart migrate` and `dart fix --apply`
- Upgrade the DNA with `gg dna upgrade`
- Fix what the analyzer still reported by hand

## Implementation

- The SDK constraint requires Dart 3.14
- Three tests now await `capturePrint`, which returns a `FutureOr`
- `gg dna upgrade` regenerated the DNA; its check-only DNA test needs
  `checkDna`

## Dependency updates

- `dna_ggsuite` ^0.2.0 → ^2.0.0: the current DNA layers of ggsuite
- `helix` → ^1.15.1: brings `checkDna`, which checks the DNA without
  writing it
