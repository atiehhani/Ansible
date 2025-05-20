✅ مراحل نصب Ansible با Python (pip)
🔹 1. نصب پیش‌نیازها
```bash
sudo apt update
sudo apt install -y python3 python3-pip
```
🔹 2. نصب Ansible با pip
```bash
pip3 install --user ansible
```
 گزینه --user باعث می‌شود ansible در مسیر ~/.local/bin/ansible نصب شود و به sudo نیاز نداشته باشی.
 🧪 تست نصب
 ```bash
~/.local/bin/ansible --version
```
یا اگر در PATH نیست، مسیر رو موقتاً اضافه کن:
```bash
export PATH=$PATH:~/.local/bin
```
```bash
ansible --version
```
🔁 نکته پیشنهادی: استفاده از virtualenv
اگر می‌خواهی انسیبل را بدون تأثیر روی سیستم اصلی نصب کنی:
```bash
sudo apt install -y python3-venv
python3 -m venv ansible-env
source ansible-env/bin/activate
pip install ansible
ansible --version
```
