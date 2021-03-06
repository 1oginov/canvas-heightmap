# canvas-heightmap

[![npm](https://img.shields.io/npm/v/canvas-heightmap)](https://www.npmjs.com/package/canvas-heightmap)
[![CI](https://github.com/loginov-rocks/canvas-heightmap/actions/workflows/ci.yml/badge.svg)](https://github.com/loginov-rocks/canvas-heightmap/actions/workflows/ci.yml)
[![CD](https://github.com/loginov-rocks/canvas-heightmap/actions/workflows/cd.yml/badge.svg)](https://github.com/loginov-rocks/canvas-heightmap/actions/workflows/cd.yml)
[![Coverage Status](https://coveralls.io/repos/github/loginov-rocks/canvas-heightmap/badge.svg?branch=main)](https://coveralls.io/github/loginov-rocks/canvas-heightmap?branch=main)

Canvas Heightmap is a package to **get images data by pixels, channels or average in different representations** that
can be used to build heightmaps.

## Quick Start

### Install

```sh
npm install canvas-heightmap
```

### Use

```js
const ch = new CanvasHeightmap();

// At first set the source and wait until it would be loaded.
ch.use('https://raw.githubusercontent.com/loginov-rocks/canvas-heightmap/master/test/resources/black-and-white.png').
    then(() => {
      // Secondly invoke draw method to render image to be able to get its data.
      ch.draw();
      // Eventually you can get needed data.
      const flatArray = ch.getFlatArray();
      const rgbaArray = ch.getRgbaArray();
    });
```

## API

### `CanvasHeightmap`

Canvas Heightmap class.

**Kind**: global class

* [CanvasHeightmap](#canvasheightmap)
  * [new CanvasHeightmap()](#new-canvasheightmap)
  * [use(source) ⇒ Promise.&lt;HTMLImageElement|HTMLCanvasElement&gt;](#usesource--promisehtmlimageelementhtmlcanvaselement)
  * [draw() ⇒ HTMLCanvasElement](#draw--htmlcanvaselement)
  * [getFlatArray([sx], [sy], [sw], [sh]) ⇒ Uint8ClampedArray](#getflatarraysx-sy-sw-sh--uint8clampedarray)
  * [getFlatAverageArray([sx], [sy], [sw], [sh]) ⇒ Uint8ClampedArray](#getflataveragearraysx-sy-sw-sh--uint8clampedarray)
  * [getFlatChannelArray(channel, [sx], [sy], [sw], [sh]) ⇒ Uint8ClampedArray](#getflatchannelarraychannel-sx-sy-sw-sh--uint8clampedarray)
  * [getFlatRgbaArray([sx], [sy], [sw], [sh]) ⇒ Array.&lt;Uint8ClampedArray&gt;](#getflatrgbaarraysx-sy-sw-sh--arrayuint8clampedarray)
  * [getAverageArray([sx], [sy], [sw], [sh]) ⇒ Array.&lt;Uint8ClampedArray&gt;](#getaveragearraysx-sy-sw-sh--arrayuint8clampedarray)
  * [getChannelArray(channel, [sx], [sy], [sw], [sh]) ⇒ Array.&lt;Uint8ClampedArray&gt;](#getchannelarraychannel-sx-sy-sw-sh--arrayuint8clampedarray)
  * [getRgbaArray([sx], [sy], [sw], [sh]) ⇒ Array.&lt;Array.&lt;Uint8ClampedArray&gt;&gt;](#getrgbaarraysx-sy-sw-sh--arrayarrayuint8clampedarray)

---

#### `new CanvasHeightmap()`

Canvas Heightmap constructor.

---

#### `use(source)` ⇒ `Promise.<HTMLImageElement|HTMLCanvasElement>`

Set canvas image source.

**Kind**: instance method of `CanvasHeightmap`

| Parameter | Type                                                          |
| --------- | ------------------------------------------------------------- |
| source    | `string` &#124; `HTMLImageElement` &#124; `HTMLCanvasElement` |

---

#### `draw()` ⇒ `HTMLCanvasElement`

Draw image source on canvas.

**Kind**: instance method of `CanvasHeightmap`

---

#### `getFlatArray([sx], [sy], [sw], [sh])` ⇒ `Uint8ClampedArray`

Get one-dimensional array containing the data in the RGBA order, with integer values between 0 and 255 (included).

**Kind**: instance method of `CanvasHeightmap`

**See**:
* https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/getImageData
* https://developer.mozilla.org/en-US/docs/Web/API/ImageData/data

| Parameter | Type     | Default        | Description                                                                                       |
| --------- | -------- | -------------- | ------------------------------------------------------------------------------------------------- |
| [sx]      | `number` | `0`            | The x coordinate of the upper left corner of the rectangle from which the data will be extracted. |
| [sy]      | `number` | `0`            | The y coordinate of the upper left corner of the rectangle from which the data will be extracted. |
| [sw]      | `number` | `this._width`  | The width of the rectangle from which the data will be extracted.                                 |
| [sh]      | `number` | `this._height` | The height of the rectangle from which the data will be extracted.                                |

---

#### `getFlatAverageArray([sx], [sy], [sw], [sh])` ⇒ `Uint8ClampedArray`

Get one-dimensional array containing the data by pixels with average over RGB channels, with integer values between 0
and 255 (included).

**Kind**: instance method of `CanvasHeightmap`

| Parameter | Type     | Default        | Description                                                                                       |
| --------- | -------- | -------------- | ------------------------------------------------------------------------------------------------- |
| [sx]      | `number` | `0`            | The x coordinate of the upper left corner of the rectangle from which the data will be extracted. |
| [sy]      | `number` | `0`            | The y coordinate of the upper left corner of the rectangle from which the data will be extracted. |
| [sw]      | `number` | `this._width`  | The width of the rectangle from which the data will be extracted.                                 |
| [sh]      | `number` | `this._height` | The height of the rectangle from which the data will be extracted.                                |

---

#### `getFlatChannelArray(channel, [sx], [sy], [sw], [sh])` ⇒ `Uint8ClampedArray`

Get one-dimensional array containing the data for specified channel, with integer values between 0 and 255 (included).

**Kind**: instance method of `CanvasHeightmap`

| Parameter | Type     | Default        | Description                                                                                       |
| --------- | -------- | -------------- | ------------------------------------------------------------------------------------------------- |
| channel   | `string` |                | Channel: `red`, `green`, `blue` or `alpha`.                                                       |
| [sx]      | `number` | `0`            | The x coordinate of the upper left corner of the rectangle from which the data will be extracted. |
| [sy]      | `number` | `0`            | The y coordinate of the upper left corner of the rectangle from which the data will be extracted. |
| [sw]      | `number` | `this._width`  | The width of the rectangle from which the data will be extracted.                                 |
| [sh]      | `number` | `this._height` | The height of the rectangle from which the data will be extracted.                                |

---

#### `getFlatRgbaArray([sx], [sy], [sw], [sh])` ⇒ `Array.<Uint8ClampedArray>`

Get two-dimensional array containing the data by pixels and RGBA array for each, with integer values between 0 and 255
(included).

**Kind**: instance method of `CanvasHeightmap`

| Parameter | Type     | Default        | Description                                                                                       |
| --------- | -------- | -------------- | ------------------------------------------------------------------------------------------------- |
| [sx]      | `number` | `0`            | The x coordinate of the upper left corner of the rectangle from which the data will be extracted. |
| [sy]      | `number` | `0`            | The y coordinate of the upper left corner of the rectangle from which the data will be extracted. |
| [sw]      | `number` | `this._width`  | The width of the rectangle from which the data will be extracted.                                 |
| [sh]      | `number` | `this._height` | The height of the rectangle from which the data will be extracted.                                |

---

#### `getAverageArray([sx], [sy], [sw], [sh])` ⇒ `Array.<Uint8ClampedArray>`

Get two-dimensional array containing the rows and cols data by pixels with average over RGB channels, with integer
values between 0 and 255 (included).

**Kind**: instance method of `CanvasHeightmap`

| Parameter | Type     | Default        | Description                                                                                       |
| --------- | -------- | -------------- | ------------------------------------------------------------------------------------------------- |
| [sx]      | `number` | `0`            | The x coordinate of the upper left corner of the rectangle from which the data will be extracted. |
| [sy]      | `number` | `0`            | The y coordinate of the upper left corner of the rectangle from which the data will be extracted. |
| [sw]      | `number` | `this._width`  | The width of the rectangle from which the data will be extracted.                                 |
| [sh]      | `number` | `this._height` | The height of the rectangle from which the data will be extracted.                                |

---

#### `getChannelArray(channel, [sx], [sy], [sw], [sh])` ⇒ `Array.<Uint8ClampedArray>`

Get two-dimensional array containing the rows and cols data for specified channel, with integer values between 0 and 255
(included).

**Kind**: instance method of `CanvasHeightmap`

| Parameter | Type     | Default        | Description                                                                                       |
| --------- | -------- | -------------- | ------------------------------------------------------------------------------------------------- |
| channel   | `string` |                | Channel: `red`, `green`, `blue` or `alpha`.                                                       |
| [sx]      | `number` | `0`            | The x coordinate of the upper left corner of the rectangle from which the data will be extracted. |
| [sy]      | `number` | `0`            | The y coordinate of the upper left corner of the rectangle from which the data will be extracted. |
| [sw]      | `number` | `this._width`  | The width of the rectangle from which the data will be extracted.                                 |
| [sh]      | `number` | `this._height` | The height of the rectangle from which the data will be extracted.                                |

---

#### `getRgbaArray([sx], [sy], [sw], [sh])` ⇒ `Array.<Array.<Uint8ClampedArray>>`

Get three-dimensional array containing the rows and cols data by pixels and RGBA array for each, with integer values
between 0 and 255 (included).

**Kind**: instance method of `CanvasHeightmap`

| Parameter | Type     | Default        | Description                                                                                       |
| --------- | -------- | -------------- | ------------------------------------------------------------------------------------------------- |
| [sx]      | `number` | `0`            | The x coordinate of the upper left corner of the rectangle from which the data will be extracted. |
| [sy]      | `number` | `0`            | The y coordinate of the upper left corner of the rectangle from which the data will be extracted. |
| [sw]      | `number` | `this._width`  | The width of the rectangle from which the data will be extracted.                                 |
| [sh]      | `number` | `this._height` | The height of the rectangle from which the data will be extracted.                                |
