# Rapidkit - Purge Recipe
This recipe sets up varnish purge to connect with your local varnish

## How to set up

When installing the recipe, you need to provide the following information:
- Hosted environment a - The hostname for the first deployed environment.
- Hosted environment b - The hostname for the second deployed environment.

IT should be able to provide this information

## How to Disable Purger

The purger configuration is set up like this:

$config['purge.plugins']['purgers'][0] : This is the local purger
$config['purge.plugins']['purgers'][1] : This is the purger on the first hosted environment
$config['purge.plugins']['purgers'][2] : This is the purger on the second hosted environment

So to disable a purger on an environment you can set the value to NULL.

This example disables the purger on both hosting environments, leaving the local purger active.
(you would probably want this setup on local)

```php
$config['purge.plugins']['purgers'][1] = NULL;
$config['purge.plugins']['purgers'][2] = NULL;
```

You can programmatically configure purper configuration per environment by using the `$_ENV['APP_ENV']` variable.
