# How to edit your Box The Box website

This is the only file you need to read. It's written for someone who has never edited a website before. If you can change a phone number in your contacts app, you can edit this site.

---

## TL;DR

1. To **share a link with anyone right now** (no domain needed), go to **https://app.netlify.com/drop** and drag this folder onto the page. You get a public link in 60 seconds.
2. To **change phone, email, address, stats, the testimonial** — open `index.html` in any text editor, find the section at the top labelled `EDIT YOUR DETAILS HERE`, change the words inside the quotes.
3. To **attach your own domain (boxthebox.in)** later — see `LAUNCH-GUIDE.md`.

---

## Part 1 — Share it as a public link RIGHT NOW (60 seconds)

You don't need to buy a domain to share this site. You can put it on the internet free, get a link like `boxthebox-xyz.netlify.app`, and share that link with anyone.

### Steps

1. Open **https://app.netlify.com/drop** in your browser.
2. Find the folder this file is in on your computer (the folder containing `index.html`, `images`, etc.).
3. **Drag the entire folder** onto the Netlify Drop page.
4. Wait about 30 seconds. Netlify will give you a link like `https://shiny-jellyfish-9a7e2c.netlify.app`.
5. Sign up (free, takes 30 seconds with Google or email). This is so the link doesn't expire and so you can update it later.
6. Once signed up, you can click "Site settings" → "Change site name" to rename the link to something nicer like `box-the-box.netlify.app`.

✅ **That link works for anyone, anywhere. Share it.**

When you're ready to use `boxthebox.in` instead, follow `LAUNCH-GUIDE.md`. You don't have to redo anything — Netlify lets you attach your own domain to the same site.

---

## Part 2 — How to change content on the website

### The big rule

**Open `index.html` in any text editor.** Don't open it in Word — Word adds invisible formatting that breaks websites. Use one of these instead:

- **Mac:** TextEdit (built-in), or download **VS Code** (free, better)
- **Windows:** Notepad (built-in), or download **VS Code** (free, better)
- **On the phone:** Apps like "QuickEdit Text Editor" (Android) or "Textastic" (iPhone)

### The easy stuff (95% of changes)

Right at the top of `index.html`, you'll see this block (scroll down a bit, it's hard to miss — it's surrounded by big boxy ╔═══╗ borders):

```javascript
const SITE = {
  phone:        "+91 00000 00000",
  phoneLink:    "+910000000000",
  email:        "hello@boxthebox.in",
  
  addressLine1: "Box The Box Fulfilment Centre",
  addressLine2: "Bhiwandi, Thane — 421302",
  addressLine3: "Maharashtra, India",
  
  hours: "Mon — Sat · 9:30 AM to 7:30 PM IST",
  ...
};
```

**Rule of thumb:** change ONLY the words inside the **double quotes**. Leave the colons (`:`), the commas (`,`), the curly braces (`{` `}`), and the quotes (`"`) exactly where they are.

#### Example — changing your phone number

Wrong:
```
phone: "+91 98765 43210"      ← good (you replaced the digits, kept the quotes)
phone: +91 98765 43210        ← BROKEN (you removed the quotes)
phone "+91 98765 43210",      ← BROKEN (you removed the colon)
```

#### After editing

1. Save the file (Ctrl/Cmd + S).
2. **If the site is already live on Netlify:** drag the folder onto Netlify Drop again — it'll update.
3. **To preview locally first:** double-click `index.html` to open it in your browser.

### What you can edit from the easy block

| What | Where in the block |
|---|---|
| Phone number (visible) | `phone:` |
| Phone number (for click-to-call) | `phoneLink:` (no spaces, no plus sign issues) |
| Email | `email:` |
| Full address (3 lines) | `addressLine1:`, `addressLine2:`, `addressLine3:` |
| Working hours | `hours:` |
| The four big numbers (40,000 sq.ft / 5,000 orders / 99.7% / <24 hrs) | `stat1:` through `stat4:` |
| The labels under those numbers | `stat1Label:` through `stat4Label:` |
| The testimonial quote | `quoteText:` |
| Who said it | `quoteAuthor:` and `quoteMeta:` |

### The slightly less easy stuff (changing other text)

If you want to change a section heading, a service description, or rewrite the hero copy — you'll be editing the actual page text. It's still simple:

1. Open `index.html` in your editor
2. Use **Ctrl+F (Cmd+F on Mac)** to *search* for the text you want to change
3. Change it
4. Save

