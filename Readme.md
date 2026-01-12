Ansible Basic Playbooks
=
This project demonstrates basic Ansible playbooks for directory creation and file copy operations on an EC2 instance.
<img width="1328" height="1328" alt="image" src="https://github.com/user-attachments/assets/6eb56107-638e-4f16-b473-b48f14983a56" />

Project Structure
=
 
 🟢 create-dir.yml : Creates a directory with specific permissions

 🟢 copy-paste.yml : Copies a file with owner and permissions
 
 🟢 README.md : Project documentation

Prerequisites
=
✔ Amazon EC2 instance (Amazon Linux)

✔ Ansible installed on the instance

✔ SSH access with root or sudo privileges

Step 1: Verify EC2 Instance
=
Ensure your EC2 instance is running.
<img width="1872" height="869" alt="Screenshot 2026-01-12 090425" src="https://github.com/user-attachments/assets/79a9140f-a341-4d2e-a164-893b62d912cc" />

Step 2: Create Directory Playbook
=
This playbook creates a directory on the target system.

```yaml
---
- name: Create a folder
  hosts: localhost
  become: yes
  tasks:
    - name: Create a new folder
      ansible.builtin.file:
        path: /home/ec2-user/aws
        state: directory
        mode: '700'
```
Run the playbook
=
ansible-playbook create-dir.yml --syntax-check

ansible-playbook create-dir.yml

<img width="1898" height="356" alt="Screenshot 2026-01-12 085422" src="https://github.com/user-attachments/assets/0074284a-f77b-42e9-81f9-6b3ae2aba3af" />

Step 3: Copy File Playbook
=
This playbook copies a file with owner and permissions.


```yaml
---
- name: Copy file with owner and permissions
  hosts: localhost
  become: yes
  tasks:
    - name: Copy file
      ansible.builtin.copy:
        src: /root/newfile.txt
        dest: /home/ec2-user/aws/newfile.txt
        owner: ec2-user
        mode: '0644'
```

Run the playbook
=
ansible-playbook copy-paste.yml --syntax-check

ansible-playbook copy-paste.yml

<img width="1221" height="359" alt="Screenshot 2026-01-12 090341" src="https://github.com/user-attachments/assets/dce1e26f-e263-41b6-8f9c-a40b75ca8107" />

Notes
=
 ✅Inventory warnings appear because implicit localhost is used.

 ✅This is expected for local execution.

Conclusion
=
 These playbooks show simple and clear examples of Ansible file and directory management.

Author

Akash Chavan

