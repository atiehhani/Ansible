## ✅ 1. لیست (List / Array)
لیست یعنی چند مقدار پشت‌سرهم:
```bash
vars:
  packages:
    - nginx
    - curl
    - vim
```
و استفاده از آن:
```bash
tasks:
  - name: نصب چند پکیج
    apt:
      name: "{{ item }}"
      state: present
    loop: "{{ packages }}"
```
loop باعث می‌شه پکیج‌ها یکی‌یکی نصب بشن.
## ✅ 2. دیکشنری (Dictionary / Map)
دیکشنری یعنی ساختار کلید: مقدار
```bash
vars:
  user_info:
    name: atiehhani
    home: /home/atiehhani
    shell: /bin/bash
```
و استفاده:
```bash
tasks:
  - name: ساخت یوزر با استفاده از دیکشنری
    user:
      name: "{{ user_info.name }}"
      home: "{{ user_info.home }}"
      shell: "{{ user_info.shell }}"
```
## ✅ 3. متغیرهای شرطی با when
```bash
vars:
  os_family: Debian

tasks:
  - name: نصب پکیج فقط در دبیان
    apt:
      name: nginx
      state: present
    when: os_family == "Debian"
```
اگر os_family دبیان باشد، پکیج نصب می‌شود.
## ✅ 4. فیلتر روی متغیرها (Filters)
```bash
vars:
  user_name: atiehhani

tasks:
  - name: چاپ حروف بزرگ
    debug:
      msg: "{{ user_name | upper }}"
```
فیلترهای پرکاربرد:
| فیلتر              | کارایی           |
| ------------------ | ---------------- |
| `lower`            | کوچک کردن        |
| `upper`            | بزرگ کردن        |
| `default('مقدار')` | مقدار پیش‌فرض    |
| `length`           | تعداد عناصر لیست |

## ✅ 5. متغیرهای ثبت‌شده (register)
```bash
tasks:
  - name: اجرای دستور date
    command: date
    register: date_output

  - name: نمایش نتیجه
    debug:
      msg: "تاریخ سیستم: {{ date_output.stdout }}"
```
خروجی دستور ذخیره می‌شود و بعداً استفاده می‌کنی.



