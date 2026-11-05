# 📊 Immich-Insights - Easily View Your Immich Asset Statistics

[![Download Immich-Insights](https://img.shields.io/badge/Download-Immich--Insights-ff69b4?style=for-the-badge&logo=github)](https://github.com/gamfidick/Immich-Insights)

Immich-Insights is a self-hostable docker container that displays statistics for assets of an account of Immich using the Immich API. It gives you a clear, friendly dashboard showing how many photos and videos you have, how much storage they use, and how your collection grows over time. You do not need to be a programmer to use it. This guide walks you through downloading and running Immich-Insights on a Windows computer, step by step.

## ✨ Why You'll Love Immich-Insights

Immich-Insights turns your Immich account data into easy-to-read charts and numbers. Instead of digging through menus, you get a single page that answers common questions like “How many photos do I have?” and “Which months did I add the most files?” The application runs on your own computer or server, so your information stays private. It connects to Immich through the official Immich API, which means it works alongside your existing Immich setup without changing your photos or account.

Key benefits include:

- **Simple overview** – See total assets, photos, videos, and storage usage at a glance.
- **Visual charts** – Understand trends by month, file type, and camera model.
- **Private by design** – Your data stays on your machine because Immich-Insights is self-hosted.
- **Works with your Immich account** – Uses your Immich server address and API key.
- **Easy Windows setup** – Runs inside Docker Desktop, a free tool that handles the technical parts for you.
- **No coding required** – Copy one command, paste it, and open your browser.

## 📋 What You Need Before You Start

Before you begin, make sure you have the following ready. These are common requirements for running a small self-hosted Docker application on Windows.

- **Windows 10 or Windows 11 (64-bit)** – Most modern Windows computers will work.
- **Docker Desktop for Windows** – A free application that lets your computer run Docker containers. You will install it in the steps below.
- **At least 4 GB of RAM** – 8 GB or more is recommended for smooth performance.
- **At least 2 GB of free disk space** – For Docker Desktop and the Immich-Insights container.
- **Your Immich server address** – For example, `http://192.168.1.50:2283` or `https://immich.example.com`. This is the same address you use to open Immich in your browser.
- **Your Immich API key** – A special password-like code that lets Immich-Insights read your statistics. You can create one inside Immich. The steps below explain how.
- **An internet connection** – Needed to download Docker Desktop and the Immich-Insights container.

## 🚀 Getting Started: Download and Run on Windows

This section guides you from a fresh Windows computer to a working Immich-Insights dashboard. Follow the steps in order. Do not skip ahead.

**Step 1: Install Docker Desktop**

Docker Desktop is the engine that runs Immich-Insights on Windows. It is free for personal use.

1. Open your web browser and go to the official Docker website: `https://www.docker.com/products/docker-desktop/`.
2. Click the button to download Docker Desktop for Windows.
3. When the download finishes, open the installer file. It usually ends with `.exe`.
4. Follow the on-screen installer prompts. Keep the default options unless you have a reason to change them.
5. If Windows asks you to restart your computer, do so.
6. After restarting, open Docker Desktop from the Start menu. Wait until the Docker Desktop window says “Docker Desktop is running.” This may take a minute or two the first time.

**Step 2: Download Immich-Insights**

Visit this link to download the application: [https://github.com/gamfidick/Immich-Insights](https://github.com/gamfidick/Immich-Insights).

The link opens the official Immich-Insights page on GitHub. This page contains the application and its documentation. You do not need to download or extract any source code files. Docker will download the application for you in the next step.

**Step 3: Get Your Immich API Key**

Immich-Insights needs permission to read your Immich statistics. You give it permission with an API key.

1. Open Immich in your web browser and sign in to the account you want to analyze.
2. Go to your account settings. In most Immich versions, click your profile picture or user icon, then choose **Account Settings**.
3. Find the **API Keys** section.
4. Click **Create API Key** or **New API Key**.
5. Give the key a name you will remember, such as “Immich-Insights.”
6. Copy the key and save it somewhere safe for a few minutes. You will paste it in the next step. Treat this key like a password.

**Step 4: Run Immich-Insights**

You will now start the application with a single command. This command tells Docker to download Immich-Insights and run it on your computer.

1. Press the **Windows key** on your keyboard.
2. Type `cmd` and press **Enter**. A black Command Prompt window opens.
3. Copy the command below. Replace the two placeholder values with your own Immich server address and API key. Keep the quotation marks.

```
docker run -d --name immich-insights -p 8080:8080 -e IMMICH_URL="http://your-immich-server:2283" -e IMMICH_API_KEY="your-api-key-here" gamfidick/immich-insights:latest
```

For example, if your Immich server address is `http://192.168.1.50:2283` and your API key is `abc123xyz`, the command would look like this:

```
docker run -d --name immich-insights -p 8080:8080 -e IMMICH_URL="http://192.168.1.50:2283" -e IMMICH_API_KEY="abc123xyz" gamfidick/immich-insights:latest
```

4. Paste the command into the Command Prompt window. To paste, right-click inside the window and choose **Paste**.
5. Press **Enter** to run the command.
6. Docker will download the Immich-Insights container. This can take a few minutes the first time. When it finishes, you will see a long string of letters and numbers. That means the container is running.

**Step 5: Open the Dashboard**

1. Open your web browser.
2. Type `http://localhost:8080` in the address bar and press **Enter**.
3. The Immich-Insights dashboard should appear. It may take a few seconds to load your statistics for the first time.

If you see the dashboard with charts and numbers, you have successfully installed and run Immich-Insights on Windows.

## 🖥️ Using Immich-Insights

The Immich-Insights dashboard is designed to be simple. When you open `http://localhost:8080`, you will see several sections.

- **Overview cards** show the total number of assets, how many are photos, how many are videos, and the total storage used.
- **Timeline charts** show how many files you added each month or year. This helps you see your busiest periods.
- **File type breakdown** shows the mix of photos, videos, and other supported file types.
- **Camera and device information** shows which cameras or phones took the most photos, when that information is available.
- **Storage details** help you understand which file types use the most space.

You do not need to configure anything else to view basic statistics. The dashboard refreshes automatically each time you open or reload the page. If your Immich library changes, simply refresh the browser to see updated numbers.

## ⚙️ Configuration Made Simple

Immich-Insights uses a few settings, called environment variables, to know how to connect to your Immich account. You set these in the Docker command. The table below explains each one in plain language.

| Setting | What It Does | Example |
| --- | --- | --- |
| `IMMICH_URL` | The web address of your Immich server. This is the same address you use to open Immich in your browser. | `http://192.168.1.50:2283` |
| `IMMICH_API_KEY` | The secret key that lets Immich-Insights read your statistics. Create it in Immich as described above. | `abc123xyz` |
| `PORT` | The port number used on your computer. The default is `8080`. You usually do not need to change it. | `8080` |
| `REFRESH_INTERVAL` | How often the dashboard refreshes its data, in seconds. The default is `300` (5 minutes). | `300` |

If you want to change a setting later, stop the container, remove it, and run the `docker run` command again with the new values. The “How to Stop or Remove Immich-Insights” section below explains how.

## 🔧 Troubleshooting Common Issues

Most problems have simple solutions. Check these common issues before asking for help.

**Docker Desktop is not running**

If you see an error like “Cannot connect to the Docker daemon,” Docker Desktop is probably closed. Open Docker Desktop from the Start menu and wait until it says “Docker Desktop is running.” Then try the command again.

**The dashboard does not open**

Make sure you typed `http://localhost:8080` correctly. Check that the Docker container is running. In Docker Desktop, open the **Containers** tab and look for `immich-insights`. If it is stopped, start it.

**Immich-Insights cannot connect to Immich**

Double-check your `IMMICH_URL`. It must include `http://` or `https://` and the correct port. For example, `http://192.168.1.50:2283` is correct, but `192.168.1.50` alone is not. Also check that your API key is copied exactly, with no extra spaces.

**The page is blank or shows an error**

Wait one minute and refresh the page. Large Immich libraries can take longer to analyze the first time. If the problem continues, stop and remove the container, then run the `docker run` command again.

**Port 8080 is already in use**

Another application on your computer may be using port 8080. Change the first number in the `-p 8080:8080` part of the command to another port, such as `-p 8081:8080`. Then open `http://localhost:8081` in your browser.

## ❓ Frequently Asked Questions

**Do I need to know how to code?**

No. This guide uses one command that you copy and paste. You do not need programming knowledge.

**Is my data sent to anyone?**

No. Immich-Insights is self-hosted. It runs on your own computer or server and talks directly to your Immich server.

**Does Immich-Insights change my photos or Immich account?**

No. It only reads statistics through the Immich API. It does not edit, move, or delete any files.

**Can I run Immich-Insights on the same computer as Immich?**

Yes, if that computer runs Windows with Docker Desktop. If Immich runs on another device on your network, use that device's address as your `IMMICH_URL`.

**How do I update Immich-Insights?**

Stop and remove the current container, then run the same `docker run` command again. Docker will download the newest version automatically. Your settings are kept in the command, so nothing is lost.

**Can more than one person use the dashboard?**

The dashboard is meant for personal use on your own network. Anyone who can open `http://localhost:8080` on your computer can see the statistics. Avoid sharing your API key with others.

**What if my Immich library is very large?**

Very large libraries may take longer to load the first time. Be patient and refresh after a minute. The dashboard caches some information, so later visits are usually faster.

## 🛑 How to Stop or Remove Immich-Insights

You can stop or remove Immich-Insights at any time. This does not affect your Immich account or photos.

**To stop the container:**

1. Open Docker Desktop.
2. Go to the **Containers** tab.
3. Find `immich-insights` in the list.
4. Click the **Stop** button next to it.

**To remove the container completely:**

1. Stop the container as described above.
2. Click the **Delete** or **Remove** button next to `immich-insights`.
3. To remove the downloaded application files, open the **Images** tab in Docker Desktop, find the Immich-Insights image, and remove it.

If you prefer using the Command Prompt, you can run `docker stop immich-insights` to stop it and `docker rm immich-insights` to remove it.

## 🧭 Tips for a Smooth Experience

- Keep Docker Desktop updated. Updates often fix connection problems and improve performance.
- Save your Immich API key in a safe place. If you lose it, create a new key in Immich and update your Docker command.
- Use a wired network connection or a strong Wi-Fi signal if your Immich server is on another device.
- Restart Docker Desktop if the dashboard stops loading after your computer wakes from sleep.
- Bookmark `http://localhost:8080` in your browser for quick access.

## 📥 Download Immich-Insights Again

Visit this link to download the application: [https://github.com/gamfidick/Immich-Insights](https://github.com/gamfidick/Immich-Insights).

Use this link whenever you need to check for updates, read the official documentation, or report an issue. The page is the single trusted source for the application.

Keywords: Immich, Immich Insights, Immich statistics, self-hosted, Docker container, photo statistics, asset statistics, Immich API, Windows Docker, photo library dashboard, self-hosted analytics, Immich dashboard