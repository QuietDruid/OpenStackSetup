
| System Name                | CPU       | Ram                      | Storage                               |
| :------------------------- | :-------- | :----------------------- | :------------------------------------ |
| Prodesk Prime              | i5 - 8th  | 16gb - 1x 16gb Crucial   | 1x 500gb NVME WD SSD                  |
| Prodesk Artemis - SHE DIED | i5 - 8th  | 16gb - 1x 16gb TeamGroup | 1x 400gb SSD, 1x 500gb NVME           |
| Prodesk Apollo             | i5 - 8th  | 16gb - 2x 8gb Mixed      | 1x 400gb SSD, 1x 500gb NVME           |
| King                       | i7 - 10th | 32gb - 2x 16gb TG        | 1x 256gb M.2 ( 1 nvme), 1x 500gb NVME |
|                            |           |                          |                                       |

# OS Choice

There's a lot of server operating systems that could have been chosen for this project considering the sheer amount of linux flavors. Although I needed to choose something that would support Openstack.

The main choices that I seriously considered were:
- RHEL
- Ubuntu
- Debian
- Rocky/Alma/CentOS
- NixOs

But all of these (except one) really didn't pan out. RHEL, while robust is not something I have a lot of experience in and currently with the large task set in front of me I couldn't try to learn this on the go while setting up the services. It would have been a great choice for an existing company who has an admin well acquainted with RHEL but as is I need more experience. Debian was my first choice of distro for this project but after attempting a manual installation of services and other weird behavioral headaches, Debian as a server seemed to not be as stable as I would have liked it to be. The other fringe operating systems that are mentioned are nice niche projects that would be cool in a home lab environment but I couldn't really justify jumping into those distros due to not knowing their upstreams very well + lack of support docs and threads.

Which left Ubuntu as the standing victor. I understand people's feelings when it comes to Ubuntu and snap packages and the weird stuff Canonical has done as a company but its the distro I have the most history with and "just works" with the packages I'm running for OpenStack

## Deployment

So considering the packages at hand, it would be good to utilize some sort of deployment model/playbook to replicate. Granted there's a lot of different possible deployment methods and underlying applications. Like deploying Openstack using charms, juju, puppet, chef, k8s, k3s, ansible, ansible-kolla, and a million other automation frameworks to fit any specific case.

In my specific case, I wanted the easiest way to setup a 3-node hyper-converged cluster cluster that can do compute, storage, and control all as highly-available as possible and 

## Self-Starting

The journal did start following the manual at openstack.com for a manual deployment of the most common services available to run locally. This was quite painful in part due to the 

## Third Time's The Charm?

Turns out Canonical's Microstack was not as easy to stand up as the docs would say and it was a real pain in my ass






