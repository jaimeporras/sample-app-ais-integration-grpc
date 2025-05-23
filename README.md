# AIS to Lattice Integration - gRPC

## Description
This is a sample application showcasing an integration between AIS vessel traffic data and Lattice.

The sample application demonstrates how to use the Lattice gRPC SDK for initializing an entity and features the `publish_entity` endpoint to illustrate publishing an entity to the Lattice API.

The AIS (Automatic Identification System) vessel traffic dataset is a repository of vessel identification and positioning data. The data is collected through an onboard navigation safety device that transmits and monitors the location and characteristics of vessels in U.S. and international waters in real time. For this sample demonstration, the only 4 fields in the dataset that we are interested in are the MMSI, latitude, longitude, and vessel name. These fields are used to simulate maritime traffic, creating and continuously updating vessel entities with their latest position and publishing them to the Lattice API in real-time.

## How to run locally

#### Prerequisites
- Python version greater than or equal to 3.9

#### Before you begin
Ensure you have [set up your development environment](https://docs.anduril.com/category/getting-started)

#### Clone the repository

```bash
git clone https://github.com/anduril/sample-app-ais-integration-grpc.git sample-app-ais-integration-grpc
cd sample-app-ais-integration-grpc
```

> Optional: Initialize a virtual environment
> ```bash
> python -m venv .venv
> source .venv/bin/activate
> ```

#### Install dependencies and configure project

1. Install the dependencies used for this project:
    ```bash
    pip install -r requirements.txt
    ```

2. Modify the configuration file in `var/config.yml`:
* Replace `<YOUR_LATTICE_IP>` and `<YOUR_LATTICE_BEARER_TOKEN>` with your Lattice IP and Lattice Bearer Token
    ```
    lattice-ip: <YOUR_LATTICE_IP>
    lattice-bearer-token: <YOUR_LATTICE_BEARER_TOKEN>
    ```
* If you would like, you can also modify:
    - `entity-update-rate-seconds`: to change the interval between publishing vessel entities
    - `vessel-mmsi`: to change the vessels to track
    - `ais-generate-interval-seconds`: to change the interval between generating vessel data

#### Run the program

Run the following command to start the program
```bash
python src/main.py --config var/config.yml
```

Note: If you don't provide the `--config` option the app will look for the config path `var/config.yml`
relative to the current working directory.

#### Verify your output
Navigate to your Lattice UI and verify that the vessel entities are displayed.

Congrats! You've successfully used the Lattice SDK to create and publish entities to Lattice!
