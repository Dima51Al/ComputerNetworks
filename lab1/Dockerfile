FROM postgres:15
RUN apt-get update && apt-get install -y --no-install-recommends netcat-openbsd python3-pip python3-venv curl iputils-ping && rm -rf /var/lib/apt/lists/*
RUN python3 -m venv /opt/patroni-venv && /opt/patroni-venv/bin/pip install --no-cache-dir --upgrade pip && /opt/patroni-venv/bin/pip install --no-cache-dir 'patroni[zookeeper]' psycopg2-binary
COPY postgres0.yml /postgres0.yml
COPY postgres1.yml /postgres1.yml
ENV PATH="/opt/patroni-venv/bin:$PATH"
USER postgres
