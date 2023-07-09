Shifting left
===========================================================

Application security has evolved over the last several years as software architecture has changed. The main goal of application security remains the same: to mitigate vulnerabilities and other threats. Today’s SDLC is faster, more iterative, and more distributed. With teams dispersed geographically and application components separated into microservices on cloud infrastructure, the network has become an attractive attack surface. And the complexity of protecting applications continues to grow.

Shift Left is a practice intended to find and prevent defects early in the software delivery process. The idea is to improve quality by moving tasks to the left as early in the lifecycle as possible.

Many factors can make such a significant cultural shift difficult, from entrenched processes, to budget, to internal politics. More on the current security landscape for cloud native application architecture, a few types of threats, and some strategies and tools for bringing a shift-left strategy to the continuous integration and continuous deployment (CI/CD) software pipeline.

.. image:: _static/images/in-progress.png
  :alt: Forever in progress ...

----

.. toctree::
   :maxdepth: 1
   :includehidden:
   :caption: Testlab

   Cloud tools <https://testlab.tymyrddin.dev/docs/cloud/readme>

----

.. toctree::
   :glob:
   :maxdepth: 1
   :includehidden:
   :caption: Notes

   docs/notes/README.md
   docs/notes/story.md
   docs/notes/challenges.md
   docs/notes/methodologies.md
   docs/notes/implement.md
   docs/notes/risk-assessment.md
   docs/notes/pia.md
   docs/notes/threat-model.md
   docs/notes/coding.md
   docs/notes/sec-assessment.md
   docs/notes/automation.md
   docs/notes/shared.md
   docs/notes/vms.md
   docs/notes/db-services.md
   docs/notes/containers.md
   docs/notes/functions.md
   docs/notes/object.md
   docs/notes/block.md
   docs/notes/file.md
   docs/notes/csi.md
   docs/notes/virt.md
   docs/notes/dns.md
   docs/notes/cdn.md
   docs/notes/vpn.md
   docs/notes/ddos.md
   docs/notes/waf.md
   docs/notes/iam.md
   docs/notes/monitoring.md

----

.. toctree::
   :glob:
   :maxdepth: 1
   :includehidden:
   :caption: Labs

   docs/labs/barebones.md

----

Best practices
------------------------------------------

.. toctree::
   :glob:
   :maxdepth: 1
   :includehidden:
   :caption: AWS

   docs/aws/README.md
   docs/aws/ec2.md
   docs/aws/rds-mysql.md
   docs/aws/ecs.md
   docs/aws/eks.md
   docs/aws/lambda.md
   docs/aws/s3.md
   docs/aws/ebs.md
   docs/aws/efs.md
   docs/aws/csi.md
   docs/aws/vpc.md
   docs/aws/route53.md
   docs/aws/cloudfront.md
   docs/aws/s2s-vpn.md
   docs/aws/client-vpn.md
   docs/aws/shield.md
   docs/aws/waf.md
   docs/aws/iam.md
   docs/aws/directory.md
   docs/aws/mfa.md

.. toctree::
   :glob:
   :maxdepth: 1
   :includehidden:
   :caption: Azure

   docs/azure/README.md
   docs/azure/vms.md
   docs/azure/db-mysql.md
   docs/azure/aci.md
   docs/azure/aks.md
   docs/azure/functions.md
   docs/azure/blob.md
   docs/azure/disks.md
   docs/azure/files.md
   docs/azure/csi.md

.. toctree::
   :glob:
   :maxdepth: 1
   :includehidden:
   :caption: GCP

   docs/gcp/README.md
   docs/gcp/gce.md
   docs/gcp/sql-mysql.md
   docs/gcp/gke.md
   docs/gcp/functions.md
   docs/gcp/storage.md
   docs/gcp/disk.md
   docs/gcp/filestore.md
   docs/gcp/csi.md

----

Books
---------------------------

.. card-carousel:: 3

    .. card::
        :link: http://devops.com/2015/10/13/devops-systems-record-new-hope-preview-talk/

        .. image:: _static/images/bookcovers/devops.png

    .. card::
        :link: https://nostarch.com/devops-desperate

        .. image:: _static/images/bookcovers/desperate-devops.png

    .. card::
        :link: https://www.manning.com/books/securing-devops

        .. image:: _static/images/bookcovers/securing-devops.png

    .. card::
        :link: https://bpbonline.com/products/implementing-devsecops-with-docker-and-kubernetes

        .. image:: _static/images/bookcovers/devsecops-containers-kubernetes.png

    .. card::
        :link: https://nostarch.com/designing-secure-software

        .. image:: _static/images/bookcovers/designing-secure-software.png

    .. card::
        :link: https://nostarch.com/websecurity

        .. image:: _static/images/bookcovers/web-security-for-developers.png
