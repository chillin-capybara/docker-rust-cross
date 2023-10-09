FROM rust:latest as base

# add the cross-compiling toolchains
RUN rustup target add x86_64-unknown-linux-gnu
RUN rustup toolchain install stable-x86_64-unknown-linux-gnu

RUN rustup target add aarch64-unknown-linux-gnu
RUN rustup toolchain install stable-aarch64-unknown-linux-gnu

RUN rustup target add aarch64-apple-darwin
RUN rustup toolchain install stable-aarch64-apple-darwin

RUN rustup target add x86_64-apple-darwin
RUN rustup toolchain install stable-x86_64-apple-darwin

RUN rustup target add x86_64-pc-windows-gnu
RUN rustup toolchain install stable-x86_64-pc-windows-gnu

# install the cross-linkers
RUN apt-get update && apt-get install -y --no-install-recommends \
    make \
    gcc-x86-64-linux-gnu \
    gcc-aarch64-linux-gnu \
    mingw-w64


# set the environment variables for the cross-compiling toolchains
ENV CARGO_TARGET_X86_64_UNKNOWN_LINUX_GNU_LINKER=x86_64-linux-gnu-gcc
ENV CARGO_TARGET_AARCH64_UNKNOWN_LINUX_GNU_LINKER=aarch64-linux-gnu-gcc

# TODO: add all darwin architectures
# TODO: app support for musl linux?