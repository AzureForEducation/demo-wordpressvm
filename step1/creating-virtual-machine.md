# Creating a new Virtual Machine (VM)

As mentioned earlier, there are a plenty of resources we're going to build in this demo and the whole thing is going to live in a single Linux-based (Ubuntu) VM. This way, we're going to start this process by creating our virtual machine host through the Azure Portal.

## Creating a new VM

1) In the Azure Portal, select the resource group we created in a earlier demo. Once inside of it, on the top menu, click on "+ Add" button. By doing this, the portal is going to show you a new window with several services suggestion. On the "Search" field type "Virtual Machine" and select the option "Ubuntu 16.04 LTS", as shown by picture below.

    <img src="https://raw.githubusercontent.com/AzureForEducation/demo-wordpressvm/master/images/wordpress-new-vm.PNG" width="600" />

2) By selecting the "Ubuntu 16.04 LTS" option, you'll be directed to a new page which describe the Virtual Machines services and such. Just click in "Create".

3) By clicking in "Create" you will dispach out the VM creation flow. There are some information to be fullfilled here, as you can see through the image below. Please, full that up with the appropriate information.

    <img src="https://raw.githubusercontent.com/AzureForEducation/demo-wordpressvm/master/images/wordpress-vm-create-form.PNG" width="600" />

    To a simple VM's configuration (which is our case here), that all we need. However, is import to point out that you can configure different aspects of that VM like VM's size, dinamic or static IP, storage, etc. Let's click out on "Review and create" to go to the next step.

4) As next step, just review the information you are about to send to Azure. If everything is correct, click on "Create". If something is not the way it should be, just update the information and then, click in "Review and create" once again.

    <img src="https://raw.githubusercontent.com/AzureForEducation/demo-wordpressvm/master/images/wordpress-vm-create-review.PNG" width="600">

5) The VM creation can take from 2 to 5 minutes. Wait a little bit and then, go to the resource group where you've deployed the VM. You should be able to see it there, as showed by the image below.

    <img src="https://raw.githubusercontent.com/AzureForEducation/demo-wordpressvm/master/images/wordpress-vm-running.PNG" width="600">

## Accessing the Virtual Machine

Now, to complete this first great step, one thing left: test out the VM accessibility through SSH (remember: we're on Linux World). You can do that either by using Windows Subsystem for Linux or Putty.

    > To see how to connect to a Linux-based VM using Putty, please, follow up [this link](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/ssh-from-windows#connect-to-your-vm).

    > To enable Linux subsystem in your Windows machine, just follow up the instructions enclosed in [this document](https://docs.microsoft.com/en-us/windows/wsl/install-win10).

Linux subsystem automatically brings SSH utility with it so I'm going to use it. To get there, I typed the following replacing "your-VM-public-ip" peace by the VM's public IP, available on the VM's blade on the Azure Portal.

```shell
ssh fabricio@{your-VM-public-ip}
```

I've added that host on my local list of accepted addresses and informed the password. Then, I 've received the access to my VM on Azure, as you can see below.

<img src="https://raw.githubusercontent.com/AzureForEducation/demo-wordpressvm/master/images/wordpress-vm-linux-access.PNG" width="400">

That's it. We now have finished the first step. Let's go to the next one and install and configure both MySQL and Apache services.