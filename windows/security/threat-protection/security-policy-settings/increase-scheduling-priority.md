---
title: Increase scheduling priority (Windows 10)
description: Describes the best practices, location, values, policy management, and security considerations for the Increase scheduling priority security policy setting.
ms.assetid: fbec5973-d35e-4797-9626-d0d56061527f
ms.prod: w10
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: brianlic-msft
ms.date: 07/13/2017
---

# Increase scheduling priority

**Applies to**
-   Windows 10

Describes the best practices, location, values, policy management, and security considerations for the **Increase scheduling priority** security policy setting.

## Reference

This policy setting determines which user accounts can increase the base priority class of a process. It is not a privileged operation to increase relative priority within a priority class. This user right is not required by administrative tools that are supplied with the operating system, but it might be required by software development tools.

Specifically, this security setting determines which accounts can use a process with Write Property access to another process to increase the run priority that is assigned to the other process. A user with this privilege can change the scheduling priority of a process through the Task Manager user interface.

Constant: SeIncreaseBasePriorityPrivilege

### Possible values

-   User-defined list of accounts
-   Not defined
-   Administrators

### Best practices

-   Allow the default value, Administrators and Window Manager/Window Manager Group, as the only accounts responsible for controlling process scheduling priorities.

### Location

Computer Configuration\\Windows Settings\\Security Settings\\Local Policies\\User Rights Assignment

### Default values

By default this setting is Administrators on domain controllers and on stand-alone servers.

The following table lists the actual and effective default policy values. Default values are also listed on the policy’s property page.

| Server type or GPO | Default value |
| - | - |
| Default Domain Policy| Not defined| 
| Default Domain Controller Policy| Not defined| 
| Stand-Alone Server Default Settings | Administrators and Window Manager/Window Manager Group| 
| Domain Controller Effective Default Settings | Administrators and Window Manager/Window Manager Group| 
| Member Server Effective Default Settings | Administrators and Window Manager/Window Manager Group|
| Client Computer Effective Default Settings | Administrators and Window Manager/Window Manager Group| 
 
## Policy management

This section describes features, tools, and guidance to help you manage this policy.

A restart of the computer is not required for this policy setting to be effective.

Any change to the user rights assignment for an account becomes effective the next time the owner of the account logs on.

### Group Policy

Settings are applied in the following order through a Group Policy Object (GPO), which will overwrite settings on the local computer at the next Group Policy update:

1.  Local policy settings
2.  Site policy settings
3.  Domain policy settings
4.  OU policy settings

When a local setting is greyed out, it indicates that a GPO currently controls that setting.

## Security considerations

This section describes how an attacker might exploit a feature or its configuration, how to implement the countermeasure, and the possible negative consequences of countermeasure implementation.

### Vulnerability

A user who is assigned this user right could increase the scheduling priority of a process to Real-Time, which would leave little processing time for all other processes and could lead to a denial-of-service condition.

### Countermeasure

Verify that only Administrators and and Window Manager/Window Manager Group have the **Increase scheduling priority** user right assigned to them.

### Potential impact

None. Restricting the **Increase scheduling priority** user right to members of the Administrators group and and Window Manager/Window Manager Group is the default configuration.

## Related topics

- [User Rights Assignment](user-rights-assignment.md)
