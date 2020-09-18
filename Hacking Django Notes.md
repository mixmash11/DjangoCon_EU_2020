# How to Hack a Django Website

Revolves around 4 Stories

## Facebook - Pickle Remote Code Execution

### Process
- Scanned Facebook IP Range
- Find Sentry
- Browse Security
    - Debug was set to True
- Read Debugged Settings
    - 3 Settings combined to allow a remote execution attack
    - Sentry showed the secret key
- Replace contents of signed cookie
- Pickle is CODE!!!
    - Attack forced a sleep 30
    
### Takeaways
- Deliberately 404 to check for DEBUG=True
- Look for things using pickle
- Build evil pickle payloads

### Lessons
- Never deploy with DEBUG = True
- Run manage.py check --deploy
- Avoid pickle - no "safe mode"
- Deprecate PickSerializer(#29708)

## GitHub - Unicode Case Collision Account Takeover

### Process
- Find case collisions
    - github (with a dot missing over the i) is the same uppercase as the normal github
    - github compares strings by forcing uppercase
- Register domain
    - registered domain with no dot over the i
    - supported by punycode
- Reset password for github
    - could reset the password for john@github.com using the non-dot i version
- Unleash chaos

*This bug was also found in Django!*

### Takeaways
- Look for case collisions
- Know other unicode features
- Detect target site's django version

### Lessons
- Upgrade Django

## YPlan - HTML Injection (Cross Site Script)

### Process
- Set name to include script tag
- Someone browses the Admin

Called mark_safe on unsafe data
- added HTML to some data before display in admin

### Fix
- Use format_html

### Takeaways
- Try adding HTML to every field you can
- Beacon resources - script/image/etc.

### Lessons
- Don't copy code with mark_safe
- Rename "mark_safe" (isn't really safe)
- Block untrusted resources with Content-Security-Policy

## Many Sites - Javascript HTML Injection
- Recurring audit issue

### Process
- Include HTML in field you control
- View forms "JSON" data
- Template Inlines JSON
    - Another instance of mark_safe style object
- Chaos

*HTML Parses First!!!*

### Fix
- Use json_script

### Takeaways
- Look for inline script tags with data
- Htry adding HTML starting </script> in every field you can

### Lessons
- Use json_script
- Block untrusted resources with Content-Security-Policy

## Security.txt

Check out the draft