---
title: "How to Use RestAssured: A Practical Guide with Examples"
author: Siva
images: [""]
type: post
draft: false
date: "2025-07-23T07:09:38+05:30"
url: "/using-restassured-with-examples"
toc: true
categories: [Java, API Testing, RestAssured]
tags: [Java, RestAssured, API Testing]
---


# Mastering REST API Testing with RestAssured in Java

RestAssured is a powerful and popular tool for testing REST APIs in Java. It streamlines the testing process by offering a domain-specific language (DSL) that simplifies making requests and verifying responses. In this article, we will delve into using RestAssured with practical examples to help you get started.

## Getting Started with RestAssured

RestAssured is an open-source Java library widely used for testing RESTful web services. It provides a straightforward approach to writing API tests and supports both JSON and XML formats.

To begin using RestAssured, include the following dependency in your `pom.xml` file if you are utilizing Maven:

```xml
<dependency>
    <groupId>io.rest-assured</groupId>
    <artifactId>rest-assured</artifactId>
    <version>4.4.0</version>
    <scope>test</scope>
</dependency>
```

## Basic Example

Let's explore a basic example of making a GET request using RestAssured:

```java
import static io.restassured.RestAssured.*;
import static org.hamcrest.Matchers.*;

public class BasicTest {
    public static void main(String[] args) {
        given().
            when().get("https://jsonplaceholder.typicode.com/posts/1").
            then().statusCode(200).
            body("userId", equalTo(1)).
            body("id", equalTo(1));
    }
}
```

In this example, we perform a GET request to a placeholder API and verify the status code along with certain fields in the response body.

## POST Request Example

Here's how to execute a POST request using RestAssured:

```java
import static io.restassured.RestAssured.*;
import org.json.JSONObject;

public class PostRequestTest {
    public static void main(String[] args) {
        JSONObject requestParams = new JSONObject();
        requestParams.put("title", "foo");
        requestParams.put("body", "bar");
        requestParams.put("userId", 1);

        given().
            header("Content-Type", "application/json").
            body(requestParams.toString()).
            when().post("https://jsonplaceholder.typicode.com/posts").
            then().statusCode(201);
    }
}
```

This example illustrates sending a JSON payload in a POST request and validating the response status code.

## Handling Authentication

RestAssured supports various authentication mechanisms. Here’s an example using basic authentication:

```java
import static io.restassured.RestAssured.*;

public class AuthTest {
    public static void main(String[] args) {
        given().
            auth().basic("username", "password").
            when().get("https://example.com/secure/api").
            then().statusCode(200);
    }
}
```

This example demonstrates how to perform basic authentication while making a GET request.

## Conclusion

RestAssured offers a simple yet powerful way to test REST APIs in Java. With its intuitive DSL, you can quickly write and execute tests for various HTTP requests and validate responses. Try these examples to familiarize yourself with RestAssured and start testing your APIs efficiently! Share your experiences or any questions in the comments below.
