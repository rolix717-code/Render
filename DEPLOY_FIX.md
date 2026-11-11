# Render deployment fix

The deployment log points to a native Node module build (`better-sqlite3` / `node-gyp`). This package now explicitly pins Node.js 22.14.0 so Render does not attempt to build the native SQLite dependencies under an old Node runtime.

## Redeploy
1. Replace the old project files in your GitHub repository with the contents of this folder (do not upload `.env`).
2. Commit and push the changes.
3. In Render, open the service and choose **Manual Deploy → Clear build cache & deploy**.
4. Keep these environment variables configured in Render: `TMDB_TOKEN`, `ADMIN_EMAIL`, `ADMIN_PASSWORD`, `SESSION_SECRET`, and `DATA_DIR=/var/data`.
5. Confirm the service is using the Node runtime specified by `.node-version` / `NODE_VERSION`.

If it still fails, open the build log and send the first error lines above `gyp ERR!`, especially the `node -v`, `node-gyp`, and compiler output. The screenshot only shows the final summary, not the root error.
