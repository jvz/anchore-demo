# Anchore Demo

This is a basic demo of using Anchore with Jenkins.

## Setup

1. Create directories `config`, `db`, and `jenkins`.
2. Run `docker-compose up -d`
3. Run `docker-compose logs -f jenkins` and wait for the unlock key.
4. Set up Jenkins; no extra plugins need to be installed as the Dockerfile preinstalls them.
5. Add global credentials for anchore-engine (admin:foobar).
6. Create a pipeline:

```groovy
node {
    git 'https://github.com/jvz/image-scan-source.git'
    anchore engineCredentialsId: 'anchore-admin', engineurl: 'http://anchore-engine:8228/v1', name: 'jenkins'
}
```
