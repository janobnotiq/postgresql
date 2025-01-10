# PostgreSQL Ma'lumotlar Bazasini Boshqarish uchun Terminal Buyruqlari

## 1. **PostgreSQL xizmatini boshqarish**
```bash
# Xizmatni ishga tushirish
sudo systemctl start postgresql

# Xizmatni qayta ishga tushirish
sudo systemctl restart postgresql

# Xizmatni to'xtatish
sudo systemctl stop postgresql

# Xizmatning holatini tekshirish
sudo systemctl status postgresql
```

## 2. **PostgreSQL konsoliga (psql) ulanish**
```bash
# postgres foydalanuvchisi sifatida ulanish
sudo -i -u postgres
psql

# Ma'lum bir foydalanuvchi nomidan ulanish
psql -U username -d databasename -W

# O'chish
\q
```

## 3. **Foydalanuvchi va huquqlar boshqaruvi**
```bash
# Yangi foydalanuvchi yaratish
CREATE USER username WITH PASSWORD 'password';

# Foydalanuvchini superuser qilish
ALTER USER username WITH SUPERUSER;

# Foydalanuvchini olib tashlash
DROP USER username;

# Foydalanuvchi huquqlarini ko‘rish
\du
```

## 4. **Ma'lumotlar bazasini boshqarish**
```bash
# Yangi ma'lumotlar bazasi yaratish
CREATE DATABASE databasename;

# Ma'lumotlar bazasini o'chirish
DROP DATABASE databasename;

# Ma'lumotlar bazalarini ro‘yxatlash
\l

# Ma'lumotlar bazasiga ulanish
\c databasename
```

## 5. **Jadvallarni boshqarish**
```bash
# Jadval yaratish
CREATE TABLE tablename (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    age INT
);

# Jadvalni ko'rish
\d tablename

# Jadvallarni ro‘yxatlash
\dt

# Jadvalni o'chirish
DROP TABLE tablename;

# Jadvalning faqat tuzilmasini chiqarish
\d+ tablename
```

## 6. **Ma'lumotlarni boshqarish**
```bash
# Ma'lumot qo'shish
INSERT INTO tablename (name, age) VALUES ('Ali', 25);

# Ma'lumotlarni ko'rish
SELECT * FROM tablename;

# Ma'lumotlarni yangilash
UPDATE tablename SET age = 30 WHERE name = 'Ali';

# Ma'lumotni o'chirish
DELETE FROM tablename WHERE name = 'Ali';
```

## 7. **Zaxira va tiklash**
```bash
# Zaxira qilish (backup)
pg_dump databasename > backup.sql

# Zaxirani tiklash
psql -U username -d databasename < backup.sql

# To'liq tizimni zaxira qilish
pg_dumpall > full_backup.sql

# To'liq tizimni tiklash
psql -U username < full_backup.sql
```

## 8. **Konfiguratsiya va port tekshiruvi**
```bash
# PostgreSQL ishlayotgan portni topish
sudo netstat -plnt | grep postgres

# Konfiguratsiya fayllarini tekshirish
SHOW config_file;
SHOW hba_file;

# Server sozlamalarini ko'rish
SHOW ALL;
```

## 9. **Indekslash va optimizatsiya**
```bash
# Jadvalga indeks qo'shish
CREATE INDEX index_name ON tablename (column_name);

# Indeksni o'chirish
DROP INDEX index_name;

# Jadvalni optimallashtirish
VACUUM tablename;

# Indekslash va statistikani yangilash
ANALYZE;
```

## 10. **Foydali qisqacha buyruqlar (psql ichida)**
```bash
# Jadval yoki ob'ekt haqida batafsil ma'lumot
\d+ tablename

# Hozirgi bazaga ulangan foydalanuvchilar ro'yxati
\du

# Yaratilgan rollar ro'yxati
\dg

# Jadvaldagi 10 ta yozuvni chiqarish
SELECT * FROM tablename LIMIT 10;

# Ma'lumotlar bazasida qancha joy ishlatilganini ko'rish
\l+

# PostgreSQL versiyasini bilish
SELECT version();
```

Bu buyruqlar yordamida PostgreSQL ma'lumotlar bazasini terminal orqali samarali boshqarishingiz mumkin! Agar qo'shimcha yordam kerak bo'lsa, menga xabar qiling. 😊

