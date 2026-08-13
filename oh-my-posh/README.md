# Flayri theme for Oh-My-Posh

Based on the [Catpuccin](https://raw.githubusercontent.com/JanDeDobbeleer/oh-my-posh/main/themes/catppuccin.omp.json) and [iTerm2](https://raw.githubusercontent.com/JanDeDobbeleer/oh-my-posh/main/themes/iterm2.omp.json) themes.

## Setup

Apply the theme in your `.*rc` by adding the line:
```zsh
eval "$(oh-my-posh init zsh --config '[path to cloned directory]/oh-my-posh/flayri.omp.json')"
```

Use with [zsh](https://www.zsh.org) for best results.

### Fonts

Make sure to use a [Nerd Font](https://www.nerdfonts.com) to show icons, such as MesloLGM. See [the oh-my-posh documentation](https://ohmyposh.dev/docs/installation/fonts) for details.
In VSCode specifically, set the font in `Users › Features › Terminal › Integrated: Font Family`:
```json
"terminal.integrated.fontFamily": "MesloLGM Nerd Font"
```
## Details

Because JSON is too cool for comments I will document and explain the more interesting parts of the theme here.

### Styles

In the main blocks, I use the following styles to obtain spacing where I want it:
```
< powerline > diamond > > powerline > powerline >  < diamond > > powerline >
```
In the case for the OS icon on the left, I use the base color of the blue gradient instead of the gradient itself, so it flows more smoothly into the next segment.

### Transient Prompt

The transient prompt replaces the regular prompt once the command is executed. However, it is way more limited than regular prompts, not allowing for style or separate blocks. See the documentation [here](https://ohmyposh.dev/docs/configuration/transient).
I recreate the pill shape inside the template, and also override the color using the `background` alias.
```go
"
<background,transparent>\ue0b6</>
 {{ .Folder }} 
<background,transparent>\ue0b0</>
"
```
For the right template, I obtain the time using [cross segment template properties](https://ohmyposh.dev/docs/configuration/templates#cross-segment-template-properties).

### Interrupt

A simple style change in the transient prompt shows when a command is interrupted with Ctrl+C. In the future I'd like to make this more noticeable with an incon and not change the background on the left. Currently this is a limitation of the transient prompts.

## Editing

When editing the theme in VSCode, make sure that `https://raw.githubusercontent.com/JanDeDobbeleer/` is a trusted domain in `Settings › JSON › Schema Download: Trusted Domains`
```json
"json.schemaDownload.trustedDomains": {
    "https://raw.githubusercontent.com/JanDeDobbeleer/": true
},
```