## Hyperic HQ HornetQ plugin

This project is a Hyperic HQ plugin for monitoring [HornetQ](http://www.jboss.org/hornetq/)

This HornetQ plugin is intended for monitoring stand-alone installations of HornetQ.
It should also support embedded HornetQ installations.

Source code is available at [github.com/ClarityServices/hyperic-hornetq](https://github.com/ClarityServices/hyperic-hornetq)

### Platform Support

Should support HornetQ Server running on any platform

### Auto-Discovery

After installing the hyperic plugin add the server "HornetQ V2.x" to the platform
being monitored.

### Metrics

For the complete list of Metrics available, please see the [HyperForge HornetQ documentation](http://support.hyperic.com/display/hypcomm/HornetQ)

Metrics Being Gathered:

* HornetQ Connection Count

* Queue Depth

* Message Processing Rates

* Java Heap Free and Used

* Thread Count

* Garbage Collection Count & Time per Minute

### Log File Tracking

Messages are optionally reported from hornetq.log and can be filtered by 
regex include/exclude.

### Config File Tracking

The hornetq config file can be monitored for changes. See client installation
instructions below

### Control Actions

For a queue:

* pause

* resume

* sendMessagesToDeadLetterAddress

* listMessages

* moveMessages

* listMessageCounterAsHTML

* listMessageCounterHistoryAsHTML

### Dependencies

Remote JMX must be enabled first for the HornetQ server

### Mongodb Version Support

Tested on Red Hat Enterprise Linux 5 with HornetQ 2.1.2.Final

### Hyperic HQ Version Support

Tested with [Hyperic HQ](http://www.hyperic.com/) version 4.4

### Install

Server Installation

* Copy the file _hyperic-hornetq.xml_ into the following folder under the server installation:
    hq-engine/server/default/deploy/hq.ear/hq-plugins

* Output similar to the following should appear in the server logfile (logs/server.log)
<pre>
2011-02-21 13:53:53,972 INFO  [ScannerThread] [org.hyperic.hq.product.server.mbean.ProductPluginDeployer@654] HQ plugin hornetq-plugin.xml undeployed
2011-02-21 13:53:53,995 INFO  [ScannerThread] [org.hyperic.hq.product.server.mbean.ProductPluginDeployer@654] HQ plugin hornetq registered
2011-02-21 13:53:54,001 INFO  [ScannerThread] [org.hyperic.hq.product.server.session.ProductManagerEJBImpl@320] hornetq unknown -- registering
2011-02-21 13:53:54,217 INFO  [ScannerThread] [org.hyperic.hq.product.server.mbean.ProductPluginDeployer@654] HQ plugin hornetq deployed
</pre>

#### Client Installation

* Add this line to the run.sh file which starts HornetQ, before the line that starts with: "export JVM_ARGS"

    export CLUSTER_PROPS="$CLUSTER_PROPS -Dcom.sun.management.jmxremote -Dcom.sun.management.jmxremote.port=6969 -Dcom.sun.management.jmxremote.ssl=false -Dcom.sun.management.jmxremote.authenticate=false"

* Copy the file _hyperic-hornetq.xml_ into the plugins folder under the client installation. The path should be similar to:
    agent/bundles/agent-4.4.0-1509/pdk/plugins/
* Restart the agent to pull in the new plugin file

### Meta

* Code: `git clone git://github.com/ClarityServices/hyperic-hornetq.git`
* Home: <https://github.com/ClarityServices/hyperic-hornetq>
* Bugs: <https://github.com/ClarityServices/hyperic-hornetq/issues>

### Developers

To generate updated documentation for the HyperForge Wiki, run the following command:

    java -jar bundles/agent-4.4.0-1509/pdk/lib/hq-product.jar -Dplugins.exclude=vsphere -m generate -a metrics-wiki

Then update the page on [HyperForge](http://support.hyperic.com/display/hypcomm/HornetQ)

### Author

Reid Morrison :: rubywmq@gmail.com :: @reidmorrison

### License

Copyright 2011 Clarity Services, Inc.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
