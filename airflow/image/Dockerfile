ARG AIRFLOW_BASE_IMAGE=apache/airflow:3.1.7
FROM ${AIRFLOW_BASE_IMAGE}

COPY requirements.txt /tmp/requirements.txt
USER root
RUN python -m venv /opt/dbt-venv \
    && /opt/dbt-venv/bin/pip install --no-cache-dir --upgrade pip \
    && /opt/dbt-venv/bin/pip install --no-cache-dir -r /tmp/requirements.txt \
    && ln -sf /opt/dbt-venv/bin/dbt /usr/local/bin/dbt \
    && chown -R airflow:0 /opt/dbt-venv \
    && chmod -R g=u /opt/dbt-venv

ENV PATH="/opt/dbt-venv/bin:${PATH}"
USER airflow
