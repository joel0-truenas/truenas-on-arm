# Summary of Changes

As of 2025-07-09, this is the list of changes I've made on this fork that diverge from upstream.

## Packaging Only

These repositories are already compatible with aarch64, but needed simple changes to the Debian package.

- [scst](https://git.jmay.us/truenas/scst/-/commits/truenas-3.10.0-pre)
- [truenas_spdk](https://git.jmay.us/truenas/truenas_spdk/-/commits/master)
- [rclone](https://git.jmay.us/truenas/rclone/-/commits/master) ([upstream PR](https://github.com/truenas/rclone/pull/13))

## Simple Build Changes

These repositories are mostly compatible with aarch64, but the build system needed minor changes, such as parameterizing a hard coded architecture string.

- [truenas-installer](https://git.jmay.us/truenas/truenas-installer/-/commits/master)
  - This change should be upstreamed, because it's an omission but doesn't surface as a problem in the amd64 installer.
- [webui](https://git.jmay.us/truenas/webui/-/commits/master)
- [sedutil](https://git.jmay.us/truenas/sedutil/-/commits/master)
  - The diff on this one is relatively large, but most of the changes are copied & pasted auto-generated files.
- [python-truenas-requirements](https://git.jmay.us/truenas/python-truenas-requirements/-/commits/master)
- [restic](https://git.jmay.us/truenas/restic/-/commits/master)

## More Substantial Changes

These repositories were lacking some functionality required for aarch64.

- [binaries](https://git.jmay.us/truenas/binaries/-/commits/master)
  - Some non-essential, closed source binaries are missing due to having no aarch64 release.
- [linux](https://git.jmay.us/truenas/linux/-/commits/truenas/linux-6.12)
- [middleware](https://git.jmay.us/truenas/middleware/-/commits/master)
  - This appears to be a bug upstream that just never got exposed.  The type system allows a null CPU model, but this causes the webui to choke when displaying the default dashboard.  Fixing the type system or webui would be ideal, but I plan to improve CPU model detection, so this won't be a problem.
- [scale-build](https://git.jmay.us/truenas/scale-build/-/commits/master)
  - This is where the majority of the changes are.  Without any peer review or guidance, I forged my own path on some decisions that may be controvertial, such as adding Jinja2 formatting to the config file.
