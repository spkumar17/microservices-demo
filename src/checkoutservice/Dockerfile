# Copyright 2020 Google LLC
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#      http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

# FROM golang:1.23.4-alpine@sha256:c23339199a08b0e12032856908589a6d41a0dab141b8b3b21f156fc571a3f1d3 AS builder
# ARG TARGETOS
# ARG TARGETARCH
# WORKDIR /src

# # restore dependencies
# COPY go.mod go.sum ./
# RUN go mod download

# COPY . .

# # Skaffold passes in debug-oriented compiler flags
# ARG SKAFFOLD_GO_GCFLAGS
# RUN GOOS=${TARGETOS} GOARCH=${TARGETARCH} CGO_ENABLED=0 go build -gcflags="${SKAFFOLD_GO_GCFLAGS}" -o /checkoutservice .

# FROM scratch

# WORKDIR /src
# COPY --from=builder /checkoutservice /src/checkoutservice

# # Definition of this variable is used by 'skaffold debug' to identify a golang binary.
# # Default behavior - a failure prints a stack trace for the current goroutine.
# # See https://golang.org/pkg/runtime/
# ENV GOTRACEBACK=single

# EXPOSE 5050
# ENTRYPOINT ["/src/checkoutservice"]


FROM golang:1.23.4-alpine 

# Set the working directory inside the container.
WORKDIR /app

COPY checkoutservice_build checkoutservice

RUN chmod +x ./checkoutservice

ENV GOTRACEBACK=single

# Expose the port your application listens on.
EXPOSE 5050

# Define the command to run when the container starts.
ENTRYPOINT ["./checkoutservice"]