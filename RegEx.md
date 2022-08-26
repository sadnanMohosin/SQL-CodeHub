```sql
--Keep only records which start with hello or Hello or a capital J

WITH test_data (text_value) AS (
VALUES
  ('Hello World!'),
  ('hello World!!'),
  ('Hello world!!!!!'),
  ('HELLO world'),
  ('Peanut Butter Jelly Sandwich'),
  ('Just for fun!'),
  ('just kidding!')
)
SELECT text_value
from test_data
WHERE text_value ~ '^(Hello|hello|J)';


--output
text_value
--------
Hello World!
hello World!!
Hello world!!!!!
Just for fun!
```