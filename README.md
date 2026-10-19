# FF Sound Effects — Simple Static Version

No admin dashboard, Firebase, login, database, or API. Users can browse categories, search, play and download sounds.

## Hosting setup
1. Upload this folder to a GitHub repository.
2. Enable GitHub Pages (Settings → Pages → Deploy from a branch → main → /root).
3. In Cloudflare R2, create a bucket and upload your MP3/WAV files and category images.
4. Give the audio/images a public HTTPS URL using an R2 custom domain or another supported public access setup.
5. Put those public HTTPS URLs into `sounds.json` as described below.
6. Connect your custom domain to GitHub Pages by following GitHub Pages' custom domain instructions and the DNS records shown there. Do not point the domain to Cloudflare Pages if GitHub Pages is hosting the website.

## Add a sound
Edit `sounds.json` in GitHub and add an object inside the `sounds` array:
```json
{
  "id": "gun-reload-01",
  "title": "Gun Reload",
  "categoryId": "gun-sounds",
  "categoryName": "GUN SOUNDS",
  "audioUrl": "https://YOUR-R2-PUBLIC-DOMAIN/gun-reload.mp3",
  "thumbnailUrl": "https://YOUR-R2-PUBLIC-DOMAIN/gun-reload.png",
  "duration": "00:03",
  "createdAt": 1792400000
}
```
`thumbnailUrl` can be an empty string. `categoryId` should match a category id already listed in `sounds.json`. Save/commit the file and GitHub Pages will publish the change.

## Important
- Audio files live in R2; the sound listing metadata lives in `sounds.json` on GitHub.
- Browser downloads for cross-origin R2 files may open/play rather than download depending on R2 response headers. Configure suitable CORS and Content-Disposition headers or use same-origin file delivery if needed.
- No download counters or “most downloaded” feature.
- Use only content you own or have permission to distribute.
