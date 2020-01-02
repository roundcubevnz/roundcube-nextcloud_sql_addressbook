***********************************************
NextCloud SQL address book plugin for Roundcube
***********************************************

Roundcube plugin that allows access to NextCloud address books.
Uses direct database access (SQL), which is much faster than accessing the
address book entries via the CardDAV plugin.

[x] List all user's NextCloud address books
[x] Search
[x] Autocomplete
[ ] Access to address books shared by other people in NextCloud
[ ] Access to more fields than "email" and "name" (full name)
[ ] Updating/adding address book entries (not planned)

## Requirements

Only tested this plugin with following environments. Other setup may work with luck.

- PHP: >= `7`
- Roundcube: `1.2.8`,`1.3.0`
  - Supported skins: `Classic`, `Larry`, `Elastic`
- NextCloud 14
  - Read-only SQL database access from Roundcube to the NextCloud database.
  to the following tables needed: ``oc_addressbooks``, ``oc_cards_properties``
- Roundcube user login e-mail addresses must equal the username in NextCloud
  (Users log in with `alice@example.org` in both Roundcube and NextCloud)


## Installation

* Clone repository into roundcube `plugins/` directory as `nextcloud_sql_addressbook`.
* Copy `config.inc.php.dist` to `config.inc.php` and adjust it:
   * Database connection
   * Table prefix (defaults to ``oc_``)
* Enable the plugin at `config/config.inc.php` by adding it to the `$config['plugins']` array.


## Debugging

If you do not see any address books:

* The address books are only found if the `principaluri` in the `oc_addressbooks`
table equals `principals/users/` + `$useremailaddress`.

If you do not see all contacts: 

* Only contacts with an e-mail address are shown.


Links
=====

- Original Git mirror: https://github.com/cweiske/roundcube-nextcloud_sql_addressbook
