# Ease

A versatile [Ghost](https://github.com/TryGhost/Ghost) theme suitable for documentation. Publish your posts or business information with ease.

**Demo: https://ease.ghost.io**

# Instructions

1. [Download this theme](https://github.com/TryGhost/Ease/archive/main.zip)
2. Log into Ghost, and go to the `Design` settings area to upload the zip file

## Local Testing with Docker

To test the theme locally with a full Ghost installation:

```bash
# Start Ghost with Docker
docker-compose up
```

This will:
- Start a Ghost instance at `http://localhost:2368`
- Mount the theme files for live development
- Set up a MySQL database with persistent storage

Once Ghost is running, you can:
1. Visit `http://localhost:2368` to see your site
2. Access the admin panel at `http://localhost:2368/ghost`
3. Make changes to the theme files - they'll be reflected immediately
4. Use `yarn zip` to package the theme for distribution

To stop the Docker environment:

```bash
docker-compose down
```

## Packaging the theme for distribution

```bash
yarn zip
```

# Contribution

This repo is synced automatically with [TryGhost/Themes](https://github.com/TryGhost/Themes) monorepo. If you're looking to contribute or raise an issue, head over to the main repository [TryGhost/Themes](https://github.com/TryGhost/Themes) where our official themes are developed.

# Copyright & License

Copyright (c) 2013-2025 Ghost Foundation - Released under the [MIT license](LICENSE).
