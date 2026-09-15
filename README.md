# Bass Fishing Conditions Score

A single-page tool that scores fishing conditions (pressure, wind, cloud cover,
precipitation, moon phase, water temp) and adjusts for bass spawn season.
Weather is pulled live from the free [Open-Meteo](https://open-meteo.com) API —
no API key or backend required.

## Run it locally

Just open `index.html` in a browser. Geolocation requires either `localhost`
or HTTPS, so opening the file directly (`file://`) will fall back to manual
lat/lon entry — that's expected.

## Deploy to GitHub Pages

1. Create a new repo and push these files to the `main` branch:
   ```
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/<your-username>/<repo-name>.git
   git push -u origin main
   ```
2. In the repo, go to **Settings → Pages**.
3. Under **Build and deployment → Source**, choose **Deploy from a branch**.
4. Under **Branch**, choose `main` and folder `/ (root)`, then **Save**.
5. GitHub will publish the site at:
   ```
   https://<your-username>.github.io/<repo-name>/
   ```
   It usually takes 1–2 minutes for the first deploy to go live.

Geolocation will work fine once served over the `github.io` HTTPS domain —
the browser will just prompt for permission the first time.

## Notes

- Water temperature is *estimated* from a 5-day trailing average of air
  temperature, since there's no free public API for lake water temp. Swap
  in real sensor/buoy data if your lake has it.
- All scoring logic lives in the `<script>` block in `index.html` — no
  build step, no dependencies.
