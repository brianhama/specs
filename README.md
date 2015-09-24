# Open Storage Specifications

Libopenstorage defines a specification to provision and manage  storage volumes for Linux containers in a distributed, multi-node environment.  It also provides a UX guideline for provisioning storage for stateful applications deployed in Linux containers.

We hope that this work aligns with the Open Containers Project.

We also encourage anyone that has an interest in supporting stateful Linux containers to join this effort. 

# The Six Factors of Storage for Linux Containers

This specification defines the following six factors of provisioning storage to Linux Containers:

1. A vendor neutral software spec that can be included as part of the Container spec.  This spec defines the properties of the storage volume, such as a specific class of service and snapshot requirements.  It also allows for an initial format of the volume with the required filesystem and its properties.

2. A RESTful API for orchestrating the provisioning of a volume, such that it can be driven by the container orchestration software.

3. An interface for binding a volume into a container's namespace.

4. A specific API for operating containers in a multi host environment.  This interface can be integrated with the distributed multi node container scheduler.

5. An interface for container granular storage operations.  These include Snapshots, Class of Service (CoS) and Clones.

6. A specification for implementing data protection for stateful containers.

# What the Open Storage specification actually specifies

Open Storage specifies the following three components of storage integration into Linux containers:

1. The specifics of the integration of a storage volume provider into the container runtime in such a way that the volume driver will work in a multi node, distributed scheduler environment.  This includes a specific driver interface that a driver would need to implement.  This part of the spec also covers how to handle quiesce a running container so that the volumes can be made stable for a clone, snapshot or backup operation.

2. A JSON and YAML specification for describing the properties of a storage volume.  This specification can be included as part of a container manifest or can be made available to the container scheduling engine some other way.  Either way, the scheduling engine that conforms to the openstorage specification will make this volume spec available to the driver.
 
### Reference implementation.
A reference implementation is available [here](https://github.com/libopenstorage/openstorage).

# Contributing

The specification and code is licensed under the Apache 2.0 license found in 
the `LICENSE` file of this repository.  

### Sign your work

The sign-off is a simple line at the end of the explanation for the
patch, which certifies that you wrote it or otherwise have the right to
pass it on as an open-source patch.  The rules are pretty simple: if you
can certify the below (from
[developercertificate.org](http://developercertificate.org/)):

```
Developer Certificate of Origin
Version 1.1

Copyright (C) 2004, 2006 The Linux Foundation and its contributors.
660 York Street, Suite 102,
San Francisco, CA 94110 USA

Everyone is permitted to copy and distribute verbatim copies of this
license document, but changing it is not allowed.


Developer's Certificate of Origin 1.1

By making a contribution to this project, I certify that:

(a) The contribution was created in whole or in part by me and I
    have the right to submit it under the open source license
    indicated in the file; or

(b) The contribution is based upon previous work that, to the best
    of my knowledge, is covered under an appropriate open source
    license and I have the right under that license to submit that
    work with modifications, whether created in whole or in part
    by me, under the same open source license (unless I am
    permitted to submit under a different license), as indicated
    in the file; or

(c) The contribution was provided directly to me by some other
    person who certified (a), (b) or (c) and I have not modified
    it.

(d) I understand and agree that this project and the contribution
    are public and that a record of the contribution (including all
    personal information I submit with it, including my sign-off) is
    maintained indefinitely and may be redistributed consistent with
    this project or the open source license(s) involved.
```

then you just add a line to every git commit message:

    Signed-off-by: Joe Smith <joe@gmail.com>

using your real name (sorry, no pseudonyms or anonymous contributions.)

You can add the sign off when creating the git commit via `git commit -s`.
