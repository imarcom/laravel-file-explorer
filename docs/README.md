# Laravel File Explorer

Laravel File Explorer is a file manager for your Laravel project using Vue and Tailwind. You can explore your storage folder a on your server or mount from another source (Local, FTP, SFTP, S3, Rackspace). You can easily upload many files, keep them organize in folders, select one or many files for your forms.

## Installation

Install the laravel package

```
composer install imarcom/laravel-file-explorer
```

Publish the configuration file

```
php artisan vendor:publish --provider="Image\LaravelFileExplorer\LaravelFileExplorerServiceProvider" --tag="config"
```

Add the routes to your `routes/web.php` or `routes/api.php`.

```php
FileExplorer::routes();
```

Add File Explorer config in your `<head>` of your layout

```
@fileExplorerConfig()
```

Use it in your component

```js
<template>
    <laravel-file-explorer></laravel-file-explorer>
</template>

<script>
import FileExplorer from "vendor/laravel-file-explorer/components/FileExplorer"

export default {
    components: {
        FileExplorer
    }
}
</script>
```

## Configuration

Available options in `config/file-explorer.php`

```php
<?php

return [

    // which disks from config/filesystems.php
    'disks' => [
        'public' => [
            // disk label
            'label' => trans('file-explorer.public_disk_label'),

            // exclude folders from showing up
            'exclude' => ['generated']
        ],
        's3' => [
            'label' => trans('file-explorer.s3_disk_label'),
        ]
    ],

]
```

```php
<?php

return [

    // which disks from config/filesystems.php
    'disks' => [
        'public' => [
            // disk label
            'label' => 'Server',
        ],
    ],

]
```

|Prop|Type|
|----|----|
|**disks**|`array`|
|**selectable**|`boolean`|
|**multiple**|`boolean`|
|**selectable-type**|`array`|

```html
<laravel-file-explorer :disks="['public', 's3']" selectable multiple :selectable-type="['image/jpg', 'image/png']" />
```

## Routes

|Method|URI|Name|Action|
|------|---|----|------|
|GET\|HEAD|file-explorer|file-explorer.index|Imarcom\LaravelFileExplorer\Http\Controllers\FileExplorerController@index|

## Features

1. Upload one or many files
1. Make directory
1. Move one or many files
1. Delete one or many files
1. Select one or many files (click [toggle])
1. Select multiple files (shift+click) [clic le 1er, shift+clic le 3e pour sélectionner aussi le 2e]
1. Change view layout [list vs grid]
1. Search
1. Show multiple disks
1. Navigate into a folder (on double-click)
1. Download file (on double-click, nav button or file options, as zip for multiple files)
1. Download folder (nav button or file options, always as zip)
1. Cancel
1. Public link (based on filesystem config)
1. Upload multiple file with drag and drop

## TODOs

1. Tests (tests)
1. ServiceProvider (src/FileExplorerServiceProvider.php)
1. Translations (resources/lang/en/file-explorer.php)
1. Config (config/file-explorer.php)
1. Blade Directive (@see https://github.com/tightenco/ziggy)
1. Facade (src/FileExplorerFacade.php)
1. Components (resources/js/...)
1. Register package to packagist

## Ideas

- WebSocket
  - At file changed/added/deleted from Laravel
  - At file changed/added/deleted from the filesystem (example with incrontab)
- Favorite
- Image manipulation (crop, brightness, gamma, rotation)
- Player (audio, video, image) and carousel

## Docs

The documentation is generated with https://vuepress.vuejs.org

## License

The MIT License (MIT). Please see License File for more information.
