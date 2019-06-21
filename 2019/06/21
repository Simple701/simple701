## 故障案例-bdm底层分区修复问题 

描述： 
    每天早上会对采集数据bdm分区进行统一repair ，如果某个pt分区下无子hour分区则会报错，无法完成修正 

影响： 
    采集数据最新分区不可用，所有下游任务受影响 

根本原因：
    采集数据出现错误的productcode 或数据中断的product code，hour分区自动清理后无新数据出现，导致分区子目录为空
    使用统一的全局分区修复方案，任意分区异常则任务失败

临时解决方案：
     开启debug ： hive --hiveconf hive.root.logger=DEBUG,console 
     执行分区修复sql语句 ，找到异常分区 
     手动 dfs -rm -r 删除异常分区
     任务重新调度执行 

长期解决方案：
     采集分区控制，使用kafka topic 不再使用数据内 product code 
     使用子分区修复任务，任务按业务线划分 （新增product code后需要手动添加）
     

    
