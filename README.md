# Ansible Role: ocstore-deploy

Deploys ocStore on Linux.

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values:

ocstore_hostname: "localhost"

ocstore_db_hostname: "localhost"
ocstore_db_database: "ocstore"
ocstore_db_username: "ocstore"
ocstore_db_password: "ocstore"
ocstore_db_port: "3306"
ocstore_db_socket: ""
ocstore_db_prefix: "oc_"

ocstore_recaptcha_public_key: "xxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
ocstore_recaptcha_private_key: "yyyyyyyyyyyyyyyyyyyyyyyyyyyyy"
ocstore_google_api_key: "zzzzzzzzzzzzzzzzzzzzzzzzzzzzz"
ocstore_google_analytics: "&lt;script&gt;\r\n&lt;/script&gt;"
ocstore_simple_license: "lllllllllllllllllllllllllllll"
ocstore_encryption_key: "kkkkkkkkkkkkkkkkkkkkkkkkkkkkk"
ocstore_google_map_code: "&lt;iframe&gt;\r\n&lt;/iframe&gt;"

ocstore_admin_dirname: "admin"
ocstore_admin_login: "admin"
ocstore_admin_password: "admin"
ocstore_admin_email: "admin@localhost"
ocstore_error_filename: "ocstore.log"

ocstore_maintenance: "1"
ocstore_robots_sitemap_enabled: "yes"

ocstore_php_display_errors: "1"
ocstore_php_error_reporting: "E_ALL"

ocstore_mysql_databases:
  - name: "{{ ocstore_db_database }}"
    encoding: utf8
    collation: utf8_general_ci

ocstore_mysql_users:
  - name: "{{ ocstore_db_username }}"
    host: "%"
    password: "{{ ocstore_db_password }}"
    priv: "{{ ocstore_db_username }}.*:ALL"

ocstore_www_root: "/var/www/{{ ocstore_hostname }}"

ocstore_keep_releases: 3
ocstore_releases_dir: "releases"
ocstore_current_dir: "current"
ocstore_shared_dir: "shared"
ocstore_public_dir: "public"
ocstore_admin_dir: "admin"
ocstore_repo_dir: "repo"

ocstore_git_repo: "git@bitbucket.org:USER/REPO.git"
ocstore_git_branch: "master"
ocstore_git_refspec: ""
ocstore_git_tree_public: "www/{{ ocstore_public_dir }}"
ocstore_git_tree_shared: "www/{{ ocstore_shared_dir }}"
ocstore_git_tree_admin: "www/{{ ocstore_admin_dir }}"

ocstore_shared_folders:
  - { path: "download" }
  - { path: "image" }
  - { path: "system/cache" }
  - { path: "system/license" }
  - { path: "system/logs" }
  - { path: "vqmod/cache" }
  - { path: "vqmod/logs" }

# 'dest' can be absolute or relative path with 'ocstore_current_release_dir' as base
ocstore_shared_files:
  - { path: "css/moneymaker-custom.css", dest: "catalog/view/theme/moneymaker/stylesheet/moneymaker-custom.css" }
  - { path: "image/data/favicon.ico", dest: "favicon.ico" }
  - { path: "image/data/no_image.jpg", dest: "{{ ocstore_www_root }}/{{ ocstore_shared_dir }}/image/no_image.jpg" }

ocstore_shared_copy_files:
  - { path: "system/license/filterpro.lic" }

ocstore_shared_template_files:
  - { path: ".htaccess" }
  - { path: "robots.txt" }
  - { path: "humans.txt" }
  - { path: "config.php" }
  - { path: "php.ini" }
  - { path: "vqmod/pathReplaces.php" }
  
ocstore_shared_template_common_files:  
  - { path: "css/.htaccess" }
  - { path: "css/moneymaker-custom.css" }
  - { path: "download/.htaccess" }
  - { path: "image/.htaccess" }

ocstore_shared_template_common_stub_files:
  - { path: "system/logs/{{ ocstore_error_filename}}" }

ocstore_admin_template_files:
  - { path: "config.php" }
  - { path: "php.ini" }

## Dependencies

None.

## Example Playbook

    - hosts: all
      roles:
        - Akman.ocstore-deploy

