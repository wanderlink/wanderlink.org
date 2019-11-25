# What is a wanderlink?

A wanderlink is intended to allow someone to take "the scenic route" when following a link from site-a to site-b on the web. When clicking a wanderlink to say, example.org, one will be taken to an arbitrary amount of targets before ariving at the example.org destination. A simple software mechanism, such as a desktop application or containing website (for demo purposes), would provide simple navigation controls for the sequence.

# Inspirations and History
The internet is an excellent tool for surface level communication but offers less opportunities for deeper understanding. We need more tools that encourage the former. That is to share in a way that is closer to [groking](https://en.wikipedia.org/wiki/Grok) then understanding. There is of course room for misunderstanding, but is also the case with direct linking or even face to face communication. The hope is to add perspective not perfection.

Why will a chained set of hyperlinks do this? Imagine you are traveling with a friend who you promised a short tour of your home town for the first time. You have the option of taking the shortest route, likely a major highway, to your destination or you can take a few of the "backroads" that you often enjoyed in your youth. The backroads will certainly take longer but will likely provide a better understanding of the person you have become. Can we do something similar online? When saying "Check out my new website" someone could wanderlink "website" to the following chained example inspiration1->inspiration2->context1->website.

# (Draft) Spec
A wanderlink is an [anchor tag](https://www.w3.org/MarkUp/1995-archive/Elements/A.html) with an extended, unnoficial, syntax to support wander targets in a manner that is backwards compatible with the existing spec.

## Proposed syntax
In all of these cases if the browser supports wanderlinks, clicking this anchor tag would send the user to link1, with navigation controls to go to link2. Link2 is the end of the wanderlink. The fallback href is only used if the browser does not support wanderlinks.

### Approach 1: Repeating "wander" attribute
Example:
`<a href="https://example.org/fallback" wander="https://example.org/link1" wander="https://example.org/link2">Check it out</a>`

Noted con: There is [existing precedent against this approach](https://www.w3.org/TR/1999/REC-html401-19991224/struct/links.html#h-12.2.3) under the "ILLEGAL EXAMPLE" section.

### Approach 2: Repeating numbered "wander" attribute
Example:
`<a href="https://example.org/fallback" wander="https://example.org/link1" wander1="https://example.org/link2">Check it out</a>`

Noted con: This puts some amount of sorting work on the user and, when errors inevitably happen, the browser will probably automatically correct common errors by simply taking definition order. As such, this approach seems to be mainly to avoid the duplicate attribute taboo by only costing, not adding, user value. 

### Approach 3: Nested "wander" children
Example:
```
<a href="https://example.org/fallback">
  Check it out
  <wander href="https://example.org/link1"/>
  <wander href="https://example.org/link2"/>
</a>
```

Noted con: This syntax is less consistent with the existing spec, messy to parse and requires more user effort to define.
