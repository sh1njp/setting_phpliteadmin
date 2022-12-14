# Ubuntu22.04で、phpliteadminをセットアップする。

## パッケージUpdate、リスタート確認を無視
```
apt update
apt upgrade -y
apt purge needrestart -y
```
## sqlite3, nkf, phpliteadminの導入（apache2.4/php8.1なども一緒に導入される）
```
apt install unzip sqlite3 nkf phpliteadmin -y
```
## phpliteadminの日本語ローカライズファイルを入手＆格納
```
cd ~
wget https://bitbucket.org/phpliteadmin/public/downloads/phpliteAdmin_lang_ja_1-9-8.zip
unzip phpliteAdmin_lang_ja_1-9-8.zip
sudo mv lang_ja.php /usr/share/phpliteadmin/languages/
```
## phpliteadminの設定
- パスワードを設定
- 日本語化
```
sudo cp -p /etc/phpliteadmin.config.php /etc/phpliteadmin.config.php.org
vi /etc/phpliteadmin.config.php
```
以下差分
```diff
12c12
< //$password = 'admin';
---
> $password = 'password-wo-ireru';
20c20
< //$language = 'en';
---
> $language = 'ja';
```
