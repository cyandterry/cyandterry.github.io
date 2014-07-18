今天在网上无意中发现了Python获得git信息的小script, 于是发现之前一直想解决的github streak problem可以分分钟搞定了, 毫不犹豫地搞起.

弄好的Script将会先对每个git path做git pull更新仓库, 同时check last mod date, 如果所有path最后更新日期都不是今天的话, 就会向固定文件写入些没用的东西, 然后git push, 这样今天的streak就不会破啦!

在这里我决定就用这个文件吧. 每次写入没有streak的日期, 也算是记录下这个小app挽救了多少天的streak, 然后我就能一直保持streak啦!

Dates: 
2014-07-12 2014-07-14 2014-07-15 2014-07-16 2014-07-17 