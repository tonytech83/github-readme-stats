# Deploy your own GitHub Readme stats

## First step: get your Personal Access Token (PAT)

For deploying your own instance of GitHub Readme Stats, you will need to create a GitHub Personal Access Token (PAT). Below are the steps to create one and the scopes you need to select for both classic and fine-grained tokens.

Selecting the right scopes for your token is important in case you want to display private contributions on your cards.

### Classic token

- Go to [Account -> Settings -> Developer Settings -> Personal access tokens -> Tokens (classic)](https://github.com/settings/tokens).
- Click on `Generate new token -> Generate new token (classic)`.
- Scopes to select:
  - repo
  - read:user
- Click on `Generate token` and copy it.

### Fine-grained token

> [!WARNING]\
> This limits the number of issues to the number of issues on your repositories only and only takes public commits into account.

- Go to [Account -> Settings -> Developer Settings -> Personal access tokens -> Fine-grained tokens](https://github.com/settings/tokens).
- Click on `Generate new token -> Generate new token`.
- Select an expiration date
- Select `All repositories`
- Scopes to select in `Repository permission`:
  - Commit statuses: read-only
  - Contents: read-only
  - Issues: read-only
  - Metadata: read-only
  - Pull requests: read-only
- Click on `Generate token` and copy it.

## On other platforms

### Step-by-step guide for deploying on other platforms

1.  Install prerequisites (Debian)

```sh
sudo apt update
sudo apt install -y git curl nodejs npm
```

2.  Clone this repo as per your needs

```sh
git clone https://github.com/<your-username>/github-readme-stats.git
cd github-readme-stats
```

3.  Create `.env` file in the project root (same folder as express.js)

```plain
PAT_1=<YOUR_GITHUB_TOKEN_HERE>
```

4.  Initial setup

```sh
npm install
```

5.  To start the server run.

```sh
npm start
# or
node express.js
```

6.  You're done 🎉

## Available environment variables

GitHub Readme Stats provides several environment variables that can be used to customize the behavior of your self-hosted instance. These include:

<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Description</th>
      <th>Supported values</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>CACHE_SECONDS</code></td>
      <td>Sets the cache duration in seconds for the generated cards. This variable takes precedence over the default cache timings for the public instance. If this variable is not set, the default cache duration is 24 hours (86,400 seconds).</td>
      <td>Any positive integer or <code>0</code> to disable caching</td>
    </tr>
    <tr>
      <td><code>WHITELIST</code></td>
      <td>A comma-separated list of GitHub usernames that are allowed to access your instance. If this variable is not set, all usernames are allowed.</td>
      <td>Comma-separated GitHub usernames</td>
    </tr>
    <tr>
      <td><code>GIST_WHITELIST</code></td>
      <td>A comma-separated list of GitHub Gist IDs that are allowed to be accessed on your instance. If this variable is not set, all Gist IDs are allowed.</td>
      <td>Comma-separated GitHub Gist IDs</td>
    </tr>
    <tr>
      <td><code>EXCLUDE_REPO</code></td>
      <td>A comma-separated list of repositories that will be excluded from stats and top languages cards on your instance. This allows repository exclusion without exposing repository names in public URLs. This enhances privacy for self-hosted instances that include private repositories in stats cards.</td>
      <td>Comma-separated repository names</td>
    </tr>
    <tr>
      <td><code>FETCH_MULTI_PAGE_STARS</code></td>
      <td>Enables fetching all starred repositories for accurate star counts, especially for users with more than 100 repositories. This may increase response times and API points usage, so it is disabled on the public instance.</td>
      <td><code>true</code> or <code>false</code></td>
    </tr>
  </tbody>
</table>
