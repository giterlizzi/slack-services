# slack-service
**Slackware Linux Service "wrapper"**

##Installation

Edit the ``/etc/rc.d/rc.local`` and remove all user-services and add this code:

```
if [ -x /etc/rc.d/rc.service ]; then
  /etc/rc.d/rc.service status
  /etc/rc.d/rc.service start &
fi
```

And finally add execution permission:

```
# chmod + /etc/rc.d/rc.service
```

##Add a service

Edit ``SERVICES`` variable present in ``/etc/slack-services.conf`` with the name of user-service present in ``/etc/rc.d`` directory, without the ``rc.`` prefix . Eg:

```
SERVICES="vboxdrv memacached postgresql"
```

##The rc.service script

***Display the enabled service on your machine***

```
# sh /etc/rc.d/rc.service status
Services enabled on darkstar:

  [x] zram
  [x] memcached
  [x] postgresql
  [ ] vdenetwork
  [x] libvirt
  [x] vboxdrv
  [x] vboxballoonctrl-service
  [x] vboxautostart-service
  [ ] vboxweb-service
```

***Display the available service in your machine***

```
# sh /etc/rc.d/rc.service list  
Available services on darkstar:

        zram
        memcached
        postgresql
        vdenetwork
        libvirt
        vboxdrv
        vboxballoonctrl-service
        vboxautostart-service
        vboxweb-service
```

***Enable a service***

```
# /etc/rc.d/rc.service enable vdenetwork
```

***Disable the service***

```
# /etc/rc.d/rc.service disable vdenetwork
```

***Start all services***

```
# /etc/rc.d/rc.service start
Starting zram:  /etc/rc.d/rc.zram start
Starting memcached:  /etc/rc.d/rc.memcached start
Starting postgresql:  /etc/rc.d/rc.postgresql start
Starting libvirt:  /etc/rc.d/rc.libvirt start
Starting vboxdrv:  /etc/rc.d/rc.vboxdrv start
Starting vboxballoonctrl-service:  /etc/rc.d/rc.vboxballoonctrl-service start
Starting vboxautostart-service:  /etc/rc.d/rc.vboxautostart-service start
```

***Stop all services***

```
# /etc/rc.d/rc.service stop
Stopping zram:  /etc/rc.d/rc.zram stop
Stopping memcached:  /etc/rc.d/rc.memcached stop
Stopping postgresql:  /etc/rc.d/rc.postgresql stop
Stopping libvirt:  /etc/rc.d/rc.libvirt stop
Stopping vboxdrv:  /etc/rc.d/rc.vboxdrv stop
Stopping vboxballoonctrl-service:  /etc/rc.d/rc.vboxballoonctrl-service stop
Stopping vboxautostart-service:  /etc/rc.d/rc.vboxautostart-service stop
```
