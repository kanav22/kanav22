# TMDB API Token Rotation

Your TMDB bearer token was previously committed to git history in `compose-movies-finder` before it was moved to `local.properties`. **Rotation is required** even though the secret is no longer in current source.

---

## Step 1: Revoke the old token

1. Log in at [themoviedb.org](https://www.themoviedb.org/settings/api)  
2. Go to **Settings → API**  
3. Delete or regenerate the API Read Access Token that was exposed  

---

## Step 2: Create a new token

1. Generate a new **API Read Access Token (v4)**  
2. Copy the token — you will not see it again  

---

## Step 3: Update local development

In `compose-movies-finder/local.properties` (not committed):

```properties
TMDB_ACCESS_TOKEN=your_new_token_here
```

Verify build:

```bash
cd compose-movies-finder
./gradlew assembleDebug
```

---

## Step 4: Update GitHub Actions secret

```bash
gh secret set TMDB_ACCESS_TOKEN -R kanav22/compose-movies-finder
# paste new token when prompted
```

Or: GitHub repo → **Settings → Secrets and variables → Actions** → update `TMDB_ACCESS_TOKEN`.

---

## Step 5: Verify CI

```bash
gh workflow run ci.yml -R kanav22/compose-movies-finder
gh run list -R kanav22/compose-movies-finder --limit 1
```

---

## Optional: purge git history

If the old token must be treated as fully compromised, use [GitHub secret scanning remediation](https://docs.github.com/en/code-security/secret-scanning/working-with-secret-scanning-and-push-protection/working-with-push-protection-from-the-command-line) or BFG Repo-Cleaner. For a personal portfolio repo, **rotation alone is usually sufficient**.

---

## Prevention

- Never commit tokens — use `local.properties.example` with placeholder only  
- CI uses GitHub Secrets, not hardcoded values  
- See `compose-movies-finder/SECURITY.md` for reporting issues  
