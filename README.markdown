PackingMinifyBundle: Enhanced Stylesheets and Javascripts for Symfony2
======================================================================

PackingMinifyBundle merge your stylesheets files and javascripts files.
The files merged can be minify.

## Installation

### Add PackingMinifyBundle to your src/Bundle dir

    git submodule add git://github.com/francisbesset/PackingMinifyBundle.git src/BeSimple/PackingMinifyBundle

### Add PackingMinifyBundle to your application kernel

    // app/AppKernel.php
    public function registerBundles()
    {
        return array(
            // ...
            new BeSimple\PackingMinifyBundle\BeSimplePackingMinifyBundle(),
            // ...
        );
    }

### Register the BeSimple namespace

    // app/autoload.php
    $loader->registerNamespaces(array(
        'BeSimple' => __DIR__.'/../src',
        // your other namespaces
    ));

### Update your config

#### Add routing

    // app/config/routing.yml
    _packing_minify:
        resource: @BeSimplePackingMinify/Resources/config/routing/packing_minify.xml
        prefix:   /_pm

#### Update config

##### Add
    // app/config/config.yml
    be_simple_packing_minify.config:
        css: { minify: true }
        js:  { minify: true }

#### Advanced config

    // app/config/config.yml
    be_simple_packing_minify.config:
        css:
            minify:   true
            minifier: cssmin
            options:
                remove-empty-blocks:     true
                remove-empty-rulesets:   true
                remove-last-semicolons:  true
                convert-css3-properties: false
                convert-color-values:    false
                compress-color-values:   false
                compress-unit-values:    false
                emulate-css3-variables:  true
        js:
            minify:   true
            minifier: packer
            options:
                encoding:      "Normal"
                fast_decode:   true
                special_chars: false

### Minifiers

#### Stylesheets

* **Basic**: No option available (minifier by default)  
* **CSSMin**:  
 remove-empty-blocks:     Boolean  
 remove-empty-rulesets:   Boolean  
 remove-last-semicolons:  Boolean  
 convert-css3-properties: Boolean  
 convert-color-values:    Boolean  
 compress-color-values:   Boolean  
 compress-unit-values:    Boolean  
 emulate-css3-variables:  Boolean  

#### Javascripts

* **JSMin**: No option available (minifier by default)  
* **Packer**:  
 encoding:      None, Numeric, Normal, High ASCII  
 fast_decode:   Boolean  
 special_chars: Boolean

## Using

### Twig

    {{ javascript(['js/jquery/jquery.js', 'js/main.js']) }}
    {{ stylesheet(['css/main.css', 'css/form.css']) }}
    
    {{ javascripts }}
    {{ stylesheets }}
