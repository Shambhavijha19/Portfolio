# Deploy to Netlify (automated)

This project includes a GitHub Actions workflow that will automatically build and deploy the site to Netlify when you push to the `main` branch.

What I added
- `.github/workflows/netlify-deploy.yml` — builds with `npm run build` and deploys `dist` to Netlify using the Netlify CLI action.

What you need to do (3 quick steps)

1) Create a Netlify Personal Access Token
- Sign in at https://app.netlify.com/
- Go to User Settings → Applications → Personal access tokens → "New access token"
- Copy the token (keep it secret)

2) Find your Netlify Site ID
- Create a site on Netlify and connect it (or create an empty site). In Site Settings → Site information you will find the "Site ID". Copy it.

3) Add GitHub repository and secrets
- Push this repository to GitHub (if you haven't):

```cmd
cd /d "C:\Users\jhash\Desktop\portfolio\Portfolio-website"
git init
git add .
git commit -m "Initial commit: portfolio"
git remote add origin <your-git-repo-url>
git push -u origin main
```

- In your GitHub repo, go to Settings → Secrets and variables → Actions → New repository secret.
  - Add `NETLIFY_AUTH_TOKEN` with the token from step 1.
  - Add `NETLIFY_SITE_ID` with the site id from step 2.

After those steps, any push to `main` will trigger the workflow and deploy the built `dist` to your Netlify site.

Alternative (Netlify UI or CLI)
- You can also connect the GitHub repo directly in Netlify (recommended) and set build command `npm run build` and publish directory `dist`.
- Or use Netlify CLI locally: `npx netlify-cli deploy --dir=dist --prod --site <SITE_ID>` (requires `NETLIFY_AUTH_TOKEN` environment variable).

If you want, tell me the GitHub repo URL and I will verify the workflow file is correct and give any small edits needed. I cannot run the deploy on your Netlify account without your token; instead, the workflow will deploy when you push and add the secrets.
