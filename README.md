# JAIN College Lost & Found — CampusFind

A responsive lost-and-found noticeboard for JAIN University.

## Included
- React + TypeScript application, Vinext and CSS
- Lost / found reports, category and search filters
- Photo picker and mobile camera file input
- Contact reporter using email
- Mark a report as reunited and delete your own reports
- Cloudflare D1 database schema and migration
- Cloudflare R2 image-storage endpoints
- JAIN campus background photo

## GitHub upload with GitHub Desktop
1. Extract this ZIP. Open the project folder, not the ZIP.
2. Install GitHub Desktop from https://desktop.github.com/download/
3. Sign in to your GitHub account.
4. Choose File > Add local repository and select this folder.
5. If prompted that it is not a Git repository, choose Create a Repository here.
6. Keep the existing README and .gitignore. Choose no extra license unless desired.
7. Commit any remaining files with summary: Initial commit - College Lost and Found.
8. Click Publish repository. Set the repository name to jain-college-lost-found.
9. Select your preferred visibility and click Publish repository.
10. Choose Repository > View on GitHub to confirm the upload.

## Important architecture notes
Publishing a repository stores the source code. It does not automatically host a working website.
The existing deployed website continues to run independently at:
https://jain-campus-lost-found.singh-01-nidhi11.chatgpt.site

This app uses Cloudflare Workers bindings named DB (D1) and BUCKET (R2), declared
in .openai/hosting.json. A separate deployment must provision these services and
apply drizzle/0000_jittery_jack_flag.sql. GitHub Pages alone cannot run these APIs.

This ZIP includes source, dependencies manifests/lockfile, setup scripts,
database schema/migration and the campus image. It excludes installed dependencies,
build output, Git history, environment files, credentials and local runtime state.
Existing hosted reports and user-uploaded images are server data and are NOT included.
The pre-existing hosting manifest identifies the original Sites project; it is not
an API secret and does not grant deployment access.

## Local development
Install Node.js meeting package.json engines (>=22.13.0) and pnpm matching
package.json packageManager. In a terminal in this folder:

    pnpm install --frozen-lockfile
    pnpm build

Initialize the local D1 database (the migration must be applied once to a fresh database):

    node --import ./scripts/sites-env.mjs ./node_modules/wrangler/bin/wrangler.js d1 execute DB --local --config dist/server/wrangler.json --persist-to .wrangler/state --file drizzle/0000_jittery_jack_flag.sql

Then start:

    pnpm dev

Use the local URL printed by the terminal. Local D1 and R2 data are separate
from the existing hosted website. External hosting needs Cloudflare-compatible
Worker deployment configuration and its own bindings.

## Source version
Exported from commit 130509c45c4b41be72ab21dc33b22312a40f8e6a.
