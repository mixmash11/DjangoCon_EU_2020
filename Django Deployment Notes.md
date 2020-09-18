# New Ways to Deploy

[Follow Along](https://gist.github.com/tomdyson/025be30855262287ae048bf4371d26f8)

## The Non-Well Known Options

- Dokku
- Static site generation
- Google Cloud Run

## Dokku

### Deployment

1. Use a Vultr or DigitalOcean server
1. Install Dokku
1. Go to IP Address of the server
1. Install Dokku Postgres Plugin
1. Create a DB
1. Link the DB to the app
1. Set up persistent storage for media
1. Add Postgres to the app
1. Link to git repo
1. Push to the dokku repo


### Notes

- You need persistent storage for media
    - Apps are ephemeral (rebuilt every time you deploy)
    
### Pros
- Easiest way to get something to production
- 12 Factor compatible
- Cheap (5e/month)

### Cons
- No horizontal scaling
    
## Static Site Generation

- You will need the bakery(makes pages "flat"[static]) available for django and wagtail
- Using Netlify
    - Just hosting the static pages

## Static Site Generation

### Deployment Using Netlify

1. Add netlify
1. Netlify deploy command

### Pros
- Cheapest
- Fastest
- Most Secure

### Cons

- Build Times
- More moving parts
- Doesn't suit things like logins

## Google Cloud Run

### Deploy
    
1. Install Google Cloud SDK
1. Create Project
1. Enable minimum APIs
1. Set ID and region for project
1. Turn on build caching
1. Store image for app
1. Deploy the image

### Google Cloud Run Notes

- This script doesn't include a persistent database, file storage, or way of running management commands
- Will scale up and down as you need it

### Pros

- Scales forever
- Scales to zero
- Its the *future*

### Cons

- Cold starts
- Still too complicated
- Database isn't serverless


# Best Fits

- Deploy ASAP: Dokku
- Information Site: SSG
- Need to scale: Cloud Run