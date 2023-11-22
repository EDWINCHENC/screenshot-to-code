FROM python:3.12-slim-bullseye

ENV POETRY_VERSION=1.4.1
# 设置 pip 使用中国科技大学的 PyPI 镜像源
ENV PIP_INDEX_URL=https://pypi.mirrors.ustc.edu.cn/simple/

# Install system dependencies
RUN pip install "poetry==$POETRY_VERSION"

# Set work directory
WORKDIR /app

# Copy only requirements to cache them in docker layer
COPY poetry.lock pyproject.toml /app/

# Disable the creation of virtual environments
RUN poetry config virtualenvs.create false

# Install dependencies using the mirror
RUN poetry install -vvv --no-interaction --no-ansi

# Copy the current directory contents into the container at /app
COPY ./ /app/

