# Bazaar Ledger — Skyblock Craft Flip Finder

A single-file HTML tool for Hypixel Skyblock. Enter a coin budget and it ranks the best bazaar craft flips you can currently afford — ingredients, exact cost, profit, margin, and (if you connect your account) whether you've actually unlocked the collection tier each recipe needs.

No build step, no server, no dependencies. Open the file in a browser and it works.

## Features

- Enter any budget (`10m`, `500k`, `2500000`, etc.) and get the top 10 craft flips that fit
- Sort by profit or by margin %
- Full ingredient list and per-item cost for each flip
- Optional: connect your Hypixel account to filter the list down to only what you can actually craft right now, based on your real collection levels
- Everything runs client-side — no data is sent to any server you don't control

## Usage

1. Download `bazaar_flip_finder.html`
2. Open it in a browser (double-click it, or serve it locally — see [Local server](#local-server-optional) below)
3. Enter a budget and hit **Find flips**

### Checking what you can actually craft

The flip data alone doesn't know your progress — for that, connect your account:

1. Go to [developer.hypixel.net](https://developer.hypixel.net), log in, and create an API key from the dashboard
2. Enter your Minecraft username and paste the key into the two fields
3. Click **Fetch my collections**

The key is stored only in your browser's local storage on your own machine — it's never sent anywhere except directly to Hypixel's own API. Use the **Forget saved username and key** link any time to clear it.

### Local server (optional)

Some browsers restrict cross-origin requests from files opened directly (`file://`), which can block the account-lookup feature. If that happens, serve the folder locally instead:

```bash
python3 -m http.server 8000
```

Then open `http://localhost:8000/bazaar_flip_finder.html`.

## How the data works

- Bazaar prices and craft margins are a **snapshot**, not a live feed — Skyblock prices move by the minute, so double-check before committing coins on anything large.
- Collection tier requirements are pulled from Hypixel's own public collections resource (`api.hypixel.net/resources/skyblock/collections`), so they're accurate to the game's actual thresholds, not guesses.
- A handful of craftable items aren't gated by any tracked collection at all (pet fusion materials, mob drops, some event items) — those are labeled "No collection needed" and always show.
- A few recipes aren't covered by Hypixel's public collections resource and may be gated by something else entirely (an NPC unlock, a quest). Those show without a collection tag rather than a guessed one.

## Limitations

- Prices are a point-in-time snapshot embedded in the file, not live-updating. Refresh the data yourself periodically if you keep using this.
- The account lookup needs your own free Hypixel API key — there's no way around that requirement, since Hypixel doesn't expose player data without one.
- This is a personal tool, not affiliated with Hypixel, Mojang, or Microsoft.

## License

Add whatever license you'd like here before publishing (MIT is a common, permissive default for small personal tools like this).
