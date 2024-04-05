
---

# Node.js Application Deployment Guide with Virtual Environment

## Introduction
This guide details the process for setting up, testing, linting, and deploying a simple Node.js application, emphasizing the use of a virtual environment for local development and GitLab CI/CD for deployment.

## Setup Instructions

### Prerequisites
- Node.js installed on your machine.
- Git and GitLab account for version control and CI/CD.
- PowerShell for Windows users or Terminal for macOS/Linux users.

### Project Setup

#### Cloning the Repository
```powershell
git clone <repository-url>
cd <repository-name>
```

#### Setting Up a Virtual Environment Locally
Using PowerShell on Windows, you can set up a virtual environment for Node.js as follows. This step is crucial for isolating project dependencies.

```powershell
npm install -g nvm-windows
nvm install <node-version>
nvm use <node-version>
```
Replace `<node-version>` with the specific Node.js version you wish to use, for example, `14.17.0`.

### Application Files
Ensure your project contains:
- `app.js`: Main server file with Express.
- `app.test.js`: Jest tests.
- `.eslintrc`: ESLint configuration.
- `package.json`: Dependency and script definitions.

### Installing Project Dependencies
Within your virtual environment:
```powershell
npm install
```

## Testing and Linting

### Running Tests
Execute Jest tests with:
```powershell
npm test
```

### Linting
Run ESLint to identify and fix issues:
```powershell
npm run lint
```

## GitLab CI/CD Pipeline

### `.gitlab-ci.yml` Overview
Defines the CI/CD stages:
- **Build**: (Optional) Compile/build the application.
- **Test**: Lint and run tests.
- **Deploy**: Deploy to production.

### Configuring CI/CD in GitLab
1. Push `.gitlab-ci.yml` and project files to GitLab.
2. GitLab detects the CI/CD configuration and initiates the pipeline.
3. Monitor progress in the **CI/CD** section of your project in GitLab.

## Deploying to Production

### Deployment Configuration
Customize the `deploy_job` in `.gitlab-ci.yml` for your production server's needs.

### Manual Deployment (Example)
To deploy your application to a production server:

```powershell
# Copy files to your server
scp -r ./build/* user@your-server:/path/to/destination
# Restart your Node.js app (if using PM2)
ssh user@your-server "pm2 restart all"
```

### Continuous Deployment
Integrate continuous deployment into the `deploy_job` section of your `.gitlab-ci.yml` file, tailoring the commands to your server setup and deployment strategy.

## Conclusion
This guide has walked you through the process of developing, testing, and deploying a Node.js application within a virtual environment, leveraging GitLab CI/CD for efficient deployment practices. This approach ensures your development process is streamlined and consistent across different environments.


## GitLab Link and Screenshots

Here are the required details for this- 

https://gitlab.com/g16162114/schealth

Image1-
![image](https://github.com/simarmehta/Assessment-SCH-P2/assets/70880900/e97b1756-13ba-4076-86d4-ca63d9adf1a5)

Build Deploy Test Pass-

![image](https://github.com/simarmehta/Assessment-SCH-P2/assets/70880900/d6eb1c0b-ac89-4298-8e1e-f439da9242c2)

![image](https://github.com/simarmehta/Assessment-SCH-P2/assets/70880900/8ab1bb78-8901-4aa7-bc7c-fd76cf62e14b)


