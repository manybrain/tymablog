---
title: A Google Interviewing Story
description: That time I interviewed at Google
date: 2020-01-10
categories:
  - "Software Engineering"
tags:
  - "Software Engineering"
  - "Interviewing"
  - "Guy in the leather pants"
---

A few years ago I was entering the Silicon Valley job market and at that time looking for senior engineering positions. A good rule of thumb about interviewing if you haven't done it in awhile is to at least somewhat accept that you'll probably make a few mistakes on your first few tries. Simply, don't go for your dream job first. There are a million nuances to interviewing that you've forgotten, and a few up-front, not-so-important interviews first will educate (or re-educate) about them.
<!--more-->

One of the first places I interviewed was a company called gofish.com. As far as I know - gofish is an utterly different company now than when I interviewed there. I'm almost sure that everyone I met there no longer works there, so the actual company isn't terribly relevant to the story. But the interviewer is. My technical interview there was with a guy named Guy.

Guy wore leather pants. Its a well-known fact that interviewers in leather pants are "extra" scary. And Guy was by no means a let down. He was also a technical crack-shot. And he was a technical crack-shot in leather pants - seriously, I didn't have a chance.

One question he asked me I'll never forget. In truth, its a pretty innocuous question - but it's also pretty standard fare for silicon valley interviewing questions at that time.

Here it is:

Say you have one string of alphabetic characters, and say you have another, guaranteed smaller string of alphabetic characters. Algorithmically speaking, what's the fastest way to find out if all the characters in the smaller string are in the larger string?

For example, if the two strings were:

```
String 1: ABCDEFGHLMNOPQRS
String 2: DCGSRQPOM
```




You'd get true as every character in string2 is in string1. If the two strings were:


String 1: ABCDEFGHLMNOPQRS
String 2: DCGSRQPOZ


you'd get false as Z isn't in the first string.

When he asked the question I literally jumped to my feet. Finally, a question I could answer with some confidence. (Note my answer to him was solely considering the worst cases as there are plenty enough nuances there for an interview question).

The naive way to do this operation would be to iterate over the 2nd string once for each character in the 1st string. That'd be O(n*m) in algorithm parlance where n is the length of string1 and m is the length of string2. Given the strings in our above example, thats 16*8 = 128 operations in the worst case.

A slightly better way would be to sort each string and then do a stepwise iteration of both sorted strings simultaneously. Sorting both strings would be (in the general case) O(m log m) + O(n log n) and the linear scan after that is O(m+n). Again for our strings above, that would be 16*4 + 8*3 = 88 plus a linear scan of both strings at a cost of 16 + 8 = 24. Thats 88 + 24 = 112 total operations. Slightly better. (As the size of the strings grow, this method would start to look better and better)

Finally, I told him the best method would simply be O(n+m). That is, iterate through the first string and put each character in a hashtable (cost of O(n) or 16). Then iterate the 2nd string and query the hashtable for each character you find. If its not found, you don't have a match. That would cost 8 operations - so both operations together is a total of 24 operations. Not bad and way better than the other solutions.

Guy wasn't impressed. He showed it by rustling his leather pants a bit. "Can you do better?" he asked.

What the heck? What did this guy want? I looked at the whiteboard and turned back to him. "No, O(n+m) is the best you have - I mean, you can't do this without looking at each character at least once - and this solution is looking at each character precisely once". The more I thought about it, the more I knew I was right.

He stepped up to the whiteboard, "What if - given that we have a limited range of possible characters - I assigned each character of the alphabet to a prime number starting with 2 and going up from there. So A would be 2, and B would be 3, and C would be 5, etc. And then I went through the first string and 'multiplied' each character's prime number together. You'd end up with some big number right? And then - what if I iterated through the 2nd string and 'divided' by every character in there. If any division gave a remainder - you knew you didn't have a match. If there was no remainders through the whole process, you knew you had a subset. Would that work?"

Every once in awhile - someone thinks so fantastically far out of your box you really need a minute to catch up. And now that he was standing, his leather pants weren't helping with this.

Now mind you - Guy's solution (and of course, needless to say I doubt Guy was the first to ever think of this) was algorithmically speaking no better than mine. Even practically, you'd still probably use mine as it was more general and didn't make you deal with messy big integers. But on the "clever scale", Guy's was way, way, (way) more fun.

I didn't get the job. Or I think they offered me some trial position or something that I refused, but it didn't matter. I was on to bigger and better things.

Next, I interviewed at become.com. After a phone interview with the CTO he sent me a "programming assignment". It was a bit over the top - but in retrospect, worth the 3 days it took me to complete. I got an interview and a job offer - but the biggest value was what the programming assignment forced me to go out and learn. I had to build a web-crawler, a spellchecker/fixer, and a few other things. Good stuff. In the end however, I turned down the offer.

