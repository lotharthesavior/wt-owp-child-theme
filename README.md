WT OceanWP Child Theme
=================

@author Savio Resende

WT Child Theme for the OceanWP WordPress theme. This theme adds useful functionalities for custom taxonomies to be displayed.

These functionalities are abstract, and have the possibility to access different repositories, not being necessarrily the Wordpress main database. For this, the Repositories are build for an common Interface.

Obs.: "vendors" and "node_modules" are included so this can be added as an usual theme for Wordpress.

### Dependencies

- Woocommerce Plugin
- OceanWP Theme

### Recommended

- Ocean Demo Import Plugin
- Ocean Extra Plugin

### Usage

By creating your own taxonomies, simply select the ones you want to see in after the title of your blog post or page.

One good implementation of this template would be built following this direction:

- apply the OceanWP Sub Theme,
- install the recommended plugins,
- install the OceanWP demo called "Blogger",
- go to "Customize" the theme,
- at the "Static Front Page", apply a home page with the Template "Landing Page",
- activate Woocommerce,

#### Core features

##### Adding a new item to Woocommerce My Account Menu

To add a new item to Woocommerce My Account Menu, you just have to add a page to any menu, than, mark that menu to be displayed at the "Words Tree My Account Menu" location, which is a custom place created but this theme.

![Adding item to menu](/image_add_page.png)

**IMPORTANT After add another page to the menu, it is necessary to visit the page Settings/Permalinks at the WP Admin Area.**

##### Adding new menu location to the theme

This is useful for developers who want to add more possible menus to pages.

At the file WTThemePlugin.php, customize this part of the code adding more items to the array, following the first element example:

```php
public static $menu_items_to_be_registered = [
    [
        'location' => 'wt_myaccount_menu',
        'description' => [
            'Words Tree My Account Menu',
            'wt-myaccount-menu'
        ]
    ]
];
```

These items will be available in the Theme's menu on the WP-Admin. Any menu can the attached to this location (e.g. the default menu, which is used by the theme to increment the Woocommerce My Account menu items, is "Words Tree My Account Menu").


#### Globals

**$wt_theme_dir** theme directory for files inclusion.

**$terms** terms loaded

**$posts** posts loaded

**$breadcrumb** breadcrumb loaded

**$chapter** chapter loaded

**$book** book loaded


#### Shortcodes (Interface and Workflow)

##### Class Interface:

- **run** small router for this shortcode
- **doAction** execute the action decided by the run method
- **returnTemplate** return template

##### Expected API:

###### Stateless Action

**Request** GET {slug}?action={action}&{paramX}={valueX}

###### Stateful Action

**Request** POST {slug}?action={action}

**Body** JSON {field1:value1,field2:value2}


##### Workflow

1. Shortcode::run
2. Shortcode::doAction
3. Shortcode::returnTemplate

TODO: doc private methods and organize them


#### Shortcode Writer

Shortcode: [wt-writer]

This shortcode allows the non-administrator user to create posts on the front end in the Woocommerce MyAdmin page.

The tree is:

1. Book (Parent Taxonomy)

2. Chapter (Sub Taxonomy)

TODO: evolve this to be recursive in the further levels. 