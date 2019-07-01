# mybatis-generator-lombok-plugin-master
本项目为mybatis-genrator的整合lombok拓展插件，可以支持@Data,@Builder,@Accessors,注解的生成与参数设置
更多注解的支持正在开发中，希望能给大家带来便利
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
