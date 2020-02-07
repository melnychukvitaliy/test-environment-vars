# test-environment-vars

## Requirements

https://github.com/direnv/direnv

## Running

### Show all environment vars

```
env
```

```
printenv
```

### Add new variable

```
export NEW_SECRET="new"

env | grep NEW_SECRET
```

### source described env

```
source .env

env | grep FOO_SOURCE

```

### add env to process

```
# prints env
bash ./bash_process.sh

NEW_SECRET="new" bash ./bash_process.sh | grep NEW_SECRET

```

### watch environment .envrc files

```
echo export IMPORTANT_SECRET=foo > .envrc

direnv allow .

# unwatch directory
direnv prune

# look inside process
bash ./bash_process.sh | grep IMPORTANT_SECRET

```

### get env from process

```
export JWT_TOKEN=123
bash demon_bash_process.sh

# from separate terminal
ps aux | grep demin_bash_process

sudo su

#LINUX
cat /proc/[process-id]/environ | tr '\0' '\n'

#OS X
ps eww [process id] | tr ' ' '\n'

```
