# Application Tracing Configuration

For a detailed information on the following technologies, please follow the linked documentation: 
- [x] [Java](https://docs.datadoghq.com/tracing/setup_overview/setup/java)
- [ ] [Python](https://docs.datadoghq.com/tracing/setup_overview/setup/python)
- [ ] [Ruby](https://docs.datadoghq.com/tracing/setup_overview/setup/ruby)
- [ ] [C++](https://docs.datadoghq.com/tracing/setup_overview/setup/cpp)
- [ ] [Go](https://docs.datadoghq.com/tracing/setup_overview/setup/go)
- [ ] [NodeJS](https://docs.datadoghq.com/tracing/setup_overview/setup/nodejs)
- [ ] [.NET Framework](https://docs.datadoghq.com/tracing/setup_overview/setup/dotnet-framework)
- [ ] [.NET Core](https://docs.datadoghq.com/tracing/setup_overview/setup/dotnet-core)
- [ ] [PHP](https://docs.datadoghq.com/tracing/setup_overview/setup/php)

## Variables

The main variables can be declared at the environment level or can also be injected in the Java parameters.

* Environment level variables
  * enable service: `export DD_ENV=prod`
  * enable version: `export DD_SERVICE=my-app`
  * enable environment: `export DD_VERSION=1.0`
  * enable log injection: `export DD_LOGS_INJECTION=true`
* JAVA options variables
  * enable environment: `-Ddd.env=prod`
  * enable service: `-Ddd.service=my-app`
  * enable version: `-Ddd.version=1.0`
  * enable log injection: `-Ddd.logs.injection=true`

## JAVA APM tracing

Most of the technologies, above listed, require a download of a library.

- [x] Download the `dd-java-agent.jar` and store in a location with datadog user permissions
- [x] enable tracing
- [x] enable profiling
- [x] enable log injection
- [x] enable tracing sample rate
- [ ] customize tags

The following example covers: APM tracing, App profiling, Injection of Log trace ID, 

* Download Java agent library: `wget -O /path/to/dd-java-agent.jar https://dtdg.co/latest-java-tracer`
* enable tracing on application: `java -javaagent:/path/to/dd-java-agent.jar`
* Java Profiling: `-Ddd.profiling.enabled=true -XX:FlightRecorderOptions=stackdepth=256`
* Java log injection: `-Ddd.logs.injection=true`
* Java sampling: `-Ddd.trace.sample.rate=1`
* Required tags: `-Ddd.service=my-app -Ddd.env=staging -Ddd.version=1.0`
* Custom tags: `-Ddd.tags=owner:logistics-team,project:jit-shipment`
* Application: `-jar /path/to/your/app.jar`

**Note:** environment variables can be used instead of declaring the `-Ddd` java options.

> Complete Java configuration:

```bash
java -javaagent:/path/to/dd-java-agent.jar \
-Ddd.profiling.enabled=true -XX:FlightRecorderOptions=stackdepth=256 \
-Ddd.logs.injection=true \
-Ddd.trace.sample.rate=1 \
-Ddd.service=my-app -Ddd.env=staging -Ddd.version=1.0 \
-Ddd.tags=owner:logistics-team,project:jit-shipment \
-jar /path/to/your/app.jar
```

## JAVA APM Log Integration

Datadog can automaticall inject log tracing ids, see [Connect Traces and Logs](https://docs.datadoghq.com/tracing/connect_logs_and_traces/):

* [Configure your logger](https://docs.datadoghq.com/logs/log_collection/java) preferrably as JSON, Datadog can also consume RAW logs. This step is optional.
  * [log4j](https://docs.datadoghq.com/logs/log_collection/java/?tab=log4j)
  * [log4j2](https://docs.datadoghq.com/logs/log_collection/java/?tab=log4j2)
  * [logback](https://docs.datadoghq.com/logs/log_collection/java/?tab=logback)

* Correlate the Application to Logs with `trace_id`:
  * [log4j](https://docs.datadoghq.com/logs/log_collection/java/?tab=log4j#inject-trace-ids-in-your-logs)
  ```
  <appender name="FILE" class="org.apache.log4j.FileAppender">
    <param name="File" value="logs/app.log"/>
    <param name="Append" value="true"/>

    <layout class="org.apache.log4j.PatternLayout">
      <param name="ConversionPattern" value="%d{yyyy-MM-dd HH:mm:ss} %-5p %c{1}:%L - %X{dd.trace_id} %X{dd.span_id} - %m%n"/>
    </layout>
  </appender>
  ```
  * [log4j2](https://docs.datadoghq.com/logs/log_collection/java/?tab=log4j2#inject-trace-ids-in-your-logs)
  ```
  <Appenders>
    <File name="FILE" fileName="logs/app.log">
      <PatternLayout pattern="%d{yyyy-MM-dd HH:mm:ss} %-5p %c{1}:%L - %X{dd.trace_id} %X{dd.span_id} - %m%n"/>
    </File>
  </Appenders>
  ```
  * [logback](https://docs.datadoghq.com/logs/log_collection/java/?tab=logback#inject-trace-ids-in-your-logs)

**NOTE:** it may require the restart of the application and the Datadog agent after making log config changes.
