## Week 4 Homework Submission File: Linux Systems Administration

### Step 1: Ensure/Double Check Permissions on Sensitive Files

1. Permissions on `/etc/shadow` should allow only `root` read and write access.

    - Command to inspect permissions: `ls -l /etc/shadow`  shows the permissions are set to `640`.

    - Command to set permissions (if needed): `sudo chmod 600 /etc/shadow`

2. Permissions on `/etc/gshadow` should allow only `root` read and write access.

    - Command to inspect permissions: `ls -l /etc/gshadow`  shows the permissions are set to `640`.

    - Command to set permissions (if needed): `sudo chmod 600 /etc/gshadow`

3. Permissions on `/etc/group` should allow `root` read and write access, and allow everyone else read access only.

    - Command to inspect permissions: `ls -l /ect/group`  shows that the permissions are already set to `644`.

    - Command to set permissions (if needed): `sudo chmod 644 /etc/group`

4. Permissions on `/etc/passwd` should allow `root` read and write access, and allow everyone else read access only.

    - Command to inspect permissions: `ls -l /etc/passwd`  shows that the permissions are already set to `644`.

    - Command to set permissions (if needed): `sudo chmod 644 /etc/group`

### Step 2: Create User Accounts

1. Add user accounts for `sam`, `joe`, `amy`, `sara`, and `admin`.

    - Command to add each user account (include all five users):
        - `sudo useradd sam`
        - `sudo useradd joe`
        - `sudo useradd amy`
        - `sudo useradd sara`
        - `sudo useradd admin`
        - `sudo grep '!' /etc/shadow`  
    ![grep](/Images/1-1.PNG)  

2. Ensure that only the `admin` has general sudo access.

    - Command to add `admin` to the `sudo` group: `sudo usermod -a -G sudo admin`
        - To check if access is granted: `sudo grep sudo /etc/group` or `sudo groups admin`
    ![1-2](/Images/1-2.PNG)

### Step 3: Create User Group and Collaborative Folder

1. Add an `engineers` group to the system.

    - Command to add group: `sudo groupadd engineers`  

2. Add users `sam`, `joe`, `amy`, and `sara` to the managed group.

    - Command to add users to `engineers` group (include all four users):
        - `sudo usermod -a -G engineers sam`
        - `sudo usermod -a -G engineers joe`
        - `sudo usermod -a -G engineers amy`
        - `sudo usermod -a -G engineers sara`  
    ![1-3](/Images/1-3.PNG)

3. Create a shared folder for this group at `/home/engineers`.

    - Command to create the shared folder: `sudo mkdir -p /home/engineers`

4. Change ownership on the new engineers' shared folder to the `engineers` group.

    - Command to change ownership of engineer's shared folder to engineer group: `sudo chmod -R 775 /home/engineers`
    ![1-4](/Images/1-4.PNG)

### Step 4: Lynis Auditing

1. Command to install Lynis: `sudo apt-get install lynis -y

2. Command to see documentation and instructions: `sudo lynis show commands` or `sudo lynis --help`
    ![1-5](/Images/1-5.PNG)  
    ![1-5-1](/Images/1-5-1.PNG)  
    ![1-6](/Images/1-6.PNG)  
    ![1-7](/Images/1-7.PNG)
    ![1-8](/Images/1-8.PNG)  

3. Command to run an audit: `sudo lynis audit system` to run an audit

4. Provide a report from the Lynis output on what can be done to harden the system.

    - Screenshot of report output:
    ![1-9](/Images/1-9.PNG)
    ![1-10](/Images/1-10.PNG)
    - `sudo cat /var/log/lynis.log` - to view the logs.


### Bonus
1. Command to install chkrootkit: `sudo apt-get update`
    ![1-11](/Images/1-11.PNG)
    - `sudo apt install chkrootkit`
    ![1-12](/Images/1-12.PNG)  
    - `sudo chkrootkit -V`  
    ![1-13](/Images/1-13.PNG)  

2. Command to see documentation and instructions: `sudo chkrootkit -h`
    ![1-14](/Images/1-14.PNG)

3. Command to run expert mode: `sudo chkrootkit -x`

4. Provide a report from the chrootkit output on what can be done to harden the system.
    - Screenshot of end of sample output:
    ```
    ! root        20688 pts/0  /bin/sh /usr/sbin/chkrootkit -x
    ! root        21121 pts/0  ./chkutmp
    ! root        21123 pts/0  ps axk tty,ruser,args -o tty,pid,ruser,args
    ! root        21122 pts/0  sh -c ps axk "tty,ruser,args" -o "tty,pid,ruser,args"
    ! root        20687 pts/0  sudo chkrootkit -x
    ! sysadmin     2928 pts/0  bash
    chkutmp: nothing deleted
    not tested
    ```

    ![1-15](/Images/1-15.PNG)

---
© 2020 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.

---
  
## :sunglasses: `Ketan Vithal Patel` :sunglasses:  


### `April 5, 2021 -- UofT Cybersecurity - Boot Camp`
#### :rose::rose:`Jai Shri Swaminarayan`:rose::rose:
```
હરે કૃષ્ણ હરે કૃષ્ણ, કૃષ્ણ કૃષ્ણ હરે હરે |  Hare Krishna Hare Krishna, Krishna Krishna Hare Hare |
હરે રામ હરે રામ, રામ રામ હરે હરે ||   Hare Ram Hare Ram, Ram Ram Hare Hare ||
```
---  
