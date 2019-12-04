# maldua-mirror
maldua-mirror updates its own git repo fork for each one of the Zimbra organization repos daily at 05:30 UTC.
You can explore the forked repos (and this one) at [madua-mirror organization page](https://github.com/maldua-mirror/).
You can learn about the maldua-project at [maldua-project repo page](https://github.com/maldua/maldua-project).

# How to add a new mirror

* Fork the repo to mirror under the maldua-mirror organisation
* Invite maldua-mirrorer user to the new created mirror with Edit permissions
* Make sure maldua-mirrorer accepts the invitation

# Edit updatemirror.yml

Edit: `.github/workflows/updatemirror.yml` in order to update the ZIMBRA_REPOS variable.

Example:
Before:
`ZIMBRA_REPOS="zm-build zm-zcs-lib"`
After:
`ZIMBRA_REPOS="zm-zcs-lib"`

Finally commit the change to main branch
