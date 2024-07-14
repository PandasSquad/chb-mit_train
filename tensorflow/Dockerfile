FROM tensorflow/tensorflow:latest-gpu-jupyter

RUN pip install --upgrade pip
RUN pip install --ignore-installed blinker mlflow

WORKDIR /tf/notebooks

COPY requirements.txt ./
RUN pip install -r requirements.txt
