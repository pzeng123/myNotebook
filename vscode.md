## new problems

### git not recognised in visual studio code
problem: 

server git was updated to [2.2.2](https://oracle-base.com/articles/linux/git-2-installation-on-linux):
```
yum install curl-devel expat-devel gettext-devel openssl-devel zlib-devel -y
yum install gcc perl-ExtUtils-MakeMaker -y
yum remove git -y

cd /usr/src
wget https://www.kernel.org/pub/software/scm/git/git-2.2.2.tar.gz
tar xzf git-2.2.2.tar.gz

cd git-2.2.2
make prefix=/usr/local/git all
make prefix=/usr/local/git install
echo "export PATH=$PATH:/usr/local/git/bin" >> /etc/bashrc
source /etc/bashrc
```
After that, vscode ssh to server to edit files on server, but got notification: 
`Git not found. Install it or configure it using the 'git.path' setting.`

*1. In VS Code -> Preferences -> Settings, add line: 
```
"git.path": "/usr/local/git/bin"
```
or 
```
"git.path": "/usr/local/git/bin/git"
```
but not working.

*2. reinstall git on server to /usr/bin, the same as local machine, then it works.
```
...
make prefix=/usr/local/git all
make prefix=/usr/local/git install
```

