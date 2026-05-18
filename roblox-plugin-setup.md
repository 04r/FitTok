# FitTok ↔ Roblox Studio — Setup (~1 minute)

The website (`04r.github.io/FitTok`) and the FitTok Studio plugin share a hosted "bin" so a click on the website spawns a mannequin in your open Studio session. **Both ends are pre-configured** — you just install the plugin, pair it once, and you're done.

---

## 1 · Install the Studio plugin

1. Download **`roblox-plugin.luau`** from this repo.
2. In Roblox Studio: top bar **Plugins → Plugins Folder** (opens a folder explorer).
3. Drop `roblox-plugin.luau` into that folder.
4. **Restart Studio**.
5. Open any game project. You'll see a **FitTok** button in the Plugins toolbar — click it. A docked panel opens.

> If you don't see it after restarting, make sure the file is `.luau` (not `.lua`) and that it's directly inside the Plugins folder (no subfolder).

---

## 2 · Pair the website to your Studio

1. The plugin window shows a **6-character Pair code** (e.g. `AB7K3X`). Click **Copy**.
2. Open the FitTok website, scroll to **Studio Sync** in settings, and paste the code into the **Pair code** field.
3. Back in Studio, make sure **HTTP requests** are enabled: **Game Settings → Security → Allow HTTP Requests** (toggle on).
4. In the plugin window, click **Connect**. Status should turn green: `Connected — listening`.
5. On the website, the green dot next to "Studio Sync" lights up within a few seconds, and the **Add to Game** button becomes clickable.

The pair code is saved on both ends, so this is one-time per machine.

> The pair code is what keeps things separate when multiple people use the website at the same time. Only **your** plugin (the one showing this code) reacts to **your** "Add to Game" clicks.

---

## 3 · Use it

On the website:
- Search a user, optionally pick a saved outfit and choose **R6** or **R15** in **Studio Sync**.
- Click **Add to Game** → green tip `✓ Sent to Studio`.

In Studio (within ~1 second):
- A new mannequin appears at your camera focus, wearing the avatar/outfit, **fully anchored** so you can drag it freely with the Move tool.
- It lands inside a `workspace.Outfits` folder (auto-created on first spawn).
- It's tagged `FitTokMannequin` (you can find them all via CollectionService) and carries attributes (`FitTokKind`, `FitTokId`, `FitTokRig`, `FitTokInstanceId`) so the website can mirror them back.
- It's auto-selected, and **Ctrl+Z** undoes the spawn cleanly.

Back on the website, the **In game** panel under Studio Sync mirrors every mannequin currently in `workspace.Outfits` — hover any tile and click the **×** to delete it from the game.

> Drag tip: in the viewport, click on the mannequin in the **Explorer** (or use **Model select** mode on the Model tab) to grab the whole model. Clicking a single body part in the viewport with default selection still grabs just that part — that's normal Studio behavior.

---

## Troubleshooting

| Symptom | Fix |
|---|---|
| Plugin status: `HTTP requests are disabled` | Enable in Game Settings → Security → Allow HTTP Requests |
| Plugin status: `Connection error` | Check your internet, then click Disconnect → Connect |
| Add to Game button stays disabled | Make sure the green dot next to "Studio Sync" is lit. If not, click Connect in the plugin window and wait a few seconds. |
| In-game panel empty even though mannequins are in workspace | Mannequins must live inside `workspace.Outfits` and carry the `FitTokMannequin` tag — only ones spawned by this plugin qualify |
| Mannequin spawns without clothing | Outfit has been deleted or set private on Roblox |

Polling is light (one HTTP request every ~1s while connected). Disconnect the plugin when you're not actively using it to save on the free-tier jsonbin quota.
