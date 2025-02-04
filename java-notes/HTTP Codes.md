
HTTP status codes server ki taraf se responses hote hain jo batate hain ki request ka kya result aaya. Inhe 5 categories me divide kiya gaya hai:

1. **1xx (Informational) - Sirf Information**
2. **2xx (Success) - Request Sahi Rahi** ✅
3. **3xx (Redirection) - Dusre Jagah Redirect Karna** 🔄
4. **4xx (Client Error) - Client Side Error** ❌
5. **5xx (Server Error) - Server Side Error** ⚠️

Chaliye detail me samajhte hain har series ke codes:

---

## **🔹 200 Series (Success) - Request Sahi Rahi ✅**

Ye codes batate hain ki request successfully complete ho gayi.

| **Code**                              | **Meaning**                                      | **Description**                    |
| ------------------------------------------- | ------------------------------------------------------ | ---------------------------------------- |
| **200 OK**                            | Request successfully complete ho gayi                  | Data server se mil gaya                  |
| **201 Created**                       | Naya resource create ho gaya                           | POST ya PUT request ke liye              |
| **202 Accepted**                      | Request accept ho gayi, lekin abhi process ho rahi hai | Background process me kaam hoga          |
| **203 Non-Authoritative Information** | Response modify kiya gaya hai                          | Proxy ya third-party source se aaya data |
| **204 No Content**                    | Request successful, lekin koi content return nahi hua  | DELETE request ke baad aata hai          |
| **205 Reset Content**                 | Client ko form ya page reset karna chahiye             | Jaise ek form clear karna                |
| **206 Partial Content**               | Sirf kuch part ka response bheja gaya hai              | Large files ko chunks me bhejne ke liye  |

---

## **🔹 300 Series (Redirection) - Dusre Jagah Redirect Karna 🔄**

Ye codes batate hain ki client ko dusre location par jaana hai.

| **Code**                          | **Meaning**                                       | **Description**                                                           |
| --------------------------------------- | ------------------------------------------------------- | ------------------------------------------------------------------------------- |
| **300 Multiple Choices**          | Multiple options available hain                         | User ko ek option choose karna padega                                           |
| **301 Moved Permanently**         | Resource permanently move ho gaya                       | Browser ya search engines naye URL ko store kar lete hain                       |
| **302 Found (Moved Temporarily)** | Resource temporarily move hua hai                       | Temporary redirection, lekin future me wapas aa sakta hai                       |
| **303 See Other**                 | Response ko ek naye URL par redirect kiya gaya hai      | Mostly POST ke baad GET request ke liye                                         |
| **304 Not Modified**              | Cache se old data use karo                              | Server bata raha hai ki resource same hi hai, isliye naye data ki zaroorat nahi |
| **307 Temporary Redirect**        | 302 jaisa hi hai, lekin request method change nahi hota | POST request wapas POST hi rahegi                                               |
| **308 Permanent Redirect**        | 301 jaisa hi hai, lekin request method same rahega      | Permanent redirect without method change                                        |

---

## **🔹 400 Series (Client Error) - Client Side Error ❌**

Ye codes batate hain ki client (browser ya API request) me kuch galat hai.

| **Code**                              | **Meaning**                                                | **Description**                                       |
| ------------------------------------------- | ---------------------------------------------------------------- | ----------------------------------------------------------- |
| **400 Bad Request**                   | Request format galat hai                                         | Server request samajh nahi pa raha                          |
| **401 Unauthorized**                  | Authentication required hai                                      | Login ya API key missing hai                                |
| **402 Payment Required**              | Payment karni padegi                                             | Mostly paid services me aata hai                            |
| **403 Forbidden**                     | Access allowed nahi hai                                          | User ke pass permission nahi hai                            |
| **404 Not Found**                     | Resource exist nahi karta                                        | Galat URL ya delete ho gaya                                 |
| **405 Method Not Allowed**            | Iss URL ke liye yeh HTTP method allowed nahi                     | Jaise POST karne ki koshish GET ke jagah                    |
| **406 Not Acceptable**                | Server jo content bhej raha hai, wo client accept nahi kar sakta | Jaise koi specific format chahiye                           |
| **407 Proxy Authentication Required** | Proxy authentication chahiye                                     | Client ko proxy me login karna padega                       |
| **408 Request Timeout**               | Server ne bohot der tak response nahi bheja                      | Network slow ya client delay ho gaya                        |
| **409 Conflict**                      | Request current state ke sath conflict ho rahi hai               | Jaise ek hi resource ko 2 log ek saath update kar rahe hain |
| **410 Gone**                          | Resource permanently delete ho gaya hai                          | 404 jaisa, but confirm hai ki wapas nahi aayega             |
| **411 Length Required**               | Content-Length header required hai                               | Server ko data length ka pata nahi                          |
| **412 Precondition Failed**           | Request ki kuch conditions fail ho gayi                          | Jaise kisi version check me fail hona                       |
| **413 Payload Too Large**             | Request body bohot badi hai                                      | Server handle nahi kar sakta                                |
| **414 URI Too Long**                  | URL bohot bada hai                                               | Mostly GET request me long query string                     |
| **415 Unsupported Media Type**        | Content type supported nahi hai                                  | Server expected format nahi samajh raha                     |
| **429 Too Many Requests**             | Client ne bohot requests bhej di                                 | Rate limiting ya throttling ke wajah se                     |

---

## **🔹 500 Series (Server Error) - Server Side Error ⚠️**

Ye codes batate hain ki problem server side me hai, client ka koi issue nahi hai.

| **Code**                           | **Meaning**                      | **Description**                              |
| ---------------------------------------- | -------------------------------------- | -------------------------------------------------- |
| **500 Internal Server Error**      | Server me unknown issue aa gaya        | General error, kuch bhi ho sakta hai               |
| **501 Not Implemented**            | Server is method ko support nahi karta | Jaise koi naya HTTP method use karna               |
| **502 Bad Gateway**                | Server ke beech me koi issue hai       | Jaise ek proxy server ka response sahi nahi hai    |
| **503 Service Unavailable**        | Server down ya busy hai                | Jaise maintenance mode ya overload                 |
| **504 Gateway Timeout**            | Server ne timely response nahi diya    | Jaise ek server doosre server ka wait kar raha hai |
| **505 HTTP Version Not Supported** | HTTP version support nahi hai          | Jaise koi purana HTTP version use ho raha ho       |

---

## **📌 Summary Table - All HTTP Status Codes**

| **Series** | **Category**                            | **Example Codes** |
| ---------------- | --------------------------------------------- | ----------------------- |
| **1xx**    | Informational (Request process ho rahi hai)   | 100, 101, 102           |
| **2xx**    | Success (Request successful)                  | 200, 201, 204           |
| **3xx**    | Redirection (Client ko dusri jagah jaana hai) | 301, 302, 304           |
| **4xx**    | Client Errors (Request me kuch galti hai)     | 400, 401, 403, 404      |
| **5xx**    | Server Errors (Server side issue hai)         | 500, 502, 503, 504      |

---

### **🚀 Conclusion**

Ye HTTP status codes har web developer aur backend engineer ke liye important hote hain. Agar kisi specific error code ka real-world example ya debugging tips chahiye, to batao! 😊
