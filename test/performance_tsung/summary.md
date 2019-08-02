```xml
<?xml version="1.0"?>
<!DOCTYPE tsung SYSTEM "/usr/share/tsung/tsung-1.0.dtd">
<tsung loglevel="notice" version="1.0">

  <!-- Client side setup -->
  <clients>
    <client host="localhost" use_controller_vm="true" maxusers='2000'/>
  </clients>
  
  <!-- Server side setup -->
  <servers>
    <server host="localhost" port="80" type="tcp"></server>
  </servers>

  <!-- to start os monitoring (cpu, network, memory). Use an erlang
  agent on the remote machine or SNMP. erlang is the default --> 
  <monitoring>
    <monitor host="localhost" type="snmp"></monitor>
  </monitoring>
  
  <load>
  <!-- several arrival phases can be set: for each phase, you can set
  the mean inter-arrival time between new clients and the phase
  duration -->
   <arrivalphase phase="1" duration="10" unit="minute">
     <users interarrival="0.01" unit="second"></users>
   </arrivalphase>
   <arrivalphase phase="2" duration="10" unit="minute">
     <users interarrival="0.025" unit="second"></users>
   </arrivalphase>
   <arrivalphase phase="3" duration="10" unit="minute">
     <users interarrival="0.05" unit="second"></users>
   </arrivalphase>
  </load>

  <sessions>
  <session name="http-example" probability="100" type="ts_http">

<!--    
    README: This is the request against your varnish local cache. Put your own paramters: provider_key, usage, and app_id, app_key or user_key
    <request> <http url="/transactions/authrep.xml?provider_key=3scale-5f491998ac038e4e8f212cc1e8cf01d2&amp;app_id=551150021&amp;usage[hits]=1" method="GET" version="1.1"></http> </request> 
-->

  </sessions>
</tsung>
```

