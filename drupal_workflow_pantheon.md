ChatGPT Prompt:

Create all the necessary files for a GitHub repository that will be used in a continuous integration (CI) workflow for deploying a Drupal 11 website to Pantheon. The repository should be structured as a template project and optimized for efficiency, modularity, and maintainability.

Repository Structure & Inclusions

- Include only essential files that cannot be generated during composer install:
- Drupal configuration directory: config/
- Custom modules directory: modules/custom/
- Uncompiled Drupal theme directory: themes/custom/your-theme/
- Lando configuration: .lando.yml
- Use a Composer-based installation, which will install Drupal core, contrib modules, and themes.
- Ensure the repository follows best practices for Drupal development and deployment.

GitHub Actions Workflow

Create two GitHub Actions workflows inside .github/workflows/:

1. CI/CD Workflow (ci.yml)

- Trigger Conditions:
- Push to main → Deploys to Pantheon Dev.
- Push to rc-\* branches → Creates/updates a Multidev environment.
- Process:
- Checkout the repository.
- Install dependencies using composer install.
- Set up Node.js (v18) and install dependencies.
- Compile the SCSS-based Drupal theme using Webpack.
- Deploy the site using Terminus:
- Authenticate with Pantheon Machine Tokens (stored as a GitHub secret).
- Deploy to Dev or Multidev, depending on the branch.
- Use GitHub Variables for configurable settings (e.g., PANTHEON_SITE_NAME).

2. Testing Workflow (test.yml)

- Trigger Condition: Runs on pull requests to main.
- Process:
- Validate Composer configuration.
- Run PHP CodeSniffer for Drupal coding standards.
- Lint SCSS files using stylelint.
- Ensure the theme builds correctly with Webpack.

Additional Configuration & Best Practices

- The .lando.yml file should:
- Use the Pantheon recipe for Drupal.
- Run PHP 8.3 with Nginx as the web server.
- Use MariaDB 10.4 as the database.
- Configure tooling for Composer, Drush, and NPM.
- The theme setup should include:
- A package.json file with Webpack, SCSS processing, and linting.
- A webpack.config.js file for compiling SCSS into CSS.
- The composer.json file should be based on Pantheon’s drupal-composer-managed upstream and configured for Drupal 11.
- Ensure GitHub secrets and variables are used to securely manage credentials and configurations.
- Include a README.md file that documents the project setup, local development, CI/CD process, and deployment instructions.

Deliverables:

- A fully structured GitHub repository with all required files.
- A CI/CD workflow (ci.yml) for automated deployment to Pantheon.
- A testing workflow (test.yml) for validating code quality on pull requests.
- A Pantheon-optimized composer.json file.
- A .lando.yml file with a Pantheon-based development setup.
- A Webpack-based SCSS theme setup (package.json, webpack.config.js).
- A detailed README.md with setup and deployment instructions.

Ask me clarifying questions until you are 95% confident you can complete the task successfully. Take a deep breath and take it step by step.
Remember to search the internet to retrieve up-to-date information.
