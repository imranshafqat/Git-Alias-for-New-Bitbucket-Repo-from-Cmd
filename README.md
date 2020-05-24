# Git-Alias-for-New-Bitbucket-Repo-from-Cmd

Simple function to create bitbucket repos from command line.

Add this function in your .gitconfig
```
[alias]
	aliasname= "!f() { curl -s -X POST -u USERNAME:APP-PASSWORD -H 'Content-Type: application/json' https://api.bitbucket.org/2.0/repositories/USERNAME/$1 -d '{ \"is_private\": \"true\", \"fork_policy\": \"no_forks\", \"mainbranch\": { \"type\": \"branch\", \"name\": \"master\" }, \"language\": \"android\", \"scm\": \"git\", \"project\": { \"key\": \"PROJECTKEY\"  } }' | /d/installations/jq-win64/jq-win64.exe '.links.clone[].href'; }; f"
```
Then create new bitbucket repo from commandline with
```
git aliasname new-repo-name
```
This will output two git remote urls, add this remote url to existing project or use git clone.
  
**Replacements:**  
USERNAME: Your bitbucket username  
APP-PASSWORD: Create an app password (Create app password https://bitbucket.org/account/settings/app-passwords/new with Repositories:Write permission)  
PROJECTKEY: Your bitbucket project key
/d/installations/jq-win64/jq-win64.exe: Download jq from https://github.com/stedolan/jq/releases and set its path here
