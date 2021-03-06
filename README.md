# `dab`

- Create images in any color
- Convert image filetypes
- Resize images

## node usage

```bash
npm install @s9a/dab
```

```js
const dab = require("@s9a/dab")
```

```js
dab(deets, callback=dab.terse)
```

### `deets`

#### properties

- <b>`from`</b> is a filename <b>or</b> color format
  - Default is `"#dab"`
  - Supports `png` `gif` `tif` `jpg` `webp` `svg`
  - Supports hexes and named colors or `rgb` `hsl` with commas
- <b>`to`</b> is the filename to save to
  - Default is like `[from]_[shape].png`
  - Supports `png` `tif` `jpg` `webp`
- <b>`shape`</b> is desired dimensions in pixels
  - Supports [wtb formats](https://github.com/ryanve/wtb/blob/master/README.md)
  - Default is `960` aka `"960"` aka `"960x960"` aka `[960, 960]`


#### create png from color

```js
dab({
  from: "#bae",
  to: "bae.png",
  shape: "1280x640",
})
```

#### convert jpg to webp

```js
dab({
  from: "foto.jpg",
  to: "foto.webp",
  shape: "1280x640",
})
```

### `callback`

- `callback` may be custom or [preset](#callback-presets)
- `callback` defaults to `dab.terse`


```js
dab({})
```

```js
dab({}, dab.verbose)
```

```js
dab({}, (err, did) => {
  if (err) throw err
  console.log(did)
})
```

#### [callback presets](radio.js)

- `dab.verbose` verbose info
- `dab.terse` terse info
- `dab.quiet` only warnings or errors
- `dab.silent` nothing

## CLI

### syntax

```bash
dab [from] [to] [shape]
```

- supports the same [properties](#properties) as the node syntax
- `from` can be a filename or [color format](#hexes)
- `to` can be a filename
- shape Dimension syntax is <code><var>width</var><b>x</b><var>height</var></code> or just `width` for square

### hexes

* **Good:** `"#000"` `'#000'` `\#000` `"rgb(0, 0, 0)"` `"black"` `'black'` `black`
* **Fails:** `#000` `rgb(0, 0, 0)`
* CLI sees **#** as comment if seen without quotes or backslash
* CLI honors **alphabet** hexes like `#bed` as `bed` as shorthand but **not** like `b3d`

### flags

- `--help`
- `--silent`
- `--quiet`
- `--terse` default
- `--verbose`

### `node` `npm` `npx`

[<b>node installers</b>](https://nodejs.org/en/download/) provide `node` `npm` `npx`

versions are checkable via your command line

```bash
node -v
npm -v
npx -v
```

## CLI examples

- [temporary](#temporary)
- [project](#project)
- [clone](#clone)
- [global](#global)

### temporary

- `npx` lets you dab on the fly with the scoped package name `@s9a/dab`
- Easy way to try dab **without** saving the package

```bash
npx @s9a/dab "#dab" dab.png 1280
npx @s9a/dab "#dab" dab.png 1280x640
npx @s9a/dab "lime" 1280
npx @s9a/dab "lime" 1280x640
npx @s9a/dab "rgb(0, 255, 0)" 1280x640
```

### project

- You can save `@s9a/dab` as a project dependency
- Recommended when you wanna dab in a project
- First create `package.json` via `npm init` or manually

```bash
npm install @s9a/dab
```

```bash
npx dab "#dab" dab.png 1280
npx dab "#dab" dab.png 1280x640
npx dab "lime" 1280
npx dab "lime" 1280x640
npx dab "rgb(0, 255, 0)" 1280x640
```

### clone

- Cloning the repo is another way to dab
- This'll create a folder where you can dab

```bash
git clone git@github.com:s9a/dab.git #team
git clone https://github.com/s9a/dab.git #guest
cd dab
npm install
npm test
```

```bash
npx . "#dab" dab.png 1280
npx . "#dab" dab.png 1280x640
npx . "lime" 1280
npx . "lime" 1280x640
npx . "rgb(0, 255, 0)" 1280x640
```

### global

- This is how to install `dab` as global command
- Recommended when you wanna dab anywhere and have access
- May need `--unsafe-perm` to build dependencies

```bash
npm install @s9a/dab --global #admin
sudo npm install @s9a/dab --global #user
```

```bash
dab "#dab" dab.png 1280
dab "#dab" dab.png 1280x640
dab "lime" 1280
dab "lime" 1280x640
dab "rgb(0, 255, 0)" 1280x640
```

#### uninstall whenever

```bash
npm uninstall @s9a/dab --global
```
