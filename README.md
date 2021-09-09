# Improving OSS Provinance

If you're visiting here, it's probably because you received a PR from @msftenhanceprovenance! This is a project at Microsoft managed by a team working in the supply chain security space. If you'd like ot learn more about what sorts of things we're working on and why, this is the spot.

# Project!

Most modern software is built on top of open source software (OSS), from web application front-ends built using react, IoT devices and libraries using OpenSSL, to entire operating systems such as Debian Linux.  These individual or community-lead projects provide amazing functional and productivity benefits, but also generate novel ways for malicious actors to attack, such as:
* Threats to OSS repositories
    * Malicious maintainers [ESLint-Scope attack](https://eslint.org/blog/2018/07/postmortem-for-malicious-package-publishes)
    *   Malicious transitive dependencies [event-stream attack](https://blog.npmjs.org/post/180565383195/details-about-the-event-stream-incident)
*	Threats to build agents
    *	Build machine compromised ([CCleaner attack](https://www.wired.com/story/inside-the-unnerving-supply-chain-attack-that-corrupted-ccleaner/) | [Solar Winds](https://www.solarwinds.com/securityadvisory))
    *   Build tools compromised ([Visual Studio Linker attack](https://medium.com/faun/zombie-infestation-software-developer-tools-the-ms-visual-studio-attack-7fc8cd257eb9) | [NetBeans IDE attack](https://securitylab.github.com/research/octopus-scanner-malware-open-source-supply-chain))
*	Threats to distribution channels
    *	Typo-squatting ([Example packages](https://latesthackingnews.com/2020/10/11/malicious-npm-packages-published-users-data-on-github-page/))
    *	Modification at rest ([ShadowHammer attack](https://securelist.com/operation-shadowhammer-a-high-profile-supply-chain-attack/90380/1))
    *	Package removal ([left-pad](https://www.theregister.com/2016/03/23/npm_left_pad_chaos/))

With so many technology products built on open source, we see an increasing trend of attacks and malware leveraging OSS dependencies, growing 430% in 2020, especially with Advanced Persistent Threats (APTs): well-funded state-actors with long-term geo-political objectives.

Common defenses for “[compromised software supply chain](https://attack.mitre.org/techniques/T1195/002/)” reported by the Mitre ATT&CK database include: Patch management process to stay up-to-date, Continuous monitoring of vulnerability sources, and verification of binaries through hash validation.  But none of these prevent the attack itself; with the Solar Winds and ShadowHammer events, the **compromised packages have valid signatures and hashes**.

According to Sonatype’s 2020 “[State of the Supply Chain Report](https://www.sonatype.com/resources/white-paper-state-of-the-software-supply-chain-2020)”, **public vulnerabilities are exploited within 3 days**.  This includes the time required to research the exploit itself, develop tools and processes to implement that exploit, and finally execute their attack targeting every company who took longer than 3 days to mitigate.  

## Enhancing trust in OSS software supply chains
At Microsoft, we both participate in the OSS ecosystem, using over 65,000 OSS packages and open-sourcing many products such as .NET and VS Code, and drive it through our investments in GitHub, NuGet, and NPM.   By leveraging our unique position, we are seeking to improve the processes and policies for securing OSS software supply chains; but we are not doing this alone, but in collaboration with industry partners, such as the [Linux Foundation’s OpenSSF](https://openssf.org/) (Google, Red Hat, AWS).

Today, we are working to improve trust in OSS developer ecosystem packages (NPM, NuGet, PyPI, Maven Central) by collecting and validating packages and their metadata:
*	Map packages back to their repository and commit ID
*	Verify packaged sources/binaries are faithful compilations of their sources
*	Verify packages are actively maintained and follow security best practices

## Enhancing Provenance information in OSS software supply chains
We are currently updating the provenance information on various OSS NPM repositories. For example, if package.json does not have the repository key, we are creating a pull request such that package.json has that missing information. The goal is that when the next version of the NPM package is published, it contains this information. Pull requests will be created with this account: [msftenhanceprovenance](https://github.com/msftenhanceprovenance).

## Validate our enhanced provenance data
This is useful because it lets you tie a NPM package to a source repository after publication, which has many uses in creating a more secure ecosystem. We then use this information to do static validation for the same artifact against the sources that were published. We also verify that we can rebuild the same artifact from sources that were published, which gives us some confidence that the publication environment was not corrupt.

## OpenSSF scorecard
To support our efforts to enhance trust in packaged OSS, we collect and use the checks available in the [OpenSSF’s Security Scorecard](https://security.googleblog.com/2021/06/introducing-slsa-end-to-end-framework.html).  These checks can be autonomously run again against the source repositories to collect a standardized set of supply chain and repository health metrics.

## Contributing

This project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.opensource.microsoft.com.

When you submit a pull request, a CLA bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., status check, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

## Trademarks

This project may contain trademarks or logos for projects, products, or services. Authorized use of Microsoft 
trademarks or logos is subject to and must follow 
[Microsoft's Trademark & Brand Guidelines](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks/usage/general).
Use of Microsoft trademarks or logos in modified versions of this project must not cause confusion or imply Microsoft sponsorship.
Any use of third-party trademarks or logos are subject to those third-party's policies.
