---
layout: post
title: Creating Virtual Machines with KVM and libvirt
---

## Create Drive

{% highlight bash %}
fallocate -l 4096 /var/lib/libvirt/images/rh1.home.nathwill.net.img
{% endhighlight %}

## CentOS

{% highlight bash %}
virt-install -n rh1.home.nathwill.net -r 512 --os-type=linux \
--os-variant=rhel6 --accelerate --graphics none -v \
-c /var/lib/libvirt/images/CentOS-6.4-x86_64-minimal.iso \
-w bridge:br0 -f /var/lib/libvirt/images/rh1.home.nathwill.net.img
{% endhighlight %}

## Scientific Linux

{% highlight bash %}
virt-install -r 512 --network=bridge:br0 --accelerate \
-n dev.home.nathwill.net -f /var/lib/libvirt/images/dev.home.nathwill.net.img \
--location http://ftp.scientificlinux.org/linux/scientific/6.4/x86_64/os/ \
--hvm --virt-type kvm --graphics none --os-variant=rhel6 --os-type=linux \
--extra-args console=ttyS0
{% endhighlight %}
