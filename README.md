# Songlink
Songlink is the best way to share music (we think). But, with your help, we can make it even better. 🙏🏼

* [How to use Songlink](#how-to-use-songlink)
* [Contributing](#contributing)
* [Songlink as a service](#songlink-as-a-service)
  * [Redirect URLs](#redirect-urls)
  * [Full Songlink URLs](#full-songlink-urls)
  * [ID-only Songlink URLs](#id-only-songlink-urls)
* [Contributing (Alternate Take)](#contributing-alternate-take)
* [Blog posts](https://github.com/kweiberth/songlink/tree/master/blog)

## How to use Songlink
Sharing Songlinks is powerful. When someone clicks on a Songlink, it is quick and easy for them to start listening to the song in the app they love:

![Songlink listen flow gif](https://s3-us-west-1.amazonaws.com/songlinkio/songlink_listen.gif)

It is easy to create and share Songlinks. Just head to our website:

![Songlink webapp flow gif](https://s3-us-west-1.amazonaws.com/songlinkio/songlink_webapp.gif)

Or, you can use a little copy and paste wizardry:

![Song spotify copy manual gif](https://s3-us-west-1.amazonaws.com/songlinkio/songlink_spotify_copy_manual.gif)

If you use Facebook Messenger, you can talk to [Songlink Bot](https://www.messenger.com/t/songlinkbot/) and he (she? it?) will find you the Songlink to share.

If you use the iOS app Workflow, there's some dope workflows like [this one](https://workflow.is/workflows/561b08115edf48d1b205dbf422ca426c).

For more info about all the ways to create Songlink URLs, see the [Songlink as a service](#songlink-as-a-service) section below

## Contributing
We want to make it as easy as possible for users to create and share Songlink URLs. Thus, we need to integrate with the tools and apps they use to listen to music and communicate with friends. We’re thinking apps and websites, messaging bots, universal share flows on iOS and Android, etc. We can’t build all of this cool shit ourselves (though we **are** working on some of them!), so we’d like to engage the community and enable all yinz to make Songlink workflows that help you (and maybe even others!) share music.

The next section describes how (easy it is) to create Songlink URLs. Please reach out to hello@song.link with any questions or comments, or to show off a new integration you’ve built. I’ll make a gif of any cool shit you build and highlight it in the [How to use Songlink](#how-to-use-songlink) section above.

## Songlink as a service
Songlink has the ability to render Songlink URLs and also redirect to music services.

1. [Redirect URLs](#redirect-urls)
2. [Full Songlink URLs](#render-full-songlink-urls)
3. [ID-only Songlink URLs](#render-id-only-songlink-urls)

### Redirect URLs

A redirect URL will not load a Songlink page, but instead redirect the user to a certain music streaming service, as defined by the `to` query param. A Songlink Redirect URL can be composed easily with the following format:

```
https://song.link/redirect?url=encodedSongUrl&to=musicService&web=boolean 
```

More info about each part:

`url`: the url to the song, e.g. a spotify song URL. It's best if it's encoded, but it can be the plain URL, too.

`to`: the music service to which you'd like to redirect. Can be one of: `spotify` , `youtube`, `itunes`, `google` or `deezer`. If the song is not available in the user's country on that music service, the Songlink page will load instead.

`web`: this param takes a boolean and defaults to `false`. If set to `true` then we will redirect to the web version of the music service. This applies mostly to Spotify, which has two completely different URLs for app and web. If the user does not have the Spotify app installed on that device, the link will not work.

This also affects Apple Music (`&to=itunes`) links, which will not attempt to open the app if `&web=true`.

Here's an example redirect URL:

https://song.link/redirect?url=https%3A%2F%2Fitun.es%2Fus%2F5Gb0-%3Fi%3D1053825088&to=spotify&web=true

which was created from the song https://itun.es/us/5Gb0-?i=1053825088 and will open that song in the Spotify web player.

### Render Full Songlink URLs

These are the easiest to create. A full Songlink URL is composed by appending the song’s share URL to the root Songlink domain. For example:

https://song.link/https://itun.es/us/5Gb0-?i=1053825088

Songlink currently supports Spotify, Apple Music, YouTube, Google Play Music and Deezer urls:

#### Spotify

https://song.link/https://open.spotify.com/track/0Jcij1eWd5bDMU5iPbxe2i
https://song.link/spotify:track:35QAUfIbfIXT3p3cWhaKxZ

#### Apple Music

https://song.link/https://itun.es/us/48WL3?i=932646721

#### YouTube

https://song.link/https://youtu.be/YZR8WMFK7Qw

https://song.link/https://www.youtube.com/watch?v=Kp7eSUU9oy8

#### Google Play Music

https://song.link/https://play.google.com/music/m/Tvvhbnefqhalxuypoxq4xqeo4h4

#### Deezer

https://song.link/https://www.deezer.com/track/78621548

### Render ID-only Songlink URLs

These are shorter, prettier, cooler Songlink URLs 😎. If you can grab the ID of the song, the rest is 🍰. We support Spotify, Apple Music, YouTube and Google Play Music IDs.

#### Spotify

`https://song.link/ + s/ + Spotify ID (id)`

https://songlink.io/s/6EsLX3ZbZbAZUn3iaO5MuX

#### Apple Music

`https://song.link/ + i/ + Apple Music ID (trackId)`

https://song.link/i/1067974803

If you know the country of the song, you should add the two-letter country code before `/i/`. For example, for an Austrian song:

https://song.link/us/i/1067974803

We default to `us` (United States) if you do not specify a country. When in doubt, your easiest and best bet is to compose a [full Songlink URL](#full-songlink-urls) for Apple Music songs.

#### YouTube

`https://song.link/ + y/ + YouTube ID (id)`

https://song.link/y/UVtpXvzzXiA

#### Google Play Music

`https://song.link/ + g/ + Google Play Music ID (storeId)`

https://song.link/g/Tps4zhpxnp3keaurdgw7wasleze

#### Deezer

`https://song.link/ + d/ + Deezer ID (id)`

https://song.link/d/66539325d

## Contributing (Alternate Take)
Songlink has no funding or revenue stream (we think banner ads are bullshit 🤑). We are committed to maintaining (and, of course, constantly improving) the Songlink platform. Unfortunately, servers aren’t free, my Philz coffee addiction is real and we drink a lot of IPAs. If you’d like to help fund our servers, ☕ or 🍺 you can send us a gift via [Venmo](https://venmo.com/songlink) or [PayPal](https://paypal.me/songlink).

✌️❤️
