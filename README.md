# mybatis-generator-lombok-plugin-master
本项目为mybatis-genrator的整合lombok拓展插件，可以支持@Data,@Builder,@Accessors,注解的生成与参数设置
更多注解的支持正在开发中，希望能给大家带来便利
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE generatorConfiguration PUBLIC "-//mybatis.org//DTD MyBatis Generator Configuration 1.0//EN" "http://mybatis.org/dtd/mybatis-generator-config_1_0.dtd">

<generatorConfiguration>
    <context id="default" targetRuntime="MyBatis3Simple" >
        <property name="javaFileEncoding" value="UTF-8"/>
        <!--模糊搜索插件-->
        <plugin type="org.mybatis.generator.plugins.CaseInsensitiveLikePlugin"></plugin>
        <!-- 分页相关 -->
        <plugin type="org.mybatis.generator.plugins.RowBoundsPlugin"/>
        <!-- 带上序列化接口 -->
        <plugin type="org.mybatis.generator.plugins.SerializablePlugin"/>
        <!--通用mapper插件-->
        <plugin type="tk.mybatis.mapper.generator.MapperPlugin">
            <property name="mappers" value="tk.mybatis.mapper.common.Mapper"/>
        </plugin>
        <plugin type="com.feier.mybatis.generator.plgins.CommentPlugin">
            <!-- 抑制警告 -->
            <property name="suppressTypeWarnings" value="true"/>
            <!-- 是否去除自动生成的注释 true：是 ： false:否 -->
            <property name="suppressAllComments" value="false"/>
            <!-- 是否生成注释代时间戳-->
            <property name="suppressDate" value="true"/>
        </plugin>
        <plugin type="com.feier.mybatis.generator.plgins.LombokPlugin">
            <!-- enable annotations -->
            <!-- 开启@Builder-->
            <property name="builder" value="true"/>
            <!--builderClassName默认值为 ""-->
            <property name="builder.builderClassName" value="myBuilder"/>
            <!--builderMethodName默认值为""不设置即为"builder" -->
            <property name="builder.builderMethodName" value="myBuilder"/>
            <!--buildMethodName默认值为"build" -->
            <property name="builder.buildMethodName" value="myBuilder"/>
            <!--toBuilder默认值为false-->
            <property name="builder.toBuilder" value="false"/>
            <!--prefix默认值为 {}，多个用逗号隔开-->
            <property name="accessors.prefix" value="abc,def" />
            <!--插件根据自己的需求来进行配置，@Data默认是开启的，为了方便链式调用再配个@Accessors就足够了足够了，通常配置如下-->
            <!-- 开启@Accessors注解-->
            <property name="accessors" value="true"/>
            <property name="accessors.chain" value="true"/>
        </plugin>

        <!-- 自动为entity生成swagger2文档-->
        <plugin type="mybatis.generator.plugins.GeneratorSwagger2Doc">
            <property name="apiModelAnnotationPackage" value="io.swagger.annotations.ApiModel" />
            <property name="apiModelPropertyAnnotationPackage" value="io.swagger.annotations.ApiModelProperty" />
        </plugin>
        <!-- 扩展entity的set方法-->
        <plugin type="mybatis.generator.plugins.ExtendEntitySetter" />
        <!-- 不希望生成的注释中包含时间戳 -->
        <commentGenerator>
            <property name="suppressDate" value="true"/>
            <property name="suppressAllComments" value="true"/>
        </commentGenerator>
        <jdbcConnection driverClass="com.mysql.jdbc.Driver" connectionURL="jdbc:mysql://192.168.10.202:3306/stekgroup?characterEncoding=utf-8" userId="root" password="123456"></jdbcConnection>
        <!-- true：使用BigDecimal对应DECIMAL和 NUMERIC数据类型 false：默认, scale>0;length>18：使用BigDecimal; scale=0;length[10,18]：使用Long； scale=0;length[5,9]：使用Integer； scale=0;length<5：使用Short； -->
        <javaTypeResolver>
            <property name="forceBigDecimals" value="false"/>
        </javaTypeResolver>
        <javaModelGenerator targetPackage="com.example.feier.entity" targetProject="src/main/java">
            <!-- 是否 自动为每一个生成的类创建一个构造方法 -->
            <!--<property name="constructorBased" value="false"/>-->
            <!--<property name="useActualColumnNames" value="true"/>-->
            <!-- 在targetPackage的基础上，根据数据库的schema再生成一层package -->
            <property name="enableSubPackages" value="false"/>
            <!-- 是否创建一个不可变的类 -->
            <!--<property name="immutable" value="false"/>-->
            <!-- 设置是否在getter方法中，对String类型字段调用trim()方法 -->
            <property name="trimStrings" value="false"/>
            <!--<property name="rootClass" value="java.io.Serializable" />-->
        </javaModelGenerator>
        <!-- 生成SQL map的XML文件生成器 -->
        <sqlMapGenerator targetPackage="mappers" targetProject="src/main/resources"></sqlMapGenerator>
        <javaClientGenerator targetPackage="com.example.feier.dao" targetProject="src/main/java" type="XMLMAPPER">
            <property name="enableSubPackages" value="false" />
        </javaClientGenerator>
        <table tableName="coach_event_process" enableUpdateByExample="true" enableDeleteByExample="true" enableSelectByExample="true" selectByExampleQueryId="true">
            <property name="useActualColumnNames" value="true"/>
            <generatedKey column="cepId" sqlStatement="Mysql"/>
        </table>
    </context>
</generatorConfiguration>

