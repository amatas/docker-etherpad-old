# Etherpad Dockerfile - Ansible version

Builds a Etherpad Docker container image. This image is built using the [Ansible role](https://github.com/idi-ops/ansible-etherpad).

## Building

Build Ansible-provisioned image:
- `docker build --no-cache -t inclusivedesign/etherpad .`

## Testing

The container can be tested as part of a deployment by setting the *CONTAINER_TEST* environment variable to *true*.

The container will exit after the test and the exit code as a result of the run command can be used for further actions. The container can (to a certain extent) self-test using the development mode - see the run examples below - but this doesn't test the real production run-time configuration

### Run Examples

#### Run a container for production

```
docker run \
--name etherpad\
-d \
-p 9001:9001 \
-e ADMIN_PASSWORD=password \
-e ADMIN_USERS={ admin1: admin1pw, admin2: admin2pw } \
-e USERS={ user1: user1pw, user2: user2pw } \
inclusivedesign/etherpad
```

#### Run a container in test mode

```
docker run \
--name etherpadtest \
-t \
--rm \
-e CONTAINER_TEST=true \
inclusivedesign/etherpad
```

