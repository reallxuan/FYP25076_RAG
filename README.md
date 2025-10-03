## backend dev specification

### Python environment

- we use pyenv [https://github.com/pyenv/pyenv] to manage environments
    - Check [https://github.com/pyenv/pyenv?tab=readme-ov-file#macos] for pyenv install guide for Mac
    - Install python 3.12.9 by pyenv
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
    pip install -r requirements.txt
    ```
    - now you are all set

### DevOps (including all other shits like nginx, chroma/ mysql)

Just start your docker and type

```
docker compose up -d
```

    


    