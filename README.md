# QuizOrbit — GitHub-only Coaching-wise Quiz Website

A static quiz library for publishing self-contained HTML tests. **No Supabase, database, API key, admin upload panel, or backend is used.** All tests added to this GitHub repository are publicly accessible to website visitors after deployment.

## How it works

- Add a folder for each coaching under `public/tests/`.
- Upload any number of `.html` quiz files into that coaching folder.
- The build script scans these folders and generates `public/tests.json` automatically.
- Push/commit to GitHub. Vercel and Render rebuild the website and the new tests appear in the public library.
- Deploy the same GitHub repository to both Vercel and Render.

## Repository layout

```text
quiz-website-repo/
├── public/
│   ├── index.html
│   ├── tests.json                 # generated during build; do not edit manually
│   └── tests/
│       ├── README.md
│       ├── Demo Coaching/
│       │   └── Rajasthan Geography Demo.html
│       ├── Vision IAS/
│       │   ├── Polity Test 01.html
│       │   └── Economy Test 02.html
│       └── Vajiram and Ravi/
│           └── Geography Mock.html
├── scripts/
│   └── build-manifest.js
├── package.json
├── vercel.json
├── render.yaml
├── .gitignore
├── LICENSE
└── README.md
```

The `Vision IAS` and `Vajiram and Ravi` files above are examples; create any coaching folder names you want. The repository includes the supplied demo quiz at `public/tests/Demo Coaching/Rajasthan Geography Demo.html`.

## Add tests through GitHub

1. Open this repository on GitHub.
2. Open `public/tests/`.
3. Create a new folder using the coaching name, such as `Vision IAS`.
4. Upload your self-contained `.html` test file into that folder.
5. Commit the changes.
6. Wait for the automatic deployment on Vercel and/or Render to finish. The coaching and test should then appear on the website.

Repeat for as many coaching folders and HTML tests as you need. Each test must be inside a coaching folder and must be a working HTML quiz. Visitors can open and attempt the published tests; files are public, so do not upload confidential material.

## Deploy on Vercel

1. Push the whole repository to GitHub.
2. In Vercel, import the GitHub repository.
3. Framework preset: **Other**.
4. Build command: `npm run build`.
5. Output directory: `public`.
6. Deploy.

`vercel.json` contains the deployment configuration too.

## Deploy on Render

1. In Render, create a **Static Site** connected to the same GitHub repository.
2. Build command: `npm run build`.
3. Publish directory: `public`.
4. Deploy.

`render.yaml` contains the Render configuration.

## Local build

Requires Node.js 18 or newer:

```bash
npm run build
```

This regenerates `public/tests.json` by scanning `public/tests/`. Do not edit the generated manifest by hand.

## Important limitations

- This is intentionally a GitHub-managed static site. There is no upload button on the live website.
- Adding, renaming, or deleting tests requires a GitHub commit and a new deployment/build.
- Only `.html` files inside a coaching folder are listed.
- Test HTML files are publicly accessible and run as normal web pages. Upload only trusted HTML files.
- Free hosting and repository limits may apply to very large files or repositories.
