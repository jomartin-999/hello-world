<!-- Copyright (C) 2019-Present Pivotal Software, Inc. All rights reserved.

This program and the accompanying materials are made available under the terms of the under the Apache License, Version
2.0 (the "License”); you may not use this file except in compliance with the License. You may obtain a copy of the
License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an
"AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific
language governing permissions and limitations under the License. -->
 
# Hello, World! Code Example

This guide presents a Hello, World! example app.
Running the app demonstrates that caching improves read performance.

Working through this introductory example provides Spring Boot developers
with the development experience of running an app in three ways:

- The first way runs the app locally with an Apache Geode cluster as
the cache. 
- The second way pushes the app to a Tanzu Application Services environment to run with a
Tanzu GemFire service instance as the cache.
- The Third way runs a Tanzu GemFire cluster on Kubernetes.

As the app runs,
the browser-based user interface allows the user to look up the value
associated with the key "hello."
The app prints the key, its value,
and the amount of time it took to do the lookup.

A lookup always first checks whether the desired key is in the cache.
The first lookup encounters a cache miss,
because the "hello" key is not in the cache.
On a cache miss, the app is responsible for acquiring the key's value.
In a real-world example, the app might send a query to a database
to acquire the value—an operation that takes a relatively
lengthy amount of time.
In this Hello World! example,
the value is computed to be the current time,
and the app injects an artificial time delay to simulate a database query. 

Before returning the value resulting from the lookup,
a cache miss has the side effect of placing the acquired value
for the key into the cache.
Subsequent lookups of that key will result in cache hits,
and the value will be returned quickly.

## App Dependencies

All supported versions of Cloud Cache use the same Spring dependencies
for this Hello, World! app.
The app uses Spring Boot, version 2.3.x 

The app uses the following dependencies:

- Spring Boot Web Starter: 

    ```
    org.springframework.boot:spring-boot-starter-web
    ```
- Spring GemFire Starter 1.3.x:

    ```
    org.springframework.geode:spring-gemfire-starter:1.3.6.RELEASE
    ```


