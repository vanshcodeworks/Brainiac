# Brainiac

Quiz platform: create quizzes, take them, and score the results. Express +
MongoDB with Passport authentication, including Google OAuth.

## Stack

- `express`, `mongoose`
- `passport`, `passport-local`, `passport-local-mongoose`, `passport-google-oauth20`
- `ejs` templates, `express-session`, `connect-flash`, `cookie-parser`
- `express-validator`, `bcrypt`, `crypto`

## Layout

```
QuizFrontend/     EJS views: quiz, create quiz, quiz results
config/           passport and database configuration
models/           Mongoose schemas
routes/           route handlers
```

## Setup

```bash
npm install
cp .env.example .env
npm start
```

## Environment

| Variable | Purpose |
| --- | --- |
| `PORT` | server port |
| `MONGO_URI` | MongoDB connection string |
| `SESSION_SECRET` | session cookie signing secret |
| `GOOGLE_CLIENT_ID` | Google OAuth client ID |
| `GOOGLE_CLIENT_SECRET` | Google OAuth client secret |

For Google sign-in, add `http://localhost:3000/auth/google/callback` as an
authorised redirect URI in the Google Cloud console.

---

## Security notice

`.env` was previously committed and contained a **Google OAuth client secret**
and a **MongoDB connection string with a username and password**. The file has
been removed, but **git history still contains them**.

If you have cloned this repository, rotate both credentials before using them
anywhere:

- Google OAuth client → [Google Cloud Console → APIs & Services → Credentials]
- MongoDB → [Atlas → Database Access → reset the user]

Deleting the file does not remove it from history. To purge it entirely:

```bash
git filter-repo --invert-paths --path .env
```