## backend dev specification

### Python environment

- we use pyenv [https://github.com/pyenv/pyenv] to manage environments
    - Check [https://github.com/pyenv/pyenv?tab=readme-ov-file#macos] for pyenv install guide for Mac
    - Install python 3. 12.9 by pyenv
    ```
    pyenv install 3.12.9
    ```
    - Just to let you understand how pyenv works, you can type `which python` in any directory and you should see `/Users/<username>/.pyenv/shims/python`.
     `which <program>` is a system command to tell which program is executed when you type `<program>`. You should see that all `python` command is now through the 'proxy' of pyenv. You can also know what is the real python path behind that proxy by typing `pyenv which python`
    -  Create a new virtual environment called `rag` using 3.12.9 you just installed in pyenv
    ```
    pyenv virtualenv 3.12.9 rag
    ```
    - `cd` to the /backend folder and type `pyenv which python`, you should see something like `/Users/<username>/.pyenv/versions/rag/bin/python` as the file `.python-version` already specify the virtual env to be `rag`
    - notice that pyenv also proxy the `pip` so you can just use `pip` to manage packages for the project. More project specific, you should then 
    ```
    pip install -r requirement.txt
    ```
    - now you are all set

### DevOps (including all other shits like nginx, chroma/ mysql)

Just start your docker and type

```
docker compose up -d
```
then all set.

#### info if you are not familiar with docker compose
- The frontend was already included in `docker-compose.yml` so if we want to work on the frontend we better create another docker compose file. 
- Now `docker-compose.yml` is for backend development as backend is not included in docker (docker restart is slower so you need to wait for long time after you change some of the backend code). Instead, you can lauch the python fastapi application by just using `uvicorn app.main:app --host 0.0.0.0 --port 8080`. 
For the deployment one use `docker-compose.prod.yml` as it already include backend. 
- Why docker is so good is because then you can just type `docker compose up -d` on your server and your server is up, no need to setup python/ react environment anymore on your server. For dev, you also don't need to install vector db, mysql, or nginx on your local machine. So it has minimum impact on your system. For the backend-dev specific copmose file `docker-compose.yml` you are get rid of the frontend and you probably can open on less terminal.


    


    