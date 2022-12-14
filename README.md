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

## WEB GUIでのログイン

http://www.example.local/phpliteadmin/phpliteadmin.php

設定時に指定したパスワードでログインする。

![image](https://user-images.githubusercontent.com/19838489/207498559-26a2bfad-c2d3-4925-91c6-33c79b081d6b.png)


## 初期データベースが作成可能となります。

test.db を作成

![image](https://user-images.githubusercontent.com/19838489/207499170-0d10fec5-56c1-4344-ad86-4b1c4e3caef9.png)

## 空のデータベースが作成されました。

![image](https://user-images.githubusercontent.com/19838489/207499299-60f4d60d-68be-4b42-b2b8-6f59cf77fcbf.png)
