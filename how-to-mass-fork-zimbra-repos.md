# New user
Create maldua-mirrorer user

# Obtain Zimbra repos

We manage to obtain Zimbra repos and save them into zimbra-repos-ordered.txt file.
```
wget "https://api.github.com/orgs/Zimbra/repos?sort=fullname&page=1" -O pag1.txt
wget "https://api.github.com/orgs/Zimbra/repos?sort=fullname&page=2" -O pag2.txt
wget "https://api.github.com/orgs/Zimbra/repos?sort=fullname&page=3" -O pag3.txt
wget "https://api.github.com/orgs/Zimbra/repos?sort=fullname&page=4" -O pag4.txt
cat pag1.txt pag2.txt pag3.txt pag4.txt > zimbra-repos-json.txt
cat zimbra-repos-json.txt | grep '"full_name"' | awk -F '/' '{print $2}' | sed 's/",//g' > zimbra-repos-full.txt
cat zimbra-repos-full.txt | sort > zimbra-repos-ordered.txt
```

# Personal Access Token
We create a new Personal Access Token associated with maldua-mirrorer user.

Scopes to be selected for this PAT are:
* repo

We write it down because we will need it later.

# Admin permissions in org

Invite maldua-mirrorer to maldua-mirror organisation as an owner role.

# Massive repo script

```
#!/bin/bash

GITHUB_TOKEN="AaBb1122"

for nrepo in $(cat zimbra-repos-ordered.txt); do
  curl \
    -u maldura-mirrorer:${GITHUB_TOKEN} \
    -d '{"organization":"maldua-mirror"}' \
    -X POST https://api.github.com/repos/Zimbra/${nrepo}/forks \
    > fork-request-log-${nrepo}.txt 2>&1
  sleep 5s
done
```

# Remove Personal Access Token
You might want to remove the Personal Access Token if you are not going to fork any more projects in a massive way.
