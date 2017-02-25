# internationalization (for the most part)

It's been a long time comin', but finally we're taking care of our international friends. We're not the White House.

So... what did we actually fix? How did we make the experience better? In short, we made the iTunes API suck less and not break our site. It still kinda sucks though. 😬 Their API has a built-in notion of `country`. This manifests itself in two ways:

1. Any API call to their servers needs to explicitly define `country` (or it will default to `US`).

2. Any response from them is country-specific (including the URLs for the songs).

The first problem cropped up when an Austrian user (big shout to [@fr3ino](https://www.twitter.com/fr3ino) for helping me debug and test!) tried to share an Austrian song from Apple Music. Since we weren't handling the `country` of the song, iTunes API defaulted to `US` and basically said "nope". And so we weren't able to find the matches and the Songlink page for this song was broken.

The second issue we faced was that the iTunes API returns country-specific URLs for the songs. By removing the country from the URL, we let the iTunes app handle access to the song, which is how most of the other music service links work, like Spotify and Deezer.

Now you might be thinking... what a terrible user experience! Why allow a user click `Listen on Apple Music` when they will be met with a blank, white screen in the Apple Music app? We agree this is shitty, but it's quite hard to determine a user's locale (country), and that locale from the browser may or may not be the same country as is set up in their Apple Music or other music services. So I'm taking a pass on this one for the time being. 😜 Do reach out if this is a consistent problem for you, though. 👍

Lastly, if you're creating Songlink URLs by appending the full song url, like https://songlink.io/https://itun.es/us/5Gb0-?i=1053825088, you don't have to worry about anything. We will correctly handle the `country`. However, if you're creating a shorter Songlink URL, like https://songlink.io/i/1202255139, and it's a non-US song, you should attach a query param `c` equal to the two-letter country code. In this example, the URL should be https://songlink.io/i/1202255139?c=at, since it was an Austrian song.

As always, please reach out to us via [email](hello@songlink.io) or hit us up on [Twitter](https://twitter.com/songlinkio).

✌️❤️
