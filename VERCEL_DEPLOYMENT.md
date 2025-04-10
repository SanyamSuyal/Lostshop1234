# Deploying to Vercel

This guide will help you deploy your Discord bot marketplace application to Vercel.

## Prerequisites

- A [Vercel account](https://vercel.com/signup)
- A [GitHub account](https://github.com/signup) to push your code to (optional, but recommended)
- A [Neon PostgreSQL](https://neon.tech) database (or another PostgreSQL provider)

## Setup Steps

### 1. Database Configuration

Make sure you have your PostgreSQL database URL ready. If you're using Neon:

1. Create a new project in Neon
2. Get your connection string from the dashboard
3. You'll need to add this as an environment variable in Vercel

### 2. Vercel Setup

1. Push your code to GitHub (recommended)
2. Log in to Vercel and create a new project
3. Import your repository from GitHub
4. Configure the project as follows:

   - **Build Command**: `npm run build`
   - **Output Directory**: `dist` 
   - **Environment Variables**:
     - `DATABASE_URL`: Your PostgreSQL connection string
     - `SESSION_SECRET`: A secure random string for session encryption
     - Any other API keys your application requires

5. Deploy your project

### 3. Vercel Configuration

Vercel should automatically detect your Node.js project. The `vercel.json` file in your project root configures:

- Server-side rendering for your backend API
- Static serving for your frontend assets
- Routing to direct API calls to your backend and all other requests to your frontend

If you encounter issues with routing or builds, you might need to adjust the `vercel.json` file.

## After Deployment

1. Run the database migration to set up your database schema:
   - This will happen during the build process if configured correctly

2. Monitor your application logs in the Vercel dashboard for any issues

3. Set up a custom domain if needed through the Vercel dashboard

## Troubleshooting

- **Database Issues**: Make sure your `DATABASE_URL` is correctly set and accessible
- **Build Errors**: Check the build logs in Vercel for specific errors
- **API Not Working**: Verify the routes in `vercel.json` are correctly configured
- **Session Issues**: Ensure `SESSION_SECRET` is set and doesn't change between deployments