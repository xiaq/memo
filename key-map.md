# Kernel

To be written

# Xorg
Xorg implements its own key-mapping mechanism, reading keycode and translating it into `keysym`, bypassing the kernel keymap table.  X applications generally only see the translated `keysym`, along with information indicating whether the `keysym` is considered a `modifier`.

The mapping may be viewed and modified using `xmodmap`.  The `keysym` are then examined against the modifier table, which can also be handled by `xmodmap`.  Syntax for `xmodmap` commands can be viewed by ``xmodmap -grammar``.
