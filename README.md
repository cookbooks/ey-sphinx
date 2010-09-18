ey-cloud-recipes/sphinx
========================

A chef recipe for enabling sphinx on the EY AppCloud.

Dependencies
============

If you're using the ultrasphinx flavor in this recipe, you'll need to make sure
you install the chronic gem in your environment (this is not handled by the recipe).

As previously mentioned, your application needs to have the appropriate plugin installed
already.

For thinking_sphinx:

    script/plugin install git://github.com/freelancing-god/thinking-sphinx.git

For ultrasphinx:

    script/plugin install git://github.com/fauna/ultrasphinx.git

Using it
========

Edit the recipe, changing the appropriate fields as annotated in recipes/default.rb.
Namely:

  * Add your application name.
  * Uncomment the flavor you want to use (thinking_sphinx or ultrasphinx).
  * Set the cron_interval to specify how frequently you want to reindex.

Add the following before_migrate.rb [deploy hook](http://docs.engineyard.com/appcloud/howtos/deployment/use-deploy-hooks-with-engine-yard-appcloud):

    run "ln -nfs #{shared_path}/config/sphinx.yml #{release_path}/config/sphinx.yml"