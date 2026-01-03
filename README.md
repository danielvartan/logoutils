# LogoUtils <a href = "https://github.com/danielvartan/logoutils"><img src = "images/logo.svg" align="right" width="120" /></a>

<!-- badges: start -->
[![Project Status: Active - The project has reached a stable, usable state and is being actively developed.](https://www.repostatus.org/badges/latest/active.svg)](https://www.repostatus.org/#active)
[![DOI Badge](https://img.shields.io/badge/doi-10.5281/zenodo.18136297-1284C5.svg)](https://doi.org/10.5281/zenodo.18136297)
[![FAIR Checklist Badge](https://img.shields.io/badge/fairsoftwarechecklist.net--00a7d9)](https://fairsoftwarechecklist.net/v0.2?f=21&a=32113&i=02220&r=123)
[![fair-software.eu](https://img.shields.io/badge/fair--software.eu-%E2%97%8F%20%E2%97%8F%20%E2%97%8F%20%E2%97%8F%20%E2%97%8B-yellow)](https://fair-software.eu)
[![GPLv3 License Badge](https://img.shields.io/badge/license-GPLv3-bd0000.svg)](https://www.gnu.org/licenses/gpl-3.0)
[![Contributor Covenant 3.0 Code of Conduct Badge](https://img.shields.io/badge/Contributor%20Covenant-3.0-4baaaa.svg)](https://www.contributor-covenant.org/version/3/0/code_of_conduct/)
<!-- badges: end -->

## Overview

`LogoUtils` is a collection of [procedures](https://docs.netlogo.org/programming.html#procedures) for common [NetLogo](https://ccl.northwestern.edu/netlogo/) programming tasks. The library includes tools for [control flow](https://en.wikipedia.org/wiki/Control_flow), logic, [defensive programming](https://en.wikipedia.org/wiki/Defensive_programming), file system operations, list manipulation, mathematical utilities, string handling, and world management.

Many of these procedures are planned for inclusion as [NetLogo modules](https://github.com/NetLogo/NetLogo/issues/2559#issuecomment-3335592459) once this feature becomes available in future NetLogo releases. Until then, `LogoUtils` offers a convenient way to access these utilities.

> If you find this project useful, please consider giving it a star! &nbsp; [![GitHub repo stars](https://img.shields.io/github/stars/danielvartan/logoutils)](https://github.com/danielvartan/logoutils)

## Usage

All procedures are found in the repository [`nls`](nls) directory. Each function is provided in its own file named after the function, except for test, check, and assertion functions, which are grouped by category.

To use a procedure, copy its code into your model or import it using the [`__includes`](https://docs.netlogo.org/dictionary.html#includes) primitive.

Some functions depend on NetLogo extensions or other utility functions. Any required dependencies are listed in the file header.

Here are some examples:

### Control Flow and Logic

- [`any-member?`](nls/check-any.nls) ([`to-report`](https://docs.netlogo.org/dictionary.html#to-report)): Tests if any element in a list is a member of another list.
- [`any-true?`](nls/check-any.nls) (`to-report`): Tests if any element in a list is `true`.
- [`list-any?`]((nls/check-any.nls)) (`to-report`): Tests if any element in a list is equal to a specified value or to values in another list.
- [`all-member?`](nls/check-all.nls) (`to-report`): Tests if all elements in a list are members of another list.
- [`all-true?`](nls/check-all.nls) (`to-report`): Tests if all elements in a list are `true`.
- [`list-all?`](nls/check-all.nls) (`to-report`): Tests if all elements in a list are equal to a specified value or to values in another list.

### Defensive Programming

These functions follow NetLogo naming conventions for testing, as well as the conventions used in the [`checkmate`](https://mllg.github.io/checkmate/) R package.

`test` functions return `true` or `false`. `check` functions return `true` if the test passes, or a string with an error message if it fails. `assert` functions are [`to`](https://docs.netlogo.org/dictionary.html#to) procedures that throw an error if the test fails.

- [`is-atomic?`](nls/check-atomic.nls) `test-atomic` (`to-report`): Tests whether a value is not a list.
- [`is-logical?`](nls/check-logical.nls) `test-logical` `test-boolean` (`to-report`): Tests whether a value is `true` or `false`.
- [`is-integer?`](nls/check-integer.nls) `test-integer` (`to-report`): Tests whether a value is an integer number.
- [`is-numeric?`](nls/check-number.nls) `test-number` `test-numeric` (`to-report`): Tests whether a value is a number (integer or float).
- [`is-string?`](nls/check-string.nls) `test-string` (`to-report`): Tests whether a value is a string.
- [`is-list?`](nls/check-list.nls) `test-list` (`to-report`): Tests whether a value is a list.
- [`is-true?`](nls/check-true.nls) `test-true` (`to-report`): Tests whether a value is `true`.
- [`is-false?`](nls/check-false.nls) `test-false` (`to-report`): Tests whether a value is `false`.
- [`dir-exists?`](nls/check-dir-exists.nls) `test-dir-exists` (`to-report`): Tests whether a directory exists.
- [`test-file-exists`](nls/check-file-exists.nls) (`to-report`): Tests whether a file exists.
- [`is-gis?`](nls/check-gis.nls) `test-gis` (`to-report`): Tests whether a value is a [GIS dataset](https://ccl.northwestern.edu/netlogo/docs/gis.html#gis:type-of).
- [`is-nan?`](nls/check-nan.nls) `test-nan` (`to-report`): Tests whether a value is `NaN` (not a number). This is useful when using the `gis` extension, as GIS datasets may contain `NaN` values.
- [`is-between?`](nls/check-between.nls) `test-between` (`to-report`): Tests whether a value is between two numbers.
- [`test-choice`](nls/check-choice.nls) (`to-report`): Tests whether a value is one of a set of choices.
- [`is-windows?`](nls/check-windows.nls) `test-windows` (`to-report`): Tests whether the user is running NetLogo on a Windows operating system.

<br>

- [`assert-atomic`](nls/check-atomic.nls) ([`to`](https://docs.netlogo.org/dictionary.html#to)): Asserts that a value is not a list.
- [`assert-logical`](nls/check-logical.nls) `assert-boolean` (`to`): Asserts that a value is `true` or `false`.
- [`assert-integer`](nls/check-integer.nls) (`to`): Asserts that a value is an integer.
- [`assert-number`](nls/check-number.nls) `assert-numeric` (`to`): Asserts that a value is a number (integer or float).
- [`assert-string`](nls/check-string.nls) (`to`): Asserts that a value is a string.
- [`assert-list`](nls/check-list.nls) (`to`): Asserts that a value is a list.
- [`assert-true`](nls/check-true.nls) (`to`): Asserts that a value is `true`.
- [`assert-false`](nls/check-false.nls) (`to`): Asserts that a value is `false`.
- [`assert-dir-exists`](nls/check-dir-exists.nls) (`to`): Asserts that a directory exists.
- [`assert-file-exists`](nls/check-file-exists.nls) (`to`): Asserts that a file exists.
- [`assert-gis`](nls/check-gis.nls) (`to`): Asserts that a value is a [GIS dataset](https://ccl.northwestern.edu/netlogo/docs/gis.html#gis:type-of).
- [`assert-between`](nls/check-between.nls) (`to`): Asserts that a value is between two numbers.
- [`assert-choice`](nls/check-choice.nls) (`to`): Asserts that a value is one of a set of choices.
- [`assert-windows`](nls/check-windows.nls) (`to`): Asserts that the user is running NetLogo on a Windows operating system.

Several other assertion functions are also available. Check the repository [`nls`](nls) directory for more details.

### File System

- [`basename`](nls/basename.nls) (`to-report`): Returns the base name of a file or directory (i.e., the last part of the path).
- [`file-path`](nls/file-path.nls) (`to-report`): Creates a file path from a directory and a file name.
- [`list-files-by-pattern`](nls/list-files-by-pattern.nls) (`to-report`): Lists files in a directory that match a specified pattern.
- [`normalize-path`](nls/normalize-path.nls) (`to-report`): Normalizes a file path making it compatible with the user operating system.

### Lists

- [`as-list`](nls/as-list.nls) (`to-report`): Converts an atomic value to a list.
- [`collapse`](nls/collapse.nls) (`to-report`): Collapses a list into a string using a separator (e.g., `[1 2 3 4]` → `"1, 2, 3, 4"`).
- [`combine`](nls/combine.nls) (`to-report`): Combines two lists into a single list.
- [`list-to-c`](nls/list-to-c.nls) (`to-report`): Converts a NetLogo list into a string formatted as an R [`c()`](https://rdrr.io/r/base/c.html) expression, with elements separated by commas (e.g., `[1 2 3]` → `"c(1, 2, 3)"`).
- [`match`](nls/match.nls) (`to-report`): Returns the first element in a list that matches a specified value.
- [`unique-outliers`](nls/unique-outliers.nls) (`to-report`): Returns a sorted list of unique outlier values from a given list. Outliers are defined as values greater than the third quartile plus a specified multiple of the interquartile range (IQR), or less than the first quartile minus the same multiple of the IQR. Duplicate values are removed before identifying outliers.

### Mathematical

- [`distance-between`](nls/distance-between.nls) (`to-report`): Returns the distance between two numbers.
- [`quartile`](nls/quartile.nls) (`to-report`): Returns the quartiles (Q1,Q2, Q3, Q4), the quartile length, and the interquartile range (IQR) of a list of numbers.
- [`random-beta`](nls/random-beta.nls) (`to-report`): Returns a random number from a beta distribution with parameters `alpha` and `beta`.
- [`rescale`](nls/rescale.nls) (`to-report`): Rescales a number from one range to another.

### Strings

- [`as-string`](nls/as-string.nls) (`to-report`): Converts any value to a string.
- [`num-to-str-month`](nls/num-to-str-month.nls) (`to-report`): Converts a numeric month value (`1` for January, `2` for February, etc.) to its corresponding string representation (e.g., `1` → `"January"`).
- [`rep-collapse`](nls/rep-collapse.nls) (`to-report`): Repeats and collapses a value into a string.
- [`single-quote`](nls/single-quote.nls) (`to-report`): Returns values with single quotes. It also works with lists.
- [`str-detect`](nls/str-detect.nls) (`to-report`): Detects the presence/absence of a match in a string using a regular expression. Returns `true` if the match is found, `false` otherwise.
- [`str-extract`](nls/str-extract.nls) (`to-report`): Extracts a match from a string using a regular expression. Returns the first match found, or `"NA"` if no match is found.
- [`str-extract-all`](nls/str-extract-all.nls) (`to-report`): Extracts all matches from a string using a regular expression. Returns a list of all matches found, with `"NA"` for any non-matching elements.
- [`str-remove`](nls/str-remove.nls) (`to-report`): Removes a match from a string using a regular expression. Returns the string with the first match removed, or the original string if no match is found.
- [`str-remove-all`](nls/str-remove-all.nls) (`to-report`): Removes all matches from a string using a regular expression. Returns the string with all matches removed, or the original string if no matches are found.
- [`str-replace`](nls/str-replace.nls) (`to-report`): Replaces a match in a string using a regular expression. Returns the string with the first match replaced, or the original string if no match is found.
- [`str-replace-all`](nls/str-replace-all.nls) (`to-report`): Replaces all matches in a string using a regular expression. Returns the string with all matches replaced, or the original string if no matches are found.
- [`str-to-num-month`](nls/str-to-num-month.nls) (`to-report`): Converts a string representing a month (e.g., `"January"`) to its corresponding numeric value (`1`  for January, `2` for February, etc.).
- [`test-string-in-r`](nls/test-string-in-r.nls) (`to-report`): Tests whether a string is a valid R string.

### World

- [`check-world-bleed`](nls/check-world-bleed.nls) (`to-report`): Checks a range of `pxcor` and `pycor` values to identify any lines of patches with a value of `0`, `NA`, or `NaN`. Returns a list containing two ordered lists: one with the `pxcor` values and one with the `pycor` values of patches that meet this condition. If no such patches are found, both lists are empty.
- [`remove-world-bleed`](nls/remove-world-bleed.nls) (`to`): Checks for and removes world bleed patches—lines of patches at the edges of the world with values of `0`, `"NA"`, or `NaN`.
- [`show-values`](nls/show-values.nls) (`to`): A procedure for use with a `forever` button that displays patch values under the mouse cursor in the NetLogo view. Useful for interactively inspecting patch data during model runs.

## Citation

[![DOI Badge](https://img.shields.io/badge/doi-10.5281/zenodo.18136297-1284C5.svg)](https://doi.org/10.5281/zenodo.18136297)

If you use `LogoUtils` in your work, please cite it to acknowledge the effort invested in its development and maintenance. Your citation helps support the ongoing improvement of the project.

To cite `LogoUtils` in publications please use the following format:

Vartanian, D. (n.d.). *LogoUtils: Utility functions for NetLogo* [Computer software]. <https://doi.org/10.5281/zenodo.18136297>

A BibLaTeX entry for LaTeX users is:

```latex
@software{vartanian,
  title = {LogoUtils: Utility functions for NetLogo},
  author = {Daniel Vartanian},
  doi = {https://doi.org/10.5281/zenodo.18136297},
  note = {Computer software}
}
```

## Contributing

[![Contributor Covenant 3.0 Code of Conduct Badge](https://img.shields.io/badge/Contributor%20Covenant-3.0-4baaaa.svg)](https://www.contributor-covenant.org/version/3/0/code_of_conduct/)

Contributions are always welcome! Whether you want to report bugs, suggest new features, or help improve the code or documentation, your input makes a difference.

Before opening a new issue, please check the [issues tab](https://github.com/danielvartan/logoutils/issues) to see if your topic has already been reported.

## License

[![GNU GPLv3 License](https://img.shields.io/badge/license-GPLv3-bd0000.svg)](https://www.gnu.org/licenses/gpl-3.0)

``` text
Copyright (C) 2025 Daniel Vartanian

LogoUtils is free software: you can redistribute it and/or modify it under
the terms of the GNU General Public License as published by the Free Software
Foundation, either version 3 of the License, or (at your option) any later
version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY
WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE. See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with
this program. If not, see <https://www.gnu.org/licenses/>.
```

## Acknowledgments

`LogoUtils` is an independent project with no affiliation to [NetLogo](https://www.netlogo.org/) or its developers.

`LogoUtils` brand identity is based on the [NetLogo 7](https://www.netlogo.org/) brand identity.
