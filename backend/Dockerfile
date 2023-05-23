FROM python:3.9

RUN apt-get update && apt-get install -y \
    graphviz \
    libgraphviz-dev \
    pkg-config \
    python3-dev \
    libpq-dev \
    gcc \
    libpython3.9-dev


WORKDIR /backend 

COPY . .

RUN pip install -r requirements.txt


CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]

