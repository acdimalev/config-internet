This is configuration management for setting up a PC Engines APU2, running
Debian, as a home router.

<http://pcengines.ch/apu2.htm>


Prerequisites
-------------

- Python 2.7 (<https://www.python.org/>)

- Python Virtualenv (<https://virtualenv.pypa.io/en/stable/>)


Usage
-----

Install Ansible.

    $ virtualenv -p python2 venv
    $ . venv/bin/activate
    (venv) $ pip install -r requirements.txt

Copy example configuration files and modify them for your installation.

    (venv) $ cp -a hosts/example hosts/my-router
    (venv) $ sensible-editor hosts/my-router
    (venv) $ cp -a host_vars/example host_vars/my-router
    (venv) $ sensible-editor host_vars/my-router

Verify that Ansible can log into your router.

    (venv) $ ansible -m ping my-router
    my-router | SUCCESS => {
        "changed": false,
        "ping": "pong"
    }

Run the playbook against your router.

    (venv) $ ansible-playbook -l my-router playbook.yml
    PLAY [all] *********************************************************************

    TASK [setup] *******************************************************************
    ok: [my-router]

    TASK [pcengines-apu2-console : ensure grub defaults are patched] ***************
    ok: [my-router]

    ...
