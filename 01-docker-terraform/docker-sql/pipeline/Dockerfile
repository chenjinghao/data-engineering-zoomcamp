FROM python:3.13

COPY --from=ghcr.io/astral-sh/uv:latest /uv /bin/

WORKDIR /code
ENV PATH="/code/.venv/bin:$PATH"

COPY pyproject.toml .python-version /

RUN uv sync

RUN pip install pandas pyarrow duckdb sqlalchemy psycopg2-binary

RUN python --version

RUN pip --version

COPY ingest_data.py .

ENTRYPOINT [ "python", "ingest_data.py" ]