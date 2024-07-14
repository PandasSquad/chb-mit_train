# Train repo - CHB MIT Dataset

This repository contains the code to train a model to detect epileptic seizures in EEG data. The model is trained on the CHB MIT dataset.
The data is already preprocessed and stored in the `data` folder.

## Components

- `mlflow` - MLflow is used to track the experiments and store the results.
- `tensorflow` - TensorFlow is used to train the model.
- `jupyter` - Jupyter notebook is used to run the code interactively.

## Dependencies

GPU is required to run the code.

You need to install GPU drivers and NVIDIA Container Toolkit to run the code in a container.

Don't listen to ChatGPT (July 2024). The instructions are outdated.

### GPU useful info and links

Docker GPU Support doesn't use `runtime: nvidia` anymore. Instead:

```bash
devices:
    - driver: nvidia
    count: 1
    capabilities: [gpu]
```

To test if the runtime is working, run:

```bash
sudo docker run --rm --runtime=nvidia --gpus all ubuntu nvidia-smi
```

In WSL2, you need to manually add the `nvidia` runtime to the Docker daemon. To do this, edit the `daemon.json` file in the Docker Desktop settings (Docker Engine).

Add the following line:

```json
{
  "default-runtime": "nvidia"
}
```

Then restart the Docker Desktop. More info [here](https://stackoverflow.com/questions/77323535/add-nvidia-runtime-to-docker-runtimes-on-windows-wsl).

```bash
"runtimes": {
    "nvidia": {
        "args": [],
        "path": "nvidia-container-runtime"
    }
}
```

- [Install NVIDIA Container Toolkit](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html#installing-with-apt)
- [Docker GPU Support](https://docs.docker.com/compose/gpu-support/)

## Usage

To run the code, you need to have Docker installed.

To build the Docker image, run:

```bash
docker compose up --build -d
```

Once it's built, you can run the Jupyter notebook by opening the browser at `localhost:8888`.

MLflow is running at `localhost:5000`.

To stop the container, run:

```bash
docker compose down
```
