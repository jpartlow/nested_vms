# Changelog

## 1.1.0 (2025-06-12)

* Pin to kvm_automation_tooling@v2.
* Fixed the debug flag. A false value should now run Bolt without
  --stream.
* Adds a checkout parameter to the action which can be set false
  to use the kvm_automation_tooling provided by the calling workflow.
  Intended primarily for internal development testing.

## 1.0.0 (2025-05-29)

* Initial v1 release of action extracted from kvm_automation_tooling
  module.
