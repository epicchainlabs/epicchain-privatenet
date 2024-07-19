# EpicChain Private Network for Blockchain Testing

This document provides comprehensive instructions for setting up and running a private network tailored for EpicChain blockchain testing. This setup is based on the [EpicChain Lab's container](https://github.com/epicchainlabs/neo-privatenet-docker) and has been customized to fit the needs of the EpicChain ecosystem.

## How to Boot Up the Environment

To initialize the private network environment, use the following command:

```bash
make up
```
or
```bash
make privnet
```

This command will start the environment and ensure all necessary components are running.

## What’s Inside?

The EpicChain private network environment includes:

- **4 EpicChain Consensus Nodes**: These nodes are crucial for maintaining the blockchain network's integrity and ensuring consensus among nodes.
- **Auto Import Smart Contract Mechanism**: This mechanism allows for the automatic import and deployment of smart contracts, facilitating seamless integration and testing.
- **EpicScan API**: This API provides essential tools and functionalities for scanning and interacting with the EpicChain blockchain.
- **PostgreSQL Database**: Used for storing and managing data related to the private network.

## Logs

The consensus nodes operate within `GNU/screen` and send their logs to Docker logs for monitoring. The mechanism for importing smart contracts waits for environment variables to be set.

To monitor the logs and see the progress of smart contract imports, use:

```bash
make logs
```

This command will display real-time logs, allowing you to track the status of various operations within the environment.

## Environment File

Here are the environment variables used for configuring the EpicChain private network:

*System*
- **TZ**: Set the system's default time zone.

*Smart Contract*
- **CONTRACT_ARGS**: Arguments required for deploying a smart contract.
- **CONTRACT_FILE**: Path to the smart contract file within the container.
- **CONTRACT_FILE_LOCAL**: Path to the local smart contract file on your host machine.

*PostgreSQL*
- **POSTGRES_USER**: Username for accessing the PostgreSQL database.
- **POSTGRES_HOSTNAME**: Hostname for the PostgreSQL database server.
- **POSTGRES_PASSWORD**: Password for the PostgreSQL database user.
- **POSTGRES_DATABASE**: Default database name for PostgreSQL.

*EpicScan*
- **NEO_SEED_{NUM:1-4}**: Host addresses for EpicScan synchronization. These are used to ensure that the EpicScan tool is in sync with the blockchain network.

## Makefile

The Makefile provides several targets to manage the private network environment:

```plaintext
  Usage:

    make <target>

  Targets:

    down      Stop the private network environment.
    help      Display this help prompt.
    kill      Terminate the private network environment.
    logs      Follow and display the logs from containers.
    privnet   Start only the private network, excluding EpicScan and PostgreSQL.
    up        Start the full private network environment.
```

## Contributing

At this time, we are not accepting contributions to this project. However, we encourage you to follow our updates and developments. Stay tuned for future opportunities to contribute.

## License

This project is licensed under the GPL v3.0 License. For further details, please refer to the [LICENSE](LICENSE) file included in this repository.

