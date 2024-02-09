# just a config repo/some notes
could be outdated

# Mac

## Faster dock
`defaults write com.apple.dock autohide-delay -float 0; defaults write 
com.apple.dock autohide-time-modifier -int 0; killall Dock`

## Continuity Markup
only works via quick view or quick actions, not via preview

# Firefox
## Side tab menu extensions: hide main tab bar dynamically/only when the extension is active
From [sidebery](https://github.com/mbnuqw/sidebery/wiki/Firefox-Styles-Snippets-(via-userChrome.css)), a tree-style sidebar tab extension. 

1. Enable `toolkit.legacyUserProfileCustomizations.stylesheets` in about:config
2. In 'Profile Directory' (Menu > Help > Troubleshooting Information > Profile Directory) create folder chrome with file `userChrome.css` with the following content:
    ```
    #main-window #titlebar {
    overflow: hidden;
    transition: height 0.3s 0.3s !important;
    }
    /* Default state: Set initial height to enable animation */
    #main-window #titlebar { height: 3em !important; }
    #main-window[uidensity="touch"] #titlebar { height: 3.35em !important; }
    #main-window[uidensity="compact"] #titlebar { height: 2.7em !important; }
    /* Hidden state: Hide native tabs strip */
    #main-window[titlepreface*="XXX"] #titlebar { height: 0 !important; }
    /* Hidden state: Fix z-index of active pinned tabs */
    #main-window[titlepreface*="XXX"] #tabbrowser-tabs { z-index: 0 !important; }
    ```
3. Set window preface value:
    Sidebery settings > Help > Preface value
    note: in this example: XXX
    mnake sure this is the same as what's in the file


My understanding is that when the extension is active, the window name will have a preface, and this can be used to either toggle the tab bar. Otherwise, the tab bar will be either on or off. 
