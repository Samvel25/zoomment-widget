# Zoomment.com

Comments and reactions for your website with less than 500kb.💬👁️😀

![screenshot comments](/images/light.png)

## Usage

1. Download [zoomment.min.js](/docs/zoomment.min.js?raw=true)
2. Clone and Run [zoomment-server](https://github.com/tigransimonyan/zoomment-server)
3. Place the following code where you'd like Zoomment to load:

```html
<!-- for the comment section -->
<div
  id="zoomment"
  data-theme="light"
  data-language="en"
  data-emotions="❤️,😀,🪄,🥸,💡,🤔,💩,😢"
></div>

<!-- the working script -->
<script src="{{YOUR_HOSTING_URL}}/zoomment.min.js"></script>
```

## Options

Options can be passed via data attributes for comment section.

| Attribute Name | Possible values                                        |
| -------------- | ------------------------------------------------------ |
| data-theme     | light, dark, black                                     |
| data-language  | en, hy, hyw, ru, zh                                    |
| data-emotions  | list comma separated emojis, leave empty if not needed |

## CDN

```html
<script src="https://cdn.jsdelivr.net/gh/zoomment/zoomment-widget@1.1.0/docs/zoomment.min.js"></script>
```

## Development

1. Make sure you have node.js installed.
2. Clone the repository and install dependencies:

```
$ git clone https://github.com/zoomment/zoomment-widget.git
$ cd zoomment-widget
$ npm install
```

3. Run it for development:

```
$ npm start
```

Open http://localhost:1234 to view it in the browser.

4. Build it for production:

```
$ npm run build
```

## API Reference

### Add Comment

```
POST {{YOUR_API_URL}}/api/comments
```

Request Body:

```
{
  "body": "Hello!",
  "pageId: "zoomment.github.io/zoomment-widget/page-1",
  "pageUrl: "https://zoomment.github.io/zoomment-widget/page-1"
  "owner": {
    "name": "Bob",
    "email": "test@gmail.com"
  }
}
```

Response Body:

```
{
  "_id": "5fa538f82378f23944454737",
  "secret": "61e68a4caea667b4a628e45a2ac3dc216e0b8327",
  "createdAt": "2020-11-06T11:52:24.449Z",
  "owner": {
    "gravatar": "21ad0bd836b90d08f4cf640b4c298e7c",
    "name": "Bob"
  },
  ...
}
```

### Get Comments

```
GET {{YOUR_API_URL}}/api/comments?pageId={{PAGE_ID}}
```

Response Body:

```
[
  {
    "_id": "5fa3fa28c5eb4a2475dd0768",
    "body": "Hello!",
    "createdAt": "2020-11-05T13:12:08.513Z",
    "owner": {
      "gravatar": "21ad0bd836b90d08f4cf640b4c298e7c",
      "name": "Bob"
    },
  },
  ...
]
```

### Delete Comment

```
DELETE {{YOUR_API_URL}}/api/comments/{{COMMENT_ID}}?secret={{COMMENT_SECRET}}
```

Response Body:

```
Ok
```
