# Emoji Picker React (v4) | [Live Demo](https://ealush.com/emoji-picker-react)

![Picker](https://user-images.githubusercontent.com/11255103/192167134-8205eb89-a71d-4463-8f3a-940e844917d5.gif)

## What to know before using

- This package assumes it runs in the browser. I have taken many steps to prevent it from failing on the server, but still, it is recommended to only render the component on the client. See troubleshooting section for more information.

## Installation

```
npm install emoji-picker-react
```

## Usage:

```jsx
import EmojiPicker from 'emoji-picker-react';

function App() {
  return (
    <div>
      <EmojiPicker />
    </div>
  );
}
```

## Shout Outs!

|                                                                                                 Component Design 🎨                                                                                                 |
| :-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
| <a href="https://pavelbolo.com" target="_blank">![317751726_1277528579755086_5320360926126813336_n copy](https://user-images.githubusercontent.com/11255103/205937426-a570b4a1-7243-4d3e-a7e5-ea04b61d940a.png)</a> |
|                                                                           <a href="https://pavelbolo.com" target="_blank">Pavel Bolo</a>                                                                            |

## Features

- Custom click handler
- Custom Emojis Support
- Dark mode
- Customizable styles via css variables
- Default skin tone selection
- Skin tone change
- Different emoji sets (Google, Apple, Facebook, Twitter)
- Native Emoji support
- Emoji Component To Render Emojis in your app

# Props

The following props are accepted by them picker:

| Prop                   | Type                                                   | Default    | Description                                                                                                                                |
| ---------------------- | ------------------------------------------------------ | ---------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| onEmojiClick           | function                                               |            | Callback function that is called when an emoji is clicked. The function receives the emoji object as a parameter.                          |
| autoFocusSearch        | boolean                                                | `true`     | Controls the auto focus of the search input.                                                                                               |
| Theme                  | string                                                 | `light`    | Controls the theme of the picker. Possible values are `light`, `dark` and `auto`.                                                          |
| emojiStyle             | string                                                 | `apple`    | Controls the emoji style. Possible values are `google`, `apple`, `facebook`, `twitter` and `native`.                                       |
| defaultSkinTone        | string                                                 | `neutral`  | Controls the default skin tone.                                                                                                            |
| lazyLoadEmojis         | boolean                                                | `false`    | Controls whether the emojis are loaded lazily or not.                                                                                      |
| previewConfig          | object                                                 | `{}`       | Controls the preview of the emoji. See below for more information.                                                                         |
| searchPlaceholder      | string                                                 | `Search`   | Controls the placeholder of the search input.                                                                                              |
| suggestedEmojisMode    | string                                                 | `frequent` | Controls the suggested emojis mode. Possible values are `frequent` and `recent`.                                                           |
| skinTonesDisabled      | boolean                                                | `false`    | Controls whether the skin tones are disabled or not.                                                                                       |
| searchDisabled         | boolean                                                | `false`    | Controls whether the search is disabled or not. When disabled, the skin tone picker will be shown in the preview component.                |
| skinTonePickerLocation | string                                                 | `SEARCH`   | Controls the location of the skin tone picker. Possible values are `SEARCH` and `PREVIEW`.                                                 |
| `width`                | `number`/`string`                                      | `350`      | Controls the width of the picker. You can provide a number that will be treated as pixel size, or your any accepted css width as string.   |
| emojiVersion           | `string`                                               | -          | Allows displaying emojis up to a certain version for compatibility.                                                                        |
| `height`               | `number`/`string`                                      | `450`      | Controls the height of the picker. You can provide a number that will be treated as pixel size, or your any accepted css height as string. |
| getEmojiUrl            | `Function`                                             | -          | Allows to customize the emoji url and provide your own image host.                                                                         |
| categories             | `Array`                                                | -          | Allows full config over ordering, naming and display of categories.                                                                        |
| customEmojis           | `Array<{names: string[], imgUrl: string, id: string}>` | -          | Allows adding custom emojis to the picker.                                                                                                 |

## Full details

- `onEmojiClick`: `(emojiData: EmojiClickData, event: MouseEvent) => void` - Callback function when an emoji is clicked. The callback receives the event and the emoji data. The emoji data is comprised of the following properties:

  ```ts
  {
    activeSkinTone: SkinTones;
    unified: string;
    unifiedWithoutSkinTone: string;
    emoji: string; // the emoji character, for example: '😀'. Emoji ID in custom emojis
    isCustom: boolean; // whether the emoji is a custom emoji or not
    names: string[];
    imageUrl: string; // the url of the emoji image with the current emoji style applied
    getImageUrl: (emojiStyle: EmojiStyle) => string; // a function that receives an emoji style and returns the url of the emoji image with the provided style applied
  }
  ```

- `theme`: `Theme` - The theme of the picker. Can be `light`, `dark` or auto. Default is `light`.
  The `Theme` enum can be imported from the package.

  ```ts
  import { Theme } from 'emoji-picker-react';
  ```

- `emojiStyle`: `EmojiStyle` - The emoji style to use. Can be either `apple`, `google`, `facebook`, `twitter` or `native`. Default is `apple`.
  The `EmojiStyle` enum can be imported from the package.

  ```ts
  import { EmojiStyle } from 'emoji-picker-react';
  ```

* `autoFocusSearch`: `boolean` - Whether to focus the search input on mount. Defaults to `true`.
*
* `lazyLoadEmojis`: `boolean` - Whether to lazy load the emojis. Defaults to `false`.

* `defaultSkinTone`: `SkinTones` - The default skin tone to use when an emoji is clicked. Defaults to `SkinTones.Neutral`. Possible skin tones are:

  - ✋ 'neutral'
  - ✋🏻 '1f3fb'
  - ✋🏼 '1f3fc'
  - ✋🏽 '1f3fd'
  - ✋🏾 '1f3fe'
  - ✋🏿 '1f3ff'

The skin tones typescript enum can be imported directly from the package:

```ts
import { SkinTones } from 'emoji-picker-react';
```

- `searchDisabled`: `boolean` - Whether to disable the search input. Defaults to `false`. When disabled, the skin tone picker will be shown in the preview component.

- `skinTonesDisabled`: `boolean` - Whether to disable the skin tone selection. Defaults to `false`.

- `skinTonePickerLocation`: `SkinTonePickerLocation` - The location of the skin tone picker. Can be either `SEARCH` or `PREVIEW`. Defaults to `SEARCH`. The `SkinTonePickerLocation` enum can be imported from the package.

  ```ts
  import { SkinTonePickerLocation } from 'emoji-picker-react';
  ```

- `previewConfig`: `PreviewConfig` - Full control over the Preview component, either to show/hide it, change the default emoji or the default caption.

```ts
{
  defaultEmoji: string; // defaults to: "1f60a"
  defaultCaption: string; // defaults to: "What's your mood?"
  showPreview: boolean; // defaults to: true
}
```

- `searchPlaceholder`: `string` - The placeholder text for the search input. Defaults to `Search`.

- categories: Allows full config over ordering, naming and display of categories.
  To only sort/omit categories, you can simply pass an array of category names to display:

  - 'suggested',
  - 'custom', - Hidden by default
  - 'smileys_people',
  - 'animals_nature',
  - 'food_drink',
  - 'travel_places',
  - 'activities',
  - 'objects',
  - 'symbols',
  - 'flags'

  For a more in-depth configuration, you can pass an array with category config:

  ```ts
  [
    {
      category: 'suggested',
      name: 'Recently Used'
    },
    {
      category: 'smileys_people',
      name: 'Faces...'
    }
  ];
  ```

- `suggestedEmojisMode`: `SuggestedEmojisMode` - The mode to use for the suggested emojis. Can be either `recent` or `frequent`. Defaults to `recent`.
  The `SuggestionMode` enum can be imported from the package.

  ```ts
  import { SuggestionMode } from 'emoji-picker-react';
  ```

- `emojiVersion`: `string` - Allows displaying emojis up to a certain version for compatibility. The passed version will be parsed as a float and each emoji will be tested against it. Common values are:
  - `"0.6"`
  - `"1.0"`
  - `"2.0"`
  - `"3.0"`
  - `"4.0"`
  - `"5.0"`

* `getEmojiUrl`: `(unified: string, emojiStyle: EmojiStyle) => string` - Allows to customize the emoji url and provide your own image host. The function receives the emoji unified and the emoji style as parameters. The function should return the url of the emoji image.

## Custom Emojis

The customEmojis prop allows you to add custom emojis to the picker. The custom emojis prop takes an array of custom emojis, each custom emoji has three keys:

id: Unique identifier for each of the custom emojis
names: an array of string identifiers, will be used both for display, search and indexing.
imgUrl: URL for the emoji image

### Usage Example:

```jsx
<Picker
  customEmojis={[
    {
      names: ['Alice', 'alice in wonderland'],
      imgUrl:
        'https://cdn.jsdelivr.net/gh/ealush/emoji-picker-react@custom_emojis_assets/alice.png',
      id: 'alice'
    },
    {
      names: ['Dog'],
      imgUrl:
        'https://cdn.jsdelivr.net/gh/ealush/emoji-picker-react@custom_emojis_assets/dog.png',
      id: 'dog'
    },
    {
      names: ['Hat'],
      imgUrl:
        'https://cdn.jsdelivr.net/gh/ealush/emoji-picker-react@custom_emojis_assets/hat.png',
      id: 'hat'
    },
    {
      names: ['Kid'],
      imgUrl:
        'https://cdn.jsdelivr.net/gh/ealush/emoji-picker-react@custom_emojis_assets/kid.png',
      id: 'kid'
    },
    {
      names: ['Mic'],
      imgUrl:
        'https://cdn.jsdelivr.net/gh/ealush/emoji-picker-react@custom_emojis_assets/mic.png',
      id: 'mic'
    },
    {
      names: ['Moab', 'desert'],
      imgUrl:
        'https://cdn.jsdelivr.net/gh/ealush/emoji-picker-react@custom_emojis_assets/moab.png',
      id: 'moab'
    },
    {
      names: ['Potter', 'harry', 'harry potter'],
      imgUrl:
        'https://cdn.jsdelivr.net/gh/ealush/emoji-picker-react@custom_emojis_assets/potter.png',
      id: 'potter'
    },
    {
      names: ['Shroom', 'mushroom'],
      imgUrl:
        'https://cdn.jsdelivr.net/gh/ealush/emoji-picker-react@custom_emojis_assets/shroom.png',
      id: 'shroom'
    },
    {
      names: ['Smily'],
      imgUrl:
        'https://cdn.jsdelivr.net/gh/ealush/emoji-picker-react@custom_emojis_assets/smily.png',
      id: 'smily'
    },
    {
      names: ['Tabby', 'cat'],
      imgUrl:
        'https://cdn.jsdelivr.net/gh/ealush/emoji-picker-react@custom_emojis_assets/tabby.png',
      id: 'tabby'
    },
    {
      names: ['Vest'],
      imgUrl:
        'https://cdn.jsdelivr.net/gh/ealush/emoji-picker-react@custom_emojis_assets/vest.png',
      id: 'vest'
    }
  ]}
/>
```

Here are some additional things to keep in mind about custom emojis:

- The custom emojis will be added to the Custom category.
- The location or name of the Custom category can be controlled via the categories prop.
- The custom emojis will be indexed by their id property. This means that you can search for custom emojis by their id or names.

# Customization

## Custom Picker Width and Height

To customize the dimensions of the picker, use the `height` and `width` props. You can pass in a number that will be treated as pixel size, or your any accepted css width/height as string.

```jsx
<EmojiPicker height={500} width={400} />
```

```jsx
<EmojiPicker height="100%" width="15em" />
```

## CSS Variables

The picker can be customized via css variables. The root selector for the picker is `.EmojiPickerReact`, when overriding, make sure to provide a more specific selector.

In dark mode, the specific selector is `.EmojiPickerReact.epr-dark-theme`.

The list of possible variables is quite extensive, but the main ones you may want to override are:

- `--epr-emoji-size`: The size of the emojis.
- `--epr-emoji-gap`: The space between emojis.

- `--epr-hover-bg-color` Hovered emoji background color.
- `--epr-bg-color`: The background color of the picker. When changing it, you should also change `--epr-category-label-bg-color` as they are usually the same color.
- `--epr-text-color`: The text color in the picker.

# Rendering Output Emojis in Your App

The picker exports an `Emoji` component. The emoji component is the same used within the picker, so it will render the same way as the emojis in the picker. You can choose to render emojis either as native, or as images.

## Props

| Name          | Type         | Default            | Description                                                                                 |
| ------------- | ------------ | ------------------ | ------------------------------------------------------------------------------------------- |
| `unified`     | string       | ""                 | The unified code of the emoji.                                                              |
| `size`        | number       | 32                 | The size of the emoji.                                                                      |
| `emojiStyle`  | `EmojiStyle` | `EmojiStyle.APPLE` | The emoji style to use. Can be either `apple`, `google`, `facebook`, `twitter` or `native`. |
| `lazyLoad`    | boolean      | `false`            | Whether to lazy load the emoji. image                                                       |
| `emojiUrl`    | string       | -                  | The url of the emoji image to render. Useful for custom emojis.                             |
| `getEmojiUrl` | Function     | -                  | Allows to customize the emoji url and provide your own image host for dynamic resolution.   |

```js
import { Emoji, EmojiStyle } from 'emoji-picker-react';

export function MyApp() {
  return (
    <p>
      My Favorite emoji is:
      <Emoji unified="1f423" size="25" />
    </p>
  );
}
```

# Troubleshooting

## Error Boundary

emoji-picker-react has a top-level error boundary, trying to catch rendering errors. It won't catch server side related errors, or event handlers errors. If an error is caught, the picker will not render, and a console error will be logged.

## Next.js

To avoid errors such as "document is not defined" on the server side, you should make sure the library is only imported on the client side. Here is how to do that:

```javascript
import dynamic from 'next/dynamic';

const Picker = dynamic(
  () => {
    return import('emoji-picker-react');
  },
  { ssr: false }
);
```

## Vite

For reference, if you only need to shim global, you can add

```html
<script>
  window.global = window;
</script>
```

# Other stuff I build

If you enjoy using emoji-picker-react, you may be interested in some of my other open source projects:

- [Vest](https://github.com/ealush/vest) - The best form validation framwork to date.
- [Context](https://github.com/ealush/vest/tree/latest/packages/context) - Context propagation library for JS Apps.
- [n4s](https://github.com/ealush/vest/tree/latest/packages/n4s) - enforce: fluent assertion library.
