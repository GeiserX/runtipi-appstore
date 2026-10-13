vettarr decides what downloads. Send it a link, a Telegram post, a magnet, a `.torrent` file or a Seerr request, or let it watch a Telegram group. It looks the title up and checks it against rules you write: age rating by country, the IMDb parents guide, TMDB genres and keywords, size, resolution, seeders, and whether your library already has it. Then it approves the item, holds it for you, or refuses it and says why.

Approved items go to qBittorrent, Radarr or Sonarr, or back to Seerr as an approval. Every decision keeps the rules that made it. Shadow mode decides and records without acting, so you can watch it on real posts before you trust it. It handles films, series, books and magazines.

The web UI has an Inbox, a one-at-a-time Review that works with keys or swipes, Policy, Setup and Stats, in light and dark. A Telegram bot can push each item that needs you, with the same actions.

## First use

The first start writes `config.yaml` from the shipped example into the app's data folder, under `data/app/`. That example runs the web UI and the policy in shadow mode and nothing else: no source reads anything and nothing downloads until you turn it on. The database is created on the first start too.

1. Set a password first. Until you do, anyone who reaches the app's port can approve and reject. This prints the line for it without echoing the password or leaving it in the shell history:

   `read -rs P && printf '%s\n' "$P" | docker exec -i vettarr vettarr web hash-password; unset P`

   Paste the line into the app's **Web password hash** setting and save it. In `config.yaml`, uncomment `auth:` and its `password_hash` line under `web:`, then restart the app. The web UI now asks for the password.

2. Add your sources, the services you run (Prowlarr, qBittorrent, Radarr, Sonarr, Seerr, TMDB) and where each media type goes, in `config.yaml` or on the Setup and Policy pages. The app settings hold the common secrets, which the file reads as `${VAR}`. Write any other value straight into the file.

3. Check the file before you restart the app to apply it:

   `docker exec vettarr vettarr config check /data/config.yaml`

   The check sees the settings the app last started with, so after you change a setting, restart first.

The IMDb parents-guide signals use IMDb's undocumented website API, which IMDb's terms do not allow for automated use. Use them on a private, single-user instance at your own risk. TMDB certifications are the licensed alternative.

Configuration reference: https://github.com/GeiserX/vettarr/blob/main/docs/CONFIG.md
