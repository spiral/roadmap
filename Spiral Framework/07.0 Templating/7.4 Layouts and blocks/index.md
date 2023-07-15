# Layouts and blocks

Layouts and blocks provide a way to define a common structure for your views. A layout is a template that defines the overall structure of the page, while blocks are sections of the layout that can be overridden by individual views.

```php
<!-- layout.php -->
<html>
<body>
    <div class="content">
        <?= $this->block('content') ?>
    </div>
</body>
</html>
```

### Links and materials to read more:
1. [Spiral Views](https://spiral.dev/docs/views-configuration/current/en)