For example, if the hero says "You build the brand. We'll ship the boxes." and you want to change it:

1. Search for `build the brand`
2. You'll see this:
   ```html
   <h1>You <em>build the brand.</em><br>We'll <em>ship the boxes.</em></h1>
   ```
3. Change the words but **keep all the `<...>` tags exactly as they are**:
   ```html
   <h1>You <em>do the marketing.</em><br>We'll <em>do the shipping.</em></h1>
   ```

Tags like `<em>...</em>` make text italic. `<br>` is a line break. Don't worry about understanding them — just don't delete them.

---

## Part 3 — Replacing images

The 13 images live in the `images/` folder, with names like `hero-1.jpg`, `pack-1.jpg`, etc.

To replace any image:
1. Take your new image
2. Crop / resize it to the same approximate size as the original (you can check by right-clicking the existing one)
3. Save it with **the exact same filename** (e.g., `hero-1.jpg`)
4. Drop it into the `images/` folder, replacing the old one
5. Re-deploy (drag folder onto Netlify Drop)

If you want to keep both versions and swap which one shows, give the new file a different name (e.g., `hero-1-new.jpg`) and update the reference in `index.html` — search for `hero-1.jpg` to find the spot.

---

## Part 4 — Things you should NOT touch

- Anything inside `<style>...</style>` (that's the CSS — controls colors, fonts, layout)
- Anything starting with `data:image/jpeg;base64,...` (those are encoded images, in the `index.html` of the standalone version)
- The `<script>` tags at the bottom

If you accidentally break something:
1. Don't panic
2. Open the **original** zip you downloaded (you kept it, right?)
3. Copy `index.html` from there back over your broken one
4. You're back to square one

**Pro tip:** before making any change, **make a copy of the folder** and call it something like `box-the-box-backup`. Edit the original. If you mess up, you have a known-good backup.

---

## Part 5 — Making the contact form actually deliver to your inbox

Right now, when someone fills out the form on the website and hits "Send", it opens *their* email app with a pre-filled message to your `hello@boxthebox.in`. This works, but only if they have an email app set up.

To make form submissions land directly in your inbox automatically:

1. Sign up at **https://web3forms.com** (it's free, takes 60 seconds).
2. Enter the email where you want submissions delivered. They'll send you an "access key" — a long string of letters and numbers.
3. In `index.html`, search for `<form class="form" id="contact-form" onsubmit="handleSubmit(event)">`.
4. Replace that line with:
   ```html
   <form class="form" id="contact-form" action="https://api.web3forms.com/submit" method="POST">
     <input type="hidden" name="access_key" value="YOUR-ACCESS-KEY-HERE">
     <input type="hidden" name="subject" value="New enquiry from boxthebox.in">
   ```
5. Replace `YOUR-ACCESS-KEY-HERE` with the key Web3Forms gave you.
6. Below that, find the existing button line and change `type="submit"` if needed (it should already say submit).
7. Save and re-deploy.

That's it. Form submissions now land in your inbox.

---

## Part 6 — Common questions

**Q: I changed the phone number but the website still shows the old one.**
A: Two possibilities. Either you didn't save the file (Ctrl+S), or the website you're looking at is the *deployed* version and you haven't re-deployed yet. Drag the folder onto Netlify Drop again.

**Q: I see weird symbols like `&amp;` in the code. What is that?**
A: That's HTML's way of writing the `&` symbol. Leave it as `&amp;` — it'll display as `&` on the actual webpage.

**Q: Can I add a new section?**
A: Yes, but you'll need someone with basic HTML skills. The structure is well-commented so it's not hard. Look for the big comment headers like `<!-- ====================== SERVICES ====================== -->` and copy the pattern.

**Q: How do I see what the website looks like before deploying?**
A: Just double-click `index.html` on your computer. It opens in your browser.

**Q: My boss wants to know — is this secure? Can people hack it?**
A: It's a static website (no server-side code, no database, no login). There's nothing to "hack" in the usual sense. The only thing that can go wrong is if someone gets your domain registrar password — keep that strong.

**Q: I'm scared I'll break it.**
A: You won't. Make a backup folder first. Then change one thing at a time, save, refresh the browser, see what happened. Worst case you copy back from the backup. That's how everyone learns.

---

That's the whole thing. The site is yours. You're not stuck waiting on a developer for every small change.
