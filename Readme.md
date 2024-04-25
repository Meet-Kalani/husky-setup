
## Instructions for Setting Up lint-staged and husky

Follow these steps to set up lint-staged and husky in your project:

1. **Install `lint-staged` using `mrm`:**
    ```bash
    npx mrm@2 lint-staged
    ```

2. **Initialize `husky` in your project:**
    ```bash
    npx husky init
    ```

3. **After executing the above command, a `pre-commit` file  is generated inside the `.husky` folder, Paste the following code into that file:**

    ```bash
    npm run prettier:fix
    npm run lint:staged
    ```

3. **Add the following commands under the `scripts` section in your `package.json` file:**
    ```json
    {
      "scripts": {
        "prettier:fix": "prettier --write .",
        "lint:staged": "lint-staged"
      }
    }
    ```

4. **Add the following configuration for `husky` as a sibling after `devDependencies` in your `package.json` file:**
    ```json
    {
      "husky": {
        "hooks": {
          "pre-commit": "lint-staged"
        }
      }
    }
    ```

5. **Ensure that the following `lint-staged` configuration is present in your `package.json` file, positioned after the above code:**
    ```json
    {
      "lint-staged": {
        "*.{js,jsx}": "eslint --cache --fix",
        "*.{js,css,md}": "prettier --write ."
      }
    }
    ```

Follow these steps, and you'll have lint-staged and husky set up in your project!

## Example

```json
{
  "name": "tmdb-clone",
  "private": true,
  "version": "0.0.0",
  "type": "module",
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "lint": "eslint . --ext js,jsx --report-unused-disable-directives --max-warnings 0",
    "preview": "vite preview",
    "prepare": "husky",
    "prettier:fix": "prettier --write .",
    "lint:staged": "lint-staged"
  },
  "dependencies": {
    "@emotion/react": "^11.11.4",
    "@emotion/styled": "^11.11.5",
    "@mui/material": "^5.15.15",
    "axios": "^1.6.8",
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "react-router-dom": "^6.22.3"
  },
  "devDependencies": {
    "@types/react": "^18.2.66",
    "@types/react-dom": "^18.2.22",
    "@vitejs/plugin-react": "^4.2.1",
    "eslint": "^8.57.0",
    "eslint-plugin-react": "^7.34.1",
    "eslint-plugin-react-hooks": "^4.6.0",
    "eslint-plugin-react-refresh": "^0.4.6",
    "husky": "^9.0.11",
    "lint-staged": "^15.2.2",
    "prettier": "^3.2.5",
    "sass": "^1.74.1",
    "vite": "^5.2.0"
  },
  "husky": {
    "hooks": {
      "pre-commit": "lint-staged"
    }
  },
  "lint-staged": {
    "*.{js,jsx}": "eslint --cache --fix",
    "*.{js,css,md}": "prettier --write ."
  }
}