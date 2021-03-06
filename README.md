# Lingo Provider

[![Language](https://img.shields.io/badge/Swift-3.2-brightgreen.svg)](http://swift.org)
[![Language](https://img.shields.io/badge/Swift-4-brightgreen.svg)](http://swift.org)
[![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](https://raw.githubusercontent.com/vapor-community/markdown-provider/master/LICENSE)

A Vapor provider for [Lingo](https://github.com/miroslavkovac/Lingo) - a pure Swift localization library ready to be used in Server Side Swift projects.

## Setup 

### Add a dependancy

Add LingoProvider as a dependancy in your `Package.swift` file:

```swift
dependencies: [
	...,
	.Package(url: "https://github.com/vapor-community/lingo-provider.git", majorVersion: 1)]
]
```

### Add the Provider

After you have initialized the `Config` object, simply add the provider:

```swift
import LingoProvider
...
try config.addProvider(LingoProvider.Provider.self)
```

### Config

Lingo can be configured in a `lingo.json` file located inside your Vapor `Config` dir:

```json
{
    "defaultLocale": "en",
    "localizationsDir": "Localizations"
}
```

> The `localizationsDir` can be omitted in this case, as the _Localizations_ is also the default path. Note that this folder should exist under the _drop.workDir_.

## Use

LingoProvider adds an extension on Droplet for easier access to Lingo, so it can be used simply as:

```swift
let localizedTitle = droplet.lingo.localize("welcome.title", locale: "en")
```

Use the following syntax for defining localizations in a JSON file:

```swift
{
	"title": "Hello Swift!",
	"greeting.message": "Hi %{full-name}!",
	"unread.messages": {
		"one": "You have one unread message.",
		"other": "You have %{count} unread messages."
	}
}
```

## Learn more

- [Lingo](https://github.com/miroslavkovac/Lingo) - learn more about the localization file format, pluralization support, and see how you can get the most out of the Lingo.
