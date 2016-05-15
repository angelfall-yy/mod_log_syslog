Mod log syslog
================

`mod_log_syslog` is an Apache module to send access logs to syslog or to udp url

Usage
    CustomLog syslog:<facility>:<priority>:ip:port:ident  <format>
    CustomLog syslog:<facility>:<priority>:/dev/log:Apache  <format>

Examples:

    CustomLog syslog:local1:info:127.0.0.1:514:Apache combined

    <VirtualHost *:80>
    CustomLog syslog:local2:debug:/dev/log/Apache common
    </VirtualHost>

Possible facilities: `local[0-7]` and `user`

Possible priorities: `debug`, `info`, `notice`, `warning`, `err`, `crit`, `alert`, and `emerg`

Possible syslog format:

    syslog:user:info:127.0.0.1:514:ident
    syslog:user:info:/dev/log:ident
    syslog:user:info:127.0.0.1::ident
        is short for syslog:user:info:127.0.0.1:514:ident
    syslog:user:info:/dev/log
        is short for syslog:user:info:/dev/log:APACHE
    syslog:user:info:127.0.0.1
        is short for syslog:user:info:127.0.0.1:514:APACHE
    syslog:user::/dev/log:ident
        is short for syslog:user:info:/dev/log:ident
    syslog:user:info::ident
        is short for syslog:user:info:/dev/log:ident
    syslog:user:info
        is short for syslog:user:info:/dev/log:APACHE
    syslog:user
        is short for syslog:user:info:/dev/log:APACHE

Requirements
------------

* Apache 2.2, 2.4

Install
------------

    make install

    # If your apxs is not in the PATH
    make PATH=/usr/sbin:$PATH install

