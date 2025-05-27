# EdgeOne Pages Deploy Action

A GitHub Action to deploy your static sites to [EdgeOne Pages](https://edgeone.ai/products/pages).

## Features

- 🚀 Easy deployment to EdgeOne Pages
- 📦 Supports any static site generator (Next.js, React, Vue, etc.)
- ⚡ Fast and reliable deployment
- 🔧 Configurable build paths and project names

## Usage

### Basic Example

```yaml
name: Deploy to EdgeOne Pages

on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: "20"

      - name: Install dependencies
        run: npm install

      - name: Build
        run: npm run build

      - name: Deploy to EdgeOne Pages
        uses: TencentEdgeOne/edgeone-pages-action@v1
        with:
          token: ${{ secrets.EDGEONE_API_TOKEN }}
          project-name: "my-awesome-site"
          build-path: "./dist"
```

### Next.js Example

```yaml
name: Deploy Next.js to EdgeOne Pages

on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: "20"

      - name: Install dependencies
        run: npm install

      - name: Build Next.js
        run: npm run build

      - name: Deploy to EdgeOne Pages
        uses: TencentEdgeOne/edgeone-pages-action@v1
        with:
          token: ${{ secrets.EDGEONE_API_TOKEN }}
          project-name: "my-nextjs-site"
          build-path: "./out"
```

## Inputs

| Input          | Description                    | Required | Default  |
| -------------- | ------------------------------ | -------- | -------- |
| `token`        | EdgeOne API token              | Yes      | -        |
| `project-name` | Project name for EdgeOne Pages | Yes      | -        |
| `build-path`   | Path to the built static files | No       | `./dist` |
| `node-version` | Node.js version to use         | No       | `20`     |

## Setup

### 1. Get EdgeOne API Token

1. Visit [EdgeOne Pages](https://edgeone.ai/document/177158578324279296)
2. Generate your API token
3. Copy the token for the next step

### 2. Add Repository Secret

1. Go to your GitHub repository
2. Navigate to **Settings** → **Secrets and variables** → **Actions**
3. Click **New repository secret**
4. Name: `EDGEONE_API_TOKEN`
5. Value: Your EdgeOne API token from step 1
6. Click **Add secret**

### 3. Create Workflow

Create a `.github/workflows/deploy.yml` file in your repository with one of the examples above.

## Supported Static Site Generators

This action works with any static site generator that outputs static files:

- ✅ Next.js (with `output: 'export'`)
- ✅ React (Create React App)
- ✅ Vue.js
- ✅ Nuxt.js
- ✅ Gatsby
- ✅ Vite
- ✅ Astro
- ✅ Hugo
- ✅ Jekyll
- ✅ And many more...

## License

MIT License. See [LICENSE](LICENSE) for more information.

## Support

- 📖 [EdgeOne Pages Documentation](https://edgeone.ai/document/160427672992178176)
- 🐛 [Report Issues](https://github.com/TencentEdgeOne/edgeone-pages-action/issues)
