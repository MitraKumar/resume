# Resume Management with LaTeX & GitHub Actions

This repository contains the LaTeX source code for my professional resume, along with an automated CI/CD pipeline to compile it into a PDF and distribute it via GitHub Releases.

## 📂 Project Structure

- **[src/resume.tex](file:///home/kaushik/Projects/resume/src/resume.tex)**: The main LaTeX source document.
- **[.github/workflows/compile-resume.yml](file:///home/kaushik/Projects/resume/.github/workflows/compile-resume.yml)**: The GitHub Actions workflow configuration.
- **[.gitignore](file:///home/kaushik/Projects/resume/.gitignore)**: Configured to ignore intermediate LaTeX build output files and compiled PDF files locally.

---

## 🚀 CI/CD Pipeline

The GitHub Actions workflow automates the LaTeX compilation using the standard `pdflatex` engine (via `xu-cheng/latex-action`).

### Workflow Triggers & Actions:
1. **GitHub Release Publication**: When a release is published, the workflow compiles the resume, renames the output to `Kaushik Kumar Mitra - CV.pdf`, and automatically attaches it to the release assets using the GitHub CLI (`gh release upload`).
2. **Manual Trigger (`workflow_dispatch`)**: Allows compiling the PDF on-demand from the GitHub Actions tab, producing the `Kaushik Kumar Mitra - CV.pdf` workflow artifact.

---

## 🛠️ How to Edit & Publish

### 1. Make Changes Locally
Edit the LaTeX source in **[src/resume.tex](file:///home/kaushik/Projects/resume/src/resume.tex)**.

#### Local Compilation (Optional)
If you have a LaTeX distribution installed (like TeX Live or MacTeX), you can compile it locally:
```bash
pdflatex -output-directory=src src/resume.tex
```
> [!NOTE]
> Ensure you have the `lato` font package installed on your local TeX distribution.

### 2. Push Changes
Commit and push your updates to the remote repository:
```bash
git add src/resume.tex
git commit -m "Update experience / skills"
git push origin main
```

### 3. Create a Release (to publish the PDF)
To generate the final PDF and attach it to a release:
1. Go to your repository on GitHub.
2. Under the **Releases** section on the right sidebar, click **Create a new release** (or **Draft a new release**).
3. Choose a tag version (e.g., `v1.0.0` or `v2026.07.18`).
4. Enter a release title and description.
5. Click **Publish release**.
6. The GitHub Action will trigger, compile the PDF, rename it, and attach the compiled `Kaushik Kumar Mitra - CV.pdf` to the release assets.
