# mvp infrastructure

## A manual startup for application

### Build test container for playbook

```bash
docker build -t ansible_test .
```

### Start docker container for playbook

```bash
docker run -p 5000:5000 -d -ti --name test_ans_1 ansible_test
```

### Run the test playbook

```bash
ansible-playbook playbook.yml -i inventory
```

### Test 

Web application should be accessible on port `5000`. The `Welcome! sign should be visible òn web server.

`http://127.0.0.1:5000/`

## Some helpful commands

### To enter container

```bash
docker exec -it test_ans_1 bash 
```

### Use the following commands to stop and remove container

```bash
docker stop test_ans_1
docker rm test_ans_1 
```

### Get information for docker container

```bash
docker inspect test_ans_1
```

### Container IP

```bash
docker inspect --format='{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' test_ans_1
```