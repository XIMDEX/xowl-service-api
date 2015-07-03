# xowl-service-api
Xowl service is a product owned by Open Ximdex Evolution. It's a API service that enhance your content with semantic links. To be able to use the service follow the steps below:

 1. Register in ximdex platform: http://x8.ximdex.net/register/signup
 2. Confirm your email an access the platform to grab your token.
 3. At this point you are ready to query the service, you can get a response using the following data:
   - endpoint: service url
   - token: is a string of character
   - content: text to be enhancer
 4. So if to make a low level request you can use curl: curl _URL_ -d 'token=_TOKEN_&content=_TEXTUAL CONTENT_'

Example:
```bash
curl http://x8.ximdex.net/api/v1/enhance -d 'token=55715f3e0761a&content=This is a very important text that talks about Albert Einstein'
```
At this moment the api service support both GET and POST request, but depending on the tool you use, you may have to manually url-encode the parameters to make a correct query.

The response is always a json object with the following structure:
```javascript
{
  "semantic": [LabelWithEntities, ...],
  "text": "This is a very important <a href=\"http://dbpedia.org/resource/TEXT\" class=\"xowl-suggestion\" data-cke-annotation=\"text\" data-cke-type=\"dOrganisation\" data-cke-suggestions=\"3\">text<\/a> that <a href=\"http://dbpedia.org/resource/Talks\" class=\"xowl-suggestion\" data-cke-annotation=\"talks\" data-cke-type=\"others\" data-cke-suggestions=\"2\">talks</a> about <a href=\"http://dbpedia.org/resource/Albert_Einstein\" class=\"xowl-suggestion\" data-cke-annotation=\"Albert Einstein\" data-cke-type=\"dPerson\" data-cke-suggestions=\"3\">Albert Einstein<\/a>"
}
```
The *semantic* key  is an array with objects. Each of them represents a portion of the original text that have been recognized as an entity. In semantic world a string could  refer to many entities, so each *LabelWithEntities* has an array called **entities**.
It's up to the user/developer how to manage this information, depending on the editor, the cms/dms, the visual editor used...
Check [drupal 7 client](https://github.com/XIMDEX/drupal7-xowl-client), [drupal 8 client](https://github.com/XIMDEX/drupal8-xowl-client) and [wordpress 3.x client](https://github.com/XIMDEX/wp-xowl-client), these are plugins that integrates with those cms.
