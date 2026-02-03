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

VERSION: 0.0.12

## Sync Workflow Setup
- Add a repository secret `SYNC_TOKEN` (Personal Access Token) with `repo` scope or fine-grained access:
	- Upstream repo: `contents: read`
	- This repo: `contents: write`, `pull requests: write`
- The workflow at `.github/workflows/sync-template.yml` runs every 10 minutes and on manual dispatch.
- If `SYNC_TOKEN` is not set, it falls back to `GITHUB_TOKEN` which only works when upstream is accessible to the workflow's token.