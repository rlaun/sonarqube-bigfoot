
Project Bigfoot
===============

This test project should help reproducing an elusive(?) Sonarqube bug.

see https://groups.google.com/forum/#!topic/sonarqube/mzId9fnN9pI for discussion


* start with a fresh Sonarqube instance (6.7 LTS or 5.6.x LTS)

* create a "minimal" Java profile with squid:S00103 and squid:S109 only; set as default

* checkout step 1 / commit d86b7d509

* run sonar:sonar -Dsonar.host.url=http://....

* SonarQube has found 2 code smells, as displayed in the dashboard ("Overview")

* resolve both as "Won't fix" (practical example! :) 

  * note: the "overview" dashboard still shows 2 code smells. why?

* checkout step 2 / 4c2a879e - i.e. the code gets heavily refactored: different lines in different locations.

* rerun sonar:sonar

* voila - there are no new findings


Failure to detect new issues does not match the [documentation](https://docs.sonarqube.org/display/SONAR/Issue+Lifecycle)
 or what I'd expect intuitively after heavily altering the code.
