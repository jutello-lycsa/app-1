# Front Template

## Getting Started

### Installation
Run the following command to install dependencies:
```bash
npm install
```

### Development Server
Start the development server with:
```bash
npm start
```

VERSION: 0.0.6

## Sync Workflow Setup
- Add a repository secret `SYNC_TOKEN` (Personal Access Token) with `repo` scope or fine-grained access:
	- Upstream repo: contents: read
	- This repo: contents: write, pull requests: write
- The workflow at .github/workflows/sync-template.yml runs daily at 06:00 UTC and on manual dispatch.
- If `SYNC_TOKEN` is not set, it falls back to `GITHUB_TOKEN` which only works when upstream is accessible to the workflow's token.

### Verify and Run
1) Confirm upstream access (replace `<TOKEN>` if private):
```bash
git ls-remote https://github.com/jutello-lycsa/front-template.git
git ls-remote https://x-access-token:<TOKEN>@github.com/jutello-lycsa/front-template.git
```
2) Trigger the workflow manually in GitHub → Actions → "Sync Template" → Run workflow.
3) Expected result: branch `sync/front-template` is pushed and a PR is opened to the default branch if there are changes.