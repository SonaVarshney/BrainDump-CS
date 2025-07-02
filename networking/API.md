##  What are APIs?

APIs (Application Programming Interfaces) are tools that allow software applications to **communicate** and **interact** with one another. They act as intermediaries, abstracting the internal complexities of an application and exposing only the necessary parts through well-defined interfaces.

###  Why Are APIs Important?

- **Simplify development:** Developers don’t need to understand the internal code—just how to interact with it.
- **Encourage modularity:** Applications can be broken into independent services that interact via APIs.
- **Enable integrations:** Different systems (e.g., frontend & backend, third-party services) can work together smoothly.
- **Power the web:** From weather apps to payment gateways, APIs are everywhere behind the scenes.

### What Do APIs Define?

- **Methods** — What functions are available (e.g., `GET /users`)
- **Data formats** — Typically JSON or XML for request/response structures
- **Rules** — Authentication, rate limits, usage guidelines



> ### 🔒 What is a Rate Limit?
> **Rate limiting** is a technique used to **control the number of requests** a user or application can make to an API **within a specific time window** (e.g., per second, per minute, or per hour).
>It helps to:
>*  **Prevent abuse or overuse** (e.g., spamming API requests)
>*  **Ensure fair usage** among all users
>*  **Protect backend resources** from being overwhelmed
>
>---
>
>###  Example
> An API might allow:
> **100 requests per minute per user.**
> If you exceed that, you'll receive a response like:
>
>```json
>{
>  "error": "Rate limit exceeded. Try again in 30 seconds."
>}
>```
>---
>
>###  How It's Implemented
>
>* **Fixed Window:** 100 requests per minute reset every minute.
>* **Sliding Window:** More flexible, tracks usage in the past 60 seconds continuously.
>* **Token Bucket / Leaky Bucket:** Allows bursts of traffic while controlling average rate.
>---
>### Headers You Might See
> When using APIs, rate limits are often visible in the response headers:
>
>```
>X-RateLimit-Limit: 100  
>X-RateLimit-Remaining: 20  
>X-RateLimit-Reset: 1723451325 (Unix timestamp)
>```


