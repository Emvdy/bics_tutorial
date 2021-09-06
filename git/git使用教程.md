```
cd git_dict
git init --bare --share=group git_name.git
chmod g+s -R git_name
chown -R owner_name:group_name git_name/
```



```
git config --global core.quotepath=false
git config --global user.name="your name"
git config --global user.email="example@mail.com"
git config --global alias.st=status
git config --global --list
```



```
git clone git_dict/git_name
cd ./git_name
touch file
git add file
git commit -m "commit message"
git pull origin master
git push orgin master
```

