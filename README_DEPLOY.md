# Deployment notes

## Render
Build command:
`pip install -r requirements.txt`

Start command:
`python app.py`

Add these Environment Variables in Render (do not commit real credentials):
- BOT_UID
- BOT_LOGIN_UID
- BOT_LOGIN_PASSWORD
- RELEASE_VERSION
- GAME_CLIENT_VERSION

The HTTP server starts immediately. Check:
`/health`

Expected while the bot is logged in:
`{"status":"ok","bot_connected":true,"loop_running":true}`

If `bot_connected` is false, the web server is alive but the game connection/login has not succeeded.

The `/join` endpoint now waits for the coroutine result and returns the real exception instead of reporting success when the game action failed.
