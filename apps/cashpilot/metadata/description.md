## CashPilot

CashPilot runs passive income services on your own server and shows what they earn in one web dashboard. Bandwidth sharing, storage and compute services are deployed from a catalog with a guided setup, so there is no compose file to write for each one. Balances are read every hour into an earnings history, and one dashboard can manage several servers.

### First run

1. Open the app and go to the logs of the `cashpilot-ui` container in Runtipi.
2. Copy the setup token from the line that starts with `FIRST-RUN SETUP`.
3. Enter it on the welcome page to create the owner account, then follow the setup wizard.

### Security

The worker container mounts the Docker socket so it can start and stop the earning services. Access to the Docker socket is equivalent to root on the host. Create the owner account right after install, and do not expose the dashboard to the internet without a reason.

The worker and the dashboard keep separate data folders on purpose. The dashboard's folder holds the encrypted credential store and its key, and the worker never sees it.

### Optional: isolate the earning containers

Set **Container network** to the name of a Docker bridge network you created, and the earning containers join it instead of Docker's default bridge. That lets host firewall rules keep them away from your home network. The network must exist before you deploy a service:

```bash
docker network create --driver bridge -o com.docker.network.bridge.name=cp-isolated cashpilot-isolated
```

See the guide: https://geiserx.github.io/CashPilot/home-network-security/

### Links

- Documentation: https://geiserx.github.io/CashPilot/
- Source: https://github.com/GeiserX/CashPilot
