---
name: deploy
description: Deploy the application with pre-deploy validation, deployment, and post-deploy verification
command: /deploy
---

## First Run Adaptation

Before your first deploy, scan the project:
1. Read package.json for the framework and build/test scripts
2. Check for deployment configs (vercel.json, railway.json, netlify.toml, fly.toml)
3. Look for .env.example or .env.production to know required environment variables
4. Identify the deployment platform from existing configs or ask

## Pre-deploy Checks

Run through this checklist before every deploy:

1. Run the build command (pnpm build, npm run build, etc.) and fix any errors
2. Run the test suite and make sure everything passes
3. Search for console.log statements in src/. Remove any that aren't intentional
4. Compare .env.example against the production environment to verify all required vars are set
5. Check that no .env files or secret files are staged for commit
6. Verify the git working tree is clean (no uncommitted changes)

## Deploy

If all checks pass:
1. Commit any pending changes with a descriptive message
2. Push to the main branch
3. Run the platform-specific deploy command:
   - Vercel: `vercel --prod`
   - Railway: `railway up`
   - Netlify: `netlify deploy --prod`
   - Fly.io: `fly deploy`
4. Wait for the deployment to complete

## Post-deploy

1. Hit the health endpoint (or homepage) and confirm it returns 200
2. Check deployment logs for any warnings or errors
3. Report the deployment URL and status
4. If anything fails, check the logs and report what went wrong
