# Implementing SSDLC

Secure SDLC involves instilling security processes at all lifecycle phases. From security testing tools to writing security requirements alongside functional requirements.

## Security posture

Understanding the gaps and current state is critical for successfully introducing a new tool, solution, or change.

To help grasp what the current security posture is, start by doing the following:

* Perform a gap analysis to determine what activities and policies exist in the organisation and how effective they are. For example, ensuring policies are in place (what the team does) with security procedures (how the team executes those policies).
* Create Software Security Initiatives (SSI) by establishing realistic and achievable goals with defined metrics for success. For example, this could be a Secure Coding Standard, playbooks for handling data, etcetera are tracked using project management tools.
* Formalise processes for security activities within your SSI. After starting a program or standard, it is essential to spend an operational period helping engineers get familiarised with it and gather feedback before enforcing it. When performing a gap analysis, every policy should have defined procedures to make them effective.
* Invest in security training for engineers as well as appropriate tools. Ensure people are aware of new processes and the tools that will come with them to operationalise them, and invest in training early, ideally before using the tool. 

## SSDLC processes

A secure SDLC involves integrating processes like security testing and other activities into <br>an existing development process:

![Implementation](../../_static/images/implementation.png)

* [Risk Assessment](risk-assessment.md) - during the early stages of SDLC, it is essential to identify security considerations that promote a security by design approach when functional requirements are gathered in the planning and requirements stages. For example, if a user requests a blog entry from a site, the user should not be able to edit the blog or remove unnecessary input fields.
* [Threat Modelling](threat-model.md) - is the process of identifying potential threats when there is a lack of appropriate safeguards. It is very effective when following a risk assessment and during the design stage of the SDLC, as Threat Modelling focuses on what should not happen. In contrast, design requirements state how the software will behave and interact. For example, ensure there is verification when a user requests account information.
* [Code Scanning / Review](coding.md) -  Code reviews can be either manual or automated. Code Scanning or automated code reviews can leverage Static and Dynamic Security testing technologies. These are crucial in the Development stages as code is being written.
* [Security Assessments](sec-assessment.md) - Like Penetration Testing, Vulnerability Assessments are a form of automated testing that can identify critical paths of an application that may lead to exploitation of a vulnerability. However, these are hypothetical as the assessment doesn't carry simulations of those attacks. Pentesting, on the other hand, identifies these flaws and attempts to exploit them to demonstrate validity. Pentests and Vulnerability Assessments are carried out during the Operations & Maintenance phase of the SDLC after a prototype of the application.




