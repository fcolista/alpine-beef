# alpine-beef

This Docker image allow to run the latest BeEF on Alpine Linux. 

You can start the alpine-beef container with the commands:

```
docker run -t fcolista/alpine-beef
```

This container exposes port TCP/3000: once you've run the container, look at the ip address BeEF is binding to:

Example:

``` 
[14:16:25][*] Bind socket [imapeudora1] listening on [0.0.0.0:2000].
[14:16:26][*] Browser Exploitation Framework (BeEF) 0.4.7.0-alpha
[14:16:26]    |   Twit: @beefproject
[14:16:26]    |   Site: http://beefproject.com
[14:16:26]    |   Blog: http://blog.beefproject.com
[14:16:26]    |_  Wiki: https://github.com/beefproject/beef/wiki
[14:16:26][*] Project Creator: Wade Alcorn (@WadeAlcorn)
[14:16:27][*] BeEF is loading. Wait a few seconds...
[14:16:36][*] 12 extensions enabled.
[14:16:36][*] 259 modules enabled.
[14:16:36][*] 2 network interfaces were detected.
[14:16:36][+] running on network interface: 127.0.0.1
[14:16:36]    |   Hook URL: http://127.0.0.1:3000/hook.js
[14:16:36]    |_  UI URL:   http://127.0.0.1:3000/ui/panel
[14:16:36][+] running on network interface: 172.17.0.3
[14:16:36]    |   Hook URL: http://172.17.0.3:3000/hook.js
[14:16:36]    |_  UI URL:   http://172.17.0.3:3000/ui/panel
[14:16:36][*] RESTful API key: c1dc74128c430e74572ebef2cfed4a7388141ffe
[14:16:36][*] HTTP Proxy: http://127.0.0.1:6789
[14:16:36][*] BeEF server started (press control+c to stop)
````

Then, open your browser and point to http://$IPADDRESS:3000/ui/panel

Username: beef
Password: beef

##Note:

If you are running with a grsec kernel, you should disable those features:
```
chroot_deny_chmod
chroot_deny_mknod
```
On an Alpine host, you can do it by decommenting from ```/etc/conf.d/docker```:

```
disable_grsec="chroot_deny_chmod chroot_deny_mknod"
```
and then restart docker:
```
rc-service docker restart
```

Enjoy, Francesco

