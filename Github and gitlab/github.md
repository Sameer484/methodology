#####  Access to /explore/groups
![Screenshot from 2023-05-31 13-24-28](https://github.com/Sameer484/methodology/assets/110039044/1e93e6d6-ab1c-490c-8c27-848135014f23)

### Found .git/index? try dumping the whole github using tool gitdumper.sh  
`gitdumper.sh https://<address-here.com>/.git/ <output-folder>`
- Than navigate into output folder and execute:
   ```
   git status
   git checkout — .
   ```
- After that just print source code of files to your terminal (note that not all files will be restored).
- Check this blog to understand in depth detail about dumping the full source code. https://en.internetwache.org/dont-publicly-expose-git-or-how-we-downloaded-your-websites-sourcecode-an-analysis-of-alexas-1m-28-07-2015/
