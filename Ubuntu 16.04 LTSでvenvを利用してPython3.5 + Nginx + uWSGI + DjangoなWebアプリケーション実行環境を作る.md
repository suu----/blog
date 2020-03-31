# Nginx環境とPython3とvenvの構築  
  
[Ubuntu 14.04 LTSでvenvを利用して速攻でPython3.4 + Nginx + uWSGI + FlaskなWebアプリケーション実行環境を作る - Qiita](http://qiita.com/5t111111/items/3f2065699fbc4b43c4a8 "Ubuntu 14.04 LTSでvenvを利用して速攻でPython3.4 + Nginx + uWSGI + FlaskなWebアプリケーション実行環境を作る - Qiita")  
この記事の「Nginxのインストール」と「サンプルアプリケーション用のvenvの作成」を実行してNginxとDjango実行用のvenv環境を構築  
Ubuntu16.04のPython 3.5でvenvの作成は問題なく実行可能なので  
  
```
pyvenv3.5  /var/www/demoapp/venv
```  
  
で作成可能です  
  
# uWSGI環境の構築  
## uWSGIの導入  
uWSGIは  
  
```
sudo pip install uWSGI
```  
で導入します。  
続いて設定ファイルはuWSGIのドキュメントの  
[Setting up Django and your web server with uWSGI and nginx — uWSGI 2.0 documentation](http://uwsgi-docs.readthedocs.io/en/latest/tutorials/Django_and_nginx.html "Setting up Django and your web server with uWSGI and nginx — uWSGI 2.0 documentation")  
「Configuring uWSGI to run with a .ini file」という項目を参考にiniファイルを作成  
## uWSGIをデーモンとして起動する  
uWSGIの公式ドキュメントではupstartで起動することを推奨しているのですが、ubuntu15から導入されたsystemdと干渉してうまく動かない事があるようです。  
[いつか、そのとき、あの場所で。 | [Ubuntu][Systemd][upstart][自分用メモ] ”Start: Unable To Connect To Upstart: Failed To Connect To Socket /Com/Ubuntu/Upstart: Connection Refused”と出力される時の対処方法。](http://kometchtech.blog.fc2.com/blog-entry-1875.html "いつか、そのとき、あの場所で。 | [Ubuntu][Systemd][upstart][自分用メモ] ”Start: Unable To Connect To Upstart: Failed To Connect To Socket /Com/Ubuntu/Upstart: Connection Refused”と出力される時の対処方法。")  
  
そこでsystemdにuWSGIを登録してデーモンとして起動します。  
[How to Set Up Django with Nginx, uWSGI &amp; systemd on Debian/Ubuntu | luxagraf:src](https://luxagraf.net/src/how-set-django-uwsgi-systemd-debian-8 "How to Set Up Django with Nginx, uWSGI &amp; systemd on Debian/Ubuntu | luxagraf:src")  
このページの通りに設定していく。  
  
さらにiniファイルのシンボリックリンクを上記のページに従って配置する。  
  
で、Djangoに何も書き加えて無くてもadminページを開けばアクセスできる  
