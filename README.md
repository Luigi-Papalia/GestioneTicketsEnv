# GestioneTicketsEnv

This repository provides a Docker environment that includes a simple SMTP server with webmail and a local DNS service. It can be used for development or adapted for production deployments.

## Components

- **Bind9**: local DNS server used to expose an MX record for `example.local`.
- **Docker Mailserver**: provides Postfix and Dovecot for sending/receiving mail.
- **Roundcube**: web interface to read emails.

All services run in the `mailnet` network and expose minimal ports for local usage.

## Usage

1. Create a mailbox using the setup utility:
   ```bash
   docker compose run --rm mail setup email add user@example.local password
   ```
2. Start the stack:
   ```bash
   docker compose up -d
   ```
3. Point your system DNS to the container `dns` (e.g., `127.0.0.1`) so that the backend can resolve the `example.local` domain.
4. Access Roundcube at <http://localhost:8080> and log in with the credentials created above.

This environment is ready for local development. Adjust domain names and credentials in `docker-compose.yml`, `dns` configuration and `mailserver.env` for production deployment.
