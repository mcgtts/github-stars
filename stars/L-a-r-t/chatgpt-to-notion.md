---
project: chatgpt-to-notion
stars: 364
description: |-
    ChatGPT to Notion brings the cleverness of ChatGPT right into your Notion workspace!
url: https://github.com/L-a-r-t/chatgpt-to-notion
---

# Chat to Notion

[Chat to Notion](https://chrome.google.com/webstore/detail/chatgpt-to-notion/oojndninaelbpllebamcojkdecjjhcle) (previously ChatGPT to Notion) brings the cleverness of your favorite LLMs into your favorite app!

Side note: I have taken note that there are unfixed bugs (especially on Edge browser) and will be working on fixing them over the following weeks. I have been away for quite some time because of interships and my studies but I will at least make sure that the extension is bug free.

## Overview

For information about the extension itself more than the code behind it, check out [this notion page](https://theo-lartigau.notion.site/theo-lartigau/ChatGPT-to-Notion-af29d9538dca4493a15bb4ed0fde7f91) or the [FAQ](https://github.com/L-a-r-t/chatgpt-to-notion/wiki/FAQ). This extension was built using the [Plasmo framework](https://www.plasmo.com/) and Typescript. A simple Express server (hosted on a free Render webservice) that can be found on the "server" branch, it allows the secure long-term storage of Notion's access tokens.

## Motive

While some tools already exist to save a webpage to Notion, and some going as far as allowing the user to save the page's contents, these solutions fall short when trying to save a conversation with ChatGPT. As such, providing a specialized extension to do this work efficiently felt natural. Then, with the emergence of new credible alternatives to ChatGPT, the need to expand this tool to other LLMs felt bigger and bigger.

## Usage

On ChatGPT/Deepseek/Claude/Mistral's page, you'll notice a new pin icon under each of its answers. You can use it to save specifically that answer and the related prompt to your Notion database of choice. If you want to save the whole discussion, you can do so from the extension popup.

You may link as many databases with the extension as you need to, and you can then choose which database to save your discussion at saving time. If a page with the same title already exists in the database, the newly saved content will be appended to the end of said page.

### Websites access

Please refer to the [FAQ](https://github.com/L-a-r-t/chatgpt-to-notion/wiki/FAQ) for more info about the websites the extensions needs to access.

## Roadmap

These are the things that I plan to work on at some point. I hope to have the following (ranked by priority) done in the near future:

- [ ] Adding Perplexity & Grok support
- [ ] Adding history save to Mistral & autosave to every LLM
- [ ] Document the code properly for anyone who's interested

