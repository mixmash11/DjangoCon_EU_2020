# Search options in Django

# Fulltext-Search
Search some text

- Why?
    - Fuzzy matching
    - Relevance sorting
    - Give me what I *mean* (vs what i say)
- Relevance
    - What makes something relevant
        - Terms present?
        - Position in doc
        - Specific Factors: New, Frequently seen
        - User specific: recommendations
        
## Aspects of Good Search
product/user:
    - Fast, current, correct, relevant, UX fits
dev:
    - scalability, performance, cost, size
    
## PostgreSQL Fulltext Search
Scenario: Looking at movie reviews
- Ranked Search via SearchVector
    - Attach to query
    - filter by rank

## Indexing Text
You can add a full text search index to PostgreSQL
- need a migration/trigger to add text during inserts/updates

## ElasticSearch
Search application 

### Time to get off the ground 
2 days to get running, 2 weeks to get ready
- GitHub repo with PostGreSQL, takes 1-2 hours
- Docs from research paper to search
