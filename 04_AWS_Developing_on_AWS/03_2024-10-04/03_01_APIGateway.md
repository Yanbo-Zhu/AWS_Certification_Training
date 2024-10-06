

# 1 理论 

![](image/Pasted%20image%2020241003165101.png)




![](image/Pasted%20image%2020241003165123.png)



![](image/Pasted%20image%2020241003165311.png)


![](image/Pasted%20image%2020241003165349.png)

# 2 API type 

![](image/Pasted%20image%2020241004094200.png)


## 2.1 HTTP API

## 2.2 web socket API

I can push xx to your brauser 

## 2.3 REST API

An Amazon API Gateway REST API is a collection of HTTP resources and methods that are integrated with backend HTTP endpoints, Lambda functions, or other AWS services. You can deploy this collection in one or more stages. Typically, API resources are organized in a resource tree according to the application logic. Each API resource can expose one or more API methods that have unique HTTP verbs supported by API Gateway.

![](image/Pasted%20image%2020241004094608.png)

![](image/Pasted%20image%2020241004094616.png)


add aws cogonito to  authrithoution 
![](image/Pasted%20image%2020241004094650.png)


## 2.4 Rest API private 

> rest API Private that's only accessible from within a VPC.

不是为了防止 同事访问 
而是一定程度上 限制访问, 同事仍然可以访问, 但是 不能过度访问 

I know if I want this is exactly to protect him from my colleagues in the case, he says.
Your colleagues from the marketing department they have another API and they come to you and say we need to call to get the list of all the customers that flew with Lufthansa this week right but
put the API gateway to protect yourself and your internal apps from other apps of the company




# 3 Cost

![](image/Pasted%20image%2020241004092938.png)



# 4 Create a API 

![](image/Pasted%20image%2020241003154620.png)

![](image/Pasted%20image%2020241003165649.png)


### 4.1.1 API endpints type 

- Regional 
- Edge-optimized 
- Priavte: 
    - to protect the api  form my colledege 


![](image/Pasted%20image%2020241003165717.png)

## 4.2 Resources 

In RESTful APIs, a **resource** refers to any piece of information or entity that can be addressed, manipulated, and represented over the web. Each resource is identified by a **URI (Uniform Resource Identifier)**, and clients interact with these resources using standard HTTP methods like GET, POST, PUT, DELETE, etc.

![](image/Pasted%20image%2020241003165522.png)



![](image/Pasted%20image%2020241003165547.png)

![](image/Pasted%20image%2020241004094959.png)





## 4.3 Stage


![](image/Pasted%20image%2020241003165911.png)


![](image/Pasted%20image%2020241003165919.png)


---


在stage 中添加 SDK


![](image/Pasted%20image%2020241003165936.png)


## 4.4 Authorizers


![](image/Pasted%20image%2020241003165622.png)


## 4.5 usage plans and API keys 

![](image/Pasted%20image%2020241003170004.png)


# 5 Type of integrations


![](image/Pasted%20image%2020241004095059.png)


proxy : json request with go passing through 
non-proxy:  


# 6 Request Validation 


![](image/Pasted%20image%2020241004100103.png)


![](image/Pasted%20image%2020241004095136.png)


![](image/Pasted%20image%2020241004095145.png)


![](image/Pasted%20image%2020241004095150.png)

---

templating language 
https://velocity.apache.org/engine/1.7/vtl-reference.html
- You are using a templating language that is an open source is called vtl velocity templates
- That would allow you to extract the values like you see doing here.
- Validating food or extract the values from the request

So you can use xml also: https://velocity.apache.org/engine/devel/developer-guide.html#velocity-and-structured-data



