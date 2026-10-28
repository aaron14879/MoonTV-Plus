# Fork updates

Use Actions → Fork upstream sync (daily at 06:23 Asia/Taipei, or Run workflow). It opens/updates a single fork/upstream-sync PR and never pushes upstream code directly to main. Review and merge the PR normally; this triggers Docker Full/Lite and Cloudflare deployment.

The sync preserves the entire fork-owned .github directory and ignores upstream automation additions, changes and deletions. Conflicts outside .github stop without publishing changes. Review upstream workflow improvements separately and apply them intentionally. This also protects the sync workflow itself.

Do not use Sync fork → Discard commits, force-push upstream/main, or hard-reset main: those external operations bypass this protection. No repository workflow can prevent an administrator from overwriting its own files.

The repository must allow GitHub Actions to create pull requests. If disabled, enable Settings → Actions → General → Allow GitHub Actions to create and approve pull requests. No extra secret or PAT is required. The PR is not auto-merged; normal user merge triggers the deployment workflows.

Docker images publish by digest first; only the merge job assigns vVERSION and latest to the combined amd64/arm64 manifest. GHCR destinations and cleanup owner derive from the fork owner. Keep secrets in repository settings.
