# d3-package-dependency

Package Depencency Graph using D3 based on Hierarchical Edge Bundling.

The resulting interactive graph visualizes the how bundles depend on each other. This can be helpful when checking which bundle loads which bundle in a OSGi-Framework.

Based on [Mike Bostock Hierarchical Edge Bundling](https://bl.ocks.org/mbostock/7607999, "Hierarchical Edge Bundling").


## JSON

Takes a json specifying which package imports which package and visualizes it.
~~~
[
{"name":"org.onosproject.onos-protocols-netconf-api","size":1,"imports":["com.google.guava","org.onosproject.onlab-misc","org.onosproject.onos-api","org.onosproject.onos-api","org.ops4j.pax.logging.pax-logging-api","org.ops4j.pax.logging.pax-logging-api"]},
{"name":"org.onosproject.onos-protocols-netconf-ctl","size":1,"imports":["ch.ethz.ganymed.ganymed-ssh2","com.google.guava","com.google.guava","org.onosproject.onlab-misc","org.onosproject.onlab-misc","org.onosproject.onos-api","org.onosproject.onos-api","org.onosproject.onos-api","org.onosproject.onos-api","org.onosproject.onos-api","org.onosproject.onos-protocols-netconf-api","org.apache.felix.scr","org.ops4j.pax.logging.pax-logging-api","org.ops4j.pax.logging.pax-logging-api"]},
{"name":"org.onosproject.onos-providers-netconf-device","size":1,"imports":["com.fasterxml.jackson.core.jackson-databind","com.fasterxml.jackson.core.jackson-databind","com.google.guava","com.google.guava","org.onosproject.onlab-misc","org.onosproject.onlab-misc","org.onosproject.onos-api","org.onosproject.onos-api","org.onosproject.onos-api","org.onosproject.onos-incubator-api","org.onosproject.onos-api","org.onosproject.onos-api","org.onosproject.onos-api","org.onosproject.onos-api","org.onosproject.onos-api","org.onosproject.onos-api","org.onosproject.onos-api","org.onosproject.onos-api","org.onosproject.onos-api","org.onosproject.onos-protocols-netconf-api","org.ops4j.pax.logging.pax-logging-api","org.ops4j.pax.logging.pax-logging-api"]},
{"name":"org.onosproject.onos-drivers-netconf","size":1,"imports":["com.google.guava","org.apache.commons.configuration","org.onosproject.onos-api","org.onosproject.drivers.utilities","org.onosproject.onos-api","org.onosproject.onos-api","org.onosproject.onos-api","org.onosproject.onos-api","org.onosproject.onos-protocols-netconf-api","org.ops4j.pax.logging.pax-logging-api","org.ops4j.pax.logging.pax-logging-api"]},
{"name":"org.onosproject.drivers.utilities","size":2,"imports":[]},
{"name":"org.apache.felix.scr","size":2,"imports":[]},
{"name":"com.fasterxml.jackson.core.jackson-databind","size":2,"imports":[]},
{"name":"org.onosproject.onlab-misc","size":2,"imports":[]},
{"name":"org.apache.commons.configuration","size":2,"imports":[]},
{"name":"org.onosproject.onos-api","size":2,"imports":[]},
{"name":"org.onosproject.onos-incubator-api","size":2,"imports":[]},
{"name":"org.ops4j.pax.logging.pax-logging-api","size":2,"imports":[]},
{"name":"ch.ethz.ganymed.ganymed-ssh2","size":2,"imports":[]},
{"name":"com.google.guava","size":2,"imports":[]}
]
~~~

Size is a dummy value:

* size=1 specifies that the bundle is in the loaded bundles
* size=3 specifies that the bundle is loaded by another bundle, but currently not loaded

## Visualization

![Vis](/example.png "Vis")

Single bundles can be hovered. 

* The bundles this bundle includes are then highlighted with a red line between them.
* The bundles which include this bundle are highlighted with a green line.

Single nodes can be clicked to remember the highlighting and allow hovering another line.

## Testing

To test the graph locally, you need to start a local webserver, e.g. using `python -m SimpleHTTPServer`