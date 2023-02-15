# What is it?
It's just a configuration I had to use for my ThinkPad after moving from Windows to Ubuntu. I wanted to keep my undervolting without ThrottleStop and to keep my battery tresholds.  
> **Warning**   
If you want to use these commands, just keep in mind that 3rd step will be different for everybody. Don't just copy-paste commands from internet, read about undervolting first!

# Step by step
1. Install tlp and dependencies, also just update everything:
    ```bash
    sudo apt update && sudo apt install -y git tlp tlp-rdw python3-pip libcairo2-dev libgirepository1.0-dev
    sudo snap refresh
    sudo reboot
    ```
2. Install tlpui and undervolt:
    ```bash
    sudo add-apt-repository -y ppa:linuxuprising/apps && sudo apt update
    sudo apt install -y tlpui
    sudo pip install undervolt
    ```
3. Read current undervolt stats, then set your own configuration and start the service:
    ```bash
    sudo undervolt --read
    sudo undervolt --core -115 --cache -115 --gpu -80
    sudo systemctl start undervolt
    ```
4. Clone repository anywhere:
    ```bash
    git clone git@github.com:dominikgomulka/thinkpad_configuration.git
    ```
5. Go into cloned repository catalog and copy configuration files:
    ```bash
    cd thinkpad_configuration
    sudo cp undervolt.service /etc/systemd/system/undervolt.service
    sudo cp undervolt.timer /etc/systemd/system/undervolt.timer
6. Start and enable timer:
    ```bash
    sudo systemctl enable undervolt.timer
    sudo systemctl start undervolt.timer
    ```
