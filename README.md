# Nested VMs

On an ubuntu test runner, this action will install and prepare [libvirt]
for nested virtualization and then stand up a cluster of vms for
testing using [Bolt] and [Terraform].

The Bolt module [kvm_automation_tooling] is used to provision the VMs.

## Supported Platforms

Ubuntu 24.04

## Usage

TODO

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
[Bolt]: https://www.puppet.com/docs/bolt/latest/bolt.html
[Terraform]: https://developer.hashicorp.com/terraform
