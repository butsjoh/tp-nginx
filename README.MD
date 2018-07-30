# Why?

The stock nginx full package in debian (>= stretch) does not longer contain the nginx upload module. That's why we needed to build our own nginx package with the upload module included. The result you see here is inspired by the script: https://github.com/a-rodin/nginx-dpkg-build

# How to install?

rsync the files from this repo to your sever, and the install package as suitable user: (order is important)

```
apt-get install libgeoip1 libgd3

dpkg --install nginx-common_1.10.3-1+deb9u1~tp_all.deb
dpkg --install libnginx-mod-http-upload-module_1.10.3-1+deb9u1~tp_amd64.deb
dpkg --install libnginx-mod-http-auth-pam_1.10.3-1+deb9u1~tp_amd64.deb
dpkg --install libnginx-mod-http-dav-ext_1.10.3-1+deb9u1~tp_amd64.deb
dpkg --install libnginx-mod-http-echo_1.10.3-1+deb9u1~tp_amd64.deb
dpkg --install libnginx-mod-http-geoip_1.10.3-1+deb9u1~tp_amd64.deb
dpkg --install libnginx-mod-http-image-filter_1.10.3-1+deb9u1~tp_amd64.deb
dpkg --install libnginx-mod-http-subs-filter_1.10.3-1+deb9u1~tp_amd64.deb
dpkg --install libnginx-mod-http-upstream-fair_1.10.3-1+deb9u1~tp_amd64.deb
dpkg --install libnginx-mod-http-xslt-filter_1.10.3-1+deb9u1~tp_amd64.deb
dpkg --install libnginx-mod-mail_1.10.3-1+deb9u1~tp_amd64.deb
dpkg --install libnginx-mod-stream_1.10.3-1+deb9u1~tp_amd64.deb
dpkg --install nginx-full_1.10.3-1+deb9u1~tp_amd64.deb
```

# How to update?

Just run the above dpkg --install again but then with update packages you build yourself using the nginx-dpkg-build build script.

# How to remove?

Watch out, below will only destroy the package a not the configuration files. If you also want to remove the config files use -P instead.

```
dpkg -r nginx-common_1.10.3-1+deb9u1~tp_all.deb
dpkg -r libnginx-mod-http-upload-module_1.10.3-1+deb9u1~tp_amd64.deb
dpkg -r libnginx-mod-http-auth-pam_1.10.3-1+deb9u1~tp_amd64.deb
dpkg -r libnginx-mod-http-dav-ext_1.10.3-1+deb9u1~tp_amd64.deb
dpkg -r libnginx-mod-http-echo_1.10.3-1+deb9u1~tp_amd64.deb
dpkg -r libnginx-mod-http-geoip_1.10.3-1+deb9u1~tp_amd64.deb
dpkg -r libnginx-mod-http-image-filter_1.10.3-1+deb9u1~tp_amd64.deb
dpkg -r libnginx-mod-http-subs-filter_1.10.3-1+deb9u1~tp_amd64.deb
dpkg -r libnginx-mod-http-upstream-fair_1.10.3-1+deb9u1~tp_amd64.deb
dpkg -r libnginx-mod-http-xslt-filter_1.10.3-1+deb9u1~tp_amd64.deb
dpkg -r libnginx-mod-mail_1.10.3-1+deb9u1~tp_amd64.deb
dpkg -r libnginx-mod-stream_1.10.3-1+deb9u1~tp_amd64.deb
dpkg -r nginx-full_1.10.3-1+deb9u1~tp_amd64.deb
```

# Prevent dist-upgrade from updating the packages

This should prevent updating the package automatically. It is up to you to make sure that it is up to date security wise ...

sudo apt-mark hold nginx-full