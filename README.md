<h1 align="center">asciiart.nvim</h1>

<p align="center">
	<b>Image Viewer as ASCII Art for Neovim, written in Lua. Forked from <a href="https://github.com/samodostal/image.nvim">https://github.com/samodostal/image.nvim</a> to provide integration with <a href="https://github.com/doctorfree/Asciiville">Asciiville</a></b>
</p>

<p align="center">
    <a href="https://github.com/doctorfree/asciiart.nvim/issues">
			<img src="https://img.shields.io/github/issues/doctorfree/asciiart.nvim" alt="Issues"/>
		</a>
		<a href="https://github.com/doctorfree/asciiart.nvim/stargazers">
			<img src="https://img.shields.io/github/stars/doctorfree/asciiart.nvim" alt="Repository's starts"/>
		</a>
    <a href="https://github.com/doctorfree/asciiart.nvim/blob/master/LICENSE">
			<img src="https://img.shields.io/github/license/doctorfree/asciiart.nvim" alt="License"/>
		</a>
    <a href="https://github.com/doctorfree/asciiart.nvim/commits/main">
			<img src="https://img.shields.io/github/last-commit/doctorfree/asciiart.nvim" alt="Latest commit"/>
		</a>
</p>

<p align="center">
  <img src="https://user-images.githubusercontent.com/44208530/215286501-80d355f4-5b67-4b6a-a584-9ef63c061089.gif" alt="animated" width="100%" />
</p>

## Features
- Supports many file formats (.png, .jpg, .jpeg, .bmp, .webp, ...)
- Colored images
- Almost **no code** runs on startup
- Rendering with a [dither](https://en.wikipedia.org/wiki/Dither) method makes images more visible than traditional ascii art
- Images are centered and have labels!

## How does it work?
When you open an image file (e.g. `portrait.png`), the open buffer becomes non-editable and non-saveable to ensure the file contents won't be overwritten. Then the buffer is filled with the ascii art generated by [ascii-image-converter](https://github.com/TheZoraiz/ascii-image-converter). I found out that a plugin similiar to this was already implemented for vim in vimscript: [image.vim](https://github.com/ashisha/image.vim), so you can consider this a modern, lua version.

## Prerequisites
- Install [ascii-image-converter](https://github.com/TheZoraiz/ascii-image-converter) and make sure it is in your path
- [plenary.nvim](https://github.com/nvim-lua/plenary.nvim)
- [baleia.nvim](https://github.com/m00qek/baleia.nvim) (optional for color support)
- Neovim 0.7+

## Install 
With packer
```lua
use {
  'doctorfree/asciiart.nvim',
  requires = {
    'nvim-lua/plenary.nvim'
  },
},
```
With vim.plug
```lua
Plug 'doctorfree/asciiart.nvim'
Plug 'nvim-lua/plenary.nvim'
```

## Setup
```lua
-- Require and call setup function somewhere in your init.lua
require('image').setup {
  render = {
    min_padding = 5,
    show_label = true,
    use_dither = true,
    foreground_color = false,
    background_color = false
  },
  events = {
    update_on_nvim_resize = true,
  },
}
```

## Colors support:
**Colors are turned off by default.**
- The reason for colors not being on by default is a significant delay when opening images + an additional dependency: plugin [baleia.nvim](https://github.com/m00qek/baleia.nvim) (no need to call setup, only install)
- Enable options`render.foreground_color` and `render.background_color`
- `render.background_color` setting is a nice addition that enables colors not only for characters, but also for the space behind them.
