Obsidian Imgur Plugin
===

This plugin uploads images to [imgur.com](https://imgur.com/) instead of storing them locally in your vault.

![obsidian-imgur-plugin-demo](https://user-images.githubusercontent.com/1719646/120395609-efe33b80-c33d-11eb-9960-95b9aac0b0b9.gif)

## Why?

Obsidian stores all the data locally by design
(which is perfect for text and, in my opinion, can be improved for images).
If you often add pictures to your notes, your vault can quickly grow in size.
Which in turn can lead to reaching limits if you use free plans of cloud storage services to sync your notes
or can lead to growth of repository size if you use git to back up your notes.

This plugin is a perfect solution for people
who paste images to their notes on daily basis (i.e. students making screenshots of lecture slides)
and do not want to clutter their vaults with image files.

Having remote images also makes it much easier to share a note with anyone else,
you will only need to share a single file.

If you are uncertain if this solution is for you, you can check out the [FAQ](#faq) section
and/or a video created by [@santiyounger][santiyounger] discussing pros and cons of this approach

[![](https://img.youtube.com/vi/-a1vJVy20cQ/0.jpg)](https://www.youtube.com/watch?v=-a1vJVy20cQ)

[santiyounger]: https://github.com/santiyounger

## Features

- Upload images by pasting from the clipboard or from the filesystem using drag-and-drop
- Animated gifs upload support on drag-and-drop

## Installation

Install the plugin via the _Community Plugins_ tab within Obsidian

## Getting started

All you need to start using the plugin is imgur.com **Client ID**.

![image](https://user-images.githubusercontent.com/1719646/104515726-3bea4980-5604-11eb-92c5-9e448ff9c364.png)

If you do not have an imgur.com account, you need to [get one](https://imgur.com/register) first.

When you sign in, go to https://api.imgur.com/oauth2/addclient
and generate **Client ID** for Obsidan:
- provide application name, i.e. "Obsidian"
- choose "OAuth 2 authorization without a callback URL"
- and specify your e-mail

You only need **Client ID**, Client secret is not required.

## FAQ

**Q:** How secure this approach is?  
**A:** Nobody sees your uploaded image unless you share a link or someone magically guesses an URL to your image.

**Q:** Why the images I upload do not get displayed on my imgur account?  
**A:** Even though you provide your client id in settings,
images uploaded by thins plugin get posted "anonymously" (without being tied to your imgur account).
There are plans to implement advanced authentication to [allow uploads to your account][oauth-issue],
choosing target album, etc.

[oauth-issue]: https://github.com/gavvvr/obsidian-imgur-plugin/issues/5

**Q:** Can I remove a remote image uploaded by accidence?  
**A:** It is possible (the imgur API allows it), but the answer is no, it is not implemented.

**Q:** For how long an image stays at imgur.com? Is there a chance to lose the data?  
**A:** Earlier it [was stated on imgur website][early-imgur-guarantees] that the image you upload stays **forever**.
I think this is true [since 2015][imgur-pro-free]. Today I could not find this statement on imgur.
I can assume that images which did not receive any view for years, can be removed, but there is nothing to worry about.
You can read my detailed thoughts on this in [discussions][ttl-discussion]

[imgur-pro-free]: https://blog.imgur.com/2015/02/09/imgur-pro-for-everyone/
[early-imgur-guarantees]: https://webapps.stackexchange.com/questions/75993/how-long-does-imgur-store-uploaded-images/75994#75994
[ttl-discussion]: https://github.com/gavvvr/obsidian-imgur-plugin/discussions/4#discussioncomment-590286

**Q:** Imgur supports videos. Does the plugin support videos upload?  
**A:** No. Initially I did not consider videos upload support since there is no Markdown syntax to embed videos.
On the other hand you can simply use `<video>` HTML tag, so I will probably add support for videos in future

**Q:** Can it upload images to some other service?  
**A:** For now there are no plans to support other image hosting solutions,
but it should not be difficult for you to make a fork and create your own implementation of `ImageUploader` interface.

### Known limitations
- you can not paste animated gifs from the clipboard (they get copied as a static images to the clipboard).
  Use drag and drop instead if you want to upload animated gif.
- There are daily [upload limits](https://apidocs.imgur.com/#rate-limits),
  but reaching them by manually making notes is hard to imagine.

### Known issues

- Sometimes imgur can reject your request to upload image for no obvious reason.
  The error [usually reported in this case][known-cors-problem-issue] is a failed CORS request,
  which does not allow Obsidian to proceed with image upload. If you face this problem, no action required from your side:
  just wait, and it will disappear soon. Whenever the plugin fails to upload image remotely,
  it will fall back to default method of storing image locally.

[known-cors-problem-issue]: https://github.com/gavvvr/obsidian-imgur-plugin/issues/8

### Contribution

Contributions are welcomed.
Check out the [DEVELOPMENT.md](DEVELOPMENT.md) to get started with the code.

### Your support

If this plugin is helpful to you, you can show your ❤️ by giving it a star ⭐️ on GitHub.
You can also buy me a coffee using Ko-fi:

[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/F2F44TOP7)
