Shifting left
===========================================================

Application security has evolved over the last several years as software architecture has changed. The main goal of application security remains the same: to mitigate vulnerabilities and other threats. Today’s SDLC is faster, more iterative, and more distributed. With teams dispersed geographically and application components separated into microservices on cloud infrastructure, the network has become an attractive attack surface. And the complexity of protecting applications continues to grow.

Shift Left is a practice intended to find and prevent defects early in the software delivery process. The idea is to improve quality by moving tasks to the left as early in the lifecycle as possible.

Many factors can make such a significant cultural shift difficult, from entrenched processes, to budget, to internal politics. More on the current security landscape for cloud native application architecture, a few types of threats, and some strategies and tools for bringing a shift-left strategy to the continuous integration and continuous deployment (CI/CD) software pipeline.

.. image:: _static/images/in-progress.png
  :alt: Forever in progress ...

----

.. toctree::
   :glob:
   :maxdepth: 1
   :includehidden:
   :caption: Notes

   docs/notes/README.md
   docs/notes/story.md
   docs/notes/challenges.md
   docs/notes/barebones.md

.. toctree::
   :glob:
   :maxdepth: 1
   :includehidden:
   :caption: SSDLC

   docs/ssdlc/README.md
   docs/ssdlc/implement.md
   docs/ssdlc/risk-assess.md
   docs/ssdlc/threat-model.md
   docs/ssdlc/coding.md
   docs/ssdlc/sec-assess.md
   docs/ssdlc/methodologies.md

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
