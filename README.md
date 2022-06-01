# uBlock-YouTube-Enhancer
This is for people who want to remove junk from youtube on their desktops. Install the [**uBlock Origin extension**](https://github.com/gorhill/uBlock) for your browser, copy the text below for the specific filter and paste it into uBlock's '**My filters**' section. 

## Remove Junk (General Filter)
Here is a list of non-cosmetic filters to remove junk from Youtube without the need of cosmetic filtering. 
NOTE: because of the way Youtube loads videos, these filters (except for the shorts button filter) will not work if you enter in the direct URL of a video or click on a video link.
> Credit: [u/Cat_Bot4](https://www.reddit.com/user/Cat_Bot4/)
```
! remove hashtags above video title

youtube.com###super-title

youtube.com##.super-title

! removes the info cards

||youtube.com/*/annotations_module.js^

! removes endscreens

youtube.com##+js(json-prune, endscreen)

! removes "Shorts" button

youtube.com##+js(json-prune, items.0.guideSectionRenderer.items.2.guideEntryRenderer)

! removes voice search button (only works on watch page)

youtube.com##+js(json-prune, topbar.desktopTopbarRenderer.voiceSearchButton)

! removes the "includes paid promotion message"

youtube.com##+js(json-prune, paidContentOverlay)

! removes annoying pop messages on the bottom left of the screen

youtube.com##+js(json-prune, messages)

! removes sidebar ads

youtube.com##+js(json-prune, contents.twoColumnWatchNextResults.secondaryResults.secondaryResults.results.0.promotedSparklesWebRenderer)

youtube.com##+js(json-prune, contents.twoColumnWatchNextResults.secondaryResults.secondaryResults.results.0.compactPromotedVideoRenderer)

! removes ads in search results

youtube.com##+js(json-prune, contents.twoColumnSearchResultsRenderer.primaryContents.sectionListRenderer.contents.0.itemSectionRenderer.contents.*.searchPyvRenderer.ads)

youtube.com##+js(json-prune, contents.twoColumnSearchResultsRenderer.primaryContents.sectionListRenderer.contents.0.itemSectionRenderer.contents.*.carouselAdRenderer)

youtube.com##+js(json-prune, contents.twoColumnSearchResultsRenderer.primaryContents.sectionListRenderer.contents.0.itemSectionRenderer.contents.*.promotedSparklesTextSearchRenderer)

! removes info panels under videos

youtube.com##+js(json-prune, contents.twoColumnWatchNextResults.results.results.contents.0.itemSectionRenderer.contents.0.infoPanelContentRenderer)

! removes merchandise shelf

youtube.com##+js(json-prune, contents.twoColumnWatchNextResults.results.results.contents.2.merchandiseShelfRenderer)

! removes auto playing channel trailers

youtube.com##+js(json-prune, contents.twoColumnBrowseResultsRenderer.tabs.0.tabRenderer.content.sectionListRenderer.contents.0.itemSectionRenderer.contents.0.channelVideoPlayerRenderer)

! removes shorts shelf from channel pages

youtube.com##+js(json-prune, contents.twoColumnBrowseResultsRenderer.tabs.0.tabRenderer.content.sectionListRenderer.contents.*.itemSectionRenderer.contents.0.reelShelfRenderer)

! removes movie/show upsell banners on sidebar

youtube.com##+js(json-prune, contents.twoColumnWatchNextResults.secondaryResults.secondaryResults.offerModule)
```


## Remove Junk from Search Results
When you search for something on youtube, it returns some results first, then a separate section like "[People also watched](https://i.imgur.com/xRiX6Vx.jpg)", "[For you](https://i.imgur.com/Ie7tdCm.jpg)" and "People also search for". This filter aims to remove them from your youtube search results and make them a lot cleaner.
> Credit: [u/RraaLL](https://www.reddit.com/user/RraaLL/)

### Youtube Search (Returns Videos Only)
```
youtube.com##ytd-search ytd-item-section-renderer>#contents>:not(ytd-video-renderer),ytd-secondary-search-container-renderer
```
### Youtube Search (Returns Videos and Channels)
```
youtube.com##ytd-search ytd-item-section-renderer>#contents>:not(ytd-video-renderer,ytd-channel-renderer),ytd-secondary-search-container-renderer
```

## Advaced Shorts Blocking
This filter hides the navigation bar icon and shorts videos on all lists (homepage, subscriptions, search and sidebar).
```
youtube.com###guide-content #endpoint[title="Shorts"]:upward(ytd-guide-entry-renderer)
youtube.com###items #endpoint[title="Shorts"]:upward(ytd-mini-guide-entry-renderer)
youtube.com##ytd-browse ytd-grid-video-renderer:has(span.ytd-thumbnail-overlay-time-status-renderer:has-text(/\s(0:\d\d|1:0\d)\s/))
youtube.com##ytd-browse ytd-rich-item-renderer:has(span.ytd-thumbnail-overlay-time-status-renderer:has-text(/\s(0:\d\d|1:0\d)\s/))
youtube.com##ytd-search ytd-video-renderer:has(span.ytd-thumbnail-overlay-time-status-renderer:has-text(/\s(0:\d\d|1:0\d)\s/))
youtube.com##ytd-watch-next-secondary-results-renderer ytd-compact-video-renderer:has(span.ytd-thumbnail-overlay-time-status-renderer:has-text(/\s(0:\d\d|1:0\d)\s/))
youtube.com##ytd-browse ytd-grid-video-renderer:has(span.ytd-thumbnail-overlay-time-status-renderer[aria-label="Shorts"])
youtube.com##ytd-browse ytd-rich-item-renderer:has(span.ytd-thumbnail-overlay-time-status-renderer[aria-label="Shorts"])
youtube.com##ytd-search ytd-video-renderer:has(span.ytd-thumbnail-overlay-time-status-renderer[aria-label="Shorts"])
youtube.com##ytd-watch-next-secondary-results-renderer ytd-compact-video-renderer:has(span.ytd-thumbnail-overlay-time-status-renderer[aria-label="Shorts"])

```

## Youtube Theater Mode Full Height
This simple filter makes youtube "theater mode" full height (minus the page header)
```
youtube.com##body ytd-watch-flexy[theater-requested_]:not([fullscreen]) #player-theater-container:style(height:calc(100vh - 56px) !important; max-height:calc(100vh - 56px) !important;min-height:calc(100vh - 56px) !important; )
```
> Credit: [u/anonwins](https://www.reddit.com/user/anonwins/)

## Hide Chat when viewing Live Streams
This filter allows you to remove the live chat when viewing streams on youtube

```
www.youtube.com###chat:remove()

```
