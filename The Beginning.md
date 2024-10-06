## Abstract

Initial Email that set this thing rolling

```
Just wanted to formalize the senior project plan to have a more concrete idea before enrolling next quarter with you(if possible).

  

**Senior** **Project****:**

Idea/Abstract: Original idea was setting up an on-prem cloud at my homelab as a way to gain some knowledge about OpenStack and setting up my own custom stack to just do some self-hosted services but our conversation the other day got me thinking about setting up a class lab env from scratch similar to what's in the existing server room. An environment that allows (admins/professors) to upload golden images or a golden network template that can be automatically constructed given a class roster list. Where students and professors can access the VMs remotely, can't access anyone else's, can be configured to reach out to the internet. With reset buttons for both students and professors.

**Main Goals (Kinda in Order):**

- pfSense Firewall with DDNS/Domain Set-up (I have my own for now)
    
- Openstack research on which modules to set up for compute, networking, storage, virtualization, orchestration, and management
    
- Spin up Openstack modules, play around with secure settings
    
- Spin up some virtual machines on an isolated network
    
- Apache Guacamole pointing toward those machines
    
- Set up an admin panel to
    
- Upload vm images
    
- Handle upload and available
    
- Verify images can be instantiated
    
- Potentially access student VM's
    
- Set up to reset VM's
    
- Once one isolated network can be made with golden images
    
- AUTOMATE with rosters!
    
- DOCUMENT EVERYTHING - There has to be an internal tool that can host documentation so people can access it.

Deep Dive Goals(Done if main goals were met):

- Handle special case scenarios like ML work scheduling(?)  
    
- Deeper configuration/ pentest analysis
    
- Variable student-isolated networks
    
- I.e Like Spring Quarter setting up a network with all the students' VMs on the same net and being able to attack each other for one class, alongside another with the standard set-up etc.
    
Typing it all out it seems almost too much but definitely feels doable given a span of 2 quarters. Goals are semi-setup in a way that they build on each other so it's good for watching progress. As well having more stuff lets me keep going till there's nothing left to be done or I hit the time limit and do a detailed post-mortem on why deadlines weren't met. Let me know your thoughts, comments, and potential changes if any.
```

To reiterate

- Include a router setup to mimic actual prod environment and separate from home network
- Setup the entire OpenStack stack of components across multiple devices with some differences between the tasks of devices (i.e Controller and Compute nodes)
- Set up a dashboard to graph machine status and health (Grafana/Prometheus/Dashboard Software)
- Set-up a dashboard to simplify administration process for Professors to:
	- Upload VM images - Golden Copies
		- Sanity check to make sure it can be instantiated
	- Replicate multiple instances of VM for each student from a roster
	- Retain access to VMs
	- Potentially rest VMs to base
	
With deep dives in:
- Handling special hardware scenarios:
	- 2vm private networks (linux virus dev and windows target)
	- GPU accelerating projects
	- Attacking other VMs
- More/Custom Openstack configurations

# Specs

[Spec's](Spec's.md)