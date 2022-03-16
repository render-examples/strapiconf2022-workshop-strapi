# Strapi App for StrapiConf 2022 Workshop
## Build a Productivity Tips App with Remix, Render, and Strapi

### Workshop Prep

*If possible, please complete these five steps prior to the start of the workshop.*

1. [Install Node.js](https://nodejs.org/en/download/)
2. [Install Yarn](https://classic.yarnpkg.com/lang/en/docs/install/)
3. [Install git](https://git-scm.com/downloads)
4. [Create Render account](https://dashboard.render.com/register)
5. [Create Cloundinary account](https://cloudinary.com/users/register/free)

### Set up Strapi

1. Click **Use this template** to create your own copy of this repository
2. `git clone` from your copy of this repository
3. Run `cd strapiconf2022-workshop-strapi` to go into the cloned directory
4. Run `yarn install` to install dependencies
5. Run `cp .env.example .env` to define some environment variables for Strapi for local development.
6. Run `yarn develop` to start Strapi in development mode
7. In the `/admin` Strapi GUI, create your admin account. Note that this is only for Strapi running on your local development machine. We will create another admin user for the production deploy.
8. In the **Content-Type Builder**, review **Tip** content type that's been created for you
9. In **Content Manager**, click **Create new entry** to create some sample data -- your first Productivity Tip!
10. You're now done with set up of the Strapi app for local development. Follow the steps in https://github.com/render-examples/strapiconf2022-workshop-remix#README to set up the Remix app for local development.

### Deploy to Production on Render

*Complete the steps above, including step 9, before proceding with these steps.*

1. Edit the **two** `repo:` lines in the `render.yaml` in your copy of this repository. The first one -- your Strapi API -- should be the GitHub URL of your copy of this repository. The second one -- your Remix app -- should be the GitHub URL of your Remix repository.
2. `git add render.yaml`, `git commit` and `git push` your changes.
3. Login to the [Render Dashboard](https://dashboard.render.com).
4. Click **New** --> **Blueprint**.
5. Paste the URL of your copy of this repository, and click the resolved repository. If you have not already, you will need to connect your GitHub account with Render.
6. Provide a name for your **Service Group**.
7. Provide a value for each of the three Cloudinary environment variables. Copy them from your [Cloudinary dashboard](https://cloudinary.com/console/).
8. Click **Apply**.
9. When the **productivity-tips-api** deploy is finished, go to its `.onrender.com` URL and append `/admin` to it to view the Strapi Admin GUI. You'll need to create an admin user after the first deploy to Render.
10. Then create an API Token: **Settings** --> **API Tokens** --> **Create new API Token**. This will be used by your Remix app to make secure API requests to Strapi.
11. In the Render Dashboard, click on your Remix service. It may still be deploying, but that's ok. Then in **Environment**, click **Add Environment Variable**.
12. Set the **Key** as `STRAPI_API_TOKEN` and paste in the Strapi API token you generated as the **Value**.
13. Click **Save Changes**, and your Remix app will redeploy using this new value.
14. While the Remix redeploy is happening, go back to your production Strapi Admin GUI (at `/admin` of your Strapi service `.onredner.com` URL) and add some productivity tips so that there is some data for the Remix app to display.