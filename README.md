## PDF Version of "Mastering Bitcoin 2nd Edition"

Many thanks for Andreas M. Antonopoulos, the author of the masterpiece. Thank you for your efforts to complete this book and generosity to share the book's source code free of charge.

There is a PDF of the book, you can download it in [Releases](https://github.com/cainslayer/bitcoinbook-build/releases) page.

## How to build a human-readable copy

### About the toolchain

Although the book is written in asciidoc format, but there are some differences. In fact the book is arranged by a system `Atlas` from `O'Reilly`. This system is not open for individuals. Secondly, the asciidoc standard is *VARIOUS*. Consequently, you can only get incomplete version with asciidoc-like toolchains.

### Html Version

You can easily do this with asciidoc utility, just install it with your package management utility\(apt, pacman, etc.\).

This utility can transform `asciidoc` into `html` and `docbook`, I tried pdf and latex but failed. I'm sorry.

To get html version, you may need to manually install `source-highlight` utility. Just run
```
$ asciidoc book.asciibook
```
There seems no problems. But I don't like the composition, and more, I want a http-serverless version.

### PDF version

I used `asciidoctor-pdf` to build the book into PDF successfully. But I changed the `asciidoc` to pass the errors reported by the utilities.

#### Build command

```
$ asciidoctor-pdf book.asciidoc -a source-highlighter=rouge -a rouge-style=monokai -a icons=font
```

Here is the reason why I pass these parameters:

##### source-highlighter=rouge

Select `rouge` as *syntax-highlight* resolver otherwise syntax-highlight is disabled.

##### rouge-style=monokai

Same as sample in Official Documentation, I like it.

##### icons=font

Show icon rather than ugly uppercase word.

#### Modify the asciidocs

You should change the original version to suit `asciidoctor-pdf`. I am showing my method. The following contents is based on revision 77b91b1949e2c03a36c395586a44dac20ec41533 .

##### book.asciidoc

Add `<<<` between lines to break each component\(Section\) into new page.

##### ch01.asciidoc

Line 151, remove `****`, otherwise the following contents will be included.

##### ch03.asciidoc

Line 477, JSON brackets unclose.

##### ch04.asciidoc ch10.asciidoc

The `asciidoctor-pdf` don't accept `&#x00D7;` expression, replace with letter x.

##### ch05.asciidoc

`[[mnemonic_paper_backup]]`, cols set to 4 will pass examination.

##### ch05.asciidoc ch06.asciidoc

The `asciidoctor-pdf` don't recognize `data-type="xref"`, this can be changed into normal hyperlink.

## Afterwords

If you like the book, star [bitcoinbook/bitcoinbo ok](https://github.com/bitcoinbook/bitcoinbook), and buy a book if you can afford.