# Docker Installation Scripts

## Ubuntu Installation Script

Follow these steps to install Docker on Ubuntu:

1. **Update Package List and Install Dependencies**:

    ```sh
    sudo apt-get update
    sudo apt-get install -y apt-transport-https ca-certificates curl software-properties-common
    ```

2. **Add Docker’s Official GPG Key**:

    ```sh
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
    ```

3. **Add Docker APT Repository**:

    ```sh
    sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
    ```

4. **Update Package List Again**:

    ```sh
    sudo apt-get update
    ```

5. **Install Docker**:

    ```sh
    sudo apt-get install -y docker-ce
    ```

6. **Start Docker and Enable on Boot**:

    ```sh
    sudo systemctl start docker
    sudo systemctl enable docker
    ```

7. **Verify Docker Installation**:

    ```sh
    sudo docker --version
    ```

8. **(Optional) Add Your User to the Docker Group** (To run Docker commands without `sudo`):

    ```sh
    sudo usermod -aG docker $USER
    ```

    **Note**: You may need to log out and log back in for this to take effect.

## Amazon Linux 2 Installation Script

Follow these steps to install Docker on Amazon Linux 2:

1. **Update Package List**:

    ```sh
    sudo yum update -y
    ```

2. **Install Docker**:

    ```sh
    sudo amazon-linux-extras install docker -y
    ```

3. **Start Docker and Enable on Boot**:

    ```sh
    sudo service docker start
    sudo systemctl enable docker
    ```

4. **Verify Docker Installation**:

    ```sh
    docker --version
    ```

5. **(Optional) Add Your User to the Docker Group** (To run Docker commands without `sudo`):

    ```sh
    sudo usermod -aG docker $USER
    ```

    **Note**: You may need to log out and log back in for this to take effect.