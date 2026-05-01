# modernworldfc-crosspromo-config

Static config and icon hosting for ModernWorldFC cross promotion via GitHub Pages.

## Structure

- `docs/cross_promo/config.json`: Cross promotion data consumed by the game.
- `docs/cross_promo/icons/`: Hosted PNG icons used by the config.

GitHub Pages base URL:

```text
https://gxhdky2345.github.io/modernworldfc-crosspromo-config/
```

## Config Schema

Each game entry supports one shared fallback icon plus optional platform-specific icons.

```json
{
	"games": [
		{
			"name": "Battle Shooter",
			"iconUrl": "https://gxhdky2345.github.io/modernworldfc-crosspromo-config/cross_promo/icons/battle_shooter.png",
			"iosIconUrl": "https://gxhdky2345.github.io/modernworldfc-crosspromo-config/cross_promo/icons/battle_shooter_ios.png",
			"androidIconUrl": "https://gxhdky2345.github.io/modernworldfc-crosspromo-config/cross_promo/icons/battle_shooter_android.png",
			"iosId": "1234567890",
			"androidId": "com.xformgames.battleshooter"
		}
	]
}
```

Field notes:

- `name`: Display name shown in the panel.
- `androidIconUrl`: Icon used by Android builds when set.
- `iosIconUrl`: Icon used by iOS builds when set.
- `iconUrl`: Legacy shared fallback icon. Keep this populated for backward compatibility.
- `androidId`: Google Play package name.
- `iosId`: Apple App Store numeric ID only, without the full URL.

If both platforms use the same icon, point `androidIconUrl`, `iosIconUrl`, and `iconUrl` to the same PNG.

## Replace Icons

1. Add the new PNG file to `docs/cross_promo/icons/`.
2. Prefer stable file names so old URLs do not break unless you intend to replace them.
3. Update `androidIconUrl` and `iosIconUrl` in `docs/cross_promo/config.json`.
4. Keep `iconUrl` in sync as the shared fallback.

Example icon URL:

```text
https://gxhdky2345.github.io/modernworldfc-crosspromo-config/cross_promo/icons/my_game_android.png
```

## Change Links, Package Name, Or App Store ID

Edit the matching object in `docs/cross_promo/config.json`.

- To change the Android store target, update `androidId` with the exact Google Play package name, for example `com.company.game`.
- To change the iOS store target, update `iosId` with the numeric App Store ID only.
- To change icon links, update `androidIconUrl`, `iosIconUrl`, and optionally `iconUrl`.

App Store ID example:

```text
https://apps.apple.com/app/id1234567890
```

The value stored in `iosId` is:

```text
1234567890
```

## Publish Changes

```powershell
git add docs README.md
git commit -m "update cross promo config"
git push origin main
```

GitHub Pages usually reflects the change within a few minutes after the push succeeds.
