# Auto Wordpress

Creates or upgrades a Wordpress site.  This script uses wordpress.git to
keep the site up to date.  It also applies some security measures (like
sane file permissions) and, in case of deface, you can simply rollback
to the original site with `git reset --hard` :)

Usage:

    auto-wordpress /srv/http/example.nu
