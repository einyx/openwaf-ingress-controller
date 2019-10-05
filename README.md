## Help us to improve the NGINX Ingress controller [completing the survey](https://docs.google.com/forms/d/15ULTOvYDsV920V0GWrspew4yyjEmTAi740Wr34UgKwA/viewform)

---

# NGINX Ingress Controller

# ModSecurity Web Application Firewall

ModSecurity is an open source, cross platform web application firewall (WAF) engine for Apache, IIS and Nginx that is developed by Trustwave's SpiderLabs. It has a robust event-based programming language which provides protection from a range of attacks against web applications and allows for HTTP traffic monitoring, logging and real-time analysis - [https://www.modsecurity.org](https://www.modsecurity.org)

The [ModSecurity-nginx](https://github.com/SpiderLabs/ModSecurity-nginx) connector is the connection point between NGINX and libmodsecurity (ModSecurity v3).

The default ModSecurity configuration file is located in `/etc/nginx/modsecurity/modsecurity.conf`. This is the only file located in this directory and contains the default recommended configuration. Using a volume we can replace this file with the desired configuration.
To enable the ModSecurity feature we need to specify `enable-modsecurity: "true"` in the configuration configmap.

>__Note:__ the default configuration use detection only, because that minimizes the chances of post-installation disruption.
Due to the value of the setting [SecAuditLogType=Concurrent](https://github.com/SpiderLabs/ModSecurity/wiki/Reference-Manual-(v2.x)#secauditlogtype) the ModSecurity log is stored in multiple files inside the directory `/var/log/audit`.
The default `Serial` value in SecAuditLogType can impact performance.

The OWASP ModSecurity Core Rule Set (CRS) is a set of generic attack detection rules for use with ModSecurity or compatible web application firewalls. The CRS aims to protect web applications from a wide range of attacks, including the OWASP Top Ten, with a minimum of false alerts.
The directory `/etc/nginx/owasp-modsecurity-crs` contains the [owasp-modsecurity-crs repository](https://github.com/SpiderLabs/owasp-modsecurity-crs).
Using `enable-owasp-modsecurity-crs: "true"` we enable the use of the rules.


[![Coverage Status](https://codecov.io/gh/kubernetes/ingress-nginx/branch/master/graph/badge.svg)](https://codecov.io/gh/kubernetes/ingress-nginx)
[![Go Report Card](https://goreportcard.com/badge/github.com/kubernetes/ingress-nginx)](https://goreportcard.com/report/github.com/kubernetes/ingress-nginx)
[![GitHub license](https://img.shields.io/github/license/kubernetes/ingress-nginx.svg)](https://github.com/kubernetes/ingress-nginx/blob/master/LICENSE)
[![GitHub stars](https://img.shields.io/github/stars/kubernetes/ingress-nginx.svg)](https://github.com/kubernetes/ingress-nginx/stargazers)
[![GitHub stars](https://img.shields.io/badge/contributions-welcome-orange.svg)](https://github.com/kubernetes/ingress-nginx/blob/master/CONTRIBUTING.md)
[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2Fkubernetes%2Fingress-nginx.svg?type=shield)](https://app.fossa.io/projects/git%2Bgithub.com%2Fkubernetes%2Fingress-nginx?ref=badge_shield)

# Get Involved

- **Contributing**: Pull requests are welcome!
  - Read [`CONTRIBUTING.md`](CONTRIBUTING.md) and check out [help-wanted](https://github.com/kubernetes/ingress-nginx/labels/help%20wanted) issues
  - Submit github issues for any feature enhancements, bugs or documentation problems
- **Support**: Join to [Kubernetes Slack](http://slack.kubernetes.io/) to ask questions to get support from the maintainers and other developers
  - Questions/comments can also be posted as [github issues](https://github.com/kubernetes/ingress-nginx/issues)
- **Discuss**: Tweet using the `#IngressNginx` hashtag

## Description

This repository contains the NGINX controller built around the [Kubernetes Ingress resource](http://kubernetes.io/docs/user-guide/ingress/) that uses [ConfigMap](https://kubernetes.io/docs/tasks/configure-pod-container/configure-pod-configmap/#understanding-configmaps-and-pods) to store the NGINX configuration. [Make Ingress-Nginx Work for you, and the Community](https://youtu.be/GDm-7BlmPPg) from KubeCon Europe 2018 is a great video to get you started!!

Learn more about using Ingress on [k8s.io](https://kubernetes.io/docs/concepts/services-networking/ingress/)

### What is an Ingress Controller?

Configuring a webserver or loadbalancer is harder than it should be. Most webserver configuration files are very similar. There are some applications that have weird little quirks that tend to throw a wrench in things, but for the most part you can apply the same logic to them and achieve a desired result.

The Ingress resource embodies this idea, and an Ingress controller is meant to handle all the quirks associated with a specific "class" of Ingress.

An Ingress Controller is a daemon, deployed as a Kubernetes Pod, that watches the apiserver's `/ingresses` endpoint for updates to the [Ingress resource](https://kubernetes.io/docs/concepts/services-networking/ingress/). Its job is to satisfy requests for Ingresses.

## Documentation

To check out [Live Docs](https://kubernetes.github.io/ingress-nginx/)

## Questions

For questions and support please use the [#ingress-nginx](https://kubernetes.slack.com/messages/CANQGM8BA/) channel in the [Kubernetes Slack](http://slack.kubernetes.io/) or post to the [Kubernetes Forum](https://discuss.kubernetes.io). The issue list of this repo is **exclusively** for bug reports and feature requests.

## Issues

Please make sure to read the [Issue Reporting Checklist](https://github.com/kubernetes/ingress-nginx/blob/master/CONTRIBUTING.md#issue-reporting-guidelines) before opening an issue. Issues not conforming to the guidelines may be closed immediately.

## Changelog

Detailed changes for each release are documented in the [Changelog.md](Changelog.md)

## Contribution

Please make sure to read the [Contributing Guide](CONTRIBUTING.md) before making a pull request.

Thank you to all the people who already contributed to NGINX Ingress Controller!

## Code of Conduct

This project adheres to the [Kubernetes Community Code of Conduct](https://git.k8s.io/community/code-of-conduct.md).
By participating in this project you agree to abide by its terms.

## License

[Apache License 2.0](https://github.com/kubernetes/ingress-nginx/blob/master/LICENSE)
