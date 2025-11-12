## Upvote

Upvote is a Reddit-esque web application that allows users to create posts, upvote and downvote posts, and comment on posts in a multi-threaded, nested list.

The project is built using Next.js with the /app router and [Tailwind CSS](https://tailwindcss.com/), and uses [Auth.js (formerly Next Auth)](https://authjs.dev/) for user authentication. The data is stored in a Postgres database, which is created and accessed with raw SQL queries using the `pg` package.

The project is a work in progress and is not yet complete.

## Features

- [x] View a list of posts
- [x] View a single post
- [x] Create a post
- [x] Upvote and downvote posts
- [x] Pagination of posts
- [x] Comment on posts
- [x] Nested comments (recursive lists)
- [x] User authentication

## Setup instructions (see below for corrections)

1. Fork the repository (check "copy the main branch only") and clone your fork to your local machine
2. Run `npm install`
3. Create a `.env.local` file in the root directory and add the following environment variables:
   - `DATABASE_URL` - the URL of your Postgres database (eg. the Supabase connection string)
   - `AUTH_SECRET` - the Next Auth secret string (this can be anything at all like a password, but keep it secret!)
   - `AUTH_GITHUB_ID` - the GitHub OAuth client ID (create yours in [Github developer settings](https://github.com/settings/developers)
   - `AUTH_GITHUB_SECRET` - the GitHub OAuth client secret (create this in [Github developer settings](https://github.com/settings/developers))
4. Create the database schema by running the SQL commands in `schema.sql` in your database (eg. by running the commands in Supabase Query Editor)
5. Run `npm run dev` to start the development server
6. Open [http://localhost:3000](http://localhost:3000) with your browser to see the site

## Potential future features

- [ ] User profiles
- [ ] Sorting posts by recent (date posted), top (most upvotes), and most controversial (most upvotes _and_ downvotes)
- [ ] User karma scores
- [ ] User badges / trophies (awards for achievements like number of posts, years on the site, etc.)
- [ ] User settings (eg. number of posts per page, theme, etc.)
- [ ] Moderation tools / reporting or flagging objectionable comments for removable by admins
- [ ] Searching posts (possibly using simple SQL LIKE '%some search%', or [Postgres text search](https://www.crunchydata.com/blog/postgres-full-text-search-a-search-engine-in-a-database))
- [ ] Subreddits (separate communities, that isn't just one big list of posts, that can be created by users)
- [ ] User notifications
- [ ] User private messaging
- [ ] User blocking
- [ ] User following
- [ ] User feed (posts from users you follow)
- [ ] User flair

Updates and corrections by Dale:
Ran through sett-up instructions and fixed things as went along:

## Setup instructions (corrected for current build)

1. Fork the repository (check "copy the main branch only") and clone your fork to your local machine :- [x]
2. Run `npm install` :- [x] - 11 vulnerabilities (4 low, 4 moderate, 2 high, 1 critical) - ran npm audit fix --force [x] (since 'npm audit fix' did not complete the fix.)
3. Create a `.env.local` file in the root directory and add the following environment variables: [x]
   - `DATABASE_URL` - the URL of your Postgres database (eg. the Supabase connection string) [x]
   - `AUTH_SECRET` - the Next Auth secret string (this can be anything at all like a password, but keep it secret!)
   - `AUTH_GITHUB_ID` - the GitHub OAuth client ID (create yours in [Github developer settings](https://github.com/settings/developers) [x] - followed youtube video https://www.youtube.com/watch?v=H-1ozULYdyc to crated github app and create GITHUB Auth ID and GITHUBSecret
   - `AUTH_GITHUB_SECRET` - the GitHub OAuth client secret (create this in [Github developer settings](https://github.com/settings/developers))[x]
4. Create the database schema by running the SQL commands in `schema.sql` in your database (eg. by running the commands in Supabase Query Editor) [x]
5. Run `npm run dev` to start the development server [x] see below
6. Open [http://localhost:3000](http://localhost:3000) with your browser to see the site

Also at 3.: created new Supabase project (after deleting one coz have too many for free use.): "didit app"
using SQL editor to create it using schema.sql

3 and 4: Database created with Schema provide except had to adjust the last table creation: to uncomment line 79:
-- UNIQUE(user_id, post_id, vote_type) - Schema.sql updated to be correct.

5. compilation error: Next.js (14.2.33) is outdated in browser so npm i next@latest and confirmed up to date (v).

now had the following in vcode terminal:
⨯ Unable to acquire lock at /home/dales/w11assignment/didit-reddit-upvote-example/.next/dev/lock, is another instance of next dev running?
Suggestion: If you intended to restart next dev, terminate the other process, and then try again.
unable to fix, so VScode, seemed to be OK but other things not OK: restarting computer

Needed some help to resolve this: the option had move in SupaBase to get the right postgress URL for the .env.locl file

resolved login issues with slight errors in GitHub URLs on pages to use GITHUB login
^. can now get access to site using local deployment and log in OK.

Deploying via Vetel now, aftet latest Git commit
