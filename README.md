# switch-runner-mirror

A GitHub Action that switches the package manager mirror to a reliable,
high-throughput mirror on Linux runners.

## What it does

Replaces the default Ubuntu archive mirrors in `/etc/apt/apt-mirrors.txt`,
`/etc/apt/sources.list.d/ubuntu.sources`, and `/etc/apt/sources.list` with the
Fastly CDN mirror (`http://mirrors.edge.kernel.org/ubuntu/`).

This prevents intermittent HTTP 503 errors on AWS regional mirrors and
connection timeouts on Canonical origin servers (`security.ubuntu.com` and
`archive.ubuntu.com`).

## Usage

Add this step before any `apt update` or `apt install` in your workflow:

```yaml
steps:
  - uses: compact-orb/switch-runner-mirror@v1

  - name: Install Dependencies
    run: |
      sudo apt update
      sudo apt install -y my-package
```
