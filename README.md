# ansible-windows-module-dev

https://docs.ansible.com/ansible/latest/dev_guide/developing_modules_general_windows.html

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
