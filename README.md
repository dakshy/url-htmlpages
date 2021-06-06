# URL Pages

This was a fork of [jstrieb.github.io/urlpages](http://jstrieb.github.io/urlpages). I will develop it to an advanced stage.

## About

- Create web pages in the simple, fast editor
- Share code that others can edit and modify
- Clone web pages with the bookmarklet (under active development)
- "Publish" web pages instantaneously
- Published links never stop working and ~cannot be taken down~ function as
  long as this site is trusted and extant
- No dependencies
- No signups
- No tracking
- No hosting
- No cost
- No commitment
- A few hundred total lines of clear, well-documented HTML, CSS, and JavaScript


## Encrypt

It is now possible to encrypt URL Pages using Link
Lock. This static, distributed web
application uses AES in the browser to encrypt the URL without transmitting any
data. The encrypted link is then stored in a Link Lock URL, which, when
visited, can only be unlocked with a password.


## How it works

As hinted by its name, URL Pages works by storing the entire contents of a web
page in the URL.

Thus, as long as the URL exists, so does the page it points to. The rest of the
URL Pages program is responsible for translating between web page code
(HTML/CSS/JavaScript) and an "encoded" URL.

- The **main page** takes encoded data from the URL, decodes it into regular
  web page format, and displays it to the user
- The **editor** encodes user-created web page data as a link that can be
  shared
- The **bookmarklet** takes a page that already exists and encodes it as a link
  that can be shared

When the main page is visited, the data is encoded in the URL using base 64
encoding via JavaScript's `atob` and `btoa` functions in conjunction with its
`encodeURIComponent` and `decodeURIComponent` functions. The encoded data is
stored in the
[hash](https://developer.mozilla.org/en-US/docs/Web/API/URL/hash#Examples)
portion of the URL.

In the editor, data is similarly encoded, except that the HTML, CSS, and
JavaScript portions are stored separately in one object that is converted to a
JSON string before being base 64 encoded.

The obvious downside of URL Pages is that the links get very long very quickly.
Luckily, some URL shorteners are able to accommodate fairly long URLs (shoutout
to [da.gd](http://da.gd)). In a strange way, this effectively means the
link shortener is acting as the web host since it is responsible for storing
the record of the web page's data. For simple web pages (and even simple page
hierarchies), URL Pages have proven reasonably easy and effective to use,
however it quickly becomes infeasible to use for large sites or large embedded
images.


## Disclaimer

This just becomes a toy if I am the only one hosting a running version of this
repository. If you believe it has real potential, clone it or fork your own
version that addresses any non-fundamental problems you have with it, and host
your own. The only way this actually becomes robust is if there is no single
point of failure (i.e. my GitHub Pages)

Web pages in URLs are definitely not how things on the web were meant to be
done, so don't be surprised if trying to use URL Pages causes unexpected
issues. For example, sharing these links may cause chat programs, email
clients, and unsuspecting individuals to get confused, raise exceptions, or
complain. Likewise, copy-pasting these links may take a long time, if it works
at all. I've also noticed my browser running a little hotter while I've got 5MB
links in the URL bar.

Furthermore, URL Pages is very much a proof of concept, and should not be
relied upon for anything consequential.

Read the code and understand it before using so that you understand any
associated risks. The codebase was written with readers in-mind. Since the
codebase is intentionally short, it can be read and digested fairly quickly if
you have prior experience with client-side web applications.

I originally conceived this as a simple, static CodePen clone, but I felt the
"publishing" of pages as URLs was an interesting idea. So I decided to present
that aspect of it front and center, even though it wasn't really the point of
the project at the beginning. About a year ago, I had a proof of concept
version that I ended up using fairly frequently for sharing quick
HTML/CSS/JavaScript experiments (never as a means of seriously publishing and
sharing censorship-proof content). I found that if its use is limited to that
case, it is actually very handy and robust!
