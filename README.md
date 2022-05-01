# Overview

WebRotate 360 Product Viewer Ad-hoc Integration for Magento 2 allows integrating embedded or popup 360-degree or 3D product views in place of any element on product pages in Magento 2. These product views can be created using our free publishing software available on [webrotate360.com](https://www.webrotate360.com/products/webrotate-360-product-viewer.aspx). Note that WebRotate 360 integration for the standard Magento 2 gallery is available as a [separate Magento 2 extension](https://github.com/webrotate360/magento2-standard). 


## About WebRotate 360

WebRotate 360 ® are developers of 3D components and solutions for interactive eCommerce, eLearning, and digital marketing.


## Requirements

This extension supports both Magento Open Source (Community and Enterprise) and Adobe Commerce editions. M1 extension for previous releases is available on [here](https://www.webrotate360.com/products/cms-and-e-commerce-plugins/plugin-for-magento.aspx?section=M1).


## Install via Composer

Please backup your Magento setup before proceeding with the installation.

If you have Composer installed, run these Magento CLI commands from the root of your Magneto installation:
```shell
composer require webrotate360/module-product-viewer-adhoc
php bin/magento module:enable WebRotate360_ProductViewerAdHoc --clear-static-content 
php bin/magento setup:upgrade
php bin/magento cache:flush
```


## Install from GitHub

Please backup your Magento setup before proceeding with the installation.

Download zip package by clicking "Clone or Download" and selecting Download ZIP at the top of this page. 

 * Create an /app/code/WebRotate360/ProductViewerAdHoc directory in your Magento installation.
 * Extract the contents of magento2-adhoc-master from the zip and copy or upload everything to /app/code/WebRotate360/ProductViewerAdHoc
 * Run these commands via Magento CLI  to install and enable the module:
 
 ```shell
php bin/magento module:enable WebRotate360_ProductViewerAdHoc --clear-static-content  
php bin/magento setup:upgrade
php bin/magento cache:flush
```


## Configure and test

Select Stores > Configuration and expand WebRotate 360 Product Viewer > Ad-hoc in your Magento admin. 

* Enter a CSS class or id of an html element to be used as a placeholder for 360 product views (or a popup activation button) on the product pages under Page Placeholder.
* Configure the module by following descriptions under each field on the page.
* Select a test product in Magento catalog and create a new product attribute (as a text field) with the attribute code set to webrotate_path.
* Enter this demo config URL (hosted via [PixRiot](https://www.webrotate360.com/services/pixriot.aspx)) in the attribute field for selected product and save and refresh Magento caches.

 ```shell
 https://s1.pixriot.com/433181dfa6/CMS/Magento/Example/Example.xml
 ```

Alternatively, copy "sampleshoe" folder that is installed with the plugin (under WebRotate360/ProductViewerAdHoc/view/frontend/web/360assets) to a folder in your Magento installation and update the attribute field accordingly, e.g:
 
 ```shell
/my-360-views/sampleshoe/config.xml
 ```

## Create your own views

Download [WebRotate 360 Product Viewer software](https://www.webrotate360.com/products/webrotate-360-product-viewer.aspx) (SpotEditor) and publish a 360 or a multi-row 3D product view using your images. You may use our sample images located under additional resources in the previous link.

FTP upload is available inside the software or you may upload everything manually via FileZilla or a similar client. Consider using our optimized [PixRiot](https://www.webrotate360.com/services/pixriot.aspx) service to host and manage your spins online for unmatched convenience. You only need to upload a single folder located under published/360_assets of your published SpotEditor project for each product view. You may also publish multiple product views into a single 'published' location on your hard-drive and upload all product views at once.

Note the URL of the configuration file (.xml) in the uploaded folder and enter a relative URL of the configuration file on your server in the new attribute field (webrotate_path) for selected products in the Catalog.


## CDN and 'master config' (PRO)

You can create an extra product attribute with the attribute code set to webrotate_root to allow specifying an alternative location of the images for each product. The root value is a URL (e.g http://mycdn.com/360_assets/product1/) that can point to a folder with images on an external server. When it's configured, the module will prepend the webrotate_root URL to the relative image path stored in the viewer configuration xml for each image. This is valuable when you need to host the assets on a dedicated file server or CDN.

This feature can be also used to load multiple product views via a single 'master' config xml that you can set under the plugin settings via Master Config URL. If Master Config URL is configured in the module settings, you don’t need to specify the webrotate_path attribute in the catalog for the products that share the same config , i.e you would only use the webrotate_root parameter, pointing to the image assets. Note that this will work as long a the number of images and their file names are the same across selected product views. 
