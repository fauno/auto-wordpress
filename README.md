# Auto Wordpress

Creates or upgrades a Wordpress site, its themes and plugins.  This
script uses wordpress.git to keep the site up to date.  It also applies
some security measures (like sane file permissions) and, in case of
deface, you can simply rollback to the original site with `git reset
--hard` :)

Usage:

    auto-wordpress /srv/http/example.nu


## Security

Auto-wordpress removes write permissions after every upgrade to prevent
anything from modifying a core file, while it allows to write on
wp-content/uploads.

It's best if the webserver can't modify anything, so any attack that
relies on making Wordpress write malicious code into files are thwarted.

So `auto-wordpress` will also remove read permissions and not give write
permissions to anyone, except for the uploads directory.  This means
**you have to make sure that at least the group of the files is the very
same group your webserver is running in**, otherwise the webserver won't
be able to read any file.

Common user and groups for webservers are 'http' (on Arch and
derivatives), 'www-data' (on Debian and derivatives [ultra fugly uh?]),
etc.

In any case, adapt this command:

    chown --recursive http:http /srv/http/example.nu


## TODO

* Keep track of local changes
