# Accessibility Wins for Django Projects

**Accessilbity Matters for Inclusion**

Accessibility improvments lead to usability improvements

EU 2016 Accessilbility Directive, 2019 European Accessilbility Act

2025 Act for EU ecommerce, banking, transport services

## Common Issues
- Alt text for images
    - Have a mandatory alt_text field for images that aren't decorative
    - Use in template
    - Guide: [Alt Texts](axesslab.com/alt-texts)
    - Easier to fix early
- Videos
    - Provide captions for video content
    - Make sure embed iframes have a title attribute
- Heading levels
- Forms
    - Avoid forms as tables or lists


## Developer Wins
Focus on doing things during requirements/architecture
- Training:
    - a11yproject.com
    -accessibility-developer-guide.com
- Tools
    - Axe - Accessibility rules engine
    - Accessibility Insights - Browser extension with Axe
    - Pally
- Django
    - django-html-validator
        - finds about 15% of issues
    - django-pattern-library
        - manages ui component libraries
        - test components in isolation
        - unit testing for ui