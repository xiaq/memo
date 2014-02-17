# Files and Directories

    /etc/xdg/autostart # Global autostart directory
    ~/.config/autostart # User autostart directory, overrides global where file names are identical; create a dummy entry with "Hidden=true" to invalidate a global entry
    /sys/class/backlight/acpi_video0 # Screen brightness, etc.

# split ape/cue into flac
    shnsplit -o flac -f *.cue *.ape
    cuetag *.cue split-track*.flac
