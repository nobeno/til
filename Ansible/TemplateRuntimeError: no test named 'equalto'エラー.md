## TemplateRuntimeError: no test named 'equalto'

#### エラー内容：ec2_createモジュール実行時に出たエラー
```
[root@ip-10-0-0-114 ansible]# ansible-playbook -i hosts create_ec2.yml

PLAY [ec2] *************************************************************************************************************************************************************************************************

TASK [Facts subnet] ****************************************************************************************************************************************************************************************
[WARNING]: Platform linux on host localhosts is using the discovered Python interpreter at /usr/bin/python, but future installation of another Python interpreter could change this. See
https://docs.ansible.com/ansible/2.9/reference_appendices/interpreter_discovery.html for more information.
[DEPRECATION WARNING]: The 'ec2_vpc_subnet_facts' module has been renamed to 'ec2_vpc_subnet_info'. This feature will be removed in version 2.13. Deprecation warnings can be disabled by setting
deprecation_warnings=False in ansible.cfg.
ok: [localhosts]

TASK [debug] ***********************************************************************************************************************************************************************************************
skipping: [localhosts]

TASK [EC2] *************************************************************************************************************************************************************************************************
An exception occurred during task execution. To see the full traceback, use -vvv. The error was: TemplateRuntimeError: no test named 'equalto'
failed: [localhosts] (item={u'group': [u'nobeno-sg-private'], u'name': u'ansible-test', u'instance_profile_name': u'ansible-test', u'key_name': u'nobeno-dev', u'image': u'ami-06098fd00463352b6', u'root_volume_size': 8, u'instance_type': u't2.micro', u'subnet_name': u'nobeno-subnet-private-1d', u'assign_public_ip': False}) => {"ansible_loop_var": "item", "changed": false, "item": {"assign_public_ip": false, "group": ["nobeno-sg-private"], "image": "ami-06098fd00463352b6", "instance_profile_name": "ansible-test", "instance_type": "t2.micro", "key_name": "nobeno-dev", "name": "ansible-test", "root_volume_size": 8, "subnet_name": "nobeno-subnet-private-1d"}}

PLAY RECAP *************************************************************************************************************************************************************************************************
localhosts                 : ok=1    changed=0    unreachable=0    failed=1    skipped=1    rescued=0    ignored=0
```

<br/>

#### 原因：Jinja2のバージョンが古い
#### 解決方法：Jinja2のバージョンアップ
```
[root@ip-10-0-0-114 ansible]# pip show jinja2
Name: Jinja2
Version: 2.7.2
Summary: A small but fast and easy to use stand-alone template engine written in pure python.
Home-page: http://jinja.pocoo.org/
Author: Armin Ronacher
Author-email: armin.ronacher@active-4.com
License: BSD
Location: /usr/lib/python2.7/site-packages
Requires: markupsafe
[root@ip-10-0-0-114 ansible]# pip install jinja2 --upgrade
WARNING: Running pip install with root privileges is generally not a good idea. Try `pip install --user` instead.
Collecting jinja2
  Downloading https://files.pythonhosted.org/packages/7e/c2/1eece8c95ddbc9b1aeb64f5783a9e07a286de42191b7204d67b7496ddf35/Jinja2-2.11.3-py2.py3-none-any.whl (125kB)
    100% |################################| 133kB 5.5MB/s
Collecting MarkupSafe>=0.23 (from jinja2)
  Downloading https://files.pythonhosted.org/packages/fb/40/f3adb7cf24a8012813c5edb20329eb22d5d8e2a0ecf73d21d6b85865da11/MarkupSafe-1.1.1-cp27-cp27mu-manylinux1_x86_64.whl
Installing collected packages: MarkupSafe, jinja2
  Found existing installation: MarkupSafe 0.11
    Uninstalling MarkupSafe-0.11:
      Successfully uninstalled MarkupSafe-0.11
  Found existing installation: Jinja2 2.7.2
    Uninstalling Jinja2-2.7.2:
      Successfully uninstalled Jinja2-2.7.2
Successfully installed MarkupSafe-1.1.1 jinja2-2.11.3
[root@ip-10-0-0-114 ansible]# pip show jinja2
Name: Jinja2
Version: 2.11.3
Summary: A very fast and expressive template engine.
Home-page: https://palletsprojects.com/p/jinja/
Author: Armin Ronacher
Author-email: armin.ronacher@active-4.com
License: BSD-3-Clause
Location: /usr/lib64/python2.7/site-packages
Requires: MarkupSafe
```

<br/>

#### 参考
- Jinja2とは：テンプレートエンジンライブラリ

