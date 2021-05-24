FROM quay.io/instrumentisto/rust:1-buster as builder
WORKDIR /usr/src/psi_exporter
COPY . .
#RUN cargo install --path .
RUN cargo build --verbose

FROM quay.io/instrumentisto/rust:1-slim-buster
#RUN apt-get update && apt-get install -y extra-runtime-dependencies && rm -rf /var/lib/apt/lists/*
COPY --from=builder /usr/src/psi_exporter/target/debug/psi_exporter /usr/local/bin/psi_exporter

CMD ["psi_exporter"]

