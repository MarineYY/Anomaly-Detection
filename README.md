# Anomaly-Detection

这个仓库是构建流式溯源图的一个样例

# 环境搭建

- java 17
- maven 3.8.3及以上（具体的flink，kafka版本在pom.xml中已经配置好）

# 项目框架

## 日志读取和发送

1. 离线读取：直接在项目中添加文件读取模块，将json事件转化为java对象
2. 流式实时读取：将json文件中的日志序列化，通过kafka发送，接收端通过接收这些数据，反序列为java对象

> main.java是入口处

## 接收数据构建溯源图

1. Flink是常用的流式处理框架，接收到事件信息后，使用flink转换操作实现数据流处理，生成流式溯源图
2. 统计事件的频次

> EventFrequencyDBConstructionWithFlink.java 处理流式事件，并统计频次
