## Replaced Content

### Images
```html!
<p><img src="trophyroom.jpeg" alt="aj1"></p>
```

#### Beware of Image Sizes
Chances are stock imagery is going to be too large in terms of both dimensions (takes up too much space in the browser) and file size (takes too long to load in the browser). Hence, need to resize image smaller.

Takes up too much space:
![Screenshot 2024-06-07 at 2.37.51 PM](https://hackmd.io/_uploads/HJm-Rx-S0.jpg)

Takes too long to load when on slow 3G network with cache disabled:

![Screenshot 2024-06-05 at 11.37.03 PM](https://hackmd.io/_uploads/BJRKoAR4C.png)

The image should be kept under 200 KB.

#### Providing Width and Height Attributes
```html!
<img src="trophyroom.jpeg" alt="aj1" width="1200" height="900">
```
Width and height attributes provide information to the browser about how much space on the page the image is expected to take up. Note: Do not add px to the attribute values.

This can help hold the space for the image when the network is slow. If the space is not held, content on the page will shift after the image loads.

If it is desired to display the image smaller, one possible way to do so is to scale down the width and height attribute, say 400x300. However, the image is still downloaded at 1200x900 and just displayed smaller at 400x300. Hence, using html to achieve this is undesirable, as the image is still forced to download at a large size. Instead, using CSS is more optimal. The attributes in the HTML should describe the actual size of the image.

#### Common Image Formats
* JPEG (or jpg) - Old lossy format. Most common for photographs.
* GIF - Graphical Interchange Format - This is what a lot of memes uses.
* PNG - Portable Network Graphic - Has alpha channel, but file sizes get large for photographs. Best for graphics. Can be transparent.
* SVG - Scalable Vector Graphics. Great format for vector graphics and icons.

#### SVG
![svg](https://hackmd.io/_uploads/rJwByler0.jpg)

SVG is represented as code. This looks similar to HTML as it has styling. File sizes are small so can load fast in the browser. Also, edges are super smooth and crisp regardless of how enlarged the photo is, so won't be pixelated when zoomed in.

#### Up and Coming Formats
* WebP - Generally better compression than JPEG, but has slow adoption.
* AVIF - Derived from a video format. Higher quality at much lower file size. Very promising.
* JPEG XL - Has more features than AVIF, but is not yet supported in browsers.

Note: Check [caniuse.com](https://caniuse.com) for support.

### Video and Audio
```html!
<h2>Here is a video.</h2>
<video controls width="800">
	<source src="media/video.mp4" type="video/mp4">
</video>

<h2>Here is an audio.</h2>
<audio controls src="media/audio.mp3"></audio>
```
The video and audio tags are also examples of replaced content. Modern browsers provide the interfaces for these files and there are lots of built in controls and options.

```html!
<audio controls src="media/audio.mp3"></audio>
<audio controls="controls" src="media/audio.mp3"></audio>
```
`controls` is the abbreviation for `controls="controls"`. In html5, occasions where the value is the same as the name of the attribute can be abbreviated this way.

Note: Can find out more about video and audio on the MDN website.

### iFrame
```html!
<h2>Here is an iFrame.</h2>
<iframe width="560" height="315" src="https://www.youtube.com/embed/Cd3khhCnnsY?si=rLf-avCy2YR6GlTP" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
```
An iFrame is also replaced content. It put a part of a webpage inside another web page. So, when embedding a YouTube video, actually is embedding a little bit of the YouTube website, the part that is just showing the video, right onto the page. The above code is obtained from any video from YouTube. Just click `Share` then `Embed`.
