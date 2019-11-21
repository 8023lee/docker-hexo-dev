# myhexo

1、运行服务直接退出
```
Creating network "hexo_default" with the default driver
Creating hexo_hexo_1 ... done
Attaching to hexo_hexo_1
hexo_hexo_1 exited with code 0
```
docker-compose.yml添加tty解决，容器需要保持一个前台运行的程序

2、npm install 报错

```
npm WARN checkPermissions Missing write access to /usr/local/lib/node_modules
npm ERR! path /usr/local/lib/node_modules
npm ERR! code EACCES
npm ERR! errno -13
npm ERR! syscall access
npm ERR! Error: EACCES: permission denied, access '/usr/local/lib/node_modules'
npm ERR!  { Error: EACCES: permission denied, access '/usr/local/lib/node_modules'
npm ERR!   stack: 'Error: EACCES: permission denied, access \'/usr/local/lib/node_modules\'',
npm ERR!   errno: -13,
npm ERR!   code: 'EACCES',
npm ERR!   syscall: 'access',
npm ERR!   path: '/usr/local/lib/node_modules' }
npm ERR! 
npm ERR! The operation was rejected by your operating system.
npm ERR! It is likely you do not have the permissions to access this file as the current user
npm ERR! 
npm ERR! If you believe this might be a permissions issue, please double-check the
npm ERR! permissions of the file and its containing directories, or try running
npm ERR! the command again as root/Administrator (though this is not recommended).

npm ERR! A complete log of this run can be found in:
npm ERR!     /run/npm-cache/_logs/2019-11-18T08_48_53_904Z-debug.log
```
改变了lib/node_modules的权限后，又出现了这个错...
```
npm ERR! path ../lib/node_modules/hexo-cli/bin/hexo
npm ERR! code EACCES
npm ERR! errno -13
npm ERR! syscall symlink
npm ERR! Error: EACCES: permission denied, symlink '../lib/node_modules/hexo-cli/bin/hexo' -> '/usr/local/bin/hexo'
npm ERR!  { Error: EACCES: permission denied, symlink '../lib/node_modules/hexo-cli/bin/hexo' -> '/usr/local/bin/hexo'
npm ERR!   cause: 
npm ERR!    { Error: EACCES: permission denied, symlink '../lib/node_modules/hexo-cli/bin/hexo' -> '/usr/local/bin/hexo'
npm ERR!      errno: -13,
npm ERR!      code: 'EACCES',
npm ERR!      syscall: 'symlink',
npm ERR!      path: '../lib/node_modules/hexo-cli/bin/hexo',
npm ERR!      dest: '/usr/local/bin/hexo' },
npm ERR!   stack: 'Error: EACCES: permission denied, symlink \'../lib/node_modules/hexo-cli/bin/hexo\' -> \'/usr/local/bin/hexo\'',
npm ERR!   errno: -13,
npm ERR!   code: 'EACCES',
npm ERR!   syscall: 'symlink',
npm ERR!   path: '../lib/node_modules/hexo-cli/bin/hexo',
npm ERR!   dest: '/usr/local/bin/hexo' }
npm ERR! 
npm ERR! The operation was rejected by your operating system.
npm ERR! It is likely you do not have the permissions to access this file as the current user
npm ERR! 
npm ERR! If you believe this might be a permissions issue, please double-check the
npm ERR! permissions of the file and its containing directories, or try running
npm ERR! the command again as root/Administrator (though this is not recommended).

npm ERR! A complete log of this run can be found in:
npm ERR!     /run/npm-cache/_logs/2019-11-19T07_21_04_069Z-debug.log

```
添加了选项--no-bin-links