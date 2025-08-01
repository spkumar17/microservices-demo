# Copyright 2024 Google LLC
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#      https://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

# FROM python:3.12.8-slim@sha256:123be5684f39d8476e64f47a5fddf38f5e9d839baff5c023c815ae5bdfae0df7 AS base

# FROM base AS builder

# RUN apt-get -qq update \
#     && apt-get install -y --no-install-recommends g++ \
#     && rm -rf /var/lib/apt/lists/*

# # get packages
# COPY requirements.txt .
# RUN pip install -r requirements.txt

# FROM base
# # Enable unbuffered logging
# ENV PYTHONUNBUFFERED=1

# # get packages
# WORKDIR /shoppingassistantservice

# # Grab packages from builder
# COPY --from=builder /usr/local/lib/python3.12/ /usr/local/lib/python3.12/

# # Add the application
# COPY . .

# # set listen port
# ENV PORT "8080"
# EXPOSE 8080

# ENTRYPOINT ["python", "shoppingassistantservice.py"]


FROM python:3.11-alpine

LABEL service="shoppingassistantservice"

WORKDIR /app

RUN apk add --no-cache build-base linux-headers

COPY requirements.txt .

RUN pip install --no-cache-dir -r requirements.txt

# Copy application code
COPY . .
# Set port and expose
ENV PORT=8080
EXPOSE 8080

# Start the application
ENTRYPOINT ["python", "shoppingassistantservice.py"]

