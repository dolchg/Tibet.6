
### ctpMarket 

1. 当日日内接收的Tick会存在晚上的错误Tick
```
sc1907 合约 日盘期间莫名收到晚上时间的Tick记录，时间都在23：xx
```

2. 隔日的合约的Tick时间不连续

```
在接收凌晨跨日的合约Tick时，隔日的Tick时间是下一个交易日的时间，而不是当日时间。

原始接收Tick时间
"ActionDay\" : \"20190615\", 
"TradingDay\" : \"20190617\", 
"UpdateTime\" : \"00:59:02\",

20190614 为周五 ， 下周一 20190617为下一个交易日， 当前日期为20190615 

此Tick存储时应该属于15日的还是17日的？


"DateTime" : "20190617 00:59:02.500\", 
```
目前程序处理对于这种非连续交易日的情况，会丢弃凌晨12点之后的tick数据
