# Auto Wordpress

Creates or upgrades a Wordpress site.  This script uses wordpress.git to
keep the site up to date.  It also applies some security measures (like
sane file permissions) and, in case of deface, you can simply rollback
to the original site with `git reset --hard` :)

Usage:

    auto-wordpress /srv/http/example.nu


## Security

Auto-wordpress removes write permissions after every upgrade to prevent
anything from modifying a core file, while it allows to write on
wp-content/uploads.

But it will also remove read permissions and not give write permissions
to anyone other than the owner of the files.  This means **you have to
make sure the owner of the files is the very same user your webserver is
running as**.

Common users for webservers are 'http' (on Arch and derivatives),
'www-data' (on Debian and derivatives [ultra fugly uh?]), etc.

In any case, adapt this command:

    chown --recursive http:http /srv/http/example.nu
