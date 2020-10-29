# WordPress Notes
#### October 29th 2020

Collection of code fragments and useful notes for WordPress

## Ruduimntary word-count from databse

```sql
SELECT `ID`, `post_date`, `post_name`, `post_type`, `post_status`, `post_title`, `guid`, SUM( LENGTH(`post_content`) - LENGTH(REPLACE(`post_content`, ' ', '')) + 1 ) AS 'Wordcount' 
FROM `wp_posts` GROUP BY `ID` HAVING `post_type` = 'post' AND `post_status` = 'publish' 
ORDER BY `Wordcount` DESC LIMIT 0, 10000
```

