# System Restart

The article discusses system restart for Linux server.

## System Restart Required

> When I login to a remote server, the following message prompt:
>
> ```
> ~ $ ssh my-server
> Welcome to Ubuntu 16.04.1 LTS (GNU/Linux 4.4.0-112-generic x86_64)
>
>  * Documentation:  https://help.ubuntu.com
>  * Management:     https://landscape.canonical.com
>  * Support:        https://ubuntu.com/advantage
>
>   Get cloud support with Ubuntu Advantage Cloud Guest:
>     http://www.ubuntu.com/business/services/cloud
>
> 137 packages can be updated.
> 0 updates are security updates.
>
>
> *** System restart required ***
> Last login: Mon Mar 12 10:14:56 2018 from xxx.xxx.xxx.xxx
> ```
>
> In this case, should I _always_ restart the server?

Yes, you should. For most cases, a restart is required when an update to the
Linux kernel has been installed. These updates are usually security updates,
and then only come into effect after a reboot. Updates to normal applications
such as Firefox come into effect after you restart the program. Firefox should
prompt you to do this automatically, but other programs may not, so it's
something to bear in mind.

### Check Packages to Update

You may view the list of packages that require a restart with:

```
more /var/run/reboot-required.pkgs
```

If you've N nodes in your infrastructure, count the packages with:

```
$ for id in apple banana coco; do echo "aws-$id:"; ssh "aws-$id" "cat /var/run/reboot-required.pkgs | wc -l"; done
aws-apple:
70
aws-banana:
60
aws-coco:
2
```
