---
layout: default
title: Find Data
---

# Finding our Database/How BotanyBase works

The data is stored under `/data/*.json` or `https://botanybase.github.io/data/*.json`, in multiple JSON data files, these contain the data which we use to build a search.

The data is fetched via javascript on a search page, then converted into HTML and displayed as a search entry. Before that however, since our JSON data is split into different files, we need to compile them into one JSON array first.

---

## Github Repo

In our Github Repo, you can easily find the data under the folder `data`, and can be easily retreived and used for your own purpose.

## VIA `fetch()` < Depreciated

Fetching the data from a single endpoint does not work anymore as our old `plants.json` has been split by climate for easy contribution and loading of data.

However if you'd still like to use this method, `plants.json` still exists under `https://botanybase.github.io/data/plants.json`.
