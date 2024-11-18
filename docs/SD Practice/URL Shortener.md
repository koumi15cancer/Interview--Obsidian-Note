# Design a URL Shortener like Bit.ly

Reference:
- https://www.hellointerview.com/learn/system-design/answer-keys/bitly
- 

1: Requirements
- Functional Requirements:
	- Create short URL from long one
		- Allow custom alias 
		- Set URL Time expiration time
	- Redirect to the long URL from short URL 
	Out of scope: 
- Non Functional Req:
	- Low latency on redirect ( ~ 200ms)
	- Scale to support 100M DAU and 1B urls
	- Ensure Unique of short code
	- High Availability ( Consider CAP element, P always same so considering Consistency or High Availability)


( *Estimation* is optional , can do basic for these ones:
- Latency
- Scale
- Storage
  
Should do math in high level design as could make the decision 
-> Do math when It directly informs changes to take into design
 )

2: Core Entities
- Original URL
- Short URL
- User
3: API or Interface
- Shorten URL: POST /v1/urls -> shortURL
{
	originalURL,
	 alias?,
	 expirationTime?
}

- Redirection: GET {shortenURL} -> Redirect to original URL
4: Data Flow
5: High Level Design
![[Screenshot 2024-11-18 at 1.33.17 PM.png]]
6: Deep Dives


![[Screenshot 2024-11-18 at 1.57.52 PM.png]]