FROM python:3.9-slim-buster

WORKDIR /app

COPY requirements.txt .

RUN apt-get update && apt-get install -y --no-install-recommends wget software-properties-common gnupg build-essential tcl

# Download and install SQLite 3.40.0 from source
RUN wget https://www.sqlite.org/2022/sqlite-autoconf-3400000.tar.gz && \
    tar xvf sqlite-autoconf-3400000.tar.gz && \
    cd sqlite-autoconf-3400000 && \
    ./configure --prefix=/usr/local && \
    make install

ENV LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH
RUN ldconfig

RUN pip install --upgrade pip
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

CMD ["python", "app/main.py"]
