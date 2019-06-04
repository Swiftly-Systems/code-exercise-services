# PrestoQ Services Coding Exercise

## Overview

To introduce PrestoQ to your coding style and technique, we'd like you to do a small coding exercise. This is not a coding test where we give you a score or run it through a suite of tests for correctness.

Our hope is that we can use this to seed a discussion that provides us with an understanding of your design and coding abilities and you with an idea of what working at PrestoQ will be like. We believe this better reflects what engineers do than coding common patterns on a white board does.

A link to the spec for what we'd like you to build is at the end of these instructions.

## What We're Looking For

Think of this as real code you would be checking in and shipping to production. PrestoQ leverages all of the [SOLID](https://en.wikipedia.org/wiki/SOLID) principles to produce maintainable, testable designs and code. The team will review your code to discuss how comfortable they would be extending your code to support additional business requirements without introducing any regressions.

## Requirements

* Use one of the following modern, statically typed languages: Java, C#, Kotlin, F#, Scala, Go, Swift, etc.
* Do *not* use any file/string parsing libraries
  * You may use native or third party basic string utility functions like trim, pad, format, etc.
* Complete this project on your own
* Use a GitHub repository for source control
  * Email the link to the GitHub repository when you are finished
  * The readme.md file should include (at a minimum)
    * Instructions for running the project
    * Link to the latest Continuous Integration build/release
    * Any other information you would normally include when you author a readme
  * This code is your intellectual property
    * License it however you'd like (MIT, Apache or Public Domain are great choices)
    * Ensure the license you choose allows PrestoQ employees to read, build, and execute the code for free
* Set up a continuous integration environment using a free, publicly accessible service
    * We recommend AppVeyor (https://www.appveyor.com/) for a project of this size if you don't already have a favorite
    * Configure the CI environment to build directly from your GitHub project when there's a commit to master
    * Ensure that the GitHub readme file is automatically updated with the result of the CI build (AppVeyor has an easy badge that you can embed in your readme.md)
* Email your PrestoQ contact the link to the GitHub repository when you're ready to submit your project

If you have any questions, don't hesitate to reach out to your PrestoQ contact.

## Product Specification

And without further ado, the product specification for the feature is [here](../master/ProductInformationIntegrationSpec.md).

