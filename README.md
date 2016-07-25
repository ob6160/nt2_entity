# nt2_entity

## Final goal

We want to get a place where, given a valid property reference and API details, a TABS Property can be read into a Drupal entity, then rendered.

## How to get there

  * Use Neontabs IO module to fetch the JSON
  * Create a module that defines a stub, non array values, for the property entity
  * Create a vocabulary and terms for attributes.
    * Initial just storing the label as a term title.
    * Next a term entity with firlds for each of the TABS fields on an attribute.
  * Associate the attributes of a property with terms in the vocabulary
  * Add images to the entity (use the external image cache and image optimise modules to help with this)
  * Create a multi hiearchy vocabulary for areas and locations.

We'll re-assess here, we have co-ordinates, brands, address to consider


## Install Guide (Ubuntu)
1. [Install the LAMP stack](https://help.ubuntu.com/community/ApacheMySQLPHP) and ensure permissions for `/var/www` are set appropriately
1. [Install Drush](http://docs.drush.org/en/master/install/)
1. Install drupal dependencies: ```apt-get install php-xml```
1. Create a new drupal instance:
  * ```cd /var/www/$drupal_name```
  * ```drupal_name="nt2_test"``` (can be any appropriate name)
  * ```drush dl drupal-7.40 --drupal-project-rename=$drupal_name```
  * Navigate to http://localhost/$drupal_name follow the GUI steps (create db in mysql)
1. [Get access to neontabs then clone into /var/www/html/$drupal_name/sites/all/modules/neontabs](https://bitbucket.org/neontabs/neontabs)
1. [Clone this repo into your modules folder](https://github.com/ob6160/nt2_entity)
1. Carry out drupal install steps @ `http://localhost/$drupal_name`
1. Run the following commands to set the required environment variables:
  * ```drush vset tabs_io_config_api_base_url http://zz.api.carltonsoftware.co.uk```
  * ```drush vset tabs_io_config_api_secret $secret```
  * ```drush vset tabs_io_config_api_api_key $other_secret```
1. ```cd /var/www/html/$drupal_name/ && drush en nt2_node_type```
