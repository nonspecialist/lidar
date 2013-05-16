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

Lidar pretty much relies on NRDP, since NSCA only has support for check
result forwarding;
[NRDP](http://exchange.nagios.org/directory/Addons/Passive-Checks/NRDP--2D-Nagios-Remote-Data-Processor/details "Link to NRDP site")
adds the ability to forward Nagios external commands as well (with some
fairly simple authentication), plus passes these results via HTTP or
HTTPS which tends to work better in a distributed environment since
those protocols are usually permitted to flow around the place.
