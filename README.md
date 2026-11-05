# Detach and Return

Pull a tab into its own window, move it to another monitor, and send it back when you're done.

The extension remembers where each tab came from, including tabs dragged out with the mouse. You can have several tabs detached at once and return them in any order.

## Shortcuts

| Shortcut | Action |
| --- | --- |
| Alt + Shift + D | Detach the current tab into a new window |
| Alt + Shift + R | Return the current tab to its original window and position |

Change these in `brave://extensions/shortcuts`. If a shortcut does nothing, check that it is assigned there and isn't already used by your desktop environment.

Moving the detached window between monitors doesn't change where its tab will return. Moving the tab through other windows keeps its original destination, too. Dragging it back to its original window clears that record, ready for the next detach.

## Install from Git (Linux)

You need Git installed.

```sh
mkdir -p ~/.local/share
git clone https://github.com/Mihai-Solescu/brave-tab-return.git ~/.local/share/brave-tab-return
```

Then load it in Brave:

1. Open `brave://extensions`.
2. Turn on **Developer mode**.
3. Click **Load unpacked**.
4. Select `~/.local/share/brave-tab-return`, the folder containing `manifest.json`.
5. Open `brave://extensions/shortcuts` and check the bindings.

If the folder picker hides `.local`, press Ctrl+L and enter the full path, such as `/home/yourname/.local/share/brave-tab-return`.

There is no build step. Keep the folder where you cloned it: Brave loads the extension from there.

### Update

```sh
git -C ~/.local/share/brave-tab-return pull --ff-only
```

Open `brave://extensions` and click **Reload** on Detach and Return. Reloading clears the remembered tab destinations, so return any detached tabs first.

## Install from the store

Brave uses the [Chrome Web Store](https://chromewebstore.google.com/) for extensions.

**Store listing: not published yet.** The direct install link will go here once the listing is available.

Once published, open that link in Brave, click **Add to Brave**, and confirm the installation. You won't need Git or Developer mode. Store installations receive updates automatically.

## Things to know

- Tracking starts when the extension is loaded. It cannot recover the source of a tab you dragged out before that.
- The original window must still be open for a tab to return to it.
- Destinations are remembered for the current browser session. Restarting Brave, disabling the extension, or reloading it clears them.
- The saved position is a tab index. If you rearrange the original window's tabs while a tab is away, it may return beside different tabs.
- Detaching the last tab with the shortcut leaves a new tab behind to keep the original window open.
- Returning a tab does not restore its former tab group.

## Privacy

The extension keeps tab IDs, original window IDs, tab positions, and any saved pinned state in browser session storage. It does not read page contents, collect browsing history, use analytics, or send data anywhere.

The `storage` permission lets it keep those records while its background worker is idle.
