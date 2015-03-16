```
    'esc': 'selectAddThang'
    'delete, del, backspace': 'deleteSelectedExtantThang'
    'ctrl+z, ⌘+z': 'undo'
    'ctrl+shift+z, ⌘+shift+z': 'redo'
    'alt+c': 'toggleSelectedThangCollision'
    'left': -> @moveSelectedThangBy -1, 0
    'right': -> @moveSelectedThangBy 1, 0
    'up': -> @moveSelectedThangBy 0, 1
    'down': -> @moveSelectedThangBy 0, -1
    'alt+left': -> @rotateSelectedThangTo Math.PI unless key.shift
    'alt+right': -> @rotateSelectedThangTo 0 unless key.shift
    'alt+up': -> @rotateSelectedThangTo -Math.PI / 2
    'alt+down': -> @rotateSelectedThangTo Math.PI / 2
    'alt+shift+left': -> @rotateSelectedThangBy Math.PI / 16
    'alt+shift+right': -> @rotateSelectedThangBy -Math.PI / 16
    'shift+left': -> @resizeSelectedThangBy -1, 0
    'shift+right': -> @resizeSelectedThangBy 1, 0
    'shift+up': -> @resizeSelectedThangBy 0, 1
    'shift+down': -> @resizeSelectedThangBy 0, -1
    'ctrl+\\, ⌘+\\': 'onToggleDebug'.

```