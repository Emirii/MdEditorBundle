This is a very simple implementation of [editor.md](https://github.com/pandao/editor.md) with no options currently. I might expand on it later.

Installation
============

### Step 1: Require the Bundle

Currently not on Packagist but I might change once I'm happy with the bundle.

```console
"repositories": [
    {
        "type": "vcs",
        "url": "http://github.com/Emirii/MdEditorBundle"
    }
],
```

```console
$ composer require emirii/md-editor-bundle
```

### Step 2: Enable the Bundle

Then, enable the bundle by adding it to the list of registered bundles
in the `config/bundles.php` file of your project:

```php
// config/bundles.php

return [
    // ...
    Emirii\MdEditorBundle\EmiriiMdEditorBundle::class => ['all' => true],
];
```

Install the assets:
```
php bin/console assets:install web
```

Depending on how your app is set up, you might have to add this to your config as well:
```
twig:
    form_themes:
        - '@EmiriiMdEditor/Form/fields.html.twig'
```

### Step 3: Use the Bundle

Controller or service with your form:
```
use Emirii\MdEditorBundle\Form\Type\MarkdownType;

$formMapper->add('content', MarkdownType::class);
```

Then in your templates you can use Twig's markdown parser or whatever other parser you'd like. I also like [Twig Markdown Extra](https://github.com/twigphp/markdown-extra).
```
{{ content|markdown_to_html }}
```

That's it!
