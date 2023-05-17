---
title: "Next.js on \U0001F917 Spaces"
emoji: "🐳🤗"
colorFrom: blue
colorTo: yellow
sdk: docker
pinned: false
license: agpl-3.0
app_port: 3000
---
<h1 align="center">Next.js on 🤗 Spaces</h1>

This starter can be used to run [Next.js](https://nextjs.org/) using [Docker](https://huggingface.co/docs/hub/spaces-sdks-docker) on 🤗 [Spaces](https://huggingface.co/spaces).

<!-- toc -->

- [Local development](#local-development)
- [Use the Docker container locally](#use-the-docker-container-locally)
- [Dockerize an existing project](#dockerize-an-existing-project)
- [Manage your 🤗 Space via GitHub](#manage-your-%F0%9F%A4%97-space-via-github)

<!-- tocstop -->

---

## Local development

1. Install the dependencies: `npm i`
2. Start the local dev-server: `npm run dev`
3. Open the app via [localhost:3000](http://localhost:3000)

## Use the Docker container locally

To make sure that everything is working out, you can run your container locally:

1. [Install Docker](https://docs.docker.com/get-docker/) on your machine
2. Go into the `nextjs-hf-spaces` folder
3. Build your Docker image: `docker build -t nextjs-hf-spaces .`.
4. Run your Docker container: `docker run -p 3000:3000 nextjs-hf-spaces`.
5. Open the app via [localhost:3000](http://localhost:3000)

## Dockerize an existing project

To add support for Docker to an existing project, just copy the `Dockerfile` into the root of the project and add the following to the `next.config.js` file:

```js
// next.config.js
module.exports = {
  // ... rest of the configuration.
  output: "standalone",
};
```

This will build the project as a standalone app inside the Docker image.

## Manage your 🤗 Space via GitHub

If you want to use all the features for collaborative development on GitHub, but keep your demo on Spaces, then you can set up a GitHub action that will automatically push changes from GitHub into Spaces.

> ℹ️ Git-LFS is required for files bigger than 10MB

1. Create your repo on GitHub
2. Create a [Github secret](https://docs.github.com/en/actions/security-guides/encrypted-secrets#creating-encrypted-secrets-for-a-repository) named `HF_TOKEN` and use an [access token from Hugging Face](https://huggingface.co/settings/tokens) as its value (you must be logged in to do this)
3. Update the workflow [sync_to_hf_spaces.yml](.github/workflows/sync_to_hf_spaces.yml)
   - Configure `HF_USERNAME`: Replace `failfast` with the name of your 🤗 user account or your 🤗 organization
   - Configure `HF_SPACE_NAME`: Replace `nextjs-hf-spaces` with the name of your 🤗 space
4. Push the code into your repo on GitHub

This should force push changes in the **main** branch from GitHub into your 🤗 space.

For further information, you can check out the [guide on Hugging Face](https://huggingface.co/docs/hub/spaces-github-actions).


