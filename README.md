# personal-website-hosted-on-cloud
cloud website 
html/css website code 
<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>My Personal Website</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f3f3f3;
      color: #333;
      text-align: center;
      margin-top: 50px;
    }
    h1 {
      color: #007acc;
    }
  </style>
</head>
<body>
  <h1>Hello, I'm [Your Name] 👋</h1>
  <p>Welcome to my personal cloud-hosted website!</p>
</body>
</html>
github action on auto deploy 
name: Deploy to S3

on:
  push:
    branches: [ main ]

jobs:
  deploy:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout code
      uses: actions/checkout@v3

    - name: Configure AWS credentials
      uses: aws-actions/configure-aws-credentials@v2
      with:
        aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
        aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
        aws-region: us-east-1

    - name: Deploy to S3
      run: aws s3 sync . s3://your-bucket-name --delete --acl public-read --exclude ".git/*" --exclude ".github/*"

some github code 
personal-website/
│
├── index.html
├── .github/
│   └── workflows/
│       └── deploy.yml
└── README.md
read.me
# 🌐 Personal Website Hosted on AWS S3

This is a simple personal website hosted on AWS S3 with optional GitHub Actions for continuous deployment.

## Tech Stack
- HTML/CSS
- AWS S3 (Static Hosting)
- GitHub Actions (CI/CD)

## 🚀 Live Demo
[https://your-bucket-name.s3-website-region.amazonaws.com](#)

## Project Structure
- `index.html` — the main landing page
- `.github/workflows/deploy.yml` — CI/CD pipeline to auto-deploy to S3

##Secrets Required
- `AWS_ACCESS_KEY_ID`
- `AWS_SECRET_ACCESS_KEY`

---

