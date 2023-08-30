weblogic-deploy-tooling
=========

The `weblogic-deploy-tooling` ansible role installs WebLogic Deploy Tooling in a remote machine.

Requirements
------------

N/A

Role Variables
--------------

- **github_wdt_base_url**: GitHub WDT API URL for releases. Default: "https://api.github.com/repos/oracle/weblogic-deploy-tooling/releases"
- **wdt_version**: WDT version. Default: "latest"
- **dest_dir**: Remote absolute path where the WDT archive should be unpacked. Default: "/admin/utils"
- **wdt_path**: WDT installation path after unpack. Default: "{{ dest_dir }}/weblogic-deploy"
- **user**: Installation owner username. It must exists on the remote machine. Default: "oracle"
- **group**: Installation owner group name. It must exists on the remote machine. Default: "oracle"

Dependencies
------------

N/A

Example Playbook
----------------

```yaml
- name: Install WDT
  hosts: myRemoteHost
  roles:
    - role: weblogic-deploy-tooling
      vars:
        ansible_python_interpreter: auto
        ansible_interpreter_python_fallback: ['/usr/bin/python3','/usr/bin/python2','/usr/bin/python']
        wdt_version: release-3.2.2
```


Example output
----------------

```
PLAY [Install WDT] *************************************************************
TASK [Install WDT] *************************************************************
TASK [weblogic-deploy-tooling : Validating arguments against arg spec 'main' - This role installs WDT in a remote machine] ***
ok: [myRemoteHost]
TASK [weblogic-deploy-tooling : Set GitHub API URL based on WDT version] *******
ok: [myRemoteHost]
TASK [weblogic-deploy-tooling : Get release] ***********************************
ok: [myRemoteHost]
TASK [weblogic-deploy-tooling : Get download URL and release name from the response] ***
ok: [myRemoteHost]
TASK [weblogic-deploy-tooling : Check if WDT is installed and which version] ***
ok: [myRemoteHost]
TASK [weblogic-deploy-tooling : WDT installation found.] ***********************
ok: [myRemoteHost] => {
    "msg": ""
}
TASK [weblogic-deploy-tooling : Get current WDT version installed] *************
ok: [myRemoteHost]
TASK [weblogic-deploy-tooling : Compare WDT version found = WebLogic Deploy Tooling 3.2.3. To be installed = WebLogic Deploy Tooling 3.2.2] ***
ok: [myRemoteHost]
TASK [weblogic-deploy-tooling : Different WDT version.] ************************
ok: [myRemoteHost] => {
    "msg": ""
}
TASK [weblogic-deploy-tooling : Remove current installation at /admin/utils/weblogic-deploy] ***
changed: [myRemoteHost]
TASK [weblogic-deploy-tooling : Install WebLogic Deploy Tooling 3.2.2] *********
ok: [myRemoteHost] => {
    "msg": ""
}
TASK [weblogic-deploy-tooling : Unarchive WDT file from URL] *******************
changed: [myRemoteHost]
TASK [weblogic-deploy-tooling : Set dir permissions] ***************************
changed: [myRemoteHost]
TASK [weblogic-deploy-tooling : Same WDT version.] *****************************
skipping: [myRemoteHost]
TASK [weblogic-deploy-tooling : WDT installation NOT FOUND. Installing WebLogic Deploy Tooling 3.2.2] ***
skipping: [myRemoteHost]
TASK [weblogic-deploy-tooling : Check /admin/utils/weblogic-deploy directory status] ***
skipping: [myRemoteHost]
TASK [weblogic-deploy-tooling : Remove /admin/utils/weblogic-deploy] ***********
skipping: [myRemoteHost]
TASK [weblogic-deploy-tooling : Install WebLogic Deploy Tooling 3.2.2] *********
skipping: [myRemoteHost]
TASK [weblogic-deploy-tooling : Unarchive WDT file from URL] *******************
skipping: [myRemoteHost]
TASK [weblogic-deploy-tooling : Set dir permissions] ***************************
skipping: [myRemoteHost]
PLAY RECAP *********************************************************************
myRemoteHost              : ok=13   changed=3    unreachable=0    failed=0    skipped=7    rescued=0    ignored=0 



PLAY [Install FMW Infrastructure] ***********************************************************************************************************************************************************************************************************

TASK [Install FMW Infrastructure name={{ lookup('env', 'NODECONF_HOME')}}/roles/fmw_infra] **************************************************************************************************************************************************

TASK [/home/usr-a.dbenitez/repos/arqtooling/playbooks/nodeconf/roles/fmw_infra : Validating arguments against arg spec 'main' - This role installs Oracle Fusion Middleware Infrastructure in a remote machine with a JDK installation. argument_spec={'process': {'type': 'str', 'required': False, 'description': "Process to execute ['install','deinstall']. You can choose install Oracle FMW Infrastructure or deinstall it.", 'choices': ['install', 'deinstall'], 'default': ['install']}, 'fmw_version': {'type': 'str', 'required': False, 'description': 'Oracle FMW Infrastructure version to install.', 'default': '12.2.1.4.0'}, 'oracle_home': {'type': 'str', 'required': False, 'description': 'ORACLE_HOME directory.', 'default': '/var/tmp/oracle_home'}, 'java_home': {'type': 'str', 'required': False, 'description': 'JAVA_HOME directory.', 'default': '/tmp/jdk'}, 'oraInventory': {'type': 'str', 'required': False, 'description': 'oraInventory directory.', 'default': '/var/tmp/oraInventory'}, 'create_oraInventory': {'type': 'bool', 'required': False, 'description': 'Create oraInventory file (oracle software inventory installed).', 'default': True}, 'user': {'type': 'str', 'required': False, 'description': 'Installation owner username. It must exists on the remote machine.', 'default': 'oracle'}, 'group': {'type': 'str', 'required': False, 'description': 'Installation owner group name. It must exists on the remote machine.', 'default': 'oracle'}, 'repository_server': {'type': 'str', 'required': False, 'description': 'HTTP repository server that hosts binaries.'}, 'repository_server_port': {'type': 'str', 'required': False, 'description': 'HTTP repository server port.', 'default': '8080'}, 'download_url': {'type': 'str', 'required': False, 'description': 'URL used to download Oracle FMW Infra binaries.', 'default': 'http://myHTTPRepoServer:8080/oracle/fmw/binaries/12.2.1.4.0/fmw_12.2.1.4.0_infrastructure.jar'}}, provided_arguments={}, validate_args_context={'type': 'role', 'name': '/home/usr-a.dbenitez/repos/arqtooling/playbooks/nodeconf/roles/fmw_infra', 'argument_spec_name': 'main', 'path': '/home/usr-a.dbenitez/repos/arqtooling/playbooks/nodeconf/roles/fmw_infra'}] ***
ok: [myRemoteHost]

TASK [/home/usr-a.dbenitez/repos/arqtooling/playbooks/nodeconf/roles/fmw_infra : Check oracle_home /var/tmp/oracle_home] ********************************************************************************************************************
ok: [myRemoteHost]

TASK [/home/usr-a.dbenitez/repos/arqtooling/playbooks/nodeconf/roles/fmw_infra : Create oraInventory dir /var/tmp/oraInventory] *************************************************************************************************************
changed: [myRemoteHost]

TASK [/home/usr-a.dbenitez/repos/arqtooling/playbooks/nodeconf/roles/fmw_infra : Create oraInst.loc] ****************************************************************************************************************************************
changed: [myRemoteHost]

TASK [/home/usr-a.dbenitez/repos/arqtooling/playbooks/nodeconf/roles/fmw_infra : Create tmp directory] **************************************************************************************************************************************
changed: [myRemoteHost]

TASK [/home/usr-a.dbenitez/repos/arqtooling/playbooks/nodeconf/roles/fmw_infra : Check if binary is present in repository] ******************************************************************************************************************
ok: [myRemoteHost]

TASK [/home/usr-a.dbenitez/repos/arqtooling/playbooks/nodeconf/roles/fmw_infra : Download from HTTP server] *********************************************************************************************************************************
changed: [myRemoteHost]

TASK [/home/usr-a.dbenitez/repos/arqtooling/playbooks/nodeconf/roles/fmw_infra : Create response file /tmp/fmw_infra_install-HNbLJm/fmw_infr.rsp dest=/tmp/fmw_infra_install-HNbLJm/fmw_infr.rsp, src=fmw_infr.rsp.j2] **********************
changed: [myRemoteHost]

TASK [/home/usr-a.dbenitez/repos/arqtooling/playbooks/nodeconf/roles/fmw_infra : Install software _raw_params=/admin/jdk/jdk8/bin/java  -jar /tmp/fmw_infra_install-HNbLJm/fmw_12.2.1.4.0_infrastructure.jar -responseFile /tmp/fmw_infra_install-HNbLJm/fmw_infr.rsp  -silent -invPtrLoc /var/tmp/oraInventory/oraInst.loc -logLevel Info, _uses_shell=True, _ansible_check_mode=False, _ansible_no_log=False, _ansible_debug=False, _ansible_diff=False, _ansible_verbosity=0, _ansible_version=2.13.6, _ansible_module_name=ansible.legacy.command, _ansible_syslog_facility=LOG_USER, _ansible_selinux_special_fs=['fuse', 'nfs', 'vboxsf', 'ramfs', '9p', 'vfat'], _ansible_string_conversion_action=warn, _ansible_socket=None, _ansible_shell_executable=/bin/sh, _ansible_keep_remote_files=False, _ansible_tmpdir=None, _ansible_remote_tmp=$HOME/.ansible/tmp] ***
changed: [myRemoteHost]

TASK [/home/usr-a.dbenitez/repos/arqtooling/playbooks/nodeconf/roles/fmw_infra : Remove tmp dir state=absent, dest=/tmp/fmw_infra_install-HNbLJm, _ansible_check_mode=False, _ansible_no_log=False, _ansible_debug=False, _ansible_diff=False, _ansible_verbosity=0, _ansible_version=2.13.6, _ansible_module_name=ansible.builtin.file, _ansible_syslog_facility=LOG_USER, _ansible_selinux_special_fs=['fuse', 'nfs', 'vboxsf', 'ramfs', '9p', 'vfat'], _ansible_string_conversion_action=warn, _ansible_socket=None, _ansible_shell_executable=/bin/sh, _ansible_keep_remote_files=False, _ansible_tmpdir=None, _ansible_remote_tmp=$HOME/.ansible/tmp] ***
changed: [myRemoteHost]

PLAY RECAP **********************************************************************************************************************************************************************************************************************************
myRemoteHost              : ok=10   changed=7    unreachable=0    failed=0    skipped=5    rescued=0    ignored=0
```

License
-------

BSD

Author Information
------------------

Daniel Benítez Águila
