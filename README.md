# tools

## Initial set up

### Local machine set up

1. Install [Tailscale](https://tailscale.com/).

### Remote (cloud) machine set up

1. Copy your public SSH key to the remote machine (replace `YOUR_KERBEROS` with your MIT Kerberos, and `IP_ADDRESS_OF_REMOTE_MACHINE` with the IP provided to you on Canvas:
    ```bash
    ssh-copy-id -i ~/.ssh/id_ed25519.pub YOUR_KERBEROS@IP_ADDRESS_OF_REMOTE_MACHINE
    ```
2. Connect to the remote machine with `ssh`:
    ```bash
    ssh YOUR_KERBEROS@IP_ADDRESS_OF_REMOTE_MACHINE
    ```
3. Install essential packages:
    ```bash
    sudo apt update
    sudo apt install \
        ca-certificates \
        curl \
        wget \
        git \
        rsync \
        jq \
        unzip \
        zip \
        xz-utils \
        tar \
        tree \
        less \
        file \
        bash-completion \
        tmux \
        htop \
        ncdu \
        build-essential \
        pkg-config \
        cmake \
        git
    ```
4. Run the commands found [here](https://dl.tailscale.com/stable/#ubuntu-noble) to install Tailscale on your remote machine.
5. Set up `tmux` configuration:
```

## Install Redirect3

1. Clone https://github.com/mattfeng/redirect3 into your home directory.
2. Start a `tmux` session:
    ```bash
    tmux new -s redirect3
    ```
3. `cd` into the cloned repository, and run the following commands:
    ```bash
    sudo apt install golang-go
    go mod tidy
    go build -o redirect3 .
    ./redirect3 -host 0.0.0.0 -port 8080 -db ./links.db -password 'replace-with-a-long-password'
    ```
4. Navigate to http://YOUR_KERBEROS:8080/ to see if the app is working.
5. Set up a custom search engine in Google Chrome by going to `chrome://settings/searchEngines`.
