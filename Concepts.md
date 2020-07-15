# Ansible
- created by redhat
- python
- uses jinja2 engine
- task oriented: function with params
- grup of tasks:
    - roles
    - playbook
- inventory
    - hosts
- connect via ssh
    - ssh key
- uses YAML to declare tasks/roles/playbooks
- machine running ansible = controller

## Yaml concepts
- indented from left with spaces
- has objects (dictionaries)
- has lists (arrays)

- Example:
    ```yaml
    - hosts: controller
    become: yes

    pre_tasks:
    - include_tasks: roles/kubernetes/tasks/hooks.yml
        loop: "{{ controller_execution_hooks }}"
        loop_control:
        loop_var: execution_hook
        when:
        - controller_execution_hooks | default([]) | length
    ```
- Get a value: `[0].pre_tasks.[0].loop_control.loop_var -> execution_hook`

