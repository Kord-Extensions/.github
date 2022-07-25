# Kord Extensions

![Build Status](https://badgen.net/github/checks/kord-extensions/kord-extensions/root?icon=github&label=build&scale) ![Release](https://badgen.net/maven/v/metadata-url/https/maven.kotlindiscord.com/repository/maven-releases/com/kotlindiscord/kord/extensions/kord-extensions/maven-metadata.xml?icon=maven&label=release&color=blue&scale) ![Snapshot](https://badgen.net/maven/v/metadata-url/https/maven.kotlindiscord.com/repository/maven-snapshots/com/kotlindiscord/kord/extensions/kord-extensions/maven-metadata.xml?icon=maven&label=snapshot&color=orange&scale) [![Translation status](https://hosted.weblate.org/widgets/kord-extensions/-/main/svg-badge.svg)](https://hosted.weblate.org/engage/kord-extensions/)

[![Translation status](https://hosted.weblate.org/widgets/kord-extensions/-/main/287x66-grey.png)](https://hosted.weblate.org/engage/kord-extensions/)

Kord Extensions is an addon for the excellent [Kord library](https://github.com/kordlib/kord). It intends to provide a framework for larger 
bot projects, with easy-to-use commands, rich argument parsing and event handling, wrapped up into individual extension classes.

The approach taken here is relatively different from many Kotlin Discord libraries, many of which prefer to provide a DSL for quickly 
prototyping or implementing a small application. Instead, [discord.py](https://github.com/Rapptz/discord.py) (the Discord library for Python) 
is a primary source of inspiration for our fairly object-oriented design, especially where it comes to its extensions (which are known as 
"cogs" in [discord.py](http://discord.py)). Despite this, we still strive to provide an idiomatic API that makes full use of Kotlin's niceties.

## Why not other Kord-based frameworks?

The Kord ecosystem has become rich with frameworks of many types, including an official framework named `kordx.commands`. We believe that 
Kord Extensions speaks for itself - so we've created a 
[feature comparison matrix]([https://kordex.kotlindiscord.com/framework-comparison](https://docs.google.com/spreadsheets/d/e/2PACX-1vQtsks-QAnwoR0VmWgjTzq5T2QD66wNpEsWE_g5aZ6Z-nM6cJ3MpjIVF0m79j8of8huh4bIuxOIqz2-/pubhtml)) that includes all of the major Kord-based frameworks.

Not every framework is right for every bot - be sure to make an informed choice before you get started!

## Usage

To make use of Kord Extensions, update your build script to add `https://maven.kotlindiscord.com/repository/maven-public/` as a Maven 
repository, and use `com.kotlindiscord.kord.extensions:kord-extensions:VERSION` as the Maven coordinate. You can check the badges at the 
top of this page for the latest stable and snapshot versions, or you can 
[browse the Maven repository](https://maven.kotlindiscord.com/#browse/browse:maven-public:com%2Fkotlindiscord%2Fkord%2Fextensions%2Fkord-extensions) 
for a full list of versions.

If you need a more in-depth guide to setting up your project, feel free to take a look at [our setup guide](https://kordex.kotlindiscord.com/guides/setup).
You can find the KordEx documentation at [the KordEx wiki](https://kordex.kotlindiscord.com/).
