## Fonts - My Bio

### Basic Web Fonts
#### Converting a Font
We will start by converting a font to the correct formats so it can be effectively used with @font-face. In this case, we are using a few fonts from the font family Freight Round.

The `freightround.zip` file contains the three Freight Round `.otf` font files. OTF (OpenType font) and TTF (TrueType font) are popular formats for fonts. [OTF vs TTF](https://www.coreldraw.com/en/tips/otf-vs-ttf/?alid=548090491.1719865908).

We are converting these fonts into a different format, WOFF (Web Open Font Format), to be used on web pages by compressing them and making them compatible with the browser.

![1](https://live.staticflickr.com/65535/53850290642_9d2c19774f_o.png)

Go to [fontsquirrel.com](https://fontsquirrel.com) and click on webfont generator, then upload the three Freight Round `.otf` font files. Check the box that says you are allowed to convert these fonts. Then click `Download Kit`.

![2](https://live.staticflickr.com/65535/53851184006_2f681818f1_o.png)

For each font, `.otf` gets a `.woff` and a `.woff2` file. The WOFF format is a little bit older. WOFF2 is updated and it compresses the fonts further. Modern browsers will all use the WOFF2 format without a problem. WOFF is provided just in case it is needed for some specific reason.

Using fonts with compressed small sizes is important because when using fonts on the web that are not installed in the user's computer already, the web fonts have to be downloaded when the web page downloads. Keeping the file sizes as small as possible can allow the pages to load quickly and not let the user wait for too long. This is one reason to use the web open font format.

Another reason has to do with licensing. People who are licensing their fonts generally don't want people putting the TTF or OTF versions of them up on the web where other people could download them and install them on their computers and use them without buying a license to use them.

To use these fonts, put the WOFF and WOFF files in the folder of your website. Then, copy the @font-face rules in `stylesheet.css` and paste them to the top of your website's stylesheet. Putting them at the top makes the fonts load as early as possible. Remember to adjust the file locations to where the WOFF files actually are.

![3](https://live.staticflickr.com/65535/53851446643_6bbbc04591_o.png)

In `src`, when the browser see the WOFF2 format, it will download that file if supported by the browser. If it doesn't it will proceed to download the WOFF file.

Now, we can use the fonts. In this example, we will use it on `<h1>` and `<body>`. Also, set up backup fonts.

```css
body {
  max-width: 600px;
  margin: auto;
  font-family: freightround_prolight, Arial, sans-serif;
}

h1 {
  font-family: freightround_probold, Arial, sans-serif;
}
```

![4](https://live.staticflickr.com/65535/53851619355_fbe3e89b08_o.png)

If not going to use a certain typeface, say `freightround_probook`, comment it out for optimization so that the browser is not forced to download it. This is wasting bandwidth.

#### Google Fonts
The above is the way to load fonts manually. This can be used when, for example, working with a client who has a specific font to use. However, there are also services that make it easier to load fonts. One is Adobe Fonts. Another great one is [Google Fonts](https://fonts.google.com/).

Select a font and click `Get Font`. Say we use MerriWeather Regular 400. Then, click on `Get embed code`.

![5](https://live.staticflickr.com/65535/53851619340_7d60837cfc_o.png)

Embed the code in the `<head>` of the html. Put it before the stylesheet to make it load faster.

```html
<head>
  <meta charset="UTF-8">
  <title>Font Test Page</title>

  <!-- Google Fonts -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Merriweather&display=swap" rel="stylesheet">

  <!-- My Styles -->
  <link href="styles.css" rel="stylesheet">
</head>
```

The `preconnect` is to connect to Google Fonts to try to download the file as quickly as possible. The last link is where the font download really is.

To use it on `<body>`:
```css
body {
  max-width: 600px;
  margin: auto;
  font-family: "Merriweather", serif;
}
```

![6](https://live.staticflickr.com/65535/53851548124_000f8c60dd_o.png)

Right-click at the page and click `View Page Source`. Then, click on the Merriweather Google API font link.

![7](https://live.staticflickr.com/65535/53851446633_d635a57fda_o.png)

These are the @font-face rules. These are using the same techniques when using the fonts locally. It is just Google is now hosting the font and we are linking to their @font-face rules and downloading the font from them on the fly.

As a side note, you can actually also download the Google Fonts and use them locally.

To use more than one font, for example, adding the Bold 700. Notice that the preconnect links stay the same. Only the last link tag in the embed code has changed.

![8](https://live.staticflickr.com/65535/53851619335_dc671ccf19_o.png)

```html!
<link href="https://fonts.googleapis.com/css2?family=Merriweather:wght@400;700&display=swap" rel="stylesheet">
```

To use it the Bold 700 on the `<footer>` and Regular 400 on the `<body>`:
```css
body {
  max-width: 600px;
  margin: auto;
  font-family: "Merriweather", serif;
  font-weight: 400;
}

footer p {
  font-weight: 700;
}
```

![9](https://live.staticflickr.com/65535/53851446628_4c677c4b42_o.png)

Just like the fonts that were loaded locally, only load the fonts that are actually going to be used. In this example, only load Regular 400 and Bold 700.

The preconnect script is an attempt to get fonts to download faster. There is a situation that sometimes happens where the website load, then a couple seconds later, the font loads and then everything in the page shifts. This is called FOUT, flash of unformatted text.

Side note: Sometimes to see the changes on the `github.io` website after pushing the updates, have to force reload the stylesheet by holding down the refresh button and click `Empty Cache and Hard Reload`.

#### Icon Fonts
Most popular website for this is [Font Awesome](https://fontawesome.com/icons). Sign up for an account to receive a free kit.

![10](https://live.staticflickr.com/65535/53851619320_f6ca9c02e0_o.png)

Set up icons in a project with one line of code. Copy the kit's unique embed code into the HTML's `<head>`.

![11](https://live.staticflickr.com/65535/53851183991_38de3a3edd_o.png)

To use the icons, click on `30,199 total icons in Font Awesome 6 Pro`:
![12](https://live.staticflickr.com/65535/53851548114_abac0a7764_o.png)

Click on an icon and copy the HTML code snippet:
![13](https://live.staticflickr.com/65535/53851548119_2843ba70d6_o.png)

```html
<body>
  <div class="icons">
    <i class="fa-solid fa-house"></i>
  </div>
</body>
```

![14](https://live.staticflickr.com/65535/53851619300_44186ab673_o.png)

Because this is a font, you can do all the normal things that you can do with fonts such as changing color and size.

Add this to `styles.css`:
```css
.icons {
  font-size: 32px;
  color: pink;
}
```

![15](https://live.staticflickr.com/65535/53850290617_607727df6f_o.png)


## Advanced Web Fonts

Notice that in Google Fonts there are variable fonts with 2 or 3 axes.
![16](https://live.staticflickr.com/65535/53851548094_a6fa7673b5_o.png)

### Beware of File Sizes
Variable fonts provide more options to the designer, but they come at a cost: The file sizes are larger.

Only use variable options if you need them to realize your designs! Stick to static fonts first.

### Montserrat File Sizes
If you download the Montserrat font from Google Fonts, you can see the file sizes of the fonts. The variable weight fonts are worth two of any of the other static sizes.

![17](https://live.staticflickr.com/65535/53850290612_c16e3b44af_o.png)

Note these are TTF files. The actual `.woff2` files will be significantly compressed.

When using variable fonts, we want to get the entire range. There is no reason to get less than the entire range since it is going to be one file anyway.

In the type tester, we can see that as a variable font, there are two axes, one is italic (0 off or 1 on) and the other is the weight (any number in the range 100 to 900). This gives a lot of flexibility for designers.

![18](https://live.staticflickr.com/65535/53851619295_05d84023e0_o.png)

![19](https://live.staticflickr.com/65535/53850290607_b0f229e406_o.png)

Copy the embed code to the HTML file.

![20](https://live.staticflickr.com/65535/53851619290_435882d0a7_o.png)

```html!
<link href="https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@0,100..900;1,100..900&display=swap" rel="stylesheet">
```

You can now use italics or not and any weight between 100 and 900.

```css
body {
  max-width: 600px;
  margin: auto;
  font-family: "Montserrat", serif;
	font-style: italic;
  font-weight: 236;
}
```

![21](https://live.staticflickr.com/65535/53851183961_66eab78b5c_o.png)

### Addtional Axes
Weight is the most common axis, however some fonts come with additional axes that you can use to further adjust the font.

This is the cutting edge of font design.

Check out some fonts you can download on [v-fonts.com](https://v-fonts.com). Click on license and choose open source to see some available fonts.

Notice that many of the fonts, like Robot Serif, have multiple axes.

![22](https://live.staticflickr.com/65535/53851619255_89d298682a_o.jpg)

### Roboto Serif on GitHub
Click on the GitHub link on the v-fonts page for Roboto Serif to go to the files on GitHub. If you dig into the files, you will see the variable fonts are there and in both TTF and WOFF formats.

Download the RobotoSerif woff2 font and add it to the fonts folder .

![23](https://live.staticflickr.com/65535/53851548049_6bf6b65ceb_o.png)

Add this @font-face rule to the top of the stylesheet. Note that instead of `normal`, the font weight axis declaration is set to 100 to 900, which matches the available weights. Also, `font-display: swap` is included for variable fonts.

```css
@font-face {
  font-family: 'Roboto Serif';
  src: url('fonts/RobotoSerif[grad\,opsz\,wdth\,wgth].woff2') format('woff2');
  font-weight: 100 900;
  font-style: normal;
  font-display: swap;
}
```

To use it:
```css
body {
  max-width: 600px;
  margin: auto;
  font-family: 'Roboto Serif', serif;
  font-weight: 333;
}
```

![24](https://live.staticflickr.com/65535/53851183951_df07fe7204_o.png)

Other axes are also available for access. This [web application](https://) is very helpful for accessing other axes of variable fonts.

![25](https://live.staticflickr.com/65535/53850290577_85a7dabf9f_o.jpg)

Drop your `.woff2` file on the circle in the middle, wait for it to load then scroll down the page to get information about the font.

![26](https://live.staticflickr.com/65535/53851619240_53b82768ef_o.png)

When you scroll down the page, you will get this interface for setting the different axes, with a demo of how the font will look with those settings.

![27](https://live.staticflickr.com/65535/53851446608_2b34c77734_o.png)

To use the setting, copy the line of code:
```css
"wdth" 100, "opsz" 20, "wght" 400, "GRAD" 0
```

Put them in a font-variation-settings declaration:
```css
body {
  max-width: 600px;
  margin: auto;
  font-family: 'Roboto Serif', serif;
  font-variation-settings: "wdth" 100, "opsz" 20, "wght" 400, "GRAD" 0;
}
```

![28](https://live.staticflickr.com/65535/53851446603_a868469f03_o.png)

Some axes are in lowercase letters and some are in uppercase letters. The ones that are in lowercase letters are supposed to be CSS settings, which can set indivdually. The ones in uppercase letters cannot.

This has the same affects:
```css
body {
  max-width: 600px;
  margin: auto;
  font-family: 'Roboto Serif', serif;
  font-weight: 400;
  font-variation-settings: "wdth" 100, "opsz" 20, "GRAD" 0;
}
```

Can actually animate these properties, which would be in future courses.

## General Advice for Design for the Web
### Typography
* **Avoid Long Lines of Text** - Keep lines of text to approximately 65 characters (depending on typeface, color, spacing and other factors.
* **Avoid Centered Paragraphs** - Do not center align paragraphs of text. Only 3 short lines of text or less for centered text.
* **Use Greater Line Spacing** - Generally a little more line spacing is better on the web for paragraph text. Add a bit of additional line height. Usually 1.4 - 1.6 em is good, depending on typeface, color, size and other factors.
* **Avoid Walls of Text** - No one will read it on the web. Keep paragraphs short and use type hiearchy to break it up (headers, subheaders, etc.).
* **Increase Spacing on Bulleted Text** - If you are using bulleted text of any sort, provide extra spacing if the bulleted text wraps (runs longers than one line).
* **Avoid Contrast Issues** - Avoid low contrast between text and background. Designers like subtle color contrasts, but they can make your design less usable.

### Layout
* **Consistent Spacing** - Use consistent spacing between elements. Be sure to create line alignments that don't make your design messy or confusing.
* **Respect the Radius** - If you use rounded boxes, respect the border radius space.
* **Beware of the Horizontal Rule** - In print, horizontal rules are used to separate items when you have limited space. On the web, space is not limited. If you find yourself using horizontal rules to separate content, see if your spacing needs work.
