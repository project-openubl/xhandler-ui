[![License](https://img.shields.io/github/license/project-openubl/xhandler-ui?logo=apache)](https://www.apache.org/licenses/LICENSE-2.0)
![CI](https://github.com/project-openubl/xhandler-ui/workflows/CI/badge.svg)

[![Project Chat](https://img.shields.io/badge/zulip-join_chat-brightgreen.svg?style=for-the-badge&logo=zulip)](https://projectopenubl.zulipchat.com/)

# xhandler-ui

Web server and UI for managing UBL files for SUNAT, built on top of
[xhandler-rust](https://github.com/project-openubl/xhandler-rust).

## Server

```shell
cargo run --bin server -- server --db-fs-path openubl.sqlite local --storage-local-dir .openubl
```

- The server is running at http://localhost:8080
- You can see Swagger UI at http://localhost:8080/swagger-ui

## Server UI

```shell
npm run dev --prefix ui
```

- The UI running at http://localhost:3000

## Container images

```shell
podman build -f Dockerfile.server -t openubl-server .
podman build -f Dockerfile.ui -t openubl-ui .
```

## License

- [Apache License, Version 2.0](https://www.apache.org/licenses/LICENSE-2.0)
