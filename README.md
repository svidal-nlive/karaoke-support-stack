# karaoke-support-stack

Infrastructure, monitoring, and utility stack for the Karaoke project.

## Services

- **prometheus**: Metrics collection
- **alertmanager**: Alerting, integrated with Prometheus
- **grafana**: Dashboard and visualization
- **redis**: In-memory key-value store for pipeline and bot use
- **filebrowser**: Web UI for file management across shared volumes
- **cloudflared**: Cloudflare tunnel (for secure public/external access)

## Usage

1. Clone this repo  
2. Copy `.env.example` to `.env` and fill in any sensitive config  
3. Ensure all required Docker **external** volumes/networks exist:

    ```bash
    docker volume create cookies
    docker volume create input
    docker volume create queue
    docker volume create metadata
    docker volume create stems
    docker volume create output
    docker volume create organized
    docker volume create logs
    docker network create backend
    ```

4. Start the support stack:

    ```bash
    docker compose up -d
    ```

## Notes

- Update paths in the Compose file to match your directory structure.
- All volumes and networks are external/shared.
- Requires configuration files for Prometheus, Alertmanager, and Grafana in the proper subfolders.

