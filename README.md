# Jester's CSS Framework v2 (post-test release)

A *very* simple CSS Framework for vanilla CSS development.

> [!IMPORTANT]
> The CSS file is **meant** to be tweaked to your preferences. What can be tweaked is listed below.

## Why?

This is ultimately my own mixed methodology vomited on to a re-usable CSS document. It's mainly for the convenience of my development, but also to solve the problem of inconsistencies in foundational CSS design by giving a clear cut, extremely simple framework to work with.

## Methodologies

This project uses **[BEM (Block Element Modifier)](https://bem.info/en/)** methodology for naming classes in my CSS document. I did, however, add my own changes to the methodology.

- Classes prefaced by `_`, example, `._foo`, expect a size context.
- Classes prefaced by `--`, example, `.--bar`, are utility classes. They can be used anywhere in the structure, and do not belong to a block element 

> [!NOTE]
> Knowing BEM is NOT required to use this framework. Use it however you like! However, I personally find it useful for my own methodologies, and would recommend anyone to check it out.

## Size Context

Context is the current information given for that particular state, shared amongst any other children within that state.

The reason why we have size context is simple, size consistency. Of course we can define our individual font sizes, widths, heights, etc.. But being able to scale from one source of truth i.e. the `--size` variable, makes grouped items scale relatively to the same source.

- The `--size` variable is defined when you provide a context class. It is set to a sizing unit.
- For tuning the size, you can utilize `calc()` by doing `calc(var(--size) * 0.8)`

To edit the default values, edit this field in the css document.
```css
:root {
  /* === SIZE CONTEXT TUNER VARIABLES === */

  /* base variables 
  - static variables all sizes are based off of */
  --base-size: 1rem;
  --base-response: 1vw;
  --base-static-multiplier: 2.5; /* increase static regular base */

  /* clamp multipliers
  - determine ratio relative to base to clamp */
  --lower-clamp-ratio: 0.5;
  --higher-clamp-ratio: 2;

  /* scale multipliers 
   - the ratio of scale up/down for every size change */
  --size-scale-down-ratio: 0.8;
  --size-scale-up-ratio: 1.2;
  
  ...
}
```

## Text classes?

Text classes fall under the same reasoning as Size Contexts; consistency.

- `_text` class should be applied for any text, and or text based containers.

```css
._text {
  font-family:
    var(--font-family), system-ui, "Segoe UI", Roboto, Helvetica, Arial,
    sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol";
  font-size: var(--size);
  font-weight: normal;
}
```

It also has class modifiers, following BEM methodologies.

- `._text._text--bold` makes font bold
- `._text._text--italic` makes font italic

Notice the `--font-family` variable. On the document, there are commented out `@font-face` and `._text--foo` fields. These exist as example fiels, and could be subbed out with something like `--font-family: "abel"` with the class named as `._text--abel`.

```css
._text._text--abel-font {
  --_font-family: "abel";
}
```
the font face would be defined as such.

```css
@font-face {
  font-family: "abel";
  src:
    url("abel.woff2") format("woff2"),
    url("abel.woff") format("woff");
  font-weight: normal;
  font-style: normal;
}
```
> [!NOTE]
> Use semantic names! Your font family name could be named the font itself, `abel`, but use semantic class names! In this case, the class name can be `._text--header-font`.

## Color Themes?

I use [Realtime Colors generator](https://www.realtimecolors.com) which gives me the 5 color fields defined in the CSS file.

```css
:root {
  /* ... */

  /* light theme (default) */
  --text-color: #050316;
  --background-color: #fbfbfe;
  --primary-color: #2f27ce;
  --secondary-color: #dddbff;
  --accent-color: #443dff;
}

/* dark theme */
:root[data-theme="dark"] {
  --text-color: #eae9fc;
  --background-color: #010104;
  --primary-color: #3a31d8;
  --secondary-color: #020024;
  --accent-color: #0600c2;
}
```

> [!NOTE]
> For customization, just edit the `--*` fields for light theme and dark theme. You can easily just omit the dark theme by deleting the class definition, or keep adding more `data-theme` attribute definitions for more! Obviously if you want static color variables, just add your own as an independent variable in `:root`.
