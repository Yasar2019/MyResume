# Displaying a LaTeX Resume with Language Switch on a Website

## Overview

This guide explains how to embed a LaTeX-generated PDF resume on a website with a simple language switch functionality, allowing users to switch between English and French versions. Additionally, you'll find a downloadable `.tex` file of my LaTeX resume as an example.

## Steps to Replicate

### 1. Compile LaTeX to PDF

To start, you need to create your resume in LaTeX. If you don't have LaTeX installed on your machine, you can use [Overleaf](https://www.overleaf.com/), an online LaTeX editor, to write and compile your `.tex` file into a PDF.

You can refer to my example LaTeX file, [Yasar_Nazzarian_Resume.tex](resume.tex), to get started. Download it and customize it with your own details.

### 2. Create Two PDF Versions (English and French)

Once you've created your LaTeX resume, compile two versions:

- **English** version: `Yasar_Nazzarian_Resume_EN.pdf`
- **French** version: `Yasar_Nazzarian_Resume_FR.pdf`

You can either create separate LaTeX files for each language or use LaTeX commands to localize within the same file.

### 3. Host the PDFs on Your Website

Next, upload the two PDF files to your web server or a cloud storage solution like AWS, Google Drive, or GitHub Pages.

### 4. Embed the PDFs with a Language Switch

Now, create a simple HTML page to embed the PDFs using `<embed>` or `<iframe>` tags. You can add JavaScript to allow users to switch between the English and French versions of your resume.

Below is the HTML code you can use:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>[your name] Resume</title>
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Roboto', sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f9;
            color: #333;
        }

        .container {
            width: 80%;
            margin: auto;
            padding: 20px;
            background: white;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }

        header {
            text-align: center;
            margin-bottom: 20px;
        }

        .language-switch {
            display: flex;
            justify-content: center;
            margin-bottom: 20px;
        }

        .language-switch button {
            background-color: #007bff;
            color: white;
            padding: 10px 20px;
            border: none;
            cursor: pointer;
            font-size: 16px;
            margin: 0 10px;
        }

        .language-switch button:hover {
            background-color: #0056b3;
        }

        embed {
            width: 100%;
            height: 600px;
        }
    </style>
    <script>
        function switchLanguage(lang) {
            const pdfFrame = document.getElementById('pdfFrame');
            if (lang === 'en') {
                pdfFrame.src = '[Path to EN version].pdf';
            } else {
                pdfFrame.src = '[Path to FR version].pdf';
            }
        }
    </script>
</head>
<body>
    <div class="container">
        <header>
            <h1>[Your Name] Resume</h1>
        </header>

        <div class="language-switch">
            <button onclick="switchLanguage('en')">English</button>
            <button onclick="switchLanguage('fr')">Français</button>
        </div>

        <embed id="pdfFrame" src="[Path to EN version].pdf" type="application/pdf" />
    </div>
</body>
</html>
```
