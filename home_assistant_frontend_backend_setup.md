# Home Assistant Frontend + Backend Integration Setup

Hello guys 👋,  
Here are the steps to make the integration work between the Home Assistant **core (backend)** and the **frontend** repositories.

---

## 1. Update the Configuration File

In your **Home Assistant Core** repo, open `core/config/configuration.yaml` and update the following lines:

- Replace:
  ```
  themes: !include_dir_merge_named themes
  ```
  with:
  ```
  development_repo: /home/tesfu-mbl/frontend
  ```

> **Note:** Replace `/home/tesfu-mbl/frontend` with your **absolute path** to the frontend directory.

---

## 2. Run the Core

Start the Home Assistant Core as usual:

```bash
hass -c config
```

---

## 3. Set Up and Run the Frontend

In your **frontend** repository:

```bash
nvm install
nvm use
script/bootstrap
script/setup_translations
nvm use
script/develop
nvm use
script/develop_and_serve -c http://localhost:8123
```

---

## 4. Access the Frontend

Once running, access it at:

👉 [http://localhost:8124](http://localhost:8124)

---

## 5. For WSL (Windows Subsystem for Linux) Users

If you're using **WSL on Windows**, do the following:

1. Check your WSL IP address:
   ```bash
   wsl hostname -I
   ```

2. Replace the URLs in commands and access paths:

   - Replace:
     ```
     http://localhost:8124
     ```
     with:
     ```
     http://<WSL_IP>:8124
     ```

   - Replace:
     ```
     script/develop_and_serve -c http://localhost:8123
     ```
     with:
     ```
     script/develop_and_serve -c http://<WSL_IP>:8123
     ```

---

✅ You should now have both **frontend and backend** running locally and connected!
