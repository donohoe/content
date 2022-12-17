# WordPress SQL

Every few years I need to re-create one of these from scratch...

### Get list of WP posts with coauthors, including date

If you use Coauthors Plus plugin and need a list of posts. This provides basics, including the slug of the Coauthor slug.

```sql
SELECT name, post_title, post_name 
FROM wp_term_taxonomy AS c_term_taxonomy
INNER JOIN wp_terms AS c_terms ON c_term_taxonomy.term_id = c_terms.term_id
INNER JOIN wp_term_relationships AS c_term_relationships ON c_term_taxonomy.term_taxonomy_id = c_term_relationships.term_taxonomy_id
INNER JOIN wp_posts AS c_posts ON c_term_relationships.object_id = c_posts.ID
INNER JOIN wp_postmeta AS meta ON c_posts.ID = meta.post_id
WHERE c_posts.post_status = 'publish'
AND c_posts.post_date >= "2021-01-01"
AND c_posts.post_type = 'post' 
AND c_term_taxonomy.taxonomy = 'author'
GROUP BY name, post_title
ORDER BY name, post_title;
```
