### 1. Initiate virtualbox using ```vagrant init```

- ```vagrant init``` creates a Vagrantfile which defines vm

## 2. Define ```ansible.cfg``` details

- Create ansible.cfg file at the root of the directory and define:
    - ```inventory``` which points to the hosts file
    - ```remote_user``` which is vagrant for this case
    - ```private_key_file``` which points to the virtualbox private_key
    - ```host_key_checking``` to be false
    - ```roles_path``` the path to the defined roles

## 3. Create ```hosts``` file

- Create ```hosts``` file and define ansible port and the hosts

## 4. Define ```playbook.yml``` file

- Define the name of the playbook
- Define list of hosts to use
- Make user a ```sudo``` user
- Install required packages
- Define roles. The first role ```install-docker``` because we require docker to run the application
- The second role is ```clone-repo```: which clones the repo and changes into the directory and runs command ```docker compose up```

