# 问题描述

当启动程序时，Logback会打印许多内部信息的日志，如下：

```
11:16:58,634 |-INFO in ch.qos.logback.classic.LoggerContext[default] - This is logback-classic version 1.4.5
11:16:58,704 |-INFO in ch.qos.logback.classic.LoggerContext[default] - Could NOT find resource [logback-test.xml]
11:16:58,714 |-INFO in ch.qos.logback.classic.LoggerContext[default] - Found resource [logback.xml] at [file:/C:/Users/Ho/Desktop/ruoyi/logback-test/target/classes/logback.xml]
11:16:58,897 |-WARN in ch.qos.logback.classic.joran.action.LevelAction - <level> element is deprecated. Near [level] on line 47
11:16:58,897 |-WARN in ch.qos.logback.classic.joran.action.LevelAction - Please use "level" attribute within <logger> or <root> elements instead.
11:16:59,032 |-INFO in ch.qos.logback.classic.model.processor.ConfigurationModelHandler - Registering a new ReconfigureOnChangeTask ReconfigureOnChangeTask(born:1677122219027)
11:16:59,034 |-INFO in ch.qos.logback.classic.model.processor.ConfigurationModelHandler - Will scan for changes in [file:/C:/Users/Ho/Desktop/ruoyi/logback-test/target/classes/logback.xml] 
11:16:59,035 |-INFO in ch.qos.logback.classic.model.processor.ConfigurationModelHandler - Setting ReconfigureOnChangeTask scanning period to 1 minutes
11:16:59,050 |-WARN in ch.qos.logback.core.model.processor.ImplicitModelHandler - Ignoring unknown property [jmxConfigurator] in [ch.qos.logback.classic.LoggerContext]
11:16:59,060 |-INFO in ch.qos.logback.core.model.processor.AppenderModelHandler - Processing appender named [CONSOLE]
11:16:59,060 |-INFO in ch.qos.logback.core.model.processor.AppenderModelHandler - About to instantiate appender of type [ch.qos.logback.core.ConsoleAppender]
11:16:59,073 |-INFO in ch.qos.logback.core.model.processor.ImplicitModelHandler - Assuming default type [ch.qos.logback.classic.encoder.PatternLayoutEncoder] for [encoder] property
11:16:59,149 |-INFO in ch.qos.logback.core.model.processor.AppenderModelHandler - Processing appender named [ALL]
11:16:59,149 |-INFO in ch.qos.logback.core.model.processor.AppenderModelHandler - About to instantiate appender of type [ch.qos.logback.core.rolling.RollingFileAppender]
11:16:59,169 |-INFO in c.q.l.core.rolling.TimeBasedRollingPolicy@112466394 - No compression will be used
11:16:59,172 |-INFO in c.q.l.core.rolling.TimeBasedRollingPolicy@112466394 - Will use the pattern LOG_HOME_IS_UNDEFINED/log/%d{yyyy-MM-dd}.log for the active file
11:16:59,237 |-INFO in c.q.l.core.rolling.DefaultTimeBasedFileNamingAndTriggeringPolicy - The date pattern is 'yyyy-MM-dd' from file name pattern 'LOG_HOME_IS_UNDEFINED/log/%d{yyyy-MM-dd}.log'.
11:16:59,237 |-INFO in c.q.l.core.rolling.DefaultTimeBasedFileNamingAndTriggeringPolicy - Roll-over at midnight.
11:16:59,238 |-INFO in c.q.l.core.rolling.DefaultTimeBasedFileNamingAndTriggeringPolicy - Setting initial period to Thu Feb 23 11:16:59 CST 2023
11:16:59,240 |-INFO in ch.qos.logback.core.model.processor.ImplicitModelHandler - Assuming default type [ch.qos.logback.classic.encoder.PatternLayoutEncoder] for [encoder] property
11:16:59,243 |-INFO in ch.qos.logback.core.rolling.RollingFileAppender[ALL] - Active log file name: LOG_HOME_IS_UNDEFINED/log/2023-02-23.log
11:16:59,244 |-INFO in ch.qos.logback.core.rolling.RollingFileAppender[ALL] - File property is set to [null]
11:16:59,247 |-INFO in ch.qos.logback.classic.model.processor.LevelModelHandler - ROOT level set to INFO
11:16:59,248 |-INFO in ch.qos.logback.core.model.processor.AppenderRefModelHandler - Attaching appender named [CONSOLE] to Logger[ROOT]
11:16:59,249 |-INFO in ch.qos.logback.core.model.processor.AppenderRefModelHandler - Attaching appender named [ALL] to Logger[ROOT]
11:16:59,249 |-INFO in ch.qos.logback.core.model.processor.DefaultProcessor@3b2da18f - End of configuration.
11:16:59,250 |-INFO in ch.qos.logback.classic.joran.JoranConfigurator@5906ebcb - Registering current configuration as safe fallback point
```

# 解决方法

在Logback配置中使用`NopStatusListener`

```
<!-- 将debug设置为false -->
<configuration debug="false">
    <!-- 添加此行 -->
    <statusListener class="ch.qos.logback.core.status.NopStatusListener" />
</configuration>
```