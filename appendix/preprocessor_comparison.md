# Comparing CSS Preprocessors
Many novice web developers have trouble understanding the relationship between different CSS preprocessors. This is understandable because on the one hand all these tools are quite similar, and they are also all fairly high quality. The selection of which preprocessor you use will have more to do with how it fits into your overall development patterns than any objective measure of one being a lot better than the others.

Having said that, there are differences between the preprocessors, and those are worth noting. Let's begin looking at preprocessors from the highest level: SASS vs. LESS.

## SASS
SASS is the "original" CSS preprocessor. It gained a lot of interest when it debuted and it has maintained a high level of popularity. SASS was initially written as part of another Ruby Gem, and then the Compass project became the preferred Ruby Gem that developers use to process SASS.

Since SASS has been popular outside of the Ruby development community, many other preprocessors that handle SASS have been created. The one this book uses, and one of the more popular, is called `node-sass`. 

## LESS
LESS is an alternate take on a CSS preprocessor language, but its development was influenced by the existence of SASS. It was, initially, the only pure-Javascript solution for preprocessing CSS. It generally works a lot like SASS, with some differences that, in some cases, can be key. 

## SASS vs. LESS
This debate has raged for awhile and I'm not going to settle it here. If you go look at a Google Search for the term "sass vs. less" you'll find [plenty of opinions](https://www.google.com/webhp?sourceid=chrome-instant&ion=1&espv=2&es_th=1&ie=UTF-8#es_th=1&q=sass%20vs%20less). 

But the prevailing trend these days seems to be towards SASS. More robust non-Ruby support (meaning, there are SASS processors written in many languages for many platforms) and continuing high adoption rates among developers really give it an edge.

## What's really important?
The specific choice of preprocessor, at least between SASS and LESS, is not the most important aspect of implementing a preprocessor into your work. Unless you are working with a very unique set of cases, you will not run into a problem with either preprocessor that will make it impossible to make the styles you want. 

You should focus on the things that are always most important when making choices about what components to use in projects, including:

* Is this a technology in use by others? Or will I be alone using it?
* Is this a technology my team knows and/or is enthusiastic about adopting?
* Can I plug this technology into the systems that make all the rest of my work easier (continuous integration, testing, preview, etc.)?
* Will using this technology impact my long-term maintenance in a negative way?

Since properly organizing styles, collaborating with colleagues, and delivering working code on a consistent rhythm are often the most important things to consider when building styles, it's much better to focus on those things and let your preprocessor tools get out of the way.