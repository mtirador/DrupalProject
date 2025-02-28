
![Drupal Wordmark](https://upload.wikimedia.org/wikipedia/commons/thumb/c/c1/Drupal-wordmark.svg/750px-Drupal-wordmark.svg.png)

This project is a **Drupal** implementation ready for local deployment and development using **Wodby** and **Docker**.

---

## 📌 **Prerequisites**

Before starting the installation, make sure you have the following tools installed:

- **Docker**: [Download Docker](https://www.docker.com/products/docker-desktop)
- **Docker Compose**: Comes with Docker Desktop, but if you're using another Docker installation, ensure Docker Compose is installed.
- **Git**: To clone the repository.
- **Composer**: [Download Composer](https://getcomposer.org/)

---

## 🔽 **Clone the Repository**

If you haven't cloned the repository yet, start by doing so. Open your terminal and execute the following commands:

```sh
git clone https://github.com/mtirador/DrupalProject.git
cd DrupalProject
```

---

## **Install the dependencies**

Once inside the project directory, install the project dependencies using Composer:

```sh
composer install
```

This will install Drupal Core and all required dependencies into your project.

---

## **Configure the Database**

The `settings.php` file, which contains sensitive database credentials, is not included in the repository for security reasons. 

To configure your database, follow these steps:

1. **Copy the example settings file** to the correct location:

```sh
cp web/sites/default/default.settings.php web/sites/default/settings.php
```

2. **Edit the `settings.php` file** with your database credentials. Open `web/sites/default/settings.php` and find the database section:

```php
$databases['default']['default'] = array (
  'database' => 'your_database_name',
  'username' => 'your_database_username',
  'password' => 'your_database_password',
  'host' => 'localhost',
  'driver' => 'mysql', 
  'prefix' => '',
  'charset' => 'utf8mb4',
);
```

Make sure you set up your local database before continuing. You can create it manually (e.g., via MySQL/MariaDB) if it doesn't exist yet.

---

## **Run the following command to bring up the containers**

If you're using Docker and Wodby, run the following command to start the Docker containers:

```sh
docker compose up -d
```

This will start your containers in detached mode, including the web server, database, and other necessary services.

---

## **Finish the Drupal Installation**

Once the containers are up and running, you can proceed with the Drupal installation:

1. Open your browser and navigate to [http://localhost](http://localhost) (or the appropriate URL if using a different setup).
2. Follow the standard Drupal installation steps, and when prompted, select the default installation profile (or another profile if desired).
3. Complete the installation process.

If everything is configured correctly, Drupal should now be up and running on your local machine.

---

## **Verify the Setup**

Once everything is up and running, verify that:

- The Drupal website is accessible in your browser.
- The database is properly connected, and the site can load content.
- Modules and themes have been downloaded correctly via Composer.

---

## **Common Issues and Troubleshooting**

- **Database connection issues**: Double-check your `settings.php` configuration for the correct database credentials.
- **Docker-related issues**: Ensure Docker and Docker Compose are installed and running correctly. You can check container logs with:

```sh
docker-compose logs
```
- **Troubleshooting Container Issues**:
If you encounter issues while trying to bring up the containers using PODMAN , such as the error message:

Error response from daemon: fill out specgen: getting absolute path of \\wsl.localhost\podman-machine-default\var\www\html\drupalfull: unsupported UNC path
This may be due to using relative paths for volumes within WSL (Windows Subsystem for Linux). To resolve this, you should modify your docker-compose.yml file as follows:

Update Volume Paths in docker-compose.yml: Make sure you use absolute paths for volumes within WSL. Replace relative paths like ./ with full paths like /var/www/html/fulltest.
