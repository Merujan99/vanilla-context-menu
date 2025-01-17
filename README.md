# Vanilla Context Menu

<div style='text-align:center'>
    <img src='https://img.shields.io/github/issues/GeorgianStan/vanilla-context-menu' alt='issues'>
    <img src='https://img.shields.io/github/forks/GeorgianStan/vanilla-context-menu' alt='forks'>
    <img src='https://img.shields.io/github/stars/GeorgianStan/vanilla-context-menu' alt='stars'>
    <img src='https://img.shields.io/github/license/GeorgianStan/vanilla-context-menu' alt='license'>
    <img src='https://img.shields.io/github/package-json/v/GeorgianStan/vanilla-context-menu?color=%237146f9&logo=javascript' alt='version'>
    <a href="https://david-dm.org/georgianstan/vanilla-context-menu" title="dependencies status"><img src="https://status.david-dm.org/gh/georgianstan/vanilla-context-menu.svg"/></a>
</div>

`vanilla-context-menu` - easily create context-menus using Vanilla JavaScript and integrate them in any web application

## Installation

### Browser CDN

```html
<script src="https://unpkg.com/vanilla-context-menu@1.0.0/dist/vanilla-context-menu.js"></script>
```

Where `@1.0.0` is the version that you want to use.

Then anywhere in your JavaScript code you can access the library with `window.VanillaContextMenu` or simply `VanillaContextMenu`.

### Via NPM

```bash
npm i vanilla-context-menu
```

Then anywhere in your code.

```javascript
import VanillaContextMenu from 'vanilla-context-menu';
```

## How to use it

```javascript
new VanillaContextMenu({
  scope: document.querySelector('main'),
  menuItems: [
    {
      label: 'Copy',
      callback: () => {
        // ? your code here
      },
    },
    'hr',
    {
      label: 'Paste',
      callback: pasteFunction,
    },
  ],
});
```

## Configuration options

```typescript
VanillaContextMenu(configurableOptions: ConfigurableOptions):VanillaContextMenu
```

**ConfigurableOptions**

|       Option        | Required |        Type        |  Default  |                                                                    Description                                                                    |
| :-----------------: | :------: | :----------------: | :-------: | :-----------------------------------------------------------------------------------------------------------------------------------------------: |
|        scope        | **yes**  |    HTMLElement     | undefined |                                   The HTML element on which you want to bind the `contextmenu` event listener.                                    |
|      menuItems      | **yes**  |     MenuItem[]     | undefined |                                                              Menu items to be built.                                                              |
|     customClass     |    no    |       string       | undefined |                                             A custom CSS class that can be added to the context menu                                              |
|  customThemeClass   |    no    |       string       | undefined |            A custom CSS class that can be added to the context menu theme. A value for this property will exclude the `theme` option.             |
| preventCloseOnClick |    no    |      boolean       |   false   |                          If this variable is `true`, then the context menu will not close when its elements are clicked.                          |
| transitionDuration  |    no    |       number       |    200    |                        Duration of the context menu transition. Set this value to 0 if you want to disable the animation.                         |
|        theme        |    no    | 'black' \| 'white' |   black   | By default, the library provides two themes for the context menu: `black` and `white`. You can use this option to choose the one you want to use. |

**MenuItem**

```typescript
type MenuItem = MenuOption | 'hr';
```

**MenuOption**
| Option | Required | Type | Default | Description |
|:-------------------:|:--------:|:---------:|:---------:|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| label | **yes** | string | undefined | Menu option label. |
| callback | **yes** | () => any | undefined | Callback to be executed. |
| preventCloseOnClick | no | boolean | false | If this variable is `true`, then the context menu will not close when this menu option is clicked. A value set for this option, either `true` or `false` will override the global one. |

## API <sub style='font-size:15px'>(2)</sub>

The following methods and properties are available through the class instance.

```ts
const myContextMenu = new VanillaContextMenu(...)
```

(1)

```ts
off(): void
```

This method will remove all event listeners that have been registered for the context-menu.

**!** It should be called when you want to deactivate the context menu or when the container item has been removed from the DOM.

(2)

```ts
updateOptions(configurableOptions: Partial<ConfigurableOptions>): void
```

## Examples

### Define your own theme

```scss
.context-menu-orange-theme {
  background: #d35400;

  hr {
    background-color: #eee;
  }

  // ? text color for each item
  & > *:not(hr) {
    color: #eee;

    &:hover {
      background: #e67e22;
    }
  }
}
```

### Define your own CSS class for styling

```css
.custom-context-menu-cls {
  width: 150px;
  font-family: 'Roboto', sans-serif; /* DEFAULT -- font-family: 'Open Sans', sans-serif; */
}
```

```ts
const myContextMenu = new window.VanillaContextMenu({
  scope: ...,
  menuItems: [...],
  customThemeClass: 'context-menu-orange-theme',
  customClass: 'custom-context-menu-cls',
});
```

You can check the `demo` file for more examples from [demo/index.html](https://github.com/GeorgianStan/vanilla-context-menu/blob/master/demo/index.html).

## Contributing

Pull requests and stars are always welcome. Please check the [guidelines](https://github.com/GeorgianStan/vanilla-context-menu/blob/master/CONTRIBUTING.md).

## Stay in touch

[Discussions page](https://github.com/GeorgianStan/vanilla-context-menu/discussions)

## License

This project is licensed under the [MIT License](https://github.com/GeorgianStan/vanilla-context-menu/blob/master/LICENSE)
