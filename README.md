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

ocstore_shared_stub_folders:
  - { mode: "750", dest: "batcher" }
  - { mode: "770", dest: "download" }
  - { mode: "770", dest: "image" }
  - { mode: "770", dest: "image/cache" }
  - { mode: "750", dest: "system" }
  - { mode: "770", dest: "system/cache" }
  - { mode: "770", dest: "system/license" }
  - { mode: "770", dest: "system/logs" }
  - { mode: "750", dest: "vqmod" }
  - { mode: "770", dest: "vqmod/cache" }
  - { mode: "770", dest: "vqmod/cache/vqcache" }
  - { mode: "770", dest: "vqmod/logs" }

ocstore_shared_folders:
  - { dest: "download" }
  - { dest: "image" }
  - { dest: "system/cache" }
  - { dest: "system/license" }
  - { dest: "system/logs" }
  - { dest: "vqmod/cache" }
  - { dest: "vqmod/logs" }

ocstore_shared_copy_files:
  - { mode: "660", dest: "system/license/filterpro.lic" }

ocstore_shared_stub_files:
  - { mode: "660", dest: "system/logs/{{ ocstore_error_filename }}" }
  - { mode: "660", dest: "vqmod/logs/vqmod.log" }

ocstore_shared_template_files:
  - { mode: "644", src: ".htaccess.j2", dest: ".htaccess" }
  - { mode: "640", src: "robots.txt.j2", dest: "robots.txt" }
  - { mode: "640", src: "humans.txt.j2", dest: "humans.txt" }
  - { mode: "640", src: "config.php.j2", dest: "config.php" }
  - { mode: "640", src: "php.ini.j2", dest: "php.ini" }
  - { mode: "640", src: "vqmod/pathReplaces.php.j2", dest: "vqmod/pathReplaces.php" }

ocstore_admin_template_files:
  - { mode: "640", src: "admin/config.php.j2", dest: "config.php" }
  - { mode: "640", src: "admin/php.ini.j2", dest: "php.ini" }

telegram_enabled: "no"
telegram_token: "botXXXXXX:YYYYYYYYYYYYYYYYY"
telegram_chat_id: "ZZZZZZZZ"

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

ocstore_shared_stub_folders:
  - { mode: "750", dest: "batcher" }
  - { mode: "770", dest: "download" }
  - { mode: "770", dest: "image" }
  - { mode: "770", dest: "image/cache" }
  - { mode: "750", dest: "system" }
  - { mode: "770", dest: "system/cache" }
  - { mode: "770", dest: "system/license" }
  - { mode: "770", dest: "system/logs" }
  - { mode: "750", dest: "vqmod" }
  - { mode: "770", dest: "vqmod/cache" }
  - { mode: "770", dest: "vqmod/cache/vqcache" }
  - { mode: "770", dest: "vqmod/logs" }

ocstore_shared_folders:
  - { dest: "download" }
  - { dest: "image" }
  - { dest: "system/cache" }
  - { dest: "system/license" }
  - { dest: "system/logs" }
  - { dest: "vqmod/cache" }
  - { dest: "vqmod/logs" }

ocstore_shared_copy_files:
  - { mode: "660", dest: "system/license/filterpro.lic" }

ocstore_shared_stub_files:
  - { mode: "660", dest: "system/logs/{{ ocstore_error_filename }}" }
  - { mode: "660", dest: "vqmod/logs/vqmod.log" }

ocstore_shared_template_files:
  - { mode: "644", src: ".htaccess.j2", dest: ".htaccess" }
  - { mode: "640", src: "robots.txt.j2", dest: "robots.txt" }
  - { mode: "640", src: "humans.txt.j2", dest: "humans.txt" }
  - { mode: "640", src: "config.php.j2", dest: "config.php" }
  - { mode: "640", src: "php.ini.j2", dest: "php.ini" }
  - { mode: "640", src: "vqmod/pathReplaces.php.j2", dest: "vqmod/pathReplaces.php" }

ocstore_admin_template_files:
  - { mode: "640", src: "admin/config.php.j2", dest: "config.php" }
  - { mode: "640", src: "admin/php.ini.j2", dest: "php.ini" }

telegram_enabled: "no"
telegram_token: "botXXXXXX:YYYYYYYYYYYYYYYYY"
telegram_chat_id: "ZZZZZZZZ"

## License

MIT / BSD

## Author Information

This role was created in 2017 by Alexander Kapitman
