# C is for Cookie

## What is a cookie

- The web is a stateless protocol
    - Each request can be handled independently *(great for load balancing)*
- Requests had no links between documents
- Complex interactions require presence of state

## Cookies

- Part of the HTTP standards
    - RFC6265 - RFC6265bis05

## What does a cookie look like?

During a response:

*in header*
Set-Cookie: SID=6789; favorite_color=red

Max length should be under 4096 characters

## Sesssion Cookies

Should only last until the browser closes, but they can be modified

## Permanent cookies

Set-Cookie: SID=6789; Expires=Sun, ...
OR 
EXP timer in seconds

## Cookie scope

Can only apply to one domain/path

Set-Cookie: SID=6789; Domain=paint.hardwarestore.com

Can be applicable only to path

Set-Cookie: SID=6789; Path=/purchase

## Secure Cookies

Provide protection against attack

Set-Cookie: SID=6789; Secure

will only be sent over HTTPS:

## HTTPOnly Cookies

Cookies that can't be seen from JavaScript

## SameSite Cookies
Not official but already in use

If you have code coming from CDN, server, analytics, etc

First-party (hardwarestore.com) vs. Third Party Cookie (CDN Cookie)

**Public suffix list** - lists public suffixes (for ownership, setting cookies)

Set-Cookie: SID=6789; Secure; SameSite=None
- none

Set-Cookie: SID=6789; Secure; SameSite=Lax
- allows safe requests (get or head)

Set-Cookie: SID=6789; Secure; SameSite=Strict
- strictly first party

**MUST** set secure to use

## Changing browser defaults

- Chrome
    - SameSite cookies not served unless explictly requested

Low-level setting cookies

- You can sign cookies

## Django's use of cookies

- Session ID
- CSRF
- Language settings
- Session data (if using CookieStorage or FallbackStorage)

## Future of cookies

- Tracking a user (eg. adserver sets cookie and uses ID and referer)
    - EU Directive
- Do-Not-Track header
    - Wasn't widely implemented or honored
- Third-party cookies aren't being supported much anymore
- Ad tech response:
    - Target grouping
    - Contextual advertising
    - IP Address tracking

## QnA

- EU Cookie Law
    - Regs inside EU are different

