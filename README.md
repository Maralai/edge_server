# Edge Server

## Overview

The `edge_server` project is designed to serve as an Edge Server for `edge_device` nodes which offer various plugins and monitoring solutions. This setup primarily utilizes Docker and is structured for easy deployment and management.

## Project Structure

- **docker-compose.yaml:** Defines the Docker services, networks, and volumes for the project.
- **LICENSE:** Contains the licensing information for the project.
- **README.md:** This file, providing an overview and instructions.
- **.gitignore:** Specifies intentionally untracked files to ignore.
- **grafana/:** Contains Grafana configurations for dashboards, datasources, and notifiers.

### Grafana Configuration

- **dashboards/:** Contains JSON definitions for various Grafana dashboards and a YAML configuration file.
  - **dashboards.yaml:** Configures how Grafana should discover and load dashboards.
  - **server/:** Dashboard JSON files for specific monitoring purposes like Loki logs, Docker, and host metrics, and Node Exporter metrics.

- **datasources/:** Configuration for Grafana datasources.
  - **loki.yaml:** Configuration for the Loki datasource.
  - **prometheus.yaml:** Configuration for the Prometheus datasource as the default.

- **notifiers/:** Setup for notification channels.
  - **email.yaml:** (Commented out) Template for email notification configuration.
  - **webhook.yaml:** (Commented out) Template for webhook notification configuration.

## Getting Started

1. **Pre-requisites:**
   - Docker and Docker Compose installed on your system.
   - Basic understanding of Docker, Grafana, Prometheus, and Loki.

2. **Setup:**
   - Clone the repository to your local system.
   - Navigate to the root directory of the project.
   - Create a `.env` file in the root directory and add the following environment variables:

        ```bash
        # Grafana
        GF_SECURITY_ADMIN_PASSWORD=some_strong_password
        GF_USERS_ALLOW_SIGN_UP=false

        # Grafana Log Rotation
        GF_LOG_MODE=console file
        GF_LOG_MAX_DAYS=7
        GF_LOG_ROTATE=true
        GF_LOG_MAX_LINES=1000000

        # Grafana Notifications

        # Email Notification Settings
        # SMTP_ADDRESSES=   # Comma seperated for multiple to addresses.
        # SMTP_USER=
        # SMTP_PASSWORD=
        # SMTP_SERVER=
        # SMTP_PORT=

        # Webhook Notification Settings
        # WEBHOOK_URL=
        ```

3. **Running the Project:**
   - Run `docker-compose up -d` to start the services defined in `docker-compose.yaml`.
   - Access Grafana through the specified port to view the dashboards.

4. **Configuration:**
   - Customize the Grafana datasources and dashboards as per your needs.
   - Uncomment and configure `email.yaml` and `webhook.yaml` in `grafana/notifiers/` to set up notification channels.

## License

This project is licensed under the [LICENSE](./LICENSE) file in the root directory of this project.

---

You can adjust the content as per your project specifics, add any additional instructions, or elaborate on certain aspects as needed.