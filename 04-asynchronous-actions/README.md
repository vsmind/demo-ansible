# Asynchronous Actions

- `async` How long to run task
- `poll` How frequently to check, default 10 sec

Ansible holds task for 360 sec and checks every 60 sec

```yaml
# Playbook example
-
  name: Deploy Web App
  hosts: web_server
  tasks:
    - command: /opt/check_status.py
      async: 360  # How long to run
      poll: 60    # How frequently to check, default 10 sec
```

Fire and forget tasks
Register results of the monitoring to variables

```yaml
# Playbook example
-
  name: Deploy Web App
  hosts: web_server
  tasks:
    - command: /opt/check_status.py
      async: 360
      poll: 0
      register: webapp_result
        
    - command: /opt/check_db.py
      async: 360
      poll: 0
      register: database_result
```