
# What are Kubernetes Operators?

A Kubernetes Operator is an application-specific controller that extends the Kubernetes API to create, configure, and manage instances of complex stateful applications on behalf of a Kubernetes user. It builds upon the basic Kubernetes resource and controller concepts but includes domain or application-specific knowledge to automate common tasks.

An Operator is software that encodes this domain knowledge and extends the Kubernetes API through the third party resources (Custom Resource Definitions in 1.7 version) mechanism, enabling users to create, configure, and manage applications.

## Why do we need Kubernetes Operators?

**Stateless Apps are relatively easy to operate!** With Kubernetes, it is relatively easy to manage and scale web apps, mobile backends, and API services right out of the box. Why? Because these applications are generally stateless, so the basic Kubernetes APIs, like Deployments, can scale and recover from failures without additional knowledge.

**Stateful is Hard!** A larger challenge is managing stateful applications, like databases, caches, and monitoring systems. These systems require application domain knowledge to correctly scale, upgrade, and reconfigure while protecting against data loss or unavailability. We want this application-specific operational knowledge encoded into software that leverages the powerful Kubernetes abstractions to run and manage the application correctly.


References:
1. Operator Hub
https://operatorhub.io/

2. Introducing Operators
https://coreos.com/blog/introducing-operators.html

3. What is an Operator?
https://operatorhub.io/what-is-an-operator

4. Custom Resource Definition (CRD) will replace the existing Third Party Resource (TPR):
https://coreos.com/blog/custom-resource-kubernetes-v17#:~:text=Third%20Party%20Resources%20are%20a,controlled%20with%20Kubernetes%20RBAC%20authorization.

5. Custom Resource Definition (CRD)
https://kubernetes.io/docs/concepts/extend-kubernetes/api-extension/custom-resources/
