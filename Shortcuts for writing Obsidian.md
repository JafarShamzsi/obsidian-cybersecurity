##### links from researching:
* https://markdownguide.offshoot.io/basic-syntax/

## Headings[](https://markdownguide.offshoot.io/basic-syntax/#headings)

To create a heading, add number signs (`#`) in front of a word or phrase. The number of number signs you use should correspond to the heading level. For example, to create a heading level three (`<h3>`), use three number signs (e.g., `### My Header`).

|Markdown|HTML|Rendered Output|
|---|---|---|
|`# Heading level 1`|`<h1>Heading level 1</h1>`|# Heading level 1|
|`## Heading level 2`|`<h2>Heading level 2</h2>`|## Heading level 2|
|`### Heading level 3`|`<h3>Heading level 3</h3>`|### Heading level 3|
|`#### Heading level 4`|`<h4>Heading level 4</h4>`|#### Heading level 4|
|`##### Heading level 5`|`<h5>Heading level 5</h5>`|##### Heading level 5|
|`###### Heading level 6`|`<h6>Heading level 6</h6>`|###### Heading level 6|

### Alternate Syntax[](https://markdownguide.offshoot.io/basic-syntax/#alternate-syntax)

Alternatively, on the line below the text add any number of == characters  for heading level 1 or –- characters for heading level 2.

|Markdown|HTML|Rendered Output|
|---|---|---|
|`Heading level 1   ===============`|`<h1>Heading level 1</h1>`|# Heading level 1|
|`Heading level 2   ---------------`|`<h2>Heading level 2</h2>`|## Heading level 2|

### Heading Best Practices[](https://markdownguide.offshoot.io/basic-syntax/#heading-best-practices)

Markdown applications don’t agree on how to handle a missing space between the number signs (`#`) and the heading name. For compatibility, always put a space between the number signs and the heading name.

|✅  Do this|❌  Don't do this|
|---|---|
|`# Here's a Heading      `|`#Here's a Heading`|

You should also put blank lines before and after a heading for compatibility.

|✅  Do this|❌  Don't do this|
|---|---|
|`Try to put a blank line before...      # Heading      ...and after a heading.`|`Without blank lines, this might not look right.   # Heading   Don't do this!`|

## Paragraphs[](https://markdownguide.offshoot.io/basic-syntax/#paragraphs-1)

To create paragraphs, use a blank line to separate one or more lines of text.

|Markdown|HTML|Rendered Output|
|---|---|---|
|`I really like using Markdown.      I think I'll use it to format all of my documents from now on.`|`<p>I really like using Markdown.</p>      <p>I think I'll use it to format all of my documents from now on.</p>`|I really like using Markdown.<br><br>I think I'll use it to format all of my documents from now on.|

### Paragraph Best Practices[](https://markdownguide.offshoot.io/basic-syntax/#paragraph-best-practices)

