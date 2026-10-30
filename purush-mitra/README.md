# 🦍 Operation: Missing Purush Mitra

A playful, single-page friendship investigation built as one `index.html` file (plain HTML, CSS and JavaScript, no build step). The "Friendship Investigation Bureau" interrogates Akshay about going missing, ends with a Diwali greeting, a surprise gift box and a feedback form.

## Flow
1. **Intro:** life-status check ("I'm alive" or "Who is this?").
2. **Evidence:** optional exhibits A to E and a final report if he asks for proof.
3. **Questions** (each must be answered before Next unlocks):
   - Which department should handle your case
   - How busy are you
   - Did you miss the Gorilla
   - The verdict (choose a punishment)
4. **Certificate:** "Lifetime Purush Mitra Membership", with a PDF download.
5. **Diwali screen:** wishes, a gift box that bursts out desi sweets and chai, and a star rating with a feedback box.

## Features
- One GIF per screen (loaded from Giphy, so an internet connection is needed).
- Downloadable PDF certificate, built in the browser with html2canvas and jsPDF (loaded from cdnjs).
- Silent email notification to the owner with all answers, the PDF attached, and the final feedback and rating.

## Email setup (Google Apps Script)
Emails go through a small Google Apps Script web app, since a static page cannot send mail itself.
1. Create a project at [script.google.com](https://script.google.com) with a `doPost` that checks a shared token, reads the JSON body (`token`, `subject`, `answers`, `pdf` as base64) and calls `MailApp.sendEmail`.
2. Deploy it as a **Web app** (Execute as: Me, Access: Anyone) and copy the `/exec` URL.
3. In `index.html`, set `MAIL_URL` and `MAIL_TOKEN` to your URL and token.
4. After editing the script, redeploy it as a **New version**.

The URL and token are visible in the page source, so treat them as low-security.

## Publish on GitHub Pages
1. Upload `index.html` to the root of a public GitHub repository.
2. Go to **Settings → Pages**, choose **Deploy from a branch**, select `main` and `/ (root)`, then save.
3. Open `https://<username>.github.io/<repo-name>/` after a minute or two.

After later edits, re-upload `index.html` and hard-refresh (Ctrl+F5).

## Customising
- Texts, questions and reactions are in the `lines` and `notes` objects in the script at the bottom of `index.html`.
- GIFs are `<img>` tags inside each `<section class="screen">`.
- Colours and layout are in the `<style>` block at the top.
