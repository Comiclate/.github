<a href="https://github.com/Comiclate">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="../comiclate-banner.png">
    <img src="../comiclate-banner.png" alt="Comiclate - A community-driven comic reader" />
  </picture>
</a>

[![Discord server](https://img.shields.io/discord/1345726804274581643.svg?label=&labelColor=6A7EC2&color=7389D8&logo=discord&logoColor=FFFFFF)](https://discord.gg/RjgB89pTed)

# What is Comiclate?
> Currently in early development

Comiclate is an open-source, community-driven comic reading platform built to be extensible.

> This project does not host or distribute copyrighted comics. Support for external sources may be added via community extensions. Users are responsible for compliance with copyright laws and website terms of service.

---

## The Plan

The platform will be split into 4 separate interconnected packages that together form the entire platform.
detailed below are the descriptions and order development:

### 1. `packages/comiclate` (Backend - Core Service)
Our backend, built with [**ExpressJS**](https://expressjs.com/), handles the core logic:
-   **Routing & API:** Manages all incoming requests and API endpoints.
-   **Auth & Users:** Manages authentication, permissions and settings
-   **Database Operations:** Interacts with our database for data storage and retrieval.
-   **I/O Operations:** Handles file and network interactions.
-   **External Data Sources (via Plugins):**
    -   Content can be imported from third-party sources using plugins. See `packages/comiclate-plugin`
-   **Image Storage:** media storage support (for user-uploaded comics, personal libraries, or public-domain content).

### 1.5 `packages/comiclate-plugin` - Extendable plugin class
A plugin development kit for the backend, this will allow other users in the community to write a plugin for content that they want to see.

### 2. `packages/client` (SDK - API Consumption)
A lightweight SDK designed to standardize API consumption across all other Comiclate packages:
-   A class with methods wrapping `fetch` or `axios` for internal API calls.
-   Ensures consistent and simplified interaction with the backend.

### 3. `packages/admin` (Admin Panel - Management Interface)
A set of [**RippleJS**](https://www.ripplejs.com/) templates forming a dedicated admin panel:
-   Built upon `packages/client` for all backend interactions.
-   Separated from main website for easier updates and clear separation of concerns.

### 4. `website` (Frontend - User Interface)
The public-facing website of Comiclate:
-   Built on vite, with various plugins like VitePWA for progressive web apps.
-   Utilizes [**RippleJS**](https://www.ripplejs.com/) files for its views, allowing seamless integration with the admin panel.
-   Designed to provide a beautiful and intuitive user experience for comic readers.

## Additional planned packages

### `packages/comiclate-cli` (Optional CLI Tool)
A command-line interface tool for various utilities:
-   **Comic Uploads:** Allows users to upload comic files directly from their terminal.
-   Other features are still unplanned
-   Relies on `packages/client` for authentication and other core functionalities.

### `packages/latebot` (Optional Discord Bot)
A discord bot integrated with the API:
-   Features are still unplanned
-   Once again, we can use `packages/client` to integrate with our API
