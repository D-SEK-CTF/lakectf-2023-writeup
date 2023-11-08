# digestif

PHP Digest auth på PHPs hemsida: [https://www.php.net/manual/en/features.http-auth.php](https://www.php.net/manual/en/features.http-auth.php)

Kanske jämföra koden på PHPs hemsida med koden man fick, finns det något dom har tagit bort / lagt till som kan introducera en brist?

Verkar som att Regexen som kontrollerar om HTTP Digest-attributen finns med i headern är annorlunda:

```php
# Standardiserad implementation
preg_match_all('@(' . $keys . ')=(?:([\'"])([^\2]+?)\2|([^\s,]+))@', $txt, $matches, PREG_SET_ORDER);
# Hemsidan
preg_match_all('@(\w+)=(?:([\'"])([^\2]+?)\2|([^\s,]+))@', $txt, $matches, PREG_SET_ORDER);
```

Genom att ange en key av dem som finns listade i `needed_parts` kraschar `preg_match_all`, och vi får flaggan.