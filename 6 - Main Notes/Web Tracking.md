
2026-05-11

Tags: [[Web]] [[Networking]] [[Network Security]]
# Web Tracking
## Deterministic Methods
#### Web Cookies
Firstly, one of the easiest ways to do web tracking is through the use of [[Web Cookies]] and there is a full outline there. 

#### Iframe Tracking
This is just one example of how to track users that doesn't use cookies
```js
<iframe src=tracker.com>
	const LS = localStorage
	if (LS['id']) {
		// identified user
	} else {
		// new user
		LS['id'] = math.random()
	}
	fetch(`/record?id=${LS['id']}`)
</iframe>
```

#### Defense: Partitioning
Modern browsers provide privacy defense via partitioning this has different names: for Firefox (total cookie protection), chrome (privacy sandbox), Safari (ITP). Storage is partitioned by both the tracker and the site where it appears, known as dual-keying. 

Previously:
- `browser_storage[top-level site]`
Modern (partitioned):
- `browser_storage[top-level site, tracker origin]`

Partitioning can be defeated by using unpartitioned data as a linking key, but what to use? Browsers cache things to speed up rendering and caches are generally unpartitioned. This means Images, JavaScript, etc can be used.

#### Cache Tracking
Cache tracking is more powerful since it abuses the browser's desire for speed. This works because most browsers don't partition their caches. A common example of this idea is a tracking pixel, and in practice it looks like the following:
```js
const identifier = []
for (let i = 0; i < 32; i += 1) {
	try {
		const url = `/pixel/${i}.gif?action=read`
		await fetch(url)
		// We hit the cache
		identifier[i] = 1
	} catch (_) {
		// We missed the cache
		identifier[i] = 0
	}
}
```
Tracker sets cache state, on  action=set: return pixel by a probability and on action=read: 404.  This is done many times
- e.g., 32 gifs, from /pixel/1.gif to /pixel/32.gif
- Some bits are 1 (returned pixel), and some are 0 (404)
- This creates a 32-bit ID for user at some-site.com

#### HSTS Cache Tracking - Super Cookies
HSTS is  HTTP Strict Transport Security. The Website uses HSTS to tell the browser to always use HTTPS for this website, and never uses HTTP. The abuse is through a browser-side supercookie. First assume the attacker controls many subdomains such as  `a1.tracker.com`,  `a2.tracker.com`, `a3.tracker.com`, ..., `a32.tracker.com`. Then a tracking ID can be formed by setting HSTS in the following way:
- HSTS set on $a_1 = 1$
- HSTS set on $a_2 = 0$
- HSTS set on $a_3 = 1$
- …

A tracker cannot directly read the state through a JavaScript API, but it can infer from browser behavior.

## Fingerprinting
Some commercial companies use methods to provide “device identification” through web-based fingerprinting. The constructive use is to combat fraud via device authentication, but of course the destructive uses are many. This includes tracking users between sites without their knowledge and without a simple way of opting-out and to deliver tailored malware.

Which fonts are installed on a user’s computer can serve as (part of) the fingerprints, and a particularly powerful part due to applications bundling fonts. A browser plugin or a side channel can reveal the presence or absence of any given font. Browsers should download fonts from the Internet on demand.

```
@font-face { font-family: 'Sirin Stencil'; font-style: normal; font-weight: 400;
src: url(http://themes.googleusercontent.com/static/fonts/sirinstencil/v1/[...].woff) format('woff');}
```
One way to test is through the [EFF](https://panopticlick.eff.org/)

## Prevalence
Tracking is very pervasive. Professor Li cites 64 independent tracking mechanisms in an average top-50 website. Supercookies (a.k.a. evercookies) encode a globally unique pseudonymous device identifier into any stateful web technology. For 𝑛 Internet-connected devices, ID should be log(𝑛) bits. This means only 33 bits are needed for 5 billion devices.

## What is being tracked?
Basic: Track anonymous users
 - Key is to distinguish between different visits
 - Track the pages visited by a particular browser running on a particular device
Better: Track named users
- Key is to distinguish between different individuals by associating with PII.  Websites with user registration, social networks, cloud services, or any number of data can do this. Cookies/sessions are correlated with PII, and trackers may collude with services: previous “anonymous” cookies now associated with named individuals

This can be done in a number of ways, sometimes the first party site itself wants to track you, sometimes identifiers leak, there are security bugs, and there are also many sites that will sell you this info.
## Countermeasures
**Cookies**
Disable third-party cookies:
- Can be disabled by default (Safari)
- Can be disabled by user (many browsers)
- Cannot be disabled (Android)
Deleting cookies frequently
- “20-40% of the users delete cookies” (ComScore, April 2010)
- “One in three users do it within a month after the visit”
Modern browsers have native support to reject all third-party cookies, also support for private browsing modes and browser extensions that reveal third-party tracking

**Opt Out**
Opt-out can be done through several avenues such as  Network Advertising Initiative (NAI), European Interactive Digital Advertising Alliance (EDAA),  AddThis' own Data Collection Opt-Out website, etc.

In practice, a 2014 study shows:
- Number of IDs involved in cookie sync: reduced by 30%
- Number of parties involved in cookie sync: reduced by 5%
- no change for canvas fingerprinting and evercookies

**Do Not Track (DNT) HTTP header**
- Standardization
- Browser support in IE, Firefox, Chrome, …
- No legal or technological requirements

The idea is 
- No tracking across sites
- No intrusive tracking
- Limits on regular log data
- Exceptions for fraud prevention, etc.
In practice,
- DNT reduces # of parties and # of IDs in cookie syncing by 3% (but blocking 3rd-party cookies reduces this by a factor of 2)
- The fingerprinting scripts will execute regardless of the DNT value
- Hard to verify misuse
# References
- [[Web Cookies]]