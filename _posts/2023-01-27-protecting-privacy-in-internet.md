---
tags: ["general"]
title: "How I (try to) protect my privacy in Internet"
---

First: I **know** that it isn't really possible to be anonymous anymore at a low cost. Yes, you can use Tor, VPNs, don't save any cookies, disable all JavaScript, and generally just use `wget` to browse pages, but this makes modern websites REALLY unusable. Not talking about mobile apps.

I think my setup is a bit paranoic anyway.

Note: Everything I write here is about my personal setup

## Replacing Google and Facebook

The first thing I needed to do is to avoid using products of companies that are known for tracking: Google, Facebook, Microsoft etc.

Microsoft is easy, because they track mainly through Windows. You can just NOT use Windows in most cases. Currently I use Manjaro Linux.

Facebook also. Just don't have Facebook. This makes life a bit harder because of Messenger used by everyone, but possible.

Google is the hardest, because it is everywhere. Mail, mobile phones, websites (Google Analytics), YouTube, etc. For now I replaced:

-   Search with [DuckDuckGo](https://duckduckgo.com). Doesn't change anything. If I really can't find something with DDG, I can just to `!g something` to fallback to Google. [Bangs](https://duckduckgo.com/bangs) is something that Googles doesn't have, and is very nice for searching in Wikipedia, for example (`!w`), YouTube (`!yt`), and more.
-   Gmail with [Proton](https://proton.me). The only limitation is much less storage space (500 MB instead of 15 GB), but I didn't hit a limit yet.
-   Maps with [OpenStreetMap](https://openstreetmap.org). For many use cases, this is even better as OSM maps are more detailed. This is not perfect though. OSM doesn't have a proper mobile app (or I haven't just found one). Also, I didn't tested any "navigation" features, but they are possibly worse than on Google because Google uses its location tracking to make traffic jam detection working, for example.
-   Translate with [DeepL](https://www.deepl.com). It works real nice, actually, but doesn't have all languages that Google Translate have.
-   YouTube - well, there is no real replacement. At most, I can avoid to log in. uBlock blocks ads and some track requests. For [uploading videos](https://www.youtube.com/channel/UClwskzwn2nXvoW_hJ1iGScg), everything is public so it doesn't matter that much.

## Web browser setup

Most tracking happens through websites and their third-party cookies. Also the most popular trackers are easy to block them as everyone knows about them.

Currently I use Firefox. It works for most things. My setup:

-   Clear cookies on every exit (except some sites that I want)
-   Always send DNT (This isn't that useful since most sites don't care about DNT, but also doesn't make things worse)
-   Disable telemetry (Everything in "Data Collection and Use")

Extensions (most of them are redundant with blocking, but sometimes complement each other):

-   [uBlock Origin](https://ublockorigin.com/) (obviously) - ad & tracker blocking
-   [Privacy Badger](https://privacybadger.org/) - tracker blocking
-   [DuckDuckGo Privacy Essentials](https://addons.mozilla.org/en-US/firefox/addon/duckduckgo-for-firefox/) - tracker blocking
-   [ToS:DR](https://tosdr.org/en/downloads) - website ToS rating
-   [Privacy Redirect](https://addons.mozilla.org/en-US/firefox/addon/privacy-redirect/) - redirecting to privacy-friendly websites. Hovewer, I have most options disabled as they are redirecting to offline servers.
-   [Firefox Multi-Account Containers](https://support.mozilla.org/en-US/kb/containers) - making a separate environments that store cookies separately (e.g personal, work, ...). I'm not using this that much as it requires interaction, also it is a bit redundant with clearing cookies on exit.
-   [Behind The Overlay](https://addons.mozilla.org/en-US/firefox/addon/behind_the_overlay/) - removing annoying overlays like "You need to login" from websites. This is actually needed on Twitter, which client-side blocks you from scrolling if you don't log in.
-   [SimpleLogin](https://simplelogin.io/) - email aliases instead of real e-mail. I installed that recently, and didn't use in practice yet.

If Firefox doesn't work, I have also Chromium installed.

Side note: It's a bit ironic that Google's [PageSpeed Insights](https://pagespeed.web.dev) works only on Chrome, as it is (web.dev in total) a site that describes best practices for making websites. Also, they fail some of their own tests: ![page speed insights failing core web vitals assesment](/assets/images/privacy/pagespeed.png)

## Mobile

What I have done so far:

-   Disabled every "telemetry"/"send usage data to X" control that I found, and there are multiple of them.
-   Installed [personalDNSFilter](https://www.zenz-solutions.de/personaldnsfilter-wp/) which blocks DNS entries with a blacklist, for an illusion of privacy, at least. Illusion, because it ofter crashes because of... I don't know why, but regularly all Android apps are crashing. For some reason.
-   Disabled every Google app
-   I avoid installing apps for using mobile versions of websites, if possible. Websites can be controlled better with extensions, unlike apps, which can do whatever they like and I won't even know about it.

For now, I don't want to risk with unlocking/rooting to make this protection better.

## Conclusion

So, as you can see, I do something to block tracking, as much as possible. I realize that this is not perfect, but makes me a bit more comfortable with web application and websites.

Until next time!
