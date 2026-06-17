# Jester's CSS Framework v0.1 (early stages)

A *very* simple CSS Framework for vanilla CSS development.

> [!IMPORTANT]
> The CSS file has fields that can be tweaked to your convenience. What can be tweaked will be shown through NOTE shoutouts.

## Basic Methodology Breakdown

I call this a framework, but it's more like a methodology that happens to come with helper classes. *You* should ultimately be responsible for what this simple CSS file does, and if you should follow the methodology breakdown or not. It is fully up to your discretion.

Super basic explanation. This framework uses a tweaked **[BEM](https://bem.info/en/)** methodology.

- Classes prefaced by `_`, example, `._foo`, expect a context size.
- Classes prefaced by `--`, example, `.--bar`, are utility classes, which does not exist in BEM. They are used in any part of the code base.

## What is a Context?

Context is the current information given for that particular state, shared amongst any other children within that state.

It is particularly useful for consistent styling, in this particular *context*, size styling!

- `--size` is defined by providing a context class.. by default it is `--size-context-rg`. The context will provide a size relative to its class name, that is responsive by nature.
- `--size` variable should be used for defining responsive sizes within an application, and can be slightly offset by using `calc`.

> [!NOTE]
> To tweak global sizes, look at `:root` definition.

```css
:root {
  --base-size: 0.75rem;
  --base-response: 1.5vw;

  /* ratio multiplier between sizes */
  --size-scale-down-ratio: 0.8rem;
  --size-scale-up-ratio: 1.2rem;

  /* ... */
```
| Variable Name | Description |
| -------------- | --------------- |
| `--base-size` | The base defined size. |
| `--base-response` | Responsive size to be added to base size. |
| `--size-scale-down-ratio` | Multiplier for context sizes below rg|
| `--size-scale-up-ratio` | Multiplier for context sizes above rg |

## Why text classes?

If there is one consistent thing about a application, it *should* be text. Text classes exist to standardize the styling of texts to only a few options, nothing more!

- `._text` class should be used for *any* text on a page. Since it is prefaced by `_` it expects a context size to be defined.

```css
._text {
  font-family:
    var(--_font-family), system-ui, "Segoe UI", Roboto, Helvetica, Arial,
    sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol";
  font-size: var(--size);
  font-weight: normal;
}
```

It also has class modifiers, following BEM methodologies.

- `._text._text--bold` makes font bold
- `._text._text--italic` makes font italic

> [!NOTE]
> The `--_font-family` variable is not initially defined as it is up to your discretion!

Take the foo class definition for example.

```css
._text._text--foo {
  --_font-family: var(--_foo-bar-family);
}
```
the font face would be defined as such.

```css
@font-face {
  --_foo-font-family: "foo";
  font-family: var(--_foo-font-family);
  src:
    url("foo.woff2") format("woff2"),
    url("foo.woff") format("woff");
  font-weight: normal;
  font-style: normal;
}
```

> [!IMPORTANT]
> Remember, always try to opt for **semantic class names!** For example. instead of `._text._text--foo` it could be `._text._text--header` which actually has usage meaning.
