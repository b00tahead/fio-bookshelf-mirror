# Setting up project locally

### Install Docker Desktop for Mac

Follow the instructions here: https://ddev.readthedocs.io/en/latest/users/install/docker-installation/#docker-desktop-for-mac

### Install DDEV

```sh
curl -fsSL https://ddev.com/install.sh | bash
```

### Clone project

```sh
git clone https://github.com/b00tahead/fio-bookshelf-mirror.git

cd fio-bookshelf-mirror
```

### Start up DDEV container

```sh
ddev start
```

### Install drush

```sh
ddev composer require drush/drush
```

### Configure DDEV

```sh
ddev config --auto
```

### Install Drupal site

```sh
ddev drush site:install -y
```

### Import DB

```sh
gunzip .backups/fio-bookshelf_dev_2024-03-08T01-43-57_UTC_database.sql.gz

ddev import-db fio-bookshelf-mirror < .backups/fio-bookshelf_dev_2024-03-08T01-43-57_UTC_database.sql
```

### Import files

```sh
ddev import-files --source=.backups/fio-bookshelf_dev_2024-03-08T01-43-57_UTC_files.tar.gz
```

### Restart DDEV container

```sh
ddev restart
```

### Clear DB cache

```sh
ddev drush cr
```

### Launch site

```sh
ddev launch
```
