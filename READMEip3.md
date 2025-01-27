# Overview
This project involved the containerization and deployment of a full-stack yolo application using Docker.


# Requirements
- [Ansible](https://docs.docker.com/engine/install/)
- [VirtualBox](https://www.mongodb.com/)


## How to run the app

1. Fork the repository on Git Hub.
2. Clone the repository into your local machine.

    ```
    git clone https://github.com/Michael-Otieno/yolo.git 
    ```
3. Change into the project directory.
   ```
   cd yolo
   ```
4. Use the command for the first time running the application
   ```
   vagrant up --provison
   ```

6. Subsequent running of the project, use:

    ```
    ansible-playbook playbook.yml
    ```

