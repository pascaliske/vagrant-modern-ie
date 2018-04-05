## Modern.IE VMs via Vagrant

Based on the virtual machine images released with the [Modern.IE project](http://dev.modern.ie/), this repo makes testing IE easier with help from [Vagrant](http://vagrantup.com).

## Requirements

- [Oracle Virtualbox](https://www.virtualbox.org/)
- [Vagrant](http://vagrantup.com)
- The Vagrant Boxes of [modern.io](https://developer.microsoft.com/en-us/microsoft-edge/tools/vms/) (Select Vagrant as platform)

## Installation

```bash
git clone https://github.com/pascaliske/vagrant-modern-ie.git
```

## Usage

To list the available virtual machines

```bash
vagrant status
```

To start a new virtual machine.

```bash
vagrant up ie10-win7
```
  
To remove all virtual machines (**will reset trial**).

```bash
vagrant destroy
```

To remove a specific virtual machine (**will reset trial**).

```bash
vagrant destroy ie10-win7
```

To start multiple virtual machines at once.

```bash
vagrant up msedge-win10 ie11-win7 ie10-win7 ie9-win7 ie8-win7
```


## Tips

Redirect 127.0.0.1 to the host ip while in the Windows 8+ VM command prompt.
```bash
netsh interface portproxy add v4tov4 8000 10.0.0.3
```

## Available Vagrant Boxes

ModernIE VMs

* msedge-win10
* ie11-win7
* ie11-win8.1
* ie10-win7
* ie10-win8
* ie9-win7
* ie8-win7
* ie7-vista  

System Account Credentials

* Username: IEUser  
* Password: Passw0rd!  
