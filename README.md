# 🚀 ArgoCD Sync Action

**ArgoCD Sync Action** is a GitHub Action that **refreshes and syncs multiple ArgoCD applications** using the ArgoCD API.

🔮 **Future Roadmap**: Add support for rolling back to a previous version of an ArgoCD Application. *(TODO)*

## ✨ Features

* 🔄 Refresh multiple ArgoCD applications in a single workflow run
* 🔗 Sync applications with the desired state in Git
* 🔐 Secure authentication with username/password via GitHub secrets
* ⚡ Lightweight and simple to integrate in your CI/CD pipeline

## ⚙️ Inputs

| Name | Required | Default | Description |
|------|----------|---------|-------------|
| `argocd_server` | ✅ Yes | – | ArgoCD Server URL (e.g., `https://argocd.example.com`) |
| `argocd_username` | ✅ Yes | – | ArgoCD username |
| `argocd_password` | ✅ Yes | – | ArgoCD password |
| `argocd_app_names` | ✅ Yes | – | Comma-separated list of ArgoCD Application names (e.g., `app1,app2,app3`) |
| `refresh_app` | ❌ No | `false` | Whether to refresh the applications |
| `sync_app` | ❌ No | `false` | Whether to sync the applications |

## 📋 Example Usage

```yaml
name: Deploy via ArgoCD

on:
  push:
    branches: [ "main" ]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v3

      - name: ArgoCD API Action
        uses: MayurDuduka/argocd-sync-action@v1.0
        with:
          argocd_server: ${{ secrets.ARGOCD_SERVER }}
          argocd_username: ${{ secrets.ARGOCD_USERNAME }}
          argocd_password: ${{ secrets.ARGOCD_PASSWORD }}
          argocd_app_names: "app1,app2,app3"
          refresh_app: "true"
          sync_app: "true"
```

## 🔒 Security Best Practices

* Always store your **ArgoCD server credentials** in GitHub Secrets.
* Do **not** hardcode usernames, passwords, or tokens in your workflow files.

## 🛠️ Development

Clone and test locally:

```bash
git clone https://github.com/MayurDuduka/argocd-api.git
cd argocd-api
npm install
```

Run:

```bash
node src/index.js
```

## 📜 License

This project is licensed under the Apache License 2.0.