这篇日志本来早就应该写了的, 可是最近实在是太忙了, 一点点空闲都没有,每天都是忙着刷leetcode, 好在现在已经刷了130题了, 马上就要完了, 可是也不知道这个完了之后等待的我的是什么...

说回之前的nginx, 起因是之前七夕, 本想把信纸网站上传到server上面, 可是起码debug了我一个小时都没有发现到底是出了什么问题, 后来才发现是nginx语句的问题.

```
server {
  listen 80;
  server_name loveyan.minpeng.me www.loveyan.minpeng.me;
  location / {
      root /home/ycao/src/git/Valentine;
      if (!-e $request_filename){
          rewrite ^ /index.html?$1 break;
      }
  }
}

server {
    listen 80;
    server_name resume.yancao-terry.com www.resume.yancao-terry.com;
    location / {
        root /home/ycao/src/git/resume;
        rewrite ^ /resume.pdf break;
    }
}
```

这两个东西的返回的方式不一样, 后者强制返回resume.pdf, 前者需要加入request_filename, 如果找不到的话就会返回index. 之前遇到的问题就是后面那个除了resume以外在request_file里添加任何东西都会显示Permission denied. 所以这两种返回情况要分开.

-----

然后说点最近学到的东西吧.

最近更新了emacs, 而且我的emacs可以在里面直接运行python region了, 简直是小无敌.

之前面试被问到unit test and test driven development, 当时完全没听说过, 现在知道了以后发现居然有那么多的工具来做TDD, 觉得自己以后写点小东西也可以用一用, 或者至少多写点try catch吧, 现在就这个写的实在是太少了, 但是见的不少, 关键还是不知道什么时候该写什么时候不用写于是干脆都不写了...

今天先这些.
