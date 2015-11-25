# Run Cloud9 IDE locally using Vagrant Box

VagrantCloud9Ide helps to setup Cloud9 standalone browser based IDE locally in your computer.

Cloud9 is an open source IDE built with Node.JS on the back-end and JavaScript/HTML5 on the client. Cloud9 balances the power of traditional desktop IDEs with the simplicity and elegance of editors like TextMate and Sublime.

## Prerequisites

1. A computer (Linux/ Mac/ Windows)
2. Internet Browser (Chrome/ Firefox/ Safari/ IE 10+)
3. VirtualBox - It is a powerful x86 and AMD64/Intel64 virtualization software. Installation details are available at https://github.com/w3aran/virtualbox-setup
4. Vagrant - It provides a portable and reproducible development environment using virtual machines. Installation details are available at https://github.com/w3aran/vagrant-setup

## Getting Started

1. Clone git repository: `git clone https://github.com/w3aran/vagrant-cloud9-ide.git`
2. `cd vagrant-cloud9-ide`
3. Start the Vagrant Box: `vagrant up`
4. Open the browser and visit `http://10.0.0.222:8080/` to open the Cloud9 IDE (Username: `vagrant`, Password: `vagrant`)
