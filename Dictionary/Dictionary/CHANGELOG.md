﻿# Change Log
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](http://keepachangelog.com/)
and this project adheres to [Semantic Versioning](http://semver.org/).

## 0.5.0
### Added
- `ObservableOrderedDictionary` wrapping `OrderedDictionary`
### Changed
- `ConcurrentObservableDictionary` renamed to
  `ObservableConcurrentDictionary` to better follow naming scheme
- `IsReadOnly` property hidden from `ObservableDictionaryBase` and
  derived types -- use, for example, `dict as IDictionary` to access it
- `ObservableDictionaryBase` protected notification methods simplified
- `Update` methods hidden from `OrderedDictionary` -- use `TryUpdate`
  in `Dictionary.Extensions` if it's really necessary

## 0.4.0
### Added
- `OrderedDictionary` class and `IReadOnlyOrderedDictionary` interface
### Removed
- `IList` and similar interfaces for `ObservableDictionaryBase`

## 0.3.1
### Added
- `IList` and similar interfaces for `ObservableDictionaryBase`
### Deprecated
- `IList` and similar interfaces for `ObservableDictionaryBase`
  - This throws an exception as soon as more than one element is added
    to the dictionary, and will be moved to a subclass
### Fixed
- `ObservableDictionary` doesn't update properly in a UWP `ListView`

## 0.3.0
### Added
- `ConcurrentObservableDictionary` wrapper for `ConcurrentDictionary`
- Several extension methods matching those defined on
  `ConcurrentDictionary`
- Protected overloads for triggering `ObservableDictionaryBase` events
  only when some condition is met or when the action returns some value
### Changed
- Moved extension methods to new namespace to not add them if the user
  only wants `ObservableDictionary` or similar
- Renamed `GetOrCreate` extension method to `GetOrAdd` to match method
  on `ConcurrentDictionary`
### Fixed
- `ObservableDictionary` constructors taking an existing dictionary
  doesn't initialize the object correctly

## 0.2.2
### Added
- `IObservableReadOnlyDictionary` interface combining observable
  interfaces with `IReadOnlyDictionary`
- `INotifyPropertyChanging` (as opposed to `...Changed`) for frameworks
  that support it

## 0.2.1
### Changed
- Value replacements in `ObservableDictionaryBase` subclasses no longer
  trigger a `PropertyChangedEvent` on `Keys`.
### Fixed
- Clearing `ObservableDictionaryBase` subclasses no longer throws an
  exception due to bad `NotifyCollectionChangedEventArgs` parameters.

## 0.2.0
### Added
- This change log
- `ObservableDictionaryBase` abstract class wrapping `IDictionary` and
  related interfaces in a manner supporting data binding.
- `ObservableDictionary` class implementing `ObservableDictionaryBase`
  for the standard `Dictionary` object.