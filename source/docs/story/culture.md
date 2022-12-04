# DevSecOps culture

## Promote autonomy of teams

Whether it is a large organization or a start-up in hypergrowth, the only way to not leave security behind is by promoting the autonomy of teams. This can be done by automating processes that fit seamlessly with the development pipeline until security tests become just another type of test, like unit testing, smoke bombs, etc.

Leading by example and promoting education like creating playbooks / runbooks to spot these flaws and fix them, understand their risk, and build confidence in engineers to make the secure decision independently. The ratio of developers, platform, infrastructure engineers, etc., won't be the same as security engineers, and we must understand they can't be in every conversation. Security should act as a supporting function that focuses on building trust and creating as much overlap in knowledge between teams as possible.

## Visibility and transparency

For every tool being introduced or practised, there needs to be a supporting process that provides visibility and promotes transparency to other teams. This means that if we want to build autonomy in groups, as mentioned earlier, they need to have visibility on the security state of the service they own or maintain. For example, a dashboard visualizes the number of security flaws by the criticality of the service. This helps prioritize accordingly, so tasks don't get lost in the backlog or noise, and they can tackle flaws at the right time. The security state measure depends on the company, but it could be the number of high findings a service might or might not have which determine if it is in a good security state.

Transparency would refer to introducing tools and practices that are accessible to teams. For example, if you present a check before merging code, and the review doesn't pass and shows a message saying "signature of possible code injection flaw detected, please remediate," the developer or engineer should have access to the tool that is flagging that message. Usually, these analysis tools that flag those alerts have a UI that specifies the line in code where it's affected. They include a definition and a remediation suggestion with steps. In this example, a developer role can be created so that they have access to more information. This promotes education and autonomy by extending transparency that, traditionally, was only accessible by security teams.

## Account for flexibility thanks to understanding and empathy

Instilling security in DevOps processes with visibility and transparency is no easy task. There is a factor that can determine success: the level of understanding and empathy. This means that the definition of risk for security teams is unequivocal, but for other teams, risk can be different and just as precise for them. This doesn't only apply to risk but to an umbrella of things; it ramifies into what they prioritize, how they work, and what they think is important enough to leave aside a project with a tight deadline to fix a bug.

There is no magic tool or process for everyone. It is essential to understand how developers/engineers work, what they know to be a risk, and what they prioritize. If you know their perspective, it's easier to build a process that finds common ground and has a higher chance to work vs adding another tool that creates more noise and stress for everyone. This understanding builds perspective, which accounts for empathy for how other teams work and builds a process that accounts for flexibility. This is needed because every situation might be different, deadlines might be different, and bandwidth can change over time.

As a DevSecOps engineer, suppose you took the time to understand how a team owns a service. In that case, that will have a security scanner added to its development process, worked and viewed priority; it will be easier to get their buy-in and demonstrate value. For example, if it's a platform team and owns an internal service but a core service, a risk would be a bug that disrupts the service, not a potential injection that lives behind a proxy. You would need internal credentials to exploit it. You can tune the scanners or add a triaging process that tackles the questions they would ask themselves, and this would, in turn, build trust vs crying wolf and security processes being questioned.

## Resources

* [3 DevSecOps success stories](https://www.csoonline.com/article/3439737/3-devsecops-success-stories.html)