Finally, I had an interview at Google. I've written before that the Google interviewing process does tend to live up to the hype. Its long - its rigorous and in all honesty, pretty darn fair. They do as best they can to learn about you and your abilities in an interview setting. By no means is that an exact science, but I'm convinced they give it a good try.

My 4th technical interview at Google was with a woman engineer that honestly seemed a bit bored of interviewing. I had done well in all my previous interviews there and was feeling pretty good about my chances. I was confident that if I did nothing ridiculously silly - I'd get the job.

She asked me a few softball questions about sorting or design, I'm not sure. But towards the end of our 45 minutes she told me "I have one more question. Let's say you have a string of alphabetic characters of some length. And you have another, shorter string of characters. How would you go about finding if all the characters in the smaller string are in the larger string?"

Woah. Deja-Guy.

Now, I could have probably stopped the interview right there. I could have said "Ahee! I just got this question a few weeks ago!" which was true. But when I was asked it a few weeks previous - I did get it right. It truly was a question I knew the answer to. Almost as if Guy had been one of my study partners for this very interview. And heck, people study interview questions on the internet all the time - by me non-chalantly answering the question I wouldn't be "lying" in any way. I did know the answer on my own!

Now you might think, that in the instant after her asking, and before the moment of time that I began speaking that the entire last paragraph sequenced through my thought process rationalizing that I was, indeed, morally in the right to calmly answer the question and take credit for the answer. But sadly, that wasn't the case. Metaphorically, it was more like she asked the question and my brain immediately raised its hand and started shouting "Me! ooh! ooh! ooh me! I know! ask me!" My brain kept trying to wrestle mouth-control away from me (which happens plenty) but only by stalwart resolve was I able to retain composure.

So I answered. Calmly. With almost unearthly grace and poise. And with a purposeful demeanor - with, I think, a confidence that only someone with complete and encyclopedic knowledge of this timeless and subtle problem would hold.

I breezed over the naive solution as if it were unworthy. I mentioned the sorting solution as if it were wearing a red-shirt on an early episode of Star Trek. And finally, nonchalantly, almost as if I had invented all things good and algorithmically efficient, mentioned the O(n+m) linear solution.

Now mind you - despite my apparent poise - the entire time I was fighting my brain who, internally, was screaming at me -- "TELL HER THE PRIME NUMBER SOLUTION YOU DIMWIT !"

I ignored his pitiful pleas.

As I finished the linear solution explanation, her head dutifully sank with complete non-surprise and she started writing in her notes. She had probably asked that question a hundred times before and I'd guess most people got it right. She probably wrote "yep. boring interview. got boring string question right. no surprise. boring guy but probable hire"

I waited a moment. I let the suspense build as long as possible. I am truly convinced that even a moment longer would have resulted in my brain throwing itself fully into an embolism resulting in me blurting out unintelligible mis-facts about prime numbers.

I broke the calm. "You know, there is another, somewhat cleverer solution"

She lethargically looked up with only a glimmer of hope.

"Given that our range of characters is limited. We could assign each character to a prime number starting at 2. After that we could 'multiply' each character of the large string and then 'divide' by each character of the small string. If the division operation left no remainder, we'd know we have a subset."

I'm guessing that at this point, she looked pretty much as I did when Guy had said the same thing to me. General loss of composure, one pupil was dilated, slight spitting while talking.

After a moment, she blurted "But.. wait that wouldn'... yes it would! But how.. what if.. wow. wow. that works! Neat!"

I sniffed triumphantly. I wrote down "She gave me a 'Neat!'" in my interviewing notes. I'm pretty sure I was getting the job before that question, but it was pretty clear that I was in for sure now. What's more, I'm pretty confident that I (or more precisely, Guy) had just made her day.

I spent 3 years working at Google and had a great time. I quit in 2008 to CTO a new startup and have subsequently started another of my own after that. About a year ago I randomly met Guy at a start-up party who had no idea who I was but when I recounted this story he nearly peed his leather pants laughing.

Again, if there is a moral here - it's to never chase your dream job before you chase a few you're willing to fail at. Apart from the interviewing experience you'll gain, you never know who might just get you ready for that big interview. In fact, that rule just might work for a lot of things in life.

And seriously, if you get the chance and you're looking to hire a crackshot engineer - you could do far worse than hiring Guy. That dude knows things.




The main purpose of this article is to make sure that all basic HTML Elements are decorated with CSS so as to not miss any possible elements when creating new themes for Hugo.
<!--more-->

## Headings

Let's start with all possible headings. The HTML `<h1>`—`<h6>` elements represent six levels of section headings. `<h1>` is the highest section level and `<h6>` is the lowest.

