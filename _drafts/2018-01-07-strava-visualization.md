---
title:  "Strava Visualization Tutorial"
header:
  teaser: "https://upload.wikimedia.org/wikipedia/en/thumb/c/cb/Strava_Logo.svg/1024px-Strava_Logo.svg.png"
categories:
  - running
tags:
  - strava
  - running
  - r
---

While browsing Twitter recently, similar visualizations of Strava data kept appearing, such as this one from [CanadianRunning](https://twitter.com/CanadianRunning):

<blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr">A year of running in a single, mindblowing photo: <a href="https://t.co/nx4pEQpVLe">https://t.co/nx4pEQpVLe</a> <a href="https://t.co/ykEMNU0Qh1">pic.twitter.com/ykEMNU0Qh1</a></p>&mdash; CanadianRunning (@CanadianRunning) <a href="https://twitter.com/CanadianRunning/status/949835984216059904?ref_src=twsrc%5Etfw">January 7, 2018</a></blockquote>
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

I was intrigued, and found the author's [GitHub page for the project](https://github.com/marcusvolz/strava). I thought I might as well follow the instructions as they seemed straightforward enough, and see if I could generate my own nifty Visualization.

I've added the instructions from Marcus' page below, and added slightly more detailed comments where I had to fiddle with things slightly.

## How to use

### Bulk export from Strava

1. Log in to [Strava](https://www.strava.com/)
2. Select "[Settings](https://www.strava.com/settings/profile)" from the main drop-down menu at top right of the screen
3. Select "Download all your activities" from lower right of screen
4. Wait for an email to be sent
5. Click the link in email to download zipped folder containing activities
6. Unzip files

### Install the packages

```R
install.packages(c("devtools", "mapproj", "tidyverse"))
devtools::install_github("marcusvolz/strava")
```

### Load the libraries

```R
library(strava)
library(tidyverse)
```

### Process the data

```R
data <- process_data(<gpx file path>)
```

### Plot activities as small multiples

```R
p1 <- plot_facets(data)
ggsave("plots/facets001.png", p1, width = 20, height = 20, units = "cm")
```

### Plot activity map

```R
p2 <- plot_map(data, lon_min = 144.9, lon_max = 145.73, lat_min = -38.1, lat_max = -37.475)
ggsave("plots/map001.png", p2, width = 20, height = 15, units = "cm", dpi = 600)
```
