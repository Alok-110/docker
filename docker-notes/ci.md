# CI (Continuous Integration) – Basics

## What is CI?

CI (Continuous Integration) is a system that automatically checks your code whenever you push changes to GitHub.

Instead of manually running commands every time, CI runs them for you and tells you if something is broken.

---

## Why we need CI

Normally, after writing code, we have to manually:

* Run the app (`npm run dev`)
* Check if it builds (`npm run build`)
* Check for code issues (`npm run lint`)

This is:

* easy to forget
* inconsistent
* error-prone

CI solves this by automating these checks.

---

## What CI does (flow)

1. You write code locally

2. You push code to GitHub

3. GitHub Actions (CI) starts automatically

4. It runs predefined commands like:

   * install dependencies
   * build the project
   * run lint checks

5. It gives result:

   * ✔ Success → code is safe
   * ❌ Failed → something is broken

---

## What we set up

### 1. Workflow file

We create:

.github/workflows/ci.yml

This file tells CI what to do.

---

### 2. Tools we install

We install:

* eslint → checks code quality and potential issues
* prettier → formats code consistently

---

## Install command

npm i -D eslint@9 @eslint/js@9 prettier globals eslint-plugin-react-hooks eslint-plugin-react-refresh

---

## Package.json scripts

We add scripts like:

"scripts": {
"lint": "eslint .",
"format": "prettier --write .",
"build": "npm run build"
}

---

## What each tool does

* ESLint → finds problems and bad practices in code
* Prettier → fixes formatting (spacing, alignment, etc.)

---

## What CI actually runs

CI typically runs:

* npm install
* npm run build
* npm run lint

If any step fails → CI fails

---

## Important notes

* CI does NOT run automatically on your local machine
* It runs only when you push code or create a pull request
* CI checks code — it does not deploy your app

---

## Summary

* CI = automatic code checking system
* Workflow file = instructions for CI
* ESLint = code quality checker
* Prettier = code formatter
* CI ensures broken code does not go unnoticed
