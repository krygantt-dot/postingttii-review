# PostingTTII TikTok Review Site

Standalone English-language review build for TikTok Login Kit + Content Posting API.

## What this build demonstrates

- Clear product purpose for creators.
- TikTok Login / authorization for up to 3 separate creator accounts.
- Required scopes: `user.info.basic` and `video.publish`.
- Creator Info is queried before rendering the Direct Post screen.
- The creator sees destination account, current privacy options, Comments / Duet / Stitch availability, disclosure toggles and an editable caption.
- A video is selected by the user and explicit consent is required before upload.
- File upload uses TikTok Direct Post.
- Publish status is shown back to the creator.
- Public Privacy Policy, Terms of Service and Data Deletion pages.
- TikTok client secret remains server-side.
- Access and refresh tokens are encrypted at rest.

## TikTok Developer Portal URLs

After Render gives the final HTTPS domain, use:

- Website URL: `https://YOUR-DOMAIN/`
- Terms of Service: `https://YOUR-DOMAIN/terms`
- Privacy Policy: `https://YOUR-DOMAIN/privacy`
- Redirect URI: `https://YOUR-DOMAIN/auth/tiktok/callback`

## Environment variables

Copy values from your local `.env` into Render Environment Variables. Never commit the real `.env`.

Required:

- `TIKTOK_CLIENT_KEY`
- `TIKTOK_CLIENT_SECRET`
- `TIKTOK_REDIRECT_URI`
- `APP_BASE_URL`
- `APP_SECRET`
- `SUPPORT_EMAIL`
- `OPERATOR_NAME`

Optional:

- `DATA_DIR`
- `TIKTOK_VERIFICATION_FILENAME`
- `TIKTOK_VERIFICATION_CONTENT`

## Local run

```powershell
py -3.12 -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
Copy-Item .env.example .env
uvicorn app:app --host 127.0.0.1 --port 8877
```

## Render

This repository includes `render.yaml`.

Build command:

```
pip install -r requirements.txt
```

Start command:

```
uvicorn app:app --host 0.0.0.0 --port $PORT
```

For a review/demo deployment, the free instance is sufficient. Local SQLite storage on a free ephemeral instance may be lost after restart or redeploy, so reconnect the TikTok account before recording if needed.

## Demo video checklist

1. Open the deployed PostingTTII site.
2. Show the product purpose.
3. Click **Connect TikTok**.
4. Show TikTok's authorization screen.
5. Return with the authorized creator visible.
6. Choose the connected account.
7. Show Creator Info / available publishing options.
8. Choose a short video you own or are allowed to publish.
9. Edit the caption.
10. Select a privacy option returned by TikTok.
11. Show Comments, Duet, Stitch and disclosure controls.
12. Check explicit consent.
13. Click **Publish to TikTok**.
14. Show processing status / result.
15. Show Privacy Policy, Terms and Data Deletion pages.

No implementation can guarantee approval; TikTok makes the final review decision.
