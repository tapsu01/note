1. Remove widget title

```php
// REMOVE WIDGET TITLE IF IT BEGINS WITH EXCLAMATION POINT
add_filter( 'widget_title', 'remove_widget_title' );
function remove_widget_title( $widget_title ) {
    if ( substr ( $widget_title, 0, 1 ) == '!' )
        return;
    else
        return ( $widget_title );
}
```

2. Remove style inline

```php
add_filter('wp_generate_tag_cloud', 'remove_tagcloud_inline_style',10,1);
function remove_tagcloud_inline_style($input){
  return preg_replace('/ style=("|\')(.*?)("|\')/','',$input);  
}
```

3. Limit tag

```php
function prefix_widget_tag_cloud_args( $args ) {
    $args['number'] = 5;
    return $args;
}
add_filter( 'widget_tag_cloud_args',    'prefix_widget_tag_cloud_args',      10, 1 );
```
