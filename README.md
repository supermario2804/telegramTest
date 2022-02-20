https://core.telegram.org/tdlib/getting-started
https://core.telegram.org/tdlib/docs/td__json__client_8h.html#a45cd6979ada11b7690d9dcb1ddc841a0

@extra --> The main TDLib API is fully-asyncronous. An Application can send a request to 
TDLib through ClientManager.send method and receive a response asynchronously through the 
ClientManager.receive method when it becomes available. The exact naming of these methods 
and the way in which requests are matched with responses is different for different TDLib interfaces, 
but the concept as a whole remains the same. For example, in TDLib JSON interface these methods are 
called td_send and td_receive, and their @extra field must be used to match requests with the corresponding responses.


json request received from (client *Client) SendAndCatch:

result : {Data:map[@extra:zTDvydqdKrlbKPbnIJkjKyJZHRYrJibx @type:authorizationStateWaitTdlibParameters] Raw:[123 ]}

string(result.Raw) = {"@type":"authorizationStateWaitTdlibParameters","@extra":"zTDvydqdKrlbKPbnIJkjKyJZHRYrJibx"}
or 
string(result.Raw) = {"@type":"authorizationStateWaitEncryptionKey","is_encrypted":true,"@extra":"kdDHiohEDdhmcKhKFeJJhZBWaQCIYbOP"}


at receiving end Value of @type can be one of the below:

@type:authorizationStateWaitPhoneNumber, @type":"authorizationStateWaitTdlibParameters , @type:authorizationStateWaitEncryptionKey


at sending end Value of @type can be one of the below:

"@type": "getAuthorizationState"



Description:
https://core.telegram.org/tdlib/docs/td__api_8h.html

In json request @type will be class name or function name taken from above url and 
other parameters would be same as the argument passed to the function.