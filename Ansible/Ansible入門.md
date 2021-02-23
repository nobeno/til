## Ansible入門

### 作業ディレクトリ
`cd /etc/ansible`

### 対象サーバ記述箇所
- `vi ./hosts`
- 参考
```yaml
[ec2]
xxx.xxx.xxx.xxx # IPアドレス

[ec2:vars]
ansible_user=user # user名
ansible_ssh_private_key_file=~/.ssh/xxxxx.pem # 接続先秘密鍵
```

### 実行処理のためのファイル
- `vi ./site.yml`
- 参考（localhost実行例）
```yaml
- name: local-test
  hosts: localhost
  connection: local
  gather_facts: no
  become_user: ec2-user
  become: yes
  tasks:
    - name: install httpd
      yum:
        name: http
        state: latest
      become_user: root
      become: yes
## rolesディレクトリで管理する場合
#  roles:
#    - httpd
```

### playbook実行
- 構文チェック
`ansible-playbook site.yml --syntax-check -vvv`
- 実行
`ansible-playbook site.yml -vvv`  

#### 参考
https://ops.jig-saw.com/tech-cate/howto_use_ansible