"Amazon API Gateway API request and response data mapping reference" -  [https://docs.aws.amazon.com/apigateway/latest/developerguide/request-response-data-mappings.html](https://docs.aws.amazon.com/apigateway/latest/developerguide/request-response-data-mappings.html "https://docs.aws.amazon.com/apigateway/latest/developerguide/request-response-data-mappings.html")


---

# 7 content-Type` header

ecause that's the type that is returned. Other types: [https://developer.mozilla.org/en-US/docs/Web/HTTP/MIME_types/Common_types](https://developer.mozilla.org/en-US/docs/Web/HTTP/MIME_types/Common_types "https://developer.mozilla.org/en-us/docs/web/http/mime_types/common_types")


When the `Content-Type` header is absent in the request, API Gateway assumes that its default value is `application/json`. For such a request, API Gateway uses `application/json` as the default key to select the mapping template, if one is defined. When no template matches this key, API Gateway passes the payload through unmapped if the [passthroughBehavior](https://docs.aws.amazon.com/apigateway/latest/api/API_Integration.html#passthroughBehavior "https://docs.aws.amazon.com/apigateway/latest/api/api_integration.html#passthroughbehavior") property is set to `WHEN_NO_MATCH` or `WHEN_NO_TEMPLATES`.

When the `Accept` header is not specified in the request, API Gateway assumes that its default value is `application/json`. In this case, API Gateway selects an existing mapping template for `application/json` to map the response payload. If no template is defined for `application/json`, API Gateway selects the first existing template and uses it as the default to map the response payload. Similarly, API Gateway uses the first existing template when the specified `Accept` header value does not match any existing template key. If no template is defined, API Gateway simply passes the response payload through unmapped.

For example, suppose that an API has a `application/json` template defined for a request payload and has a `application/xml` template defined for the response payload. If the client sets the `"Content-Type : application/json"`, and `"Accept : application/xml"` headers in the request, both the request and response payloads will be processed with the corresponding mapping templates. If the `Accept:application/xml` header is absent, the `application/xml` mapping template will be used to map the response payload. To return the response payload unmapped instead, you must set up an empty template for `application/json`


# 8 Mock Integrations


![](image/Pasted%20image%2020241004095236.png)


# 9 AWS apigateway CLI

![](image/Pasted%20image%2020241004095243.png)



# 10 **Cross-Origin Resource Sharing (CORS)**  跨域请求

**Cross-Origin Resource Sharing (CORS)** 是一种基于 HTTP 头的机制，它允许网页服务器通过浏览器控制跨域请求的访问权限。它解决了当网页从一个域名（源站）向另一个域名（跨域站）发出请求时，浏览器默认阻止的安全问题。

 browsers have a protection, so wouldn't allow you to run scripts that are from a different domain  from one that you downloaded from right now
Cross-domain 的访问 

## 10.1 背景

由于安全原因，浏览器限制网页在没有明确允许的情况下访问其他域的资源。这种限制被称为 **同源策略**。同源策略要求，网页只能访问与其来源相同的资源（协议、域名和端口必须一致）。

然而，在现代 web 开发中，跨域资源访问是常见需求，比如从一个域名的网页上请求另一个 API 的数据。为了解决这一问题，CORS 提供了一种标准化的方式来允许跨域请求。

## 10.2 CORS 工作原理

当一个网页向不同域名的服务器发出请求时（跨域请求），浏览器会在请求头中添加 **Origin** 字段，该字段包含请求的来源域。服务器可以根据这个信息，决定是否允许这个请求。

1. **简单请求**：对于简单的 HTTP 请求，浏览器会自动在请求头中添加 `Origin`，服务器响应时，通过 `Access-Control-Allow-Origin` 来决定是否允许请求：
    
    - 如果服务器响应头包含 `Access-Control-Allow-Origin: *`，表示允许所有域访问资源。
    - 服务器也可以指定具体的域名（如 `Access-Control-Allow-Origin: https://example.com`），仅允许该域名的请求。
2. **预检请求（Preflight Request）**：对于更复杂的请求（如使用 `PUT`, `DELETE` 等方法），浏览器会在正式请求前发出一个 **OPTIONS** 请求，称为预检请求。服务器通过返回的 CORS 头来告诉浏览器是否允许该请求。预检请求的目的是确保安全，防止未经允许的跨域请求。



## 10.3 常见的 CORS 头：

- **Access-Control-Allow-Origin**：指定允许的源站域名。
- **Access-Control-Allow-Methods**：允许的 HTTP 方法，如 `GET`, `POST`, `PUT` 等。
- **Access-Control-Allow-Headers**：允许的自定义请求头。
- **Access-Control-Allow-Credentials**：是否允许发送凭证（如 cookies）。

## 10.4 示例

客户端向跨域 API 发出请求：
```
GET /data HTTP/1.1
Host: api.example.com
Origin: https://mywebsite.com

```

服务器的响应：
```
HTTP/1.1 200 OK
Access-Control-Allow-Origin: https://mywebsite.com
```

如果服务器返回 `Access-Control-Allow-Origin` 头并匹配 `Origin`，浏览器将允许该跨域请求。

## 10.5 结论

CORS 通过让服务器明确指定哪些来源可以访问其资源，提供了一个安全而灵活的机制来处理跨域请求。这对现代 web 应用程序的跨域数据交互至关重要。
