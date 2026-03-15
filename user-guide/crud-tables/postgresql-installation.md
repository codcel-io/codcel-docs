<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## PostgreSQL version
We recommend PostgreSQL 18 (latest at the time of writing). If you already have PostgreSQL installed, you can check your version with:

```
psql --version
```

## macOS installation
You can install PostgreSQL on macOS using either Homebrew or a native app.

### Option 1: Homebrew (recommended)
1) Install Homebrew if you don't have it: https://brew.sh
2) Install PostgreSQL:
   ```
   brew install postgresql@18
   ```
3) Start PostgreSQL as a background service:
   ```
   brew services start postgresql@18
   ```
4) Verify it works:
   ```
   psql --version
   createdb testdb
   psql testdb -c "SELECT version();"
   ```

Note: On first install, Homebrew sets up a default data directory. If you need to initialize manually, consult `brew info postgresql@18` for caveats.

### Option 2: Postgres.app
1) Download Postgres.app: https://postgresapp.com/
2) Drag to Applications and open it; initialize a server.
3) Click "Open psql" and run:
   ```
   SELECT version();
   ```

## Windows installation
### Option 1: Official installer (EDB)
1) Download the Windows installer from: https://www.postgresql.org/download/windows/
2) Run the installer and select components (psql and pgAdmin are useful).
3) Set a password for the default postgres superuser, keep default port 5432 unless you need a different one.
4) Finish the install and allow the service to start.
5) Verify:
   - Open Command Prompt (or PowerShell) and run:
    ```
    "C:\Program Files\PostgreSQL\18\bin\psql.exe" --version
    ```
   - Or open pgAdmin and connect to the local server.

### Option 2: Package managers
- Winget:
  ```
  winget install PostgreSQL.PostgreSQL
  ```
- Chocolatey:
  ```
  choco install postgresql
  ```
After installation, ensure the PostgreSQL service is running (Services app) and verify with psql or pgAdmin.

## Linux installation
Instructions vary by distribution. Below are common options.

### Debian/Ubuntu (install PostgreSQL 18 via PGDG repository)
```
# Add PGDG apt repository (required to get v18 on many releases)
sudo apt update
sudo apt install -y ca-certificates curl gnupg lsb-release
sudo install -d /usr/share/postgresql-common/pgdg
curl -fsSL https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo gpg --dearmor -o /usr/share/postgresql-common/pgdg/apt.postgresql.org.gpg
echo "deb [signed-by=/usr/share/postgresql-common/pgdg/apt.postgresql.org.gpg] http://apt.postgresql.org/pub/repos/apt $(. /etc/os-release && echo $VERSION_CODENAME)-pgdg main" | sudo tee /etc/apt/sources.list.d/pgdg.list

# Install PostgreSQL 18
sudo apt update
sudo apt install -y postgresql-18 postgresql-client-18

# Start and enable service
sudo systemctl enable --now postgresql

# Verify
psql --version
sudo -u postgres psql -c "SELECT version();"
```

### Fedora/RHEL/CentOS (PGDG yum repo, PostgreSQL 18)
```
# Add PGDG repository
sudo dnf -y install https://download.postgresql.org/pub/repos/yum/reporpms/EL-$(rpm -E %rhel)-x86_64/pgdg-redhat-repo-latest.noarch.rpm

# Disable the built-in PostgreSQL module to avoid older versions
sudo dnf -y module disable postgresql

# Install PostgreSQL 18 server and client
sudo dnf -y install postgresql18-server postgresql18

# Initialize DB and start service
sudo /usr/pgsql-18/bin/postgresql-18-setup initdb
sudo systemctl enable --now postgresql-18

# Verify
psql --version
sudo -u postgres psql -c "SELECT version();"
```

### Arch Linux
```
sudo pacman -S postgresql
# Initialize the data directory (if not auto-initialized)
sudo -iu postgres initdb -D /var/lib/postgres/data
sudo systemctl enable --now postgresql
sudo -u postgres psql -c "SELECT version();"
```

## Creating a database and user for CRUD tables
After PostgreSQL is installed and running, create a database and an application user (replace placeholders as needed):

```
# Create a database
createdb codcel

# Create a user and set a password (run inside psql)
sudo -u postgres psql
CREATE USER codcel WITH PASSWORD 'your-strong-password';
GRANT ALL PRIVILEGES ON DATABASE codcel TO codcel;
\q
```

If your environment doesn’t use sudo (e.g., macOS Homebrew shell user), you can connect directly with `psql` and run the same SQL statements without `sudo -u postgres`.