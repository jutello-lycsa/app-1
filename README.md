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
- Prefer adding `SYNC_TOKEN` as a Repository secret (Actions → Secrets → New repository secret). If you keep it as an Environment secret, ensure the job targets that environment and that no approvals are required.

### Required Token Permissions
- Classic PAT: scope `repo`.
- Fine‑grained PAT: Contents: Read for the upstream repository.
- If organization SSO applies, authorize the PAT for the org.

### Verify and Run
1) Confirm upstream access (replace `<TOKEN>` if private):
```bash
git ls-remote https://github.com/jutello-lycsa/front-template.git
git ls-remote https://x-access-token:<TOKEN>@github.com/jutello-lycsa/front-template.git
```
2) Trigger the workflow manually in GitHub → Actions → "Sync Template" → Run workflow.
3) Expected result: branch `sync/front-template` is pushed and a PR is opened to the default branch if there are changes.