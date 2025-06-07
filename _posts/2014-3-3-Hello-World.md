---
layout: post
title: You're up and running!
---

Next you can update your site name, avatar and other options using the _config.yml file in the root of your repository (shown below).

![_config.yml]({{ site.baseurl }}/images/config.png)

<pre> \```php
function getSingleRowWhereMulti($con, $table, $conditions = []) {
    $table = mysqli_real_escape_string($con, $table);
    
    $whereClauses = [];
    foreach ($conditions as $column => $value) {
        $columnEscaped = mysqli_real_escape_string($con, $column);
        $valueEscaped = mysqli_real_escape_string($con, $value);
        $whereClauses[] = "`$columnEscaped` = '$valueEscaped'";
    }

    $whereSql = '';
    if (!empty($whereClauses)) {
        $whereSql = 'WHERE ' . implode(' AND ', $whereClauses);
    }

    $query = "SELECT * FROM `$table` $whereSql LIMIT 1";
    $result = mysqli_query($con, $query);

    if (!$result) {
        die("Error fetching single row from $table: " . mysqli_error($con));
    }

    return mysqli_fetch_assoc($result); // Will return null if no match
}

 \``` </pre>
The easiest way to make your first post is to edit this one. Go into /_posts/ and update the Hello World markdown file. For more instructions head over to the [Jekyll Now repository](https://github.com/barryclark/jekyll-now) on GitHub.