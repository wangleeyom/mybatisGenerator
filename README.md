# 简介
该项目可以生成mybatis所需要的pojo、Mapper接口、xxxMapper.xml
# 如何使用
1. 编辑`generatorConfig.xml`，修改数据库连接信息

```
<jdbcConnection 
  driverClass="com.mysql.jdbc.Driver"
	connectionURL="jdbc:mysql://localhost:3306/leaderment" 
	userId="root"
	password="root">
</jdbcConnection>
```
2. 修改pojo、xxxMapper.xml、Mapper接口的生成路径

```
<!-- targetProject:生成Entity类的路径 -->
<javaModelGenerator targetProject=".\src" targetPackage="com.leaderment.orm.pojo">
  <!-- enableSubPackages:是否让schema作为包的后缀 -->
  <property name="enableSubPackages" value="false" />
  <!-- 从数据库返回的值被清理前后的空格 -->
  <property name="trimStrings" value="true" />
</javaModelGenerator>
		
<!-- targetProject:XXXMapper.xml映射文件生成的路径 -->
<sqlMapGenerator targetProject=".\src" targetPackage="com.leaderment.orm.mapper">
  <!-- enableSubPackages:是否让schema作为包的后缀 -->
  <property name="enableSubPackages" value="false" />
</sqlMapGenerator>
		
<!-- targetPackage：Mapper接口生成的位置 -->
<javaClientGenerator type="XMLMAPPER" targetProject=".\src" targetPackage="com.leaderment.orm.mapper">
  <!-- enableSubPackages:是否让schema作为包的后缀 -->
  <property name="enableSubPackages" value="false" />
</javaClientGenerator>
```
3. 指定数据库表名以及我们要生成的pojo的实体类名

```
<table tableName="fulfillment_in_warehouse" domainObjectName="FulfillmentInWarehouse"/>
```
4. 执行`Mbg_GeneratorUtil.java`，刷新src目录，就可以看见生成的文件，将这些文件拷贝到你的项目中即可