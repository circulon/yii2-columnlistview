yii2-columnlistview
===================

Yii 2.x ListView for building a responsive column layout

This is ideal for portfolio style layout of model/s content 
  
## Features
- default settings for several common responsive layouts
- easily configurable for custom layouts
- generates fully responsive columns; 
  
## Installation

The preferred way to install this extension is through [composer](http://getcomposer.org/download/).

Either run

```
$ php composer.phar require circulon/yii2-columnlistview "*"
```

or add

```
"circulon/yii2-columnlistview": "*"
```

to the ```require``` section of your `composer.json` file.

## Basic usage
```php
    use circulon\widgets\ColumnListView;
    
    echo ColumnListView::widget([
        'dataProvider' => $dataProvider,
        
        'columns' => 3, // default : 1
])
```

The above example will generate a listview with the following layout per device size
- lg (Desktop) 4 columns
- md (Tablet) 3 columns
- sm (Phone) 2 columns
- xs 1 column

## Advanced usage

### Custom layout

Creating your own column layout is easy to do.

The setup of the columnsLayout var is as follows

```php
  'columns' => <column number>
  'columnsLayout' => [
    <column number> => [
      <column to break at> => <size to use>,
      <column to break at> => [<size to use>, <size to use>] 
      ...
    ],
    ...
  ],
```
> NOTE: Unless otherwise specified SIZE_TINY ('xs') defaults to 1 column
 
Generally I find it easier to layout columns for Tablet ('md' / SIZE_MEDIUM) then 
scale up for large and down for small and tiny devices.

Check the source for additional size layouts.

### Custom CSS classes for columns

For example, if you to render something like this using 3 clumns:

```html
  <div class="row">
    ...
    <div class="col-lg-4 col-xs-12" data-key="...">
      ...
    </div>
    ...
  </div>
```

You must set uo your widget as follows:

```php
  echo ColumnListView::widget([
    'dataProvider' => $dataProvider,
    'columns' => 3,
    'itemOptions' => [
      'class' => 'col-lg-4 col-xs-12',
    ],
  'itemView' => 'item',
  ]);
```
