# ansible-windows-module-dev

In this example, we will take these 2 Ansible tasks, and create an Ansible module from them

```
- name: Get current DNS search string
  win_shell: Get-DnsClientGlobalSetting | Select SuffixSearchList
  changed_when: false
  register: suffixsearchlist

- name: Set DNS search string
  win_shell: Set-DnsClientGlobalSetting -SuffixSearchList {{ dns_domain_name }}, ec2.internal
  when: "dns_domain_name not in suffixsearchlist.stdout"
```
