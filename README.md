# manual-fed-s1ap-test

### Deploy AGW
```
cd magma/lte/gateway
vagrant up magma
vagrant ssh magma

# inside vagrant vm
cd magma/lte/gateway
make run

# exit from vagrant vm
exit
```

### Deploy Fed Gateway
```
# inside magma vagrant vm
cd magma/lte/gateway/python/integ_tests/federated_tests/docker
docker-compose build
docker-compose up -d
```
