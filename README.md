EADME.md
# Ansible Role: squid
A simple yet useful role to configure squid server.  A working proxy can be set up with minimal effort.  This roles tries to balance the sensible [defaults](http://wiki.squid-cache.org/SquidFaq/ConfiguringSquid#Squid-3.5_default_config) distributed with squid but with the option to extended them or disregard them. This role also allows for multiple http and https ports to be configured along with all the usual things like acls and http_access rules.

Tested on openSUSE and on CentOS.  Should work on most platforms.  Requires Ansible version >=2.0

# Role Variables
The current defaults can be found in [defaults/main.yml](defaults/main.yml) - These should be mostly self explanatory.

```squid_acl_localnet``` - defines the src network value for the default acl "allow localnet" - does not have to be set but the reference to the acl in http_access must be removed.

```squid_default_acl``` - populated with the ditributed squid default acl

```squid_custom_acl``` - defines an additional acl

```squid_http_access``` - populated with the default http_access rules.  Any additional rules must refined the entire list

```squid_http_ports``` - a list of http_port parameters to use.  Defaults to 3128.  Redfine as an empty list to not listen with http. Use this to run on multiple ports

```squid_https_ports``` - a list of https_port parameters to use e.g. "3129 cert=/etc/squid/squid.crt"

```squid_access_log``` - set a value for access_log

``` squid_cache_dir``` - set a value for squid_cache_dir

```squid_coredump_dir``` - Sets the associated value, defaults to /var/cache/squid - likely to be useful different platforms use a different value

```squid_custom_refresh_patterns``` - a list of additional refresh pattern parameters

```squid_default_refresh_patterns``` - a list populated with the default refresh pattern parameters

# Examples

## Bare minimum
Setting just ```squid_acl_localnet``` will provide a working squid proxy
```yaml
---
icecast_admin_password: hackme
icecast_source_password: hackme
```
