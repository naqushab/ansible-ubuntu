# ansible-ubuntu

[![Build Status][github-actions-image]][github-actions-url]

This project is used to setup my Ubuntu machine :computer:

## Prerequisites

You have to install Ansible:

```
sudo apt-add-repository -y ppa:ansible/ansible && \
sudo apt-get update && \
sudo apt-get install -y ansible
```

Check your folder: `~/.ansible/`
You must be the owner of this folder, specially if you already used `sudo ansible-playbook`.

## Test with Docker

Build the Docker image

```
docker build -t ansible:test .
```

Start the container with the code inside:

```
docker run --rm -it ansible:test bash
```

Start the container, with volume, so you can change the code directly:

```
docker run --rm -it -v "$PWD":/home/jhipster/app/ ansible:test bash
```

## Roles

### Tools: curl, vim, wget

To install curl, vim and wget :

```
ansible-playbook -v playbooks/tools.yml -K
```

### Git

To install Git :

```
ansible-playbook -v playbooks/git.yml -K
```

To install Git and configure with your information :

```
ansible-playbook -v playbooks/git.yml -K -e 'git_username="Firstname Lastname"' -e git_email=yourmail
```

### zsh, oh-my-zsh, fonts-powerline, spaceship-prompt, zsh-autosuggestions

To install zsh, [oh-my-zsh](https://github.com/robbyrussell/oh-my-zsh), fonts-powerline,[spaceship-prompt](https://github.com/denysdovhan/spaceship-prompt) and [zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions)

```
ansible-playbook -v playbooks/zsh.yml -K
```

Launch this playbook to create a `.custom` file at your home, then customize it:

```
ansible-playbook -v playbooks/custom.yml
```

### OpenJDK 8

To install OpenJDK 8 :

```
ansible-playbook -v playbooks/openjdk8.yml -K
```

### Maven

To install Maven :

```
ansible-playbook -v playbooks/maven.yml -K
```

To install a specific version of Maven :

```
ansible-playbook -v playbooks/maven.yml -K -e maven_version=3.6.3
```

### NodeJS

To install [NodeJS](https://nodejs.org/en/) :

```
ansible-playbook -v playbooks/node.yml -K
```

To install a specific version of NodeJS :

```
ansible-playbook -v playbooks/node.yml -K -e node_version=12.16.1
```

### Yarn

To install [Yarn](https://yarnpkg.com/lang/en/) :

```
ansible-playbook -v playbooks/yarn.yml -K
```

### tilix

To install [tilix](https://github.com/gnunn1/tilix) :

```
ansible-playbook -v playbooks/tilix.yml -K
```

Don't forget to change default cmd to `zsh`

### Docker

To install [Docker](https://github.com/moby/moby) :

```
ansible-playbook -v playbooks/docker.yml -K
```

### Docker Compose

To install [Docker Compose](https://github.com/docker/compose) :

```
ansible-playbook -v playbooks/dockercompose.yml -K
```

### Fusuma for gesture

To install [fusuma](https://github.com/iberianpig/fusuma) :

```
ansible-playbook -v playbooks/fusuma.yml -K
```

Don't forget to add fusuma to startup application.

[github-actions-image]: https://github.com/pascalgrimaud/ansible-ubuntu/workflows/Build/badge.svg
[github-actions-url]: https://github.com/pascalgrimaud/ansible-ubuntu/actions?query=workflow%3ABuild
