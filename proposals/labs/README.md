
# 2: Labs


<table>
  <tr>
   <td><strong>Champions</strong>
   </td>
   <td>James Rawlings
   </td>
  </tr>
  <tr>
   <td><strong>Story / Task</strong>
   </td>
   <td>New features for Jenkins X
   </td>
  </tr>
</table>

# 1. Overview

We want to continue to innovate with Jenkins X, increase community contributions while all the time ensuring that Jenkins X continues to build in stability and reliability.

This proposal introduces the idea of creating an incubation area of sorts called **Jenkins X Labs** where we can experiment, inovate and attract a wider community contribution, working in a sandboxed area such that newer changes do not go into the main codebase until there's confidence in them.

Observing how other heavily based CLI projects work, such as `gcloud`, have the concept of `alpha` and `beta` CLI components that introduce changes to users who opt into them. This is a great way to gather feedback and reduce the risk of changes that need to differ significantly or be deprecated.

## 1.1 Motivation

There's a lot of innovation happening in the Kubernetes ecosystem that Jenkins X would like to integrate with, there's also a lot of innovation to happen in the Jenkins X community too, until now it has been difficult to embrace this whilst also maintaining a high level of stability in the main codebase. Given that we use trunk based develpoment as recommended by [Accelerate](https://jenkins-x.io/docs/overview/accelerate/) it's easy for changes that may alter or become deprecated to be introduced.

We would like to increase the features that people can use, collaborate on and provide feedback for so that we continually improve at a good rate.

# 2. Design

Introduce a new GitHub Organisation called [Jenkins X Labs](https://github.com/jenkins-x-labs) which is an upstream incubation hub for Jenkins X that encourages innovation and collaboration on areas that we would like to trial and gather feedback on before introducing the features in the well supported mainstream codebase.

Most changes for Jenkins X go through the [jx](https://github.com/jenkins-x/jx) CLI repository which has grown into a monolith and has a number of downstream dependencies. We have been working with a Proof of Concept in Labs that takes a microservices approach to creating commands that inturn can be used to create `alpha` or `beta` binaries which can be optionally installed via `jx`.

The proposal for Jenkins X Labs is generic, not limited in scope to the `jx` CLI. We want to take similar steps to building docker images, quickstarts, buildpacks, etc. that use labs features so they don't appear in Jenkins X until the feature is complete.

An interesting obeservation has been made that using this microservices approach combined with the `alpha` and `beta` commands could make for a good way to refactor out the current `jx` monolith, statically importing dependencies from `jx` when we need them and over time refactoring into a more modular approach which will help with maintainability, supportability and testability.

Taking a microservices approach for the CLI will introduce new challanges but given that we push microservice with the Jenkins X project it is another area of dogfooding that we can learn from and pass on a great experience to users.

## 2.1 Process

This proposal is about creating an environment, culture and process that aids innovation and maintains reliability. We have a high level suggestion for a process to take features from experimental through to `alpha`, `beta` and GA using semantic versioning for any API changes.

The Labs GitHub Org maintains the list of `alpha` commands, once defined acceptance for that feature is acheived the feature will move to `beta` which is owned by the Jenkins X GitHub Org. There is an expectation that features, UX and APIs around it will largely stay the same as it matures from `beta` to GA because the feature will have been proven with community feedback and other acceptance criteria. Any chnages to this during `beta` should be communicated and agreed upon by the Labs organisation to ensure that users who take part in the `alpha` commands continue to provide feedback.

When a feature that may and probably will span multiple repos, beit CLI, images, quickstarts, charts, etc. we will make sure that there is good involvement and understanding of features so they can be picked up and moved to `beta` inside the Jenkins X org. This will be a learning process that we seek to always improve in.

## 2.2 Technical

* we are suggesting is that `jx` has the ability to include the `alpha` and `beta` commands
* images built within the labs organisation will be pushed to `gcr.io/jenkinsxio-labs` for easy identification

## 2.3 Out of Scope

* what commands are `alpha` or which features to start with, the process is about how not what

# 3. Acceptance Criteria for this Proposal

* approval from the [Jenkins X steering committee](https://github.com/jenkins-x/steering)
