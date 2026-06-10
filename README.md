# Nested VMs

On an ubuntu test runner, this action will install and prepare [libvirt]
for nested virtualization and then stand up a cluster of vms for
testing using [OpenBolt] and [Terraform].

The OpenBolt module [kvm_automation_tooling] is used to provision the
VMs.

## Supported Platforms

Ubuntu 24.04

## Supported VM Platforms

The action can created nested vms for any OS supported by
[kvm_automation_tooling] which currently (v2) includes:

* Almalinux 10, 9, 8
* Debian 13, 12, 11
* Rocky 10, 9, 8
* Ubuntu 26.04, 24.04, 22.04

## Supported Architectures

Supports x86_64 and aarch64 architectures for the nested VMs as of
[kvm_automation_tooling] 2.8.0.

Note that the runner vm must still be x86_64, since the standard
ubuntu-24.04-arm runner does not support kvm (until such a time as
https://github.com/actions/runner-images/issues/14062 is resolved).

This also means, that while you can create aarch64 nested VMs, they
will be emulated using qemu and thus much slower than the x86_64
nested VMs. (5-20 times slower depending on the os, where alma, rocky,
debian seemed to be on the faster end of the spectrum and ubuntu on
the slower end, with ubuntu 26.04 the slowest...).

When using aarch64 nested VMs, it is recommended to provide a minimum
vm spec with "cpus" 2 and "mem_mb" 4096 to ensure the nested VMs have
enough resources to run.

## Usage

Minimally, you must specify 'os', 'os-version' and 'os-arch'
parameters.

```yaml
- uses: jpartlow/nested_vms@v1
  with:
    # The default operating system to us for the VMs in the cluster.
    os: almalinux

    # The version of the operating system.
    os-version: 9

    # The architecture of the operating system.
    os-arch: x86_64
```

By default this will generate a single nested VM with an fqdn of
'test-agent-1.vm' that can be reached via SSH on the runner using the
key "${HOME}/.ssh/ssh-id-test.pub" (where $HOME is the home directory
of the runner user on the gha runner vm).

## License

Copyright (C) 2025 Joshua Partlow

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU Affero General Public License as published
by the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU Affero General Public License for more details.

You should have received a copy of the GNU Affero General Public License
along with this program.  If not, see <https://www.gnu.org/licenses/>.

[kvm_automation_tooling]: https://github.com/jpartlow/kvm_automation_tooling
[libvirt]: https://libvirt.org/
[OpenBolt]: https://github.com/OpenVoxProject/openbolt
[Terraform]: https://developer.hashicorp.com/terraform
