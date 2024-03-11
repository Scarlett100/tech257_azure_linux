1. log into virtual machine 
2. run the command: 
    sudo waagent -deprovision+user 
3. type yes

4. if you do an ls you will see there is nothing
5. log out
6. do account show on command line
7. az login
8. to stop vm run: az vm deallocate --resource-group tech257 --name tech257-morgan-fresh-vm-again
    az vm deallocate --resource-group <yourResourceGroup> --name <yourVMName>

9. must mark vm as geralised before you can make an image:
 az vm generalize --tech257<yourResourceGroup> --name tech257-morgan-fresh-vm-again
 az vm generalize --resource-group <yourResourceGroup> --name <yourVMName>

10. go to vm on azure interface, go to overview, click capture, 
    the option to change is azure compute gallery: no,capture only a managed gallery (change to this)

    call it name_of_vm_first image