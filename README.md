# karaf-quartz-xml
OSGI Bundled Quartz Scheduler using xml files and pre-configured with an ActiveMQ message sending Job.

Run on the command line with:

    mvn package
    mvn exec:java

Prepare karaf starting with a clean 3.0.5:

    feature:repo-add activemq 5.12.2
    feature:repo-add hawtio 

    feature:install hawtio
    feature:install activemq-broker-noweb 

    bundle:install wrap:mvn:c3p0/c3p0/0.9.1.1
    bundle:install wrap:mvn:org.glassfish.main/javax.ejb/4.0-b33
    bundle:install mvn:org.quartz-scheduler/quartz/2.2.2
    bundle:install wrap:mvn:org.quartz-scheduler/quartz-jobs/2.2.2

Install using hot deploy:

    mvn package
    cp src/test/resources/jobs.xml $KARAF_HOME
    cp target/karaf-quartz-xml-0.0.1-SNAPSHOT.jar $KARAF_HOME/deploy/

Or install via maven:

    mvn install
    bundle:install -s mvn:wsinteg/karaf-quartz-xml/0.0.1-SNAPSHOT

Use hawtio to see the messages created.
