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
