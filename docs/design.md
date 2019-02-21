# Design <small>Everything you need my love...</small>

## Text

**Lorem Ispum**, dolor [MkDocs][1] sit amet, consectetur `:::js return target` adipiscing elit. Cras arcu libero,
mollis, sed massa vel, *ornare viverra ex*. Mauris (<kbd>F</kbd> or <kbd>S</kbd>) a ^^ullamcorperlac^^ us. Nullam
urna elit, *`venenatis porttitor`* malesuada eget finibus ut `mkdocs-material/material`.
  [1]: https://www.mkdocs.org

Text can be {--deleted--} and replacement text {++added++}. This can also be
combined into {~~one~>a single~~} operation. {==Highlighting==} is also
possible {>>and comments can be added inline<<}.  

[Emoji][13] adds the ability to insert a :shit: load of ~~emojis~~ that we use in
our daily lives. See the [EmojiOne demo][14] for a list [EmojiOne][15] of all available
emojis. Happy scrolling :tada:

  [13]: https://facelessuser.github.io/pymdown-extensions/extensions/emoji/
  [14]: https://emoji.codes/
  [15]: http://emojione.com

[SmartSymbols][21] converts markup for special characters into their
corresponding symbols, e.g. arrows (<--, -->, <-->), trademark and copyright
symbols ((c), (tm), (r)) and fractions (1/2, 1/4, ...).

  [21]: https://facelessuser.github.io/pymdown-extensions/extensions/smartsymbols/

[![Material for MkDocs](assets/images/material.png)](assets/images/material.png)

***

* [Admonition][26]
* [Codehilite][27]

  [26]: link
  [27]: link

``` sh
python --version
# Python 2.7.13
```

``` yaml
# Project information
site_name: 'Material for MkDocs'

# Extensions
markdown_extensions:
  - admonition
  - codehilite:
      guess_lang: false
```

``` sh
├─ assets/
│  ├─ images/                          # Images and icons
│  ├─ javascripts/                     # JavaScript
├─ partials/
│  ├─ integrations/                    # 3rd-party integrations
│  ├─ language/                        # Localized languages
├─ 404.html                            # 404 error page
├─ base.html                           # Base template
```

``` python hl_lines="3 4"
""" Bubble sort """
def bubble_sort(items):
    for i in range(len(items)):
        for j in range(len(items) - 1 - i):
            if items[j] > items[j + 1]:
                items[j], items[j + 1] = items[j + 1], items[j]
```

``` bash tab="Bash"
#!/bin/bash

echo "Hello world!"
```

``` c tab="C"
#include <stdio.h>

int main(void) {
  printf("Hello world!\n");
}
```

``` c++ tab="C++"
#include <iostream>

int main() {
  std::cout << "Hello world!" << std::endl;
  return 0;
}
```

``` c# tab="C#"
using System;

class Program {
  static void Main(string[] args) {
    Console.WriteLine("Hello world!");
  }
}
```

## Dialog boxes

{==

Formatting can also be applied to blocks, by putting the opening and closing
tags on separate lines and adding new lines between the tags and the content.

==}

!!! warning "Installation on macOS"

    When you're running the pre-installed version of Python on macOS, `pip`
    tries:

    1. **Installing in user space** (recommended): Provide the `--user` flag
      to the install command and `pip` will install.

    2. **Switching to a homebrewed Python**: This should eliminate a lot of problems you may be having with `pip`.

!!! failure "Error: unrecognized theme 'material'"

    If you run into this error, the most common reason is that you installed
    MkDocs through some package manager (e.g. Homebrew or `apt-get`) and the
    Material theme through `pip`, so both packages end up in different
    locations.

