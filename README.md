## SSL/TLS certification olish.

1-qadam - Certbotni o'rnatish
```angular2html
sudo snap install core; sudo snap refresh core
```
- Agar certbotning boshqa versiyalari bor bo'lsa  
```angular2html
sudo apt remove certbot
```
- Certbot o'rnatish kerak 
```angular2html
sudo snap install --classic certbot
```
- Siz certbot buyrug'ini tezkor o'rnatish katalogidan o'z yo'lingizga bog'lashingiz mumkin, shuning uchun uni faqat certbot yozish orqali ishga tushirishingiz mumkin.

```angular2html
sudo ln -s /snap/bin/certbot /usr/bin/certbot
```
----------------
## 2 - qadam | HTTPSga ruxsat berish hafsizlik tomondan

```angular2html
sudo ufw status
```

HTTPSga ruxsat berishimiz kerak va HTTP dan ruxsatni olishimiz kerak

```angular2html
sudo ufw allow 'Nginx Full'
sudo ufw delete allow 'Nginx HTTP'
```

Statusni ko'rish

```angular2html
sudo ufw status
```
-----------------
3 - Qadam | SSL sertifikatni olish

```angular2html
sudo certbot --nginx -d sizningdomainginiz.com
```
- Natija: 
```yml
IMPORTANT NOTES:
Successfully received certificate.
Certificate is saved at: /etc/letsencrypt/live/your_domain/fullchain.pem
Key is saved at: /etc/letsencrypt/live/your_domain/privkey.pem
This certificate expires on 2022-06-01.
These files will be updated when the certificate renews.
Certbot has set up a scheduled task to automatically renew this certificate in the background.

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
If you like Certbot, please consider supporting our work by:
* Donating to ISRG / Let's Encrypt: https://letsencrypt.org/donate
* Donating to EFF: https://eff.org/donate-le
```
----------------
## 4 - Qadam | yangilanishlarni automatik tekshirish.
Shifrlash sertifikatlari faqat to'qson kun davomida amal qiladi. Bu foydalanuvchilarni sertifikatni yangilash jarayonini avtomatlashtirishga undashdir. Biz o'rnatgan certbot paketi kuniga ikki marta ishlaydigan tizim taymerini qo'shish va o'ttiz kun ichida muddati tugaydigan har qanday sertifikatni avtomatik ravishda yangilash orqali biz uchun bu haqda g'amxo'rlik qiladi.

Taymer holatini systemctl bilan so'rashingiz mumkin:

```angular2html
sudo systemctl status snap.certbot.renew.service
```

Yangilash jarayonini sinab ko'rish uchun siz certbot bilan quruq ishga tushirishingiz mumkin:

```angular2html
sudo certbot renew --dry-run
```
## Va biz SSL Sertificatini oldilk.
