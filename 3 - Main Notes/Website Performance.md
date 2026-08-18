
2026-05-10

Tags: 
# Website Performance
## Metrics
Largest Contentful Paint
- As various pieces load the HTML, JS, Images, etc will be painted to the screen. Initially you'll get the first contentful paint, and the largest is the last contentful paint to be completed. Google says you should get to LCP within 2.5 seconds, and that it needs improvement if it's within 4 seconds.

First Input Delay
- The first input delay is the time it takes from display to the user being able to interact with the content. The only real way to optimize this is by making your javascript faster, you can also use lazy loading or a framework like quick which aggressively lazy loads. less than 100 ms is considered good, less than 300 ms is considered ok. 

Cumulative Layer Shift
- CLS is a measure of visual stability, this means things should stay mostly in the same spot on the page. An easy way to mess this up is to use images without a width/height or the CSS aspect ratio. Another trick for responsive images is using source/set to use different images in different conditions. A good CLS is considered less than 0.1, and less than 0.25 is considered needs improvement.

## Tools
lighthouse
- this is the classic tool that is super easy to use. it is bundled directly into the chrome/chromium dev tools. I'd also like to point to the chromium performance tab. Be careful with connection caching, DNS caching, server warmup, etc. I've found the best I can do is close/reopen the tab between every run.

Webvitals
- maintained by the chrome dev team and can be found at the chrome web store

unlighthouse
- `npx unlighthouse --site <the-site>`

## Tips

**More specific**
- if the customer base is global then use a CDN
- Minify your JS and CSS, IO is super slow. Also compress when sending over the network
	- Make sure that your fonts are compressed into `woff2` instead of raw `ttf`
- avoid dependency chains as much as possible where one script loads another loads another so on, eagerly load critical resources in order to reduce a lazy loading step. This works even better if your critical resources have small over the wire costs
- in the same way that you should eagerly load critical resources lazy load literally everything else that you can
- You can pre-connect to a different URL if for example you have an API or third party resource at a different location, ex `<link rel="preconnect" href="%VITE_API_URL%" crossorigin>`
- display **something** quickly, progressively make it better as more stuff arrives
	- one way to do this is use `font-display: swap` in order to progressively change the font out when it arrives
- be careful of JS blocking the main thread leading to longer wait times, an example is a synchronous `await fetch()` sort of example.
- if users will frequently return then cache wherever possible
- Perception matters a lot, for example if you just match the background color instead of having a white flash -> jump then it'll be perceived as faster.
- be sure that critical steps are actually being followed. for example, make sure that your build process is being followed and make sure it is actually minifying  + compressing etc

**More general**
- Do less. Especially when we're talking about round trip times
- make the common case fast
- Tools and metrics are important, but anecdotal user experience is waay more relevant. If your tools and your users disagree then **your tools are wrong**. Also don't get overly hung up on metrics for gui's, the point is to make it "feel" better so if a change reduces LCP by .1s but makes it feel better overall go with it.
- lastly understand that there are limits, if you're using certain frameworks you cannot avoid some costs, it's just the price of doing business. You also can't fight the speed of light and win.
# References
- 