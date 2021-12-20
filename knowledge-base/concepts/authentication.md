# Authentication

## Web

### Cookies
<u>Cookie used for authentication</u>

![](../concepts_photos/Cookie-In-HTTP-Request--THM.png)

The authentication processes can be as follows:
1. A request such as a login usually made as a [post](post.md)
2. Server verifies it received data and sets a unique cookie
	- Type of value determined by either best-practices or the web developer.
3. Once assigned, as as long as it lives in your browser, all future GET requests will use that cookie to identify you and your access using [deserialization](web/deserialization.md).