# dockBox
**Simple & Ready-to-Code Docker Environment**

A lightweight, pre-configured LAMP stack + Node.js environment.  
Ideal for React/Vue frontends communicating with PHP backends in a single container.

### 🚀 Tech Stack
*   **PHP 8.4** (Latest)
*   **Apache** (Web Server)
*   **MariaDB** (Latest)
*   **Node.js 24.x** (LTS) + **npm/yarn**
*   **Composer**
*   **Git**

---

## 🛠 Installation

```bash
# 1. Clone the repository
git clone https://github.com/rocco-giandomenico/default_container.git dockBox

# 2. Enter directory
cd dockBox

# 3. Create .env file
cp sample.env .env

# 4. Start Containers
docker compose up -d --build
```

Your environment is now running at: **[http://localhost](http://localhost)**

---

## 💻 Usage

### Directory Structure
*   **`www/html`**: This is your web root (`http://localhost`).
    *   Place your **Frontend** build here (e.g., `index.html`, `dist/`).
    *   Place your **Backend API** here (e.g., `api/index.php`).

### Access Container Shell
To run commands like `composer install`, `npm install`, or `php artisan`:
```bash
docker compose exec --user ivert webserver bash
```
*(Replace `ivert` with the username defined in your `.env` file)*

---

## 🔧 Configuration

*   **MySQL/MariaDB**:
    *   Host: `database`
    *   User/Pass: Defined in `.env` (Default: `docker`/`docker`)
*   **PHP Config**: `./config/php/php.ini`
*   **Apache Config**: `./config/vhosts/default.conf`

---

## 📦 React/Vue Setup (Example)

1.  **Enter Shell**: `docker compose exec --user ivert webserver bash`
2.  **Create App**: `npm create vite@latest my-app -- --template react`
3.  **Dev Server**:
    *   In `vite.config.js`, set `server: { host: '0.0.0.0', port: 5173 }`.
    *   Run `npm run dev`.
    *   Access at `http://localhost:5173`.
4.  **Production**:
    *   Run `npm run build`.
    *   The `dist/` folder will be served appropriately if placed in `www/html`.

---

**License**: [MIT](LICENSE)