!!! info "Call for Contributions: Add languages/translations to Material"

    Help translate Material into more languages - it's just **one click** and
    takes approximately **2 minutes**: [click here](http://bit.ly/2EbzFc8)

!!! question "Why is there an edit button at the top of every article?"

    ISee the [MkDocs documentation][19] *GitHub*  on more
    guidance regarding the `edit_uri` attribute, which defines whether the edit
    button is shown or not.

  [19]: https://www.mkdocs.org/user-guide/configuration/#edit_uri

!!! note

    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.

    ``` mysql
    SELECT
      Employees.EmployeeID,
      Employees.Name,
      Employees.Salary,
      Manager.Name AS Manager
    FROM
      Employees
    LEFT JOIN
      Employees AS Manager
    ON
      Employees.ManagerID = Manager.EmployeeID
    WHERE
      Employees.EmployeeID = '087652';
    ```

    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.

!!! note ""

    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.

??? note "Phasellus posuere in sem ut cursus"

    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.

!!! abstract
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.

!!! tip
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.

!!! success
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.

!!! danger
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.

!!! bug
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.

!!! example
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.

!!! quote
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.

## Headings

### The 3rd level

#### The 4th level

##### The 5th level

###### The 6th level

## Headings <small>with secondary text</small>

### The 3rd level <small>with secondary text</small>

#### The 4th level <small>with secondary text</small>

##### The 5th level <small>with secondary text</small>

###### The 6th level <small>with secondary text</small>

## Blockquotes

> **Lorem Ispum**, dolor [MkDocs][1] sit amet, consectetur `:::js return target` adipiscing elit. Cras arcu libero,
mollis, sed massa vel, *ornare viverra ex*. Mauris (<kbd>F</kbd> or <kbd>S</kbd>) a ^^ullamcorperlac^^ us. Nullam
urna elit, *`venenatis porttitor`* malesuada eget finibus ut `mkdocs-material/material`.
  [1]: https://www.mkdocs.org

> > **Lorem Ispum**, dolor [MkDocs][1] sit amet, consectetur `:::js return target` adipiscing elit. Cras arcu libero,
mollis, sed massa vel, *ornare viverra ex*. Mauris (<kbd>F</kbd> or <kbd>S</kbd>) a ^^ullamcorperlac^^ us. Nullam
urna elit, *`venenatis porttitor`* malesuada eget finibus ut `mkdocs-material/material`.
  [1]: https://www.mkdocs.org

> > > **Lorem Ispum**, dolor [MkDocs][1] sit amet, consectetur `:::js return target` adipiscing elit. Cras arcu libero,
mollis, sed massa vel, *ornare viverra ex*. Mauris (<kbd>F</kbd> or <kbd>S</kbd>) a ^^ullamcorperlac^^ us. Nullam
urna elit, *`venenatis porttitor`* malesuada eget finibus ut `mkdocs-material/material`.
  ``` js hl_lines="8"
  var _extends = function(target) {
    for (var i = 1; i < arguments.length; i++) {
      var source = arguments[i];
      for (var key in source) {
        target[key] = source[key];
      }
    }
    return target;
  };
  ```
  [1]: https://www.mkdocs.org

## Lists

### Unordered lists

* Sed sagittis eleifend rutrum. Donec vitae suscipit est.

    * Duis mollis est eget nibh volutpat, fermentum aliquet dui mollis.
    * Nam vulputate tincidunt fringilla.
    * Nullam dignissim ultrices urna non auctor.

* Aliquam metus eros, pretium sed nulla venenatis, faucibus auctor ex.

### Ordered lists

1. Integer vehicula feugiat magna, a mollis tellus. Nam mollis ex ante.

2. Cum sociis natoque penatibus et magnis dis parturient montes.

    1. Vivamus venenatis porttitor tortor sit amet rutrum.

        1. Mauris dictum mi lacus
        2. Ut sit amet placerat ante
        3. Suspendisse ac eros arcu

    2. Morbi eget dapibus felis. Vivamus venenatis porttitor tortor.

3. Vivamus id mi enim. Integer id turpis sapien. Ut condimentum lobortis
  sagittis.

### Definition lists

Lorem ipsum dolor sit amet

:   Sed sagittis eleifend rutrum. Donec vitae suscipit est.

    Duis mollis est eget nibh volutpat, fermentum aliquet dui mollis.

Cras arcu libero

:   Aliquam metus eros, pretium sed nulla venenatis, faucibus auctor ex. Proin
    ut eros.


## Data tables

| Sollicitudo / Pellentesi | consectetur | adipiscing | elit    | arcu | sed |
| ------------------------ | ----------- | ---------- | ------- | ---- | --- |
| Vivamus a pharetra       | yes         | yes        | yes     | yes  | yes |
| Mauris a ullamcorper     | yes         | yes        | partial | yes  | yes |
| Vestibulum sodales       | yes         | -          | yes     | -    | yes |

| Left       | Center   | Right   |
| :--------- | :------: | ------: |
| Lorem      | *dolor*  | `amet`  |
| [ipsum](#) | **sit**  |         |

| Block name   | Wrapped contents                                |
| ------------ | ----------------------------------------------- |
| `analytics`  | Wraps the Google Analytics integration          |
| `content`    | Wraps the main content                          |

<table>
  <colgroup>
    <col width="30%">
    <col width="70%">
  </colgroup>
  <thead>
    <tr class="header">
      <th>Table</th>
      <th>with colgroups (Pandoc)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Lorem</td>
      <td>ipsum dolor sit amet.</td>
    </tr>
    <tr>
      <td>Sed sagittis</td>
      <td>eleifend rutrum. Donec vitae suscipit est.</td>
    </tr>
  </tbody>
</table>

<table style="white-space: nowrap;">
  <thead>
    <tr>
      <th colspan="4">Available languages</td>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>ar</code> / Arabic</td>
      <td><code>ca</code> / Catalan</td>
      <td><code>cs</code> / Czech</td>
      <td><code>da</code> / Danish</td>
    </tr>
    <tr>
      <td colspan="2">
        <code>zh</code> / Chinese (Simplified)
      </td>
      <td colspan="2">
        <code>zh-Hant</code> / Chinese (Traditional)
      </td>
    </tr>
    <tr>
      <td colspan="2">
        <code>zh-TW</code> / Chinese (Taiwanese)
      </td>
      <td><code>tr</code> / Turkish</td>
      <td><code>uk</code> / Ukrainian</td>
    </tr>
    <tr>
      <td><code>vi</code> / Vietnamese</td>
      <td colspan="3" align="right">
        <a href="http://bit.ly/2EbzFc8">Submit a new language</a>
      </td>
    </tr>
  </tbody>
</table>

## Changelog

### 3.2.0 <small>_ December 28, 2018</small>

* Added support for redirects using metadata refresh
* Fixed [#921][921]: Load Google Analytics snippet asynchronously

  [921]: https://github.com/squidfunk/mkdocs-material/issues/921

### 3.1.0 <small>_ November 17, 2018</small>

* Added support for Progressive Web App Manifest
* Fixed [#915][915]: Search bug in Safari (upgraded Lunr.js)

  [915]: https://github.com/squidfunk/mkdocs-material/issues/915

### 3.0.6 <small>_ October 26, 2018</small>

* Added Taiwanese translations
* Fixed [#906][906]: JavaScript code blocks evaluated in search results

  [906]: https://github.com/squidfunk/mkdocs-material/issues/906


## Footnotes

Lorem ipsum[^1] dolor sit amet, consectetur adipiscing elit.[^2]

<a href="#fn:1">Jump to footnote at the bottom of the page</a>

  [^1]: Lorem ipsum dolor sit amet, consectetur adipiscing elit.

#### on multiple lines

Paragraphs should be written on the next line. As with all Markdown blocks, the
content must be indented by four spaces.

Example:

``` markdown
[^2]:
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.
```

Result:

  [^2]:
      Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
      nulla. Curabitur feugiat, tortor non consequat finibus, justo purus
      auctor massa, nec semper lorem quam in massa.

<a href="#fn:2">Jump to footnote at the bottom of the page</a>

### Tasklist

* [x] Lorem ipsum dolor sit amet, consectetur adipiscing elit
* [x] Nulla lobortis egestas semper
* [x] Curabitur elit nibh, euismod et ullamcorper at, iaculis feugiat est
* [ ] Vestibulum convallis sit amet nisi a tincidunt
    * [x] In hac habitasse platea dictumst
    * [x] In scelerisque nibh non dolor mollis congue sed et metus
    * [x] Sed egestas felis quis elit dapibus, ac aliquet turpis mattis
    * [ ] Praesent sed risus massa
* [ ] Aenean pretium efficitur erat, donec pharetra, ligula non scelerisque
* [ ] Nulla vel eros venenatis, imperdiet enim id, faucibus nisi

[25]: https://facelessuser.github.io/pymdown-extensions/extensions/tasklist/