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

### Deploy Orc8r
```
#on host
cd magma/orc8r/cloud/docker
./build.py -a
./run.py

# return to agw folder
cd magma/lte/gateway
# register gateways
fab --fabfile=dev_tools.py register_federated_vm
fab --fabfile=dev_tools.py register_feg_gw
```

### Deploy Test VM
```
cd magma/lte/gateway
vagrant up magma_test
vagrant ssh magma_test

# inside vagrant vm
cd magma/lte/gateway/python
make

# exit from vagrant vm
exit
```
### Deploy Traffic VM
```
cd magma/lte/gateway
vagrant up magma_trfserver
```

### Run test manually
We will run fed attach-detach test
```
cd magma/lte/gateway
vagrant ssh magma_test

# inside vagrant vm
cd magma/lte/gateway/python/integ_tests
make fed_integ_test TESTS=federated_tests/s1aptests/test_attach_detach.py

# once the test is done, you can exit the vagrant vm
exit
```
