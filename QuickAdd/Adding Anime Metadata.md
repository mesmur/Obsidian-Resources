# Retrieve Metadata from API and Create Obsidian Notes

This script will allow you to retrieve anime and comic metadata using the wonderful [Jikan](https://docs.api.jikan.moe/) API for MyAnimeList (MAL).

## Installation

You will need to have the [QuickAdd](https://github.com/chhoumann/quickadd) plugin for Obsidian installed. Grab the scripts, either the [Anime Script](https://gist.github.com/MESMUR/5fd905514baea9c506099774998d3158), or the [Comic Script](https://gist.github.com/MESMUR/388fed02961d58a67a8333d4d3b5a6ab).

1. Save the script inside your vault, for example, as `animeAdd.js` make sure it is saved with the `js` extension.
2. Create a new template in your templates folder. I've provided mine below.
3. Go to the QuickAdd plugin and create a new Macro under `Manage Macros`
4. Give it a name! and add the `js` file to the macro as the first step.
5. Add the template you created as the second step, and fill in relevant information. Use the `{{VALUE:fileName}}` field for the filename of the template you will be creating.
6. Go to the QuickAdd menu and create a new macro choice, e.g., `Add Anime`, and attach the macro you've created to it.

You can now run this macro. Entering an ID from MAL will retrieve the metadata directly, if you instead enter a search term, it will retrieve a list of matches out of which you can select the one you want.

For another set of instructions + demo, check out the Movie Script that inspired this [here](https://github.com/chhoumann/quickadd/blob/master/docs/Examples/Macro_MovieAndSeriesScript.md). It's the same flow (without the need for an API key!)

## Templates

A heads up that I use the templater and the banner plugins, which impact the `<% %>` code block, and `banner:` metadata respectively.

### Anime

```md

---
Alias: [{{VALUE:titleAll}}]
Season:
Episodes: {{VALUE:episodes}}
Aired: {{VALUE:aired}}
Studio: [{{VALUE:studio}}]
Rating: /10
Genre: [{{VALUE:genres}}]
Date-Completed:
banner: {{VALUE:image_big}}

---

# {{VALUE:title}}

#entertainment/anime

[MAL Link]({{VALUE:url}})
Date:: [[<%tp.date.now("YYYY-MM-DD")%>]]

![Poster]({{VALUE:image_sml}})

## Synopsis

{{VALUE:plot}}

## Review

## Related
```

### Comics

```md
---
Alias: [{{VALUE:titleAll}}]
Author: [{{VALUE:author}}]
Type: {{VALUE:type}}
Rating: /10
Genre: [{{VALUE:genres}}]
Progress:
Date-Completed:
banner: {{VALUE:image_big}}

---

# <% tp.file.title %>

#entertainment/manga

[Link]({{VALUE:url}})
Date:: [[<%tp.date.now("YYYY-MM-DD")%>]]

![Cover]({{VALUE:image_sml}})

## Synopsis

{{VALUE:plot}}

## Thoughts

## Review
```


## Acknowledgement

These scripts and the inspiration from them are largely adapted from: [Christian's Movie Script](https://github.com/chhoumann/quickadd/blob/master/docs/Examples/Macro_MovieAndSeriesScript.md). I've re-used most of the script and adapted it to a different use case!