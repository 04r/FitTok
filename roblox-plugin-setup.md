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

That's it. The pair code is saved in your browser's localStorage and inside the plugin, so you only do this once per machine.

> The pair code is what keeps things separate when multiple people use the website at the same time. Only **your** plugin (the one showing this code) reacts to **your** "Add to Game" clicks.

---

## 3 · Use it

On the website:
- Search a user, optionally pick a saved outfit and the rig type (R6 / R15) in **Studio Sync**.
- Click **Add to Game** → see the green tip `✓ Sent to Studio`.

In Studio (within ~3 seconds):
- A new mannequin appears near your camera focus, wearing the avatar/outfit.
- It's tagged `FitTokMannequin` (find all of them via CollectionService).
- It's auto-selected, and **Ctrl+Z** undoes the spawn cleanly.

You can leave the plugin running with **Connect** on while you browse — every "Add to Game" click spawns a new mannequin in your active Studio session.

---

## Troubleshooting

| Symptom | Fix |
|---|---|
| Plugin status: `HTTP requests are disabled` | Enable in Game Settings → Security → Allow HTTP Requests |
| Plugin status: `Connection error` | Check your internet connection, then click Disconnect → Connect |
| Website tip: `Search a Roblox user first` | Run a search on the website before clicking Add to Game |
| Website tip: `Paste your Pair code…` | Copy the code from the plugin window into the Studio Sync field |
| Mannequin spawns without clothing | Outfit has been deleted / set private on Roblox |
| Want to "reset" your queue | Stop both ends (Disconnect plugin, close website), wait 10 seconds, reconnect |

Polling is light (one HTTP request every 3 seconds while connected), so just disconnect the plugin when you're not actively using it to save bandwidth.
