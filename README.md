# Docker Container with Python configured

 - Several usefull package are installed.
 - SSH server is configured
 - Install all the python packages from requirements.txt located into the user directory

## Starting Container
When the container start all those action is done
 - The [locale][1] is generated. Its value is into CONTAINER_LOCALE (default is en_US.UTF-8)
 - One user is added.
   - Its name is defined in CONTAINER_USER_NAME (default is olive).
   - Its password is defined in CONTAINER_USER_PASSWORD (default is test).
   - Its userid is defined in CONTAINER_USER_UID (default is 1000).
   - Its groupid is defined in CONTAINER_USER_GID (default is 1000).
   - One ssh key is downloaded and added has autorized_key
   - A folder is created in the user directory named django
 - Bash is customized with personal prompt and aliases. File are downloaded form the URL saved into those variables   
   - CONTAINER_URL_BASH_ALIASES
   - CONTAINER_URL_BASH_PROMPT
 - Ssh key is downloaded form CONTAINER_URL_SSH_KEY

## Next configuration
 Every script which have to be run after the first start of the container have to be into the /usr/local/script/entry-point.d/ folder
 
[1]: https://help.ubuntu.com/community/Locale