# Heading 1


The main purpose of this article is to make sure that all basic HTML Elements are decorated with CSS so as to not miss any possible elements when creating new themes for Hugo.
<!--more-->

## Headings

Let's start with all possible headings. The HTML `<h1>`—`<h6>` elements represent six levels of section headings. `<h1>` is the highest section level and `<h6>` is the lowest.

# Heading 1
## Heading 2
### Heading 3
#### Heading 4
##### Heading 5
###### Heading 6

***

## Paragraph

According to the [HTML5 specification](https://www.w3.org/TR/html5/dom.html#elements) by [W3C](https://www.w3.org/), **HTML documents consist of a tree of elements and text**. Each element is denoted in the source by a [start tag](https://www.w3.org/TR/html5/syntax.html#syntax-start-tags), such as `<body>`, and an [end tag](https://www.w3.org/TR/html5/syntax.html#syntax-end-tags), such as `</body>`. (*Certain start tags and end tags can in certain cases be omitted and are implied by other tags.*)

Elements can have attributes, which control how the elements work. For example, hyperlink are formed using the `a` element and its `href` attribute.

## List Types

### Ordered List

1. First item
2. Second item
3. Third item

### Unordered List

* List item
* Another item
* And another item

### Nested list

<ul>
  <li>First item</li>
  <li>Second item
    <ul>
      <li>Second item First subitem</li>
      <li>Second item second subitem
        <ul>
          <li>Second item Second subitem First sub-subitem</li>
          <li>Second item Second subitem Second sub-subitem</li>
          <li>Second item Second subitem Third sub-subitem</li>
        </ul>
      </li>
      <li>Second item Third subitem
        <ol>
          <li>Second item Third subitem First sub-subitem</li>
          <li>Second item Third subitem Second sub-subitem</li>
          <li>Second item Third subitem Third sub-subitem</li>
        </ol>
    </ul>
  </li>
  <li>Third item</li>
</ul>

### Definition List

HTML also supports definition lists.

<dl>
  <dt>Blanco tequila</dt>
  <dd>The purest form of the blue agave spirit...</dd>
  <dt>Reposado tequila</dt>
  <dd>Typically aged in wooden barrels for between two and eleven months...</dd>
</dl>

## Blockquotes

The blockquote element represents content that is quoted from another source, optionally with a citation which must be within a `footer` or `cite` element, and optionally with in-line changes such as annotations and abbreviations.

> Quoted text.
> This line is part of the same quote.
> Also you can *put* **Markdown** into a blockquote.

Blockquote with a citation.

<blockquote>
  <p>My goal wasn't to make a ton of money. It was to build good computers. I only started the company when I realized I could be an engineer forever.</p>
  <footer>— <cite>Steve Wozniak</cite></footer>
</blockquote>

According to Mozilla's website, <q cite="https://www.mozilla.org/en-US/about/history/details/">Firefox 1.0 was released in 2004 and became a big success.</q>

## Tables

Tables aren't part of the core Markdown spec, but Hugo supports them.

| ID  | Make      | Model   | Year |
| --- | --------- | ------- | ---- |
| 1   | Honda     | Accord  | 2009 |
| 2   | Toyota    | Camry   | 2012 |
| 3   | Hyundai   | Elantra | 2010 |

Colons can be used to align columns.

| Tables      | Are           | Cool         |
|:----------- |:-------------:| ------------:|
| align: left | align: center | align: right |
| align: left | align: center | align: right |
| align: left | align: center | align: right |

You can also use inline Markdown.

| Inline     | Markdown  | In                | Table      |
| ---------- | --------- | ----------------- | ---------- |
| *italics*  | **bold**  | ~~strikethrough~~ | `code`     |

## Code

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Example HTML5 Document</title>
</head>
<body>
  <p>Test</p>
</body>
</html>
```

{{< highlight html >}}
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Example HTML5 Document</title>
</head>
<body>
  <p>Test</p>
</body>
</html>
{{< /highlight >}}

## Other stuff — abbr, sub, sup, kbd, etc.

<abbr title="Graphics Interchange Format">GIF</abbr> is a bitmap image format.

H<sub>2</sub>O

C<sub>6</sub>H<sub>12</sub>O<sub>6</sub>

X<sup>n</sup> + Y<sup>n</sup> = Z<sup>n</sup>

Press <kbd>X</kbd> to win. Or press <kbd><kbd>CTRL</kbd>+<kbd>ALT</kbd>+<kbd>F</kbd></kbd> to show FPS counter.

<mark>As a unit of information in information theory, the bit has alternatively been called a shannon</mark>, named after Claude Shannon, the founder of field of information theory.
