# Overview
This project involved the containerization and deployment of a full-stack yolo application using Docker.


# Requirements
- [Ansible](https://docs.docker.com/engine/install/)
- [VirtualBox](https://www.mongodb.com/)


## How to run the app
cd into the 
Use ```vagrant up --provison``` command for the first time

Subsequent running of the project, use ansib
Git workflow used to achieve the task

1. Fork the repository on github.
2. Clone the repository into your local machine.

    ```
    git clone https://github.com/Michael-Otieno/yolo.git 
    ```
3. Change into the project directory.
   ```
   cd yolo
   ```
4. Use ```vagrant up --provison``` command for the first time

5. Subsequent running of the project, use:

```
ansible-playbook playbook.yml
```