*Inside `vars/main.yml`*:

ocstore_hostname: "localhost"

ocstore_db_hostname: "localhost"
ocstore_db_database: "ocstore"
ocstore_db_username: "ocstore"
ocstore_db_password: "ocstore"
ocstore_db_port: "3306"
ocstore_db_socket: ""
ocstore_db_prefix: "oc_"

ocstore_recaptcha_public_key: "xxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
ocstore_recaptcha_private_key: "yyyyyyyyyyyyyyyyyyyyyyyyyyyyy"
ocstore_google_api_key: "zzzzzzzzzzzzzzzzzzzzzzzzzzzzz"
ocstore_google_analytics: "&lt;script&gt;\r\n&lt;/script&gt;"
ocstore_simple_license: "lllllllllllllllllllllllllllll"
ocstore_encryption_key: "kkkkkkkkkkkkkkkkkkkkkkkkkkkkk"
ocstore_google_map_code: "&lt;iframe&gt;\r\n&lt;/iframe&gt;"

ocstore_admin_dirname: "admin"
ocstore_admin_login: "admin"
ocstore_admin_password: "admin"
ocstore_admin_email: "admin@localhost"
ocstore_error_filename: "ocstore.log"

ocstore_maintenance: "1"
ocstore_robots_sitemap_enabled: "yes"

ocstore_php_display_errors: "1"
ocstore_php_error_reporting: "E_ALL"

ocstore_mysql_databases:
  - name: "{{ ocstore_db_database }}"
    encoding: utf8
    collation: utf8_general_ci

ocstore_mysql_users:
  - name: "{{ ocstore_db_username }}"
    host: "%"
    password: "{{ ocstore_db_password }}"
    priv: "{{ ocstore_db_username }}.*:ALL"

ocstore_www_root: "/var/www/{{ ocstore_hostname }}"

ocstore_keep_releases: 3
ocstore_releases_dir: "releases"
ocstore_current_dir: "current"
ocstore_shared_dir: "shared"
ocstore_public_dir: "public"
ocstore_admin_dir: "admin"
ocstore_repo_dir: "repo"

ocstore_git_repo: "git@bitbucket.org:USER/REPO.git"
ocstore_git_branch: "master"
ocstore_git_refspec: ""
ocstore_git_tree_public: "www/{{ ocstore_public_dir }}"
ocstore_git_tree_shared: "www/{{ ocstore_shared_dir }}"
ocstore_git_tree_admin: "www/{{ ocstore_admin_dir }}"

ocstore_shared_folders:
  - { path: "download" }
  - { path: "image" }
  - { path: "system/cache" }
  - { path: "system/license" }
  - { path: "system/logs" }
  - { path: "vqmod/cache" }
  - { path: "vqmod/logs" }

# 'dest' can be absolute or relative path with 'ocstore_current_release_dir' as base
ocstore_shared_files:
  - { path: "css/moneymaker-custom.css", dest: "catalog/view/theme/moneymaker/stylesheet/moneymaker-custom.css" }
  - { path: "image/data/favicon.ico", dest: "favicon.ico" }
  - { path: "image/data/no_image.jpg", dest: "{{ ocstore_www_root }}/{{ ocstore_shared_dir }}/image/no_image.jpg" }

ocstore_shared_copy_files:
  - { path: "system/license/filterpro.lic" }

ocstore_shared_template_files:
  - { path: ".htaccess" }
  - { path: "robots.txt" }
  - { path: "humans.txt" }
  - { path: "config.php" }
  - { path: "php.ini" }
  - { path: "vqmod/pathReplaces.php" }
  
ocstore_shared_template_common_files:  
  - { path: "css/.htaccess" }
  - { path: "css/moneymaker-custom.css" }
  - { path: "download/.htaccess" }
  - { path: "image/.htaccess" }

ocstore_shared_template_common_stub_files:
  - { path: "system/logs/{{ ocstore_error_filename}}" }

ocstore_admin_template_files:
  - { path: "config.php" }
  - { path: "php.ini" }

## License

MIT / BSD

## Author Information

This role was created in 2017 by Alexander Kapitman
