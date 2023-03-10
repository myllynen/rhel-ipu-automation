# RHEL In-Place Upgrade Automation

[![License: MIT](https://img.shields.io/badge/license-MIT-brightgreen.svg)](https://opensource.org/licenses/MIT)

Ansible playbooks for RHEL in-place upgrade (IPU) automation.

## Contents

* [inventory](inventory)
  * Example inventory
* [leapp.answerfile](leapp.answerfile)
  * Example Leapp answerfile
* [preupgrade.yml](preupgrade.yml)
  * Playbook to run Leapp preupgrade test and check results

## Quick Usage Example

These playbooks automate RHEL in-place upgrade related tasks. The
playbooks use supported RPMs from Red Hat repositories and only
[the leapp utility metadata](https://access.redhat.com/articles/3664871)
must be downloaded separately in disconnected environments.

The minimal [leapp utility answerfile](leapp.answerfile) example can be
expanded as needed according to local findings and needs.

When using Red Hat Satellite, a content view (CV) providing both the
source and target repositories is needed. The provided playbooks switch
the target systems to use such a CV automatically if a corresponding
activation key (AK) is provided. Also, the initial, real system CV is
restored after the check when, again, a corresponding AK is provided.

The `preupgrade.yml` playbook will install the Leapp RPMs and leave them
installed on target systems after the check as it is expected that Leapp
will be used later to perform the actual in-place upgrade. Leapp RPMs
and their dependencies consume some 20 MB of disk space so this should
not be an issue.

For further details please see the related documentation listed below.

To run RHEL in-place preupgrade test and automatically check results
without doing permanent modifications on target systems:

```
# Edit inventory and parameters to suite local environment
vi inventory preupgrade.yml
# Run Leapp preupgrade test and check results
ansible-playbook -i inventory preupgrade.yml
```

## Related Documentation

* [https://www.redhat.com/en/resources/upgrading-your-linux-infrastructure-overview](https://www.redhat.com/en/resources/upgrading-your-linux-infrastructure-overview)
* [https://access.redhat.com/support/policy/updates/errata](https://access.redhat.com/support/policy/updates/errata)
* [https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html-single/considerations_in_adopting_rhel_8/index](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html-single/considerations_in_adopting_rhel_8/index)
* [https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/upgrading_from_rhel_7_to_rhel_8/index](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/upgrading_from_rhel_7_to_rhel_8/index)
* [https://access.redhat.com/solutions/21964](https://access.redhat.com/solutions/21964)
* [https://access.redhat.com/articles/4263361](https://access.redhat.com/articles/4263361)
* [https://access.redhat.com/solutions/4120411](https://access.redhat.com/solutions/4120411)
* [https://access.redhat.com/articles/3664871](https://access.redhat.com/articles/3664871)
* [https://access.redhat.com/solutions/5392811](https://access.redhat.com/solutions/5392811)
* [https://access.redhat.com/solutions/4067471](https://access.redhat.com/solutions/4067471)
* [https://access.redhat.com/solutions/5057391](https://access.redhat.com/solutions/5057391)
* [https://access.redhat.com/articles/4977891](https://access.redhat.com/articles/4977891)
* [https://access.redhat.com/articles/5777571](https://access.redhat.com/articles/5777571)
* [https://access.redhat.com/articles/rhel-limits](https://access.redhat.com/articles/rhel-limits)

## Related Issues and RFEs

* [https://bugzilla.redhat.com/show_bug.cgi?id=1794460](https://bugzilla.redhat.com/show_bug.cgi?id=1794460)
* [https://github.com/ansible/ansible/issues/78007](https://github.com/ansible/ansible/issues/78007)

## Application and Compatibility Documentation

* [Application Compatibility Guide](https://access.redhat.com/articles/rhel8-abi-compatibility)
* [Application Compatibility Policies](https://access.redhat.com/solutions/5154)
* [Application Streams Life Cycle](https://access.redhat.com/support/policy/updates/rhel-app-streams-life-cycle)
* [RHEL Container Compatibility Matrix](https://access.redhat.com/support/policy/rhel-container-compatibility)
* [RHEL hardware support](https://access.redhat.com/solutions/60940)
* [Kernel ABI (kABI)](https://access.redhat.com/solutions/444773)
* [32-bit applications](https://access.redhat.com/solutions/509373)
* [Ansible](https://www.redhat.com/en/blog/updates-using-ansible-rhel-86-and-90)
* [C/C++ developer blog post](https://developers.redhat.com/blog/2020/10/08/migrating-c-and-c-applications-from-red-hat-enterprise-linux-version-7-to-version-8)
* [C/C++ RHEL documentation](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/developing_c_and_cpp_applications_in_rhel_8/index)
* [Docker](https://access.redhat.com/solutions/3696691)
* [Java](https://access.redhat.com/articles/1299013)
* [Python](https://access.redhat.com/solutions/4455511)
* [C, C++, Go, Rust on RHEL 9](https://www.redhat.com/en/blog/what-c-go-or-rust-developer-should-know-about-rhel-9)
* [Support Scope Details](https://access.redhat.com/support/offerings/production/scope_moredetail)

## See Also

See also
[https://lab.redhat.com/tracks/in-place-upgrades](https://lab.redhat.com/tracks/in-place-upgrades).

See also
[https://access.redhat.com/documentation/en-us/red_hat_satellite/6.12/html/managing_hosts/upgrading_hosts_to_next_major_rhel_release_managing-hosts](https://access.redhat.com/documentation/en-us/red_hat_satellite/6.12/html/managing_hosts/upgrading_hosts_to_next_major_rhel_release_managing-hosts).

See also
[https://www.redhat.com/en/blog/take-unknowns-out-rhel-upgrades-red-hat-insights](https://www.redhat.com/en/blog/take-unknowns-out-rhel-upgrades-red-hat-insights).

See also
[https://console.redhat.com/ansible/automation-hub/repo/published/redhat/rhel_system_roles](https://console.redhat.com/ansible/automation-hub/repo/published/redhat/rhel_system_roles).

See also
[https://github.com/myllynen/rhel-ansible-roles](https://github.com/myllynen/rhel-ansible-roles).

## License

MIT
