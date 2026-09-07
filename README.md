# Aaron Jones Artist Website — Editing Guide

This website is intentionally simple. You can edit it in Visual Studio Code without installing anything or running commands.

## 1. Keep the website folder organized

Keep these files together:

```text
artist-site/
├── index.html
├── style.css
├── cv.pdf
├── landing-01.mp4
├── landing-02.mp4
├── landing-03.mp4
├── my-font.woff2              (optional)
└── images/
    ├── 2026-installation-01.webp
    ├── 2026-installation-02.webp
    ├── 2026-framed-01.webp
    └── ...
```

- `index.html` contains the text, links, years, video information and image lists.
- `style.css` controls fonts, colours, sizing, spacing, transparency and mobile layout.
- `cv.pdf` is displayed in the CV popup and can be downloaded by visitors.
- The `images` folder contains your installation and framed-work documentation.

Do not change a filename without also changing its matching name inside `index.html`.

## 2. Open and preview the website

1. Open the `artist-site` folder in Visual Studio Code.
2. Double-click `index.html` in Finder to open it in your browser.
3. After making a change, save the file with `Command + S`.
4. Refresh the browser with `Command + R`.

If a change does not appear, confirm that you saved the file and are opening the correct copy of `index.html`.

## 3. Enter the landing-video information

Open `index.html` and find:

```text
EDIT 8: VIDEO FILENAMES + INFORMATION
```

Each video has four editable parts:

```javascript
{
  filename: "landing-01.mp4",
  title: "Video Title One",
  details: "2026 — Exhibition Name, City"
}
```

Replace only the text inside quotation marks. Example:

```javascript
{
  filename: "landing-01.mp4",
  title: "Wandering",
  details: "2023 — The Robert McLaughlin Gallery, Oshawa"
}
```

Important:

- Keep the quotation marks, commas, colons and braces.
- The filename must match the actual video exactly, including capital letters.
- A different video is selected randomly on each consecutive page load.
- The same video will not appear twice in a row during the same browser session.
- Clicking **Next film** loads the next video.
- The title and details appear for 4.5 seconds when a video starts. Each line independently switches to black or white according to the video directly beneath it.

### Add another landing video

1. Put the new MP4 in the website folder.
2. Add a comma after the previous video object.
3. Add another object:

```javascript
{
  filename: "landing-04.mp4",
  title: "Fourth Video Title",
  details: "2022 — Exhibition Name, City"
}
```

The website automatically includes it in the random selection. It will not display a video count.

## 4. Edit the Work years

Open `index.html` and find:

```text
EDIT 4: WORK SECTION
```

Each year is written in one row:

```html
<li class="year-row">
  <button class="year-toggle" type="button" aria-expanded="false">2026</button>
  <div class="year-options">
    <button type="button" data-year="2026" data-view="installation">Installation</button>
    <button type="button" data-year="2026" data-view="framed">Framed</button>
  </div>
</li>
```

If you change a year, change it in all three places in that row:

- The visible year between `>` and `<`
- `data-year` on the Installation button
- `data-year` on the Framed button

## 5. Enter documentation images

Open `index.html` and find:

```text
EDIT 9: DOCUMENTATION IMAGE FILES
```

The files are organized by year and then by `installation` or `framed`:

```javascript
"2026": {
  installation: [
    "images/2026-installation-01.webp",
    "images/2026-installation-02.webp"
  ],
  framed: [
    "images/2026-framed-01.webp",
    "images/2026-framed-02.webp"
  ]
}
```

### Add an image

1. Put the image inside the `images` folder.
2. Add a comma after the previous filename.
3. Add the new filename inside quotation marks:

```javascript
installation: [
  "images/2026-installation-01.webp",
  "images/2026-installation-02.webp",
  "images/2026-installation-03.webp"
]
```

### Remove an image

Delete its complete filename line. Make sure the final remaining filename does not require a comma after it.

You may use `.webp`, `.jpg`, `.jpeg` or `.png`, but the extension inside the code must match the real file.

Recommended image preparation:

- WebP format
- Approximately 2,000 pixels on the longest side
- Clear filenames containing the year and category
- Avoid spaces and special characters in filenames

## 6. Replace the CV

1. Name your PDF `cv.pdf`.
2. Put it beside `index.html`.

The CV links, viewer and download button will then work automatically.

If you use another filename, such as `aaron-jones-cv.pdf`, replace every occurrence of `cv.pdf` inside `index.html`.

## 7. Edit the About text

Open `index.html` and find:

