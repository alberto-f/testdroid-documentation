---
layout: default
title: Testdroid Run In Cloud Plugin
---


Testdroid Run In Cloud Jenkins plugin can be used to launch test runs
directly from your Jenkins job.

<!-- or have a look at its [source](https://github.com/bitbar/testdroid-run-in-cloud). -->


## Configuration Instructions

[Download Testdroid Run In Cloud
Plugin](https://github.com/jenkinsci/testdroid-run-in-cloud-plugin/blob/master/bin/testdroid-run-in-cloud-1.0.9.hpi)
and open your Jenkins main page. Then navigate to: *Manage Jenkins ->
Manage plugins -> Advanced -> Upload plugin*. After installing and
restarting Jenkins you can configure plugin from Jenkins Configuration
page. The plugin adds a new build step that can be used in any Jenkins
job to launch builds in Testdroid cloud

## Configure

Open Jenkins main configuration page(*Manage Jenkins -> Configure System*)
and there is Testdroid Cloud section where you can fill out your
Testdroid account details. Press Authorize button to validate your
account details.

![]({{site.baseurl}}/assets/testdroid-cloud-integration/ric-main-config.png)


## Run In Cloud - Build step

Open existing Jenkins job or create a new one. Then from job
configuration and a new build step: Android: Run tests in Testdroid
Cloud You can select the target project and upload a new application
or/and instrumentation package into that project by defining file name
in corresponding field. If you need to customize projects settings
click the "Edit project on Testdroid Cloud website" button and it will
open Cloud webpage.

![]({{site.baseurl}}/assets/testdroid-cloud-integration/ric-build-step.png)

You can configure annotations in the following section. [Here is more
information on how to use annotations](using-annotations) to execute subsets of tests.


![]({{site.baseurl}}/assets/testdroid-cloud-integration/ric-build-step-2.png)

There's 2 ways to get notification from Testdroid your test runs are finished.
 
### API CALL

Jenkins is polling Testdroid for the results. Test results are copied
from Testdroid to Jenkins workspace after the tests are finished.

![]({{site.baseurl}}/assets/testdroid-cloud-integration/ric-api-call.png)

### HOOK URL

Testdroid sends post message to that url when test run is
finished. RiC listens the message in default location and it downloads
results when post message arrives. User can change the URL.
 
POST message body:

    testRunId=%s&projectId=%s&status=FINISHED

**Note!** This requires your HOOK URL is reachable from Internet
eg. Jenkins instance can be reached from Testdroid Cloud.

![]({{site.baseurl}}/assets/testdroid-cloud-integration/ric-hook-url.png)
