# maldua-mirror
TODO: What is maldua-mirror?

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
