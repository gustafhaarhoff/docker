<b>Usefull docker recipes </b>

Most images available on dockerhub under the cotech account.

<b>Examples:</b>
```
- cotech/ubuntu-18-04-ssh-dev
- cotech/ubuntu-20-04-ssh-dev
- cotech/toolchain-ionic-3.2
- cotech/toolchain-esp32-ftm
```

<b>Docker run example:</b>
```bash
$ docker run --rm -it -p 22:22 cotech/toolchain-esp32-ftm

# ssh server on port 22, user: dev, password: 123
```



