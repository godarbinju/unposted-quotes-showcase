# UnpostedQuotes

A full-stack quote platform built for my YouTube channel, UnpostedQuotes. Visitors browse quote images by emotion, sign in with Google, and like their favorites. An admin panel lets the channel owner manage the collection.

## Live demo

**https://unpostedquotes-1.onrender.com**

The site runs on a free hosting tier, so the first load after a quiet period can take up to a minute.


<img width="925" height="853" alt="Home page" src="https://github.com/user-attachments/assets/d4f8f682-61e3-421a-8792-08f0e9866fff" />


## Features

- Quote gallery with emotion filters, tag search, and "Show more"
- Google sign-in (OAuth 2.0), with a signed httpOnly cookie session
- Like and unlike quotes, with one like per user per quote enforced by the database
- Profile page listing the quotes you liked
- Role-based admin panel to add, edit, and delete quotes
- Responsive layout with a mobile menu and an animated hero
- Security basics: helmet, rate limiting, and server-side input validation

## Tech stack

| Layer | Technology |
|---|---|
| Frontend | HTML, CSS, JavaScript (no framework) |
| Backend | Node.js, Express |
| Database | MongoDB Atlas with Mongoose |
| Auth | Google Identity Services, JWT in an httpOnly cookie |
| Hosting | Render |

## How it works

- The browser talks to a REST API under `/api` (quotes, auth, likes, admin).
- **Login:** Google issues an ID token, the server verifies it, then sets its own signed cookie.
- **Admin access** is decided on the server from a verified Google email, never from data sent by the browser.
- **Likes** live in their own collection with a unique index on (user, quote), so duplicates are impossible. The like count is recalculated from that collection.
- **Abuse protection:** rate limits on the API, stricter limits on login and likes.

## Screenshots

### Quotes
<img width="905" height="892" alt="quotes image" src="https://github.com/user-attachments/assets/59d96f09-cbb0-45da-8eca-afa4ef9fc67a" />




###Profile



<img width="927" height="913" alt="image" src="https://github.com/user-attachments/assets/4cd16bd2-88f1-46a8-9a28-d7ca20108649" />



## Planned improvements

- User-submitted quotes with moderation
- Automatic emotion tagging of quote images using an ML model
- Latest videos from the YouTube channel
- Custom domain

## Built by

Binju Thapa and Priyam Tyagi

*The source code is in a private repository. It can be shared on request.*
