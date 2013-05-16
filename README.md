What is Lidar?
==============

It's a Nagios addon which allows the monitoring service to be
reconfigured dynamically, based on changes to the monitored topology
outside the monitoring server.

How is Lidar different from Radar?
----------------------------------

[Radar](http://exchange.nagios.org/directory/Addons/Passive-Checks/Radar--2D-add-hosts-and-services-automatically/details "Link to Radar on nagios exchange")
permits the dynamic addition of hosts and services based on a pair of
simple, generic templates.

Lidar adds:

* external hosts/services can register themselves for active checks
* passive check registrations can define their own freshness thresholds
* hosts and services can remove themselves from monitoring (for example
  when they are shut down)
* hostgroup and servicegroup membership can be registered, as can
  dependencies on existing monitors

What dependencies does Lidar have?
----------------------------------

Lidar works with Nagios, and is firmly based in the concepts used within
Nagios. It's intended to provide missing functionality to Nagios, so it
probably won't be easy (or even possible) to adapt to other monitoring
systems. 

Other than that, you need a reasonably standard Python runtime
environment.

What other projects work well with Lidar?
-----------------------------------------

Lidar works well with NRDP, since NSCA only has support for check
result forwarding;
[NRDP](http://exchange.nagios.org/directory/Addons/Passive-Checks/NRDP--2D-Nagios-Remote-Data-Processor/details "Link to NRDP site")
adds the ability to accept Nagios external commands as well (with some
fairly simple authentication), via HTTP or
HTTPS which tends to work better in a distributed environment since
those protocols are usually permitted to flow around the place.

Since NRDP is most commonly implemented on top of Apache (or some other
webserver), the SSL and authentication component is handed off to that
layer, which makes NRDP much simpler.

If you need some way of getting the check results (and remote command
submissions) from one Nagios system to another, there are a few ways:

* `send_nrdp` which comes in various flavours (Perl, Python, PHP, etc)
  and which takes care of submitting a single NRDP result across the
  wire to a remote NRDP server
* `NSCAweb` which reads from a local Nagios server and forwards the
  check results to (potentially many) remote systems in different
  formats, one of which is NRDP.