Unless the [paragraph is in a list](https://markdownguide.offshoot.io/basic-syntax/#paragraphs), don’t indent paragraphs with spaces or tabs.

 **Note:** If you need to indent paragraphs in the output, see the section on how to [indent (tab)](https://markdownguide.offshoot.io/hacks/#indent-tab).

|✅  Do this|❌  Don't do this|
|---|---|
|`Don't put tabs or spaces in front of your paragraphs.      Keep lines left-aligned like this.      `|`This can result in unexpected formatting problems.        Don't add tabs or spaces in front of paragraphs.`|

## Line Breaks[](https://markdownguide.offshoot.io/basic-syntax/#line-breaks)

To create a line break or new line (`<br>`), end a line with two or more spaces, and then type return.

|Markdown|HTML|Rendered Output|
|---|---|---|
|`This is the first line.     And this is the second line.`|`<p>This is the first line.<br>   And this is the second line.</p>`|This is the first line.  <br>And this is the second line.|

### Line Break Best Practices[](https://markdownguide.offshoot.io/basic-syntax/#line-break-best-practices)

You can use two or more spaces (commonly referred to as “trailing whitespace”) for line breaks in nearly every Markdown application, but it’s controversial. It’s hard to see trailing whitespace in an editor, and many people accidentally or intentionally put two spaces after every sentence. For this reason, you may want to use something other than trailing whitespace for line breaks. If your Markdown application [supports HTML](https://markdownguide.offshoot.io/basic-syntax/#html), you can use the `<br>` HTML tag.

For compatibility, use trailing white space or the `<br>` HTML tag at the end of the line.

There are two other options I don’t recommend using. CommonMark and a few other lightweight markup languages let you type a backslash (`\`) at the end of the line, but not all Markdown applications support this, so it isn’t a great option from a compatibility perspective. And at least a couple lightweight markup languages don’t require anything at the end of the line — just type return and they’ll create a line break.

|✅  Do this|❌  Don't do this|
|---|---|
|`First line with two spaces after.     And the next line.      First line with the HTML tag after.<br>   And the next line.      `|`First line with a backslash after.\   And the next line.      First line with nothing after.   And the next line.      `|

## Emphasis[](https://markdownguide.offshoot.io/basic-syntax/#emphasis)

You can add emphasis by making text bold or italic.

### Bold[](https://markdownguide.offshoot.io/basic-syntax/#bold)

To bold text, add two asterisks or underscores before and after a word or phrase. To bold the middle of a word for emphasis, add two asterisks without spaces around the letters.

|Markdown|HTML|Rendered Output|
|---|---|---|
|`I just love **bold text**.`|`I just love <strong>bold text</strong>.`|I just love **bold text**.|
|`I just love __bold text__.`|`I just love <strong>bold text</strong>.`|I just love **bold text**.|
|`Love**is**bold`|`Love<strong>is</strong>bold`|Love**is**bold|

#### Bold Best Practices[](https://markdownguide.offshoot.io/basic-syntax/#bold-best-practices)

Markdown applications don’t agree on how to handle underscores in the middle of a word. For compatibility, use asterisks to bold the middle of a word for emphasis.

|✅  Do this|❌  Don't do this|
|---|---|
|`Love**is**bold`|`Love__is__bold`|

### Italic[](https://markdownguide.offshoot.io/basic-syntax/#italic)

To italicize text, add one asterisk or underscore before and after a word or phrase. To italicize the middle of a word for emphasis, add one asterisk without spaces around the letters.

|Markdown|HTML|Rendered Output|
|---|---|---|
|`Italicized text is the *cat's meow*.`|`Italicized text is the <em>cat's meow</em>.`|Italicized text is the _cat’s meow_.|
|`Italicized text is the _cat's meow_.`|`Italicized text is the <em>cat's meow</em>.`|Italicized text is the _cat’s meow_.|
|`A*cat*meow`|`A<em>cat</em>meow`|A_cat_meow|

#### Italic Best Practices[](https://markdownguide.offshoot.io/basic-syntax/#italic-best-practices)

Markdown applications don’t agree on how to handle underscores in the middle of a word. For compatibility, use asterisks to italicize the middle of a word for emphasis.

|✅  Do this|❌  Don't do this|
|---|---|
|`A*cat*meow`|`A_cat_meow`|

### Bold and Italic[](https://markdownguide.offshoot.io/basic-syntax/#bold-and-italic)

To emphasize text with bold and italics at the same time, add three asterisks or underscores before and after a word or phrase. To bold and italicize the middle of a word for emphasis, add three asterisks without spaces around the letters.

|Markdown|HTML|Rendered Output|
|---|---|---|
|`This text is ***really important***.`|`This text is <em><strong>really important</strong></em>.`|This text is _**really important**_.|
|`This text is ___really important___.`|`This text is <em><strong>really important</strong></em>.`|This text is _**really important**_.|
|`This text is __*really important*__.`|`This text is <em><strong>really important</strong></em>.`|This text is _**really important**_.|
|`This text is **_really important_**.`|`This text is <em><strong>really important</strong></em>.`|This text is _**really important**_.|
|`This is really***very***important text.`|`This is really<em><strong>very</strong></em>important text.`|This is really_**very**_important text.|

 **Note:** The order of the `em` and `strong` tags might be reversed depending on the Markdown processor you're using.

#### Bold and Italic Best Practices[](https://markdownguide.offshoot.io/basic-syntax/#bold-and-italic-best-practices)

Markdown applications don’t agree on how to handle underscores in the middle of a word. For compatibility, use asterisks to bold and italicize the middle of a word for emphasis.

|✅  Do this|❌  Don't do this|
|---|---|
|`This is really***very***important text.`|`This is really___very___important text.`|

## Blockquotes[](https://markdownguide.offshoot.io/basic-syntax/#blockquotes-1)

To create a blockquote, add a `>` in front of a paragraph.

```
> Dorothy followed her through many of the beautiful rooms in her castle.
```

The rendered output looks like this:

> Dorothy followed her through many of the beautiful rooms in her castle.

### Blockquotes with Multiple Paragraphs[](https://markdownguide.offshoot.io/basic-syntax/#blockquotes-with-multiple-paragraphs)

Blockquotes can contain multiple paragraphs. Add a `>` on the blank lines between the paragraphs.

```
> Dorothy followed her through many of the beautiful rooms in her castle.
>
> The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.
```

The rendered output looks like this:

> Dorothy followed her through many of the beautiful rooms in her castle.
> 
> The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.

### Nested Blockquotes[](https://markdownguide.offshoot.io/basic-syntax/#nested-blockquotes)

Blockquotes can be nested. Add a `>>` in front of the paragraph you want to nest.

```
> Dorothy followed her through many of the beautiful rooms in her castle.
>
>> The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.
```

The rendered output looks like this:

> Dorothy followed her through many of the beautiful rooms in her castle.
> 
> > The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.

### Blockquotes with Other Elements[](https://markdownguide.offshoot.io/basic-syntax/#blockquotes-with-other-elements)

Blockquotes can contain other Markdown formatted elements. Not all elements can be used — you’ll need to experiment to see which ones work.

```
> #### The quarterly results look great!
>
> - Revenue was off the chart.
> - Profits were higher than ever.
>
>  *Everything* is going according to **plan**.
```

The rendered output looks like this:

> #### The quarterly results look great!
> 
> - Revenue was off the chart.
> - Profits were higher than ever.
> 
> _Everything_ is going according to **plan**.

### Blockquotes Best Practices[](https://markdownguide.offshoot.io/basic-syntax/#blockquotes-best-practices)

For compatibility, put blank lines before and after blockquotes.

|✅  Do this|❌  Don't do this|
|---|---|
|`Try to put a blank line before...      > This is a blockquote      ...and after a blockquote.`|`Without blank lines, this might not look right.   > This is a blockquote   Don't do this!`|

## Lists[](https://markdownguide.offshoot.io/basic-syntax/#lists-1)

You can organize items into ordered and unordered lists.

### Ordered Lists[](https://markdownguide.offshoot.io/basic-syntax/#ordered-lists)

To create an ordered list, add line items with numbers followed by periods. The numbers don’t have to be in numerical order, but the list should start with the number one.

|Markdown|HTML|Rendered Output|
|---|---|---|
|`1. First item   2. Second item   3. Third item   4. Fourth item`|`<ol>     <li>First item</li>     <li>Second item</li>     <li>Third item</li>     <li>Fourth item</li>   </ol>`|1. First item<br>2. Second item<br>3. Third item<br>4. Fourth item|
|`1. First item   1. Second item   1. Third item   1. Fourth item`|`<ol>     <li>First item</li>     <li>Second item</li>     <li>Third item</li>     <li>Fourth item</li>   </ol>`|1. First item<br>2. Second item<br>3. Third item<br>4. Fourth item|
|`1. First item   8. Second item   3. Third item   5. Fourth item`|`<ol>     <li>First item</li>     <li>Second item</li>     <li>Third item</li>     <li>Fourth item</li>   </ol>`|1. First item<br>2. Second item<br>3. Third item<br>4. Fourth item|
|`1. First item   2. Second item   3. Third item       1. Indented item       2. Indented item   4. Fourth item`|`<ol>     <li>First item</li>     <li>Second item</li>     <li>Third item       <ol>         <li>Indented item</li>         <li>Indented item</li>       </ol>     </li>     <li>Fourth item</li>   </ol>`|1. First item<br>2. Second item<br>3. Third item<br>    1. Indented item<br>    2. Indented item<br>4. Fourth item|

#### Ordered List Best Practices[](https://markdownguide.offshoot.io/basic-syntax/#ordered-list-best-practices)

CommonMark and a few other lightweight markup languages let you use a parenthesis (`)`) as a delimiter (e.g., `1) First item`), but not all Markdown applications support this, so it isn’t a great option from a compatibility perspective. For compatibility, use periods only.

|✅  Do this|❌  Don't do this|
|---|---|
|`1. First item   2. Second item`|`1) First item   2) Second item`|

### Unordered Lists[](https://markdownguide.offshoot.io/basic-syntax/#unordered-lists)

To create an unordered list, add dashes (`-`), asterisks (`*`), or plus signs (`+`) in front of line items. Indent one or more items to create a nested list.

|Markdown|HTML|Rendered Output|
|---|---|---|
|`- First item   - Second item   - Third item   - Fourth item`|`<ul>     <li>First item</li>     <li>Second item</li>     <li>Third item</li>     <li>Fourth item</li>   </ul>`|- First item<br>- Second item<br>- Third item<br>- Fourth item|
|`* First item   * Second item   * Third item   * Fourth item`|`<ul>     <li>First item</li>     <li>Second item</li>     <li>Third item</li>     <li>Fourth item</li>   </ul>`|- First item<br>- Second item<br>- Third item<br>- Fourth item|
|`+ First item   + Second item   + Third item   + Fourth item`|`<ul>     <li>First item</li>     <li>Second item</li>     <li>Third item</li>     <li>Fourth item</li>   </ul>`|- First item<br>- Second item<br>- Third item<br>- Fourth item|
|`- First item   - Second item   - Third item       - Indented item       - Indented item   - Fourth item`|`<ul>     <li>First item</li>     <li>Second item</li>     <li>Third item       <ul>         <li>Indented item</li>         <li>Indented item</li>       </ul>     </li>     <li>Fourth item</li>   </ul>`|- First item<br>- Second item<br>- Third item<br>    - Indented item<br>    - Indented item<br>- Fourth item|

#### Starting Unordered List Items With Numbers[](https://markdownguide.offshoot.io/basic-syntax/#starting-unordered-list-items-with-numbers)

If you need to start an unordered list item with a number followed by a period, you can use a backslash (`\`) to [escape](https://markdownguide.offshoot.io/basic-syntax/#escaping-characters) the period.

|Markdown|HTML|Rendered Output|
|---|---|---|
|`- 1968\. A great year!   - I think 1969 was second best.`|`<ul>     <li>1968. A great year!</li>     <li>I think 1969 was second best.</li>   </ul>`|- 1968. A great year!<br>- I think 1969 was second best.|

#### Unordered List Best Practices[](https://markdownguide.offshoot.io/basic-syntax/#unordered-list-best-practices)

Markdown applications don’t agree on how to handle different delimiters in the same list. For compatibility, don’t mix and match delimiters in the same list — pick one and stick with it.

|✅  Do this|❌  Don't do this|
|---|---|
|`- First item   - Second item   - Third item   - Fourth item`|`+ First item   * Second item   - Third item   + Fourth item`|

### Adding Elements in Lists[](https://markdownguide.offshoot.io/basic-syntax/#adding-elements-in-lists)

To add another element in a list while preserving the continuity of the list, indent the element four spaces or one tab, as shown in the following examples.

 **Tip:** If things don't appear the way you expect, double check that you've indented the elements in the list four spaces or one tab.

#### Paragraphs[](https://markdownguide.offshoot.io/basic-syntax/#paragraphs)

```
* This is the first list item.
* Here's the second list item.

    I need to add another paragraph below the second list item.

* And here's the third list item.
```

The rendered output looks like this:

- This is the first list item.
- Here’s the second list item.
    
    I need to add another paragraph below the second list item.
    
- And here’s the third list item.

#### Blockquotes[](https://markdownguide.offshoot.io/basic-syntax/#blockquotes)

```
* This is the first list item.
* Here's the second list item.

    > A blockquote would look great below the second list item.

* And here's the third list item.
```

The rendered output looks like this:

- This is the first list item.
- Here’s the second list item.
    
    > A blockquote would look great below the second list item.
    
- And here’s the third list item.

#### Code Blocks[](https://markdownguide.offshoot.io/basic-syntax/#code-blocks-1)

[Code blocks](https://markdownguide.offshoot.io/basic-syntax/#code-blocks) are normally indented four spaces or one tab. When they’re in a list, indent them eight spaces or two tabs.

```
1. Open the file.
2. Find the following code block on line 21:

        <html>
          <head>
            <title>Test</title>
          </head>

3. Update the title to match the name of your website.
```

The rendered output looks like this:

1. Open the file.
2. Find the following code block on line 21:
    
    ```
     <html>
       <head>
         <title>Test</title>
       </head>
    ```
    
3. Update the title to match the name of your website.

#### Images[](https://markdownguide.offshoot.io/basic-syntax/#images)

```
1. Open the file containing the Linux mascot.
2. Marvel at its beauty.

    ![Tux, the Linux mascot](/assets/images/tux.png)

3. Close the file.
```

The rendered output looks like this:

1. Open the file containing the Linux mascot.
2. Marvel at its beauty.
    
    ![Tux, the Linux mascot](https://mdg.imgix.net/assets/images/tux.png)
    
3. Close the file.

#### Lists[](https://markdownguide.offshoot.io/basic-syntax/#lists)

You can nest an unordered list in an ordered list, or vice versa.

```
1. First item
2. Second item
3. Third item
    - Indented item
    - Indented item
4. Fourth item
```

The rendered output looks like this:

1. First item
2. Second item
3. Third item
    - Indented item
    - Indented item
4. Fourth item

## Code[](https://markdownguide.offshoot.io/basic-syntax/#code)

To denote a word or phrase as code, enclose it in backticks (`` ` ``).

|Markdown|HTML|Rendered Output|
|---|---|---|
|``At the command prompt, type `nano`.``|`At the command prompt, type <code>nano</code>.`|At the command prompt, type `nano`.|

### Escaping Backticks[](https://markdownguide.offshoot.io/basic-syntax/#escaping-backticks)

If the word or phrase you want to denote as code includes one or more backticks, you can escape it by enclosing the word or phrase in double backticks (` `` `).

|Markdown|HTML|Rendered Output|
|---|---|---|
|``` ``Use `code` in your Markdown file.`` ```|``<code>Use `code` in your Markdown file.</code>``|``Use `code` in your Markdown file.``|

### Code Blocks[](https://markdownguide.offshoot.io/basic-syntax/#code-blocks)

To create code blocks, indent every line of the block by at least four spaces or one tab.

```
    <html>
      <head>
      </head>
    </html>
```

The rendered output looks like this:

```
<html>
  <head>
  </head>
</html>
```

 **Note:** To create code blocks without indenting lines, use [fenced code blocks](https://markdownguide.offshoot.io/extended-syntax/#fenced-code-blocks).

## Horizontal Rules[](https://markdownguide.offshoot.io/basic-syntax/#horizontal-rules)

To create a horizontal rule, use three or more asterisks (`***`), dashes (`---`), or underscores (`___`) on a line by themselves.

```
***

---

_________________
```

The rendered output of all three looks identical:

---

### Horizontal Rule Best Practices[](https://markdownguide.offshoot.io/basic-syntax/#horizontal-rule-best-practices)

For compatibility, put blank lines before and after horizontal rules.

|✅  Do this|❌  Don't do this|
|---|---|
|`Try to put a blank line before...      ---      ...and after a horizontal rule.`|`Without blank lines, this would be a heading.   ---   Don't do this!`|

## Links[](https://markdownguide.offshoot.io/basic-syntax/#links)

To create a link, enclose the link text in brackets (e.g., `[Duck Duck Go]`) and then follow it immediately with the URL in parentheses (e.g., `(https://duckduckgo.com)`).

```
My favorite search engine is [Duck Duck Go](https://duckduckgo.com).
```

The rendered output looks like this:

My favorite search engine is [Duck Duck Go](https://duckduckgo.com/).

 **Note:** To link to an element on the same page, see [linking to heading IDs](https://markdownguide.offshoot.io/extended-syntax/#linking-to-heading-ids). To create a link that opens in a new tab or window, see the section on [link targets](https://markdownguide.offshoot.io/hacks/#link-targets).

### Adding Titles[](https://markdownguide.offshoot.io/basic-syntax/#adding-titles)

You can optionally add a title for a link. This will appear as a tooltip when the user hovers over the link. To add a title, enclose it in quotation marks after the URL.

```
My favorite search engine is [Duck Duck Go](https://duckduckgo.com "The best search engine for privacy").
```

The rendered output looks like this:

My favorite search engine is [Duck Duck Go](https://duckduckgo.com/ "The best search engine for privacy").

### URLs and Email Addresses[](https://markdownguide.offshoot.io/basic-syntax/#urls-and-email-addresses)

To quickly turn a URL or email address into a link, enclose it in angle brackets.

```
<https://www.markdownguide.org>
<fake@example.com>
```

The rendered output looks like this:

[https://www.markdownguide.org](https://www.markdownguide.org/)  
[fake@example.com](mailto:fake@example.com)

### Formatting Links[](https://markdownguide.offshoot.io/basic-syntax/#formatting-links)

To [emphasize](https://markdownguide.offshoot.io/basic-syntax/#emphasis) links, add asterisks before and after the brackets and parentheses. To denote links as [code](https://markdownguide.offshoot.io/basic-syntax/#code), add backticks in the brackets.

```
I love supporting the **[EFF](https://eff.org)**.
This is the *[Markdown Guide](https://www.markdownguide.org)*.
See the section on [`code`](#code).
```

The rendered output looks like this:

I love supporting the **[EFF](https://eff.org/)**.  
This is the _[Markdown Guide](https://www.markdownguide.org/)_.  
See the section on [`code`](https://markdownguide.offshoot.io/basic-syntax/#code).

### Reference-style Links[](https://markdownguide.offshoot.io/basic-syntax/#reference-style-links)

Reference-style links are a special kind of link that make URLs easier to display and read in Markdown. Reference-style links are constructed in two parts: the part you keep inline with your text and the part you store somewhere else in the file to keep the text easy to read.

#### Formatting the First Part of the Link[](https://markdownguide.offshoot.io/basic-syntax/#formatting-the-first-part-of-the-link)

The first part of a reference-style link is formatted with two sets of brackets. The first set of brackets surrounds the text that should appear linked. The second set of brackets displays a label used to point to the link you’re storing elsewhere in your document.

Although not required, you can include a space between the first and second set of brackets. The label in the second set of brackets is not case sensitive and can include letters, numbers, spaces, or punctuation.

This means the following example formats are roughly equivalent for the first part of the link:

- `[hobbit-hole][1]`
- `[hobbit-hole] [1]`

#### Formatting the Second Part of the Link[](https://markdownguide.offshoot.io/basic-syntax/#formatting-the-second-part-of-the-link)

The second part of a reference-style link is formatted with the following attributes:

1. The label, in brackets, followed immediately by a colon and at least one space (e.g., `[label]:` ).
2. The URL for the link, which you can optionally enclose in angle brackets.
3. The optional title for the link, which you can enclose in double quotes, single quotes, or parentheses.

This means the following example formats are all roughly equivalent for the second part of the link:

- `[1]: https://en.wikipedia.org/wiki/Hobbit#Lifestyle`
- `[1]: https://en.wikipedia.org/wiki/Hobbit#Lifestyle "Hobbit lifestyles"`
- `[1]: https://en.wikipedia.org/wiki/Hobbit#Lifestyle 'Hobbit lifestyles'`
- `[1]: https://en.wikipedia.org/wiki/Hobbit#Lifestyle (Hobbit lifestyles)`
- `[1]: <https://en.wikipedia.org/wiki/Hobbit#Lifestyle> "Hobbit lifestyles"`
- `[1]: <https://en.wikipedia.org/wiki/Hobbit#Lifestyle> 'Hobbit lifestyles'`
- `[1]: <https://en.wikipedia.org/wiki/Hobbit#Lifestyle> (Hobbit lifestyles)`

You can place this second part of the link anywhere in your Markdown document. Some people place them immediately after the paragraph in which they appear while other people place them at the end of the document (like endnotes or footnotes).

#### An Example Putting the Parts Together[](https://markdownguide.offshoot.io/basic-syntax/#an-example-putting-the-parts-together)

Say you add a URL as a [standard URL link](https://markdownguide.offshoot.io/basic-syntax/#links) to a paragraph and it looks like this in Markdown:

```
In a hole in the ground there lived a hobbit. Not a nasty, dirty, wet hole, filled with the ends
of worms and an oozy smell, nor yet a dry, bare, sandy hole with nothing in it to sit down on or to
eat: it was a [hobbit-hole](https://en.wikipedia.org/wiki/Hobbit#Lifestyle "Hobbit lifestyles"), and that means comfort.
```

Though it may point to interesting additional information, the URL as displayed really doesn’t add much to the existing raw text other than making it harder to read. To fix that, you could format the URL like this instead:

```
In a hole in the ground there lived a hobbit. Not a nasty, dirty, wet hole, filled with the ends
of worms and an oozy smell, nor yet a dry, bare, sandy hole with nothing in it to sit down on or to
eat: it was a [hobbit-hole][1], and that means comfort.

[1]: <https://en.wikipedia.org/wiki/Hobbit#Lifestyle> "Hobbit lifestyles"
```

In both instances above, the rendered output would be identical:

> In a hole in the ground there lived a hobbit. Not a nasty, dirty, wet hole, filled with the ends of worms and an oozy smell, nor yet a dry, bare, sandy hole with nothing in it to sit down on or to eat: it was a [hobbit-hole](https://en.wikipedia.org/wiki/Hobbit#Lifestyle "Hobbit lifestyles"), and that means comfort.

and the HTML for the link would be:

```
<a href="https://en.wikipedia.org/wiki/Hobbit#Lifestyle" title="Hobbit lifestyles">hobbit-hole</a>
```

### Link Best Practices[](https://markdownguide.offshoot.io/basic-syntax/#link-best-practices)

Markdown applications don’t agree on how to handle spaces in the middle of a URL. For compatibility, try to URL encode any spaces with `%20`. Alternatively, if your Markdown application [supports HTML](https://markdownguide.offshoot.io/basic-syntax/#html), you could use the `a` HTML tag.

|✅  Do this|❌  Don't do this|
|---|---|
|`[link](https://www.example.com/my%20great%20page)      <a href="https://www.example.com/my great page">link</a>      `|`[link](https://www.example.com/my great page)      `|

Parentheses in the middle of a URL can also be problematic. For compatibility, try to URL encode the opening parenthesis (`(`) with `%28` and the closing parenthesis (`)`) with `%29`. Alternatively, if your Markdown application [supports HTML](https://markdownguide.offshoot.io/basic-syntax/#html), you could use the `a` HTML tag.

|✅  Do this|❌  Don't do this|
|---|---|
|`[a novel](https://en.wikipedia.org/wiki/The_Milagro_Beanfield_War_%28novel%29)      <a href="https://en.wikipedia.org/wiki/The_Milagro_Beanfield_War_(novel)">a novel</a>      `|`[a novel](https://en.wikipedia.org/wiki/The_Milagro_Beanfield_War_(novel))`|

## Images[](https://markdownguide.offshoot.io/basic-syntax/#images-1)

To add an image, add an exclamation mark (`!`), followed by alt text in brackets, and the path or URL to the image asset in parentheses. You can optionally add a title in quotation marks after the path or URL.

```
![The San Juan Mountains are beautiful!](/assets/images/san-juan-mountains.jpg "San Juan Mountains")
```

The rendered output looks like this:

![The San Juan Mountains are beautiful!](https://mdg.imgix.net/assets/images/san-juan-mountains.jpg "San Juan Mountains")

 **Note:** To resize an image, see the section on [image size](https://markdownguide.offshoot.io/hacks/#image-size). To add a caption, see the section on [image captions](https://markdownguide.offshoot.io/hacks/#image-captions).

### Linking Images[](https://markdownguide.offshoot.io/basic-syntax/#linking-images)

To add a link to an image, enclose the Markdown for the image in brackets, and then add the link in parentheses.

```
[![An old rock in the desert](/assets/images/shiprock.jpg "Shiprock, New Mexico by Beau Rogers")](https://www.flickr.com/photos/beaurogers/31833779864/in/photolist-Qv3rFw-34mt9F-a9Cmfy-5Ha3Zi-9msKdv-o3hgjr-hWpUte-4WMsJ1-KUQ8N-deshUb-vssBD-6CQci6-8AFCiD-zsJWT-nNfsgB-dPDwZJ-bn9JGn-5HtSXY-6CUhAL-a4UTXB-ugPum-KUPSo-fBLNm-6CUmpy-4WMsc9-8a7D3T-83KJev-6CQ2bK-nNusHJ-a78rQH-nw3NvT-7aq2qf-8wwBso-3nNceh-ugSKP-4mh4kh-bbeeqH-a7biME-q3PtTf-brFpgb-cg38zw-bXMZc-nJPELD-f58Lmo-bXMYG-bz8AAi-bxNtNT-bXMYi-bXMY6-bXMYv)
```

The rendered output looks like this:

[![An old rock in the desert](https://mdg.imgix.net/assets/images/shiprock.jpg "Shiprock, New Mexico by Beau Rogers")](https://www.flickr.com/photos/beaurogers/31833779864/in/photolist-Qv3rFw-34mt9F-a9Cmfy-5Ha3Zi-9msKdv-o3hgjr-hWpUte-4WMsJ1-KUQ8N-deshUb-vssBD-6CQci6-8AFCiD-zsJWT-nNfsgB-dPDwZJ-bn9JGn-5HtSXY-6CUhAL-a4UTXB-ugPum-KUPSo-fBLNm-6CUmpy-4WMsc9-8a7D3T-83KJev-6CQ2bK-nNusHJ-a78rQH-nw3NvT-7aq2qf-8wwBso-3nNceh-ugSKP-4mh4kh-bbeeqH-a7biME-q3PtTf-brFpgb-cg38zw-bXMZc-nJPELD-f58Lmo-bXMYG-bz8AAi-bxNtNT-bXMYi-bXMY6-bXMYv)

## Escaping Characters[](https://markdownguide.offshoot.io/basic-syntax/#escaping-characters)

To display a literal character that would otherwise be used to format text in a Markdown document, add a backslash (`\`) in front of the character.

```
\* Without the backslash, this would be a bullet in an unordered list.
```

The rendered output looks like this:

* Without the backslash, this would be a bullet in an unordered list.

### Characters You Can Escape[](https://markdownguide.offshoot.io/basic-syntax/#characters-you-can-escape)

You can use a backslash to escape the following characters.

|Character|Name|
|---|---|
|\|backslash|
|`|backtick (see also [escaping backticks in code](https://markdownguide.offshoot.io/basic-syntax/#escaping-backticks))|
|*|asterisk|
|_|underscore|
|{ }|curly braces|
|[ ]|brackets|
|< >|angle brackets|
|( )|parentheses|
|#|pound sign|
|+|plus sign|
|-|minus sign (hyphen)|
|.|dot|
|!|exclamation mark|
|\||pipe (see also [escaping pipe in tables](https://markdownguide.offshoot.io/extended-syntax/#escaping-pipe-characters-in-tables))|

## HTML[](https://markdownguide.offshoot.io/basic-syntax/#html)

Many Markdown applications allow you to use HTML tags in Markdown-formatted text. This is helpful if you prefer certain HTML tags to Markdown syntax. For example, some people find it easier to use HTML tags for images. Using HTML is also helpful when you need to change the attributes of an element, like specifying the [color of text](https://markdownguide.offshoot.io/hacks/#color) or changing the width of an image.

To use HTML, place the tags in the text of your Markdown-formatted file.

```
This **word** is bold. This <em>word</em> is italic.
```

The rendered output looks like this:

This **word** is bold. This _word_ is italic.

### HTML Best Practices[](https://markdownguide.offshoot.io/basic-syntax/#html-best-practices)

For security reasons, not all Markdown applications support HTML in Markdown documents. When in doubt, check your Markdown application’s documentation. Some applications support only a subset of HTML tags.

Use blank lines to separate block-level HTML elements like `<div>`, `<table>`, `<pre>`, and `<p>` from the surrounding content. Try not to indent the tags with tabs or spaces — that can interfere with the formatting.

You can’t use Markdown syntax inside block-level HTML tags. For example, `<p>italic and **bold**</p>` won’t work