```text
EDIT 5: ABOUT SECTION
```

Replace the Lorem Ipsum text between `<p>` and `</p>` with your biography. Keep the opening `<p>` and closing `</p>`.

Example:

```html
<p>
  Aaron Jones is a Toronto-based visual artist working across collage,
  photography, moving image, sound and installation.
</p>
```

## 8. Edit navigation, ticker and links

The top navigation is labelled:

```text
EDIT 2: NAME + TOP NAVIGATION
```

The bottom ticker is labelled:

```text
EDIT 4: BOTTOM TICKER
```

The ticker contains two matching groups to create a seamless loop. Make the same changes in both groups.

### Email link

Replace:

```html
href="mailto:YOUR-EMAIL-HERE"
```

with:

```html
href="mailto:yourname@example.com"
```

### External website link

Use the complete address:

```html
href="https://www.example.com/"
```

Keep `target="_blank"` when you want an external link to open in a new tab.

## 9. Change fonts

Open `style.css` and find:

```text
EDIT A: FONTS
```

### Use a common computer font

Change:

```css
--main-font: Arial, Helvetica, sans-serif;
```

For example:

```css
--main-font: Georgia, "Times New Roman", serif;
```

### Use your own font file

1. Put a `.woff2` font file inside the website folder.
2. Add this near the top of `style.css`:

```css
@font-face {
  font-family: "My Font";
  src: url("my-font.woff2") format("woff2");
  font-weight: normal;
  font-style: normal;
  font-display: swap;
}
```

3. Change the main-font variable:

```css
--main-font: "My Font", Arial, sans-serif;
```

The spelling of `My Font` must match in both places.

## 10. Change video size and colours

At the top of `style.css`, find the variables inside `:root`.

### Desktop video width

```css
--desktop-video-width: 68vw;
```

- Smaller video: try `60vw`.
- Larger video: try `75vw`.
- This setting does not make the mobile video narrower.

### Maximum desktop width

```css
--desktop-video-maximum: 1050px;
```

This prevents the video from becoming too large on wide or tall desktop displays.

### Page colours

```css
--background-colour: #f7f7f4;
--text-colour: #0b0b0b;
```

The Work and About sections are completely transparent. All website text is solid black by default. A text element switches to solid white only while its centre is positioned inside the visible video window. As the video shrinks, the text colour is recalculated. There is no blend-mode inversion, outline, shadow, tint or text box.

## 11. Change ticker speed

Find:

```css
--ticker-speed: 34s;
```

- Larger number = slower movement
- Smaller number = faster movement

Try `45s` for slower or `25s` for faster.

## 12. How scrolling and clicking work

- The video is fixed underneath the rest of the website.
- Work and About scroll over the video with transparent backgrounds.
- All text is solid black unless its centre is inside the visible video window, where it switches to solid white.
- The fixed video smoothly shrinks from full size to 25% size during the first screen of scrolling, improving readability in Work and About.
- Empty transparent areas allow clicks to pass through to the video.
- Clickable year and category text takes priority wherever it overlaps the video.
- Installation or Framed opens the documentation popup.
- CV opens an in-window PDF viewer with a download button.
- Clicking outside a popup or pressing Escape closes it.

## 13. Mobile testing checklist

Test the website at narrow and wide sizes before publishing:

- Video reaches both edges of a phone screen.
- Sound and Next film buttons remain visible on touchscreens.
- Year options are easy to tap.
- Documentation images fit the popup width.
- CV opens and downloads correctly.
- Navigation does not overlap your name.
- Work and About text remains readable over every video.

You can test a narrow layout on desktop by making the browser window very narrow. Final testing should also be done on an actual phone.

## 14. Common problems

### A video or image does not appear

- Check spelling, capital letters and the file extension.
- Confirm the file is inside the correct folder.
- Do not use smart quotation marks such as `“ ”` inside code.
- Open the browser developer console if you need to find a missing filename.

### A section stops working after an edit

- Check that quotation marks and commas are still present.
- Check that every `{` has a matching `}`.
- Check that every `[` has a matching `]`.
- Undo your latest edit with `Command + Z`, save and refresh.

### The CSS does not update

- Confirm `index.html` still contains `<link rel="stylesheet" href="style.css">`.
- Confirm the file is named exactly `style.css`.
- Save the CSS file and refresh the browser.

### The CV downloads but does not display

Some browsers restrict PDF viewing when opening a website directly from Finder. Test again after the website has been uploaded to your web host. The download button should still work.
