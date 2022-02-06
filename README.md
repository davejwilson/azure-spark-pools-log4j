# Azure Spark Pools - Log4J

This document traces the status of log4j used by Azure Spark Pools.

## Azure Spark Pool Version Info

* Apache Spark Version 3.1
* Java Version 1.8.0_282
* Scala Version 2.12.10

## Apache Spark Version 3.1 - Log4J

### Maven Dependency

```
<log4j.version>1.2.17</log4j.version>
```

### Log4J 1.2 Info

#### Web Site

https://logging.apache.org/log4j/1.2/ (End of Life August 5, 2015 - Advised to upgrade to Log4J 2)

#### Vunerabilities

https://www.cvedetails.com/cve/CVE-2019-17571/
https://www.cvedetails.com/cve/CVE-2020-9488/
https://www.cvedetails.com/cve/CVE-2021-4104/
https://www.cvedetails.com/cve/CVE-2022-23302/
https://www.cvedetails.com/cve/CVE-2022-23305/
https://www.cvedetails.com/cve/CVE-2022-23307/

### Published Vunerability Info

https://github.com/NCSC-NL/log4shell/blob/main/software/software_list_a.md

|Software    |Versions|Status CVE-2021-4104|Status CVE-2021-44228|Status CVE-2021-45046|Status CVE-2021-45105|Notes         |Links|
|------------|--------|--------------------|---------------------|---------------------|---------------------|--------------|-----|
|Apache	Spark|All     |Not vuln            |Not vuln             |Not vuln             |Not vuln             |Uses log4j 1.x|https://lists.apache.org/thread/wwm13b9764vjms5t8n96j6jklys49cyr|

### Conclusion

* "The log4j vulnerability appears to affect log4j 2, not 1.x.
There was mention that it could affect 1.x when used with JNDI or SMS
handlers, but Spark does neither. (unless anyone can think of something I'm
missing, but never heard or seen that come up at all in 7 years in Spark)" - Posted to dev@spark.apache.org

* Log4J 1.x was end of life from August 5, 2015, advise is to upgrade to Log4J 2

### Possible Actions

* Check the log4j 1.x CVE list and make sure that the usage scenarios do not match the vunerabilities
  * If the usage does not match the scenario, short term use is ok
  * If the usage fits the vunerability scenario, an upgrade is needed immediately
* Plan for an upgrade by contacting azure support to:-
  * See when they will be upgrading the version of spark on the spark pools
  * Verify that the new version of spark in the spark pools is secure (void from CVEs)
