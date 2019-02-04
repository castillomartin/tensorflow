### Run PowerAI on Polus with bsub
```
bsub -o res.out -W 00:10 -gpu "num=2:mode=exclusive_process:mps=yes" "nvidia-docker run -v ~/test_folder:/home/ --rm powerai:latest /bin/sh -c \"/home/script.sh\""
```
Flag '-v' is for mounting folder from host to container. In example we mount ~/test_folder from the host to /home/ in PowerAI container.  
/bin/sh -c \"/home/script.sh\" - start script.sh in container
### (OLD) Run tensorflow on Polus:
1. Run PowerAI container (Docker)
```
nvidia-docker run --rm -it powerai:yk /bin/bash
```
2. Activate Tensorflow
```
. /opt/DL/tensorflow/bin/tensorflow-activate
```
3. Test MNIST with tensorflow (optional). 
Copy code from:
  https://raw.githubusercontent.com/aymericdamien/TensorFlow-Examples/master/examples/3_NeuralNetworks/neural_network_raw.py
and save it to test.py. 
Testing:
```
python test.py
```

4.1 Obtain id docker
```
docker ps
docker inspect -f   '{{.Id}}' d8e703d7e303
```
4.2 Copy files to docker
```
docker cp file.txt container-id:/home
```

5. docker images

