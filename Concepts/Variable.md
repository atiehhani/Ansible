📌 روش‌های تعریف متغیرها در Ansible
1. درون یک Playbook
```bash
- name: مثال ساده متغیر
  hosts: all
  vars:
    username: atiehhani
    filepath: /home/{{ username }}/important.txt

  tasks:
    - name: ایجاد فایل
      file:
        path: "{{ filepath }}"
        state: touch
```
در این مثال، متغیر username استفاده شده و مسیر فایل از ترکیب متغیر ساخته شده.
2. به صورت فایل جداگانه (vars.yml)
```bash
# vars.yml
my_package: nginx
```
و در Playbook:
```bash
- name: نصب پکیج
  hosts: all
  vars_files:
    - vars.yml

  tasks:
    - name: Install package
      apt:
        name: "{{ my_package }}"
        state: present

```
3. در فایل Inventory (hosts.ini)
   ```bash
   [webservers]
192.168.1.10 ansible_user=ubuntu app_path=/var/www/html
```
و در Playbook:
```bash
- name: نمایش مسیر
  hosts: webservers
  tasks:
    - name: نمایش متغیر
      debug:
        msg: "برنامه در مسیر {{ app_path }} قرار دارد"
```
4. با استفاده از --extra-vars در خط فرمان
   ```bash
   ansible-playbook playbook.yml -e "myvar=value"
```
و در playbook:
```bash
msg: "متغیر از خط فرمان: {{ myvar }}"
```
🧠 نکته مهم در استفاده:
همیشه متغیرها را با {{ }} فراخوانی کنید.
می‌تونی از فیلترهایی مثل upper, lower, default هم استفاده کنی:
```bash
- name: نمایش متغیر
  debug:
    msg: "نام یوزر: {{ username | upper }}"
```

