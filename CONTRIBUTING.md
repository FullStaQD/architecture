# Contributing to the FullStaQD Architecture
First off, thanks for taking the time to contribute to this project!
An open standard like our architecture depends on a continuous exchange with the
community to live up to the complex requirements of the quantum software
ecosystem.

This guide outlines how you can contribute to this project, and how changes to
the architecture are governed.
Here’s what’s included:
* [Code of Conduct](#code-of-conduct)
* [Asking Questions / Getting Help](#asking-questions--getting-help)
* [Raising Issues](#raising-issues)
* [Changing the Architecture](#changing-the-architecture)
* [Maintainers](#maintainers)
* [Sources](#sources)

## Code of Conduct
This project and everyone participating in it is governed by our
[Code of Conduct](./CODE_OF_CONDUCT.md) (tl;dr: be respectful!).
By participating, you are expected to uphold this code.
Please report unacceptable behaviour to
[fullstaqd@lists.kit.edu](mailto:fullstaqd@lists.kit.edu).

## Asking Questions / Getting Help
To learn about the FullStaQD Reference Architecture, please have a look at our
[architecture documentation](https://fullstaqd.github.io/architecture/).
If you have any questions regarding the architecture, please
[open a new discussion](https://github.com/FullStaQD/architecture/discussions/new?category=q-a)
on our GitHub repository and we will try to help you out.
For confidential requests only, please reach out to
[fullstaqd@lists.kit.edu](mailto:fullstaqd@lists.kit.edu).

## Raising Issues
Please
[raise an issue](https://github.com/FullStaQD/architecture/issues/new/choose) on
our GitHub repository to point out problems with the reference, or to suggest
improvements.
Here are typical issues that we expect to see:
* **Limitations of the architecture:**
  If you find a usage scenario for a quantum software system that cannot be
  accomplished with our architecture, we would love to know about it!
  In your report, please describe your intended usage scenario comprehensively
  and help us understand why it does not fit into our architecture.
* **Addressing new concerns:**
  Please tell us about common aspects in quantum software that are not covered
  by our architecture yet.
  One goal of the architecture is to give guidance on common questions in
  quantum software architecture, so we would love to hear about common questions
  that we have missed.
  In your report, please describe the concern that you would like to address and
  elaborate why this concern is architecturally significant.
* **Minor documentation improvements:**
  You can also use issues to point out shortcomings in the documentation such as
  typos, vague descriptions and inconsistencies.
* **Other issues:** Please feel free to also raise issues that do not fit in the
  above categories!

All issues are up for discussion in the wider community.
They are the drivers for changes to the architecture, as discussed in the next
section.

## Changing the Architecture
The field of quantum software still evolves rapidly, and requirements for its
architecture can change too.
As an open architecture project, we want to keep up with the state of the art
while providing stable interfaces and a clear separation of concerns at the same
time.
This section outlines how we plan to adopt changes to the FullStaQD Reference
Architecture.
1. **Triage:**
   Changes should address relevant shortcomings of the architecture.
   Before implementing any changes, these shortcomings should be discussed
   publicly as issues (see previous section) to establish their relevance.
   Maintainers will investigate relevance of the issues thoroughly through
   discussions with the issue authors, and by consulting relevant
   stakeholders/experts.
   In the end, maintainers need to decide whether to close the issue
   (e.g. dismiss it for being off-topic or architecturally insignificant) or to
   approve it by applying a label.
2. **Suggesting changes:**
   Anyone can suggest changes to address approved issues by opening a
   corresponding pull request.
   Pull requests should ideally address a single issue and clearly state which
   issue that is.
   PRs should be marked as drafts until they are ready to be reviewed.
3. **Reviewing and approving changes:**
   Everyone is welcome to give constructive feedback on the changes suggested in
   a ready PR.
   Reviews should address both the conceptual change and the quality of its
   textual and pictoral descriptions.
   Two maintainers need to sign off the PR for it to be approved.
4. **Merging and releasing changes:**
   We distinguish two types of changes for our release schedule:
   * **Minor improvements** to the documentation can be merged and released as
     soon as they are approved.
   * **Major changes** to the architecture should not be released too
     frequently.
     These changes should be stalled to be released in a planned release
     schedule.
     Early after the initial release, we intend to release such changes at most
     biannually.
     At a later stage, major changes should be much less frequent with an annual
     or even five-year release.

## Maintainers
Maintainers are core contributors of the project.
They are further responsible for triaging issues, approving pull requests,
releasing new versions of the architecture, and upholding the code of conduct.

While the initial version of this project is being developed at KIT as part of
the FullStaQD project, maintainership is with the corresponding researchers at
KIT.
In later stages of this project, we intend to expand the maintainer team to
include other contributors based on their merit and expertise and including a
diverse mix of stakeholders from industry and academia.

The current maintainers are:
* [Max Schweikart (KIT)](https://tva.kastel.kit.edu/english/team_schweikart.php) -- [@schweikart](https://github.com/schweikart)
* [Rinor Kelmendi (KIT)](https://tva.kastel.kit.edu/english/team_kelmendi.php) -- [@RinorKIT](https://github.com/RinorKIT)

## Sources
Parts of this contribution guide were adapted from various open source projects
including
[atom’s contribution guide](https://github.com/atom/atom/blob/master/CONTRIBUTING.md)
and
[openQSE's contribution workflow](https://github.com/openQSE/openqse-spec/blob/b251d3383b71a6b42ec127c27a964bd7adf03319/procedures/contribution_workflow.md).
