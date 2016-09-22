# Atom Key map

```yaml
'body':
  'ctrl-tab ^ctrl': 'unset!'
  'ctrl-tab': 'pane:show-next-item'
  'ctrl-shift-tab ^ctrl': 'unset!'
  'ctrl-shift-tab': 'pane:show-previous-item'

'atom-workspace atom-text-editor:not([mini])':
  'ctrl-up': 'keyboard-scroll:scrollUp'
  'ctrl-down': 'keyboard-scroll:scrollDown'

  'ctrl-shift-up': 'editor:move-line-up'
  'ctrl-shift-down': 'editor:move-line-down'

'atom-workspace atom-text-editor':
  'alt-left': 'pane:show-previous-item'
  'alt-right': 'pane:show-next-item'
```
