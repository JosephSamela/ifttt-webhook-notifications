# IFTTT Webhook Notifications

[IFTTT](https://ifttt.com) offers free-no-strings-attached webhooks for use in personal projects. I've been experimenting with these on my latest Raspberry Pi project to send notifications to my phone. The project is an always-active webcam pointed at a scenic vista that posts to Instagram and streams to Youtube. When a job finishes, or error occurs I get immediately notified - pretty cool!   

## Get Started

Signup on the website [https://ifttt.com](https://ifttt.com) and download the app for [iOS](https://itunes.apple.com/app/apple-store/id660944635?mt=8) or [Android](https://play.google.com/store/apps/details?id=com.ifttt.ifttt&utm_source=/&utm_medium=web). Under "My Applets" select "New Applet". Setup the applet so `IF` webhook is triggered `THEN` notification is sent. When creating the applet choose a unique `{event}` name, you will need that later.

You can choose between *regular* notification or *rich* notification. A *regular* notification sends text only. A *rich* notification can send text with links and photos. Create a simple message that includes*ingredients* from the dropdown menu. `value1` `value2` `value3` are optional fields sent in the body of webhook request. These can be used to customize the notification message.

Next go to [https://ifttt.com/services/maker_webhooks/settings](https://ifttt.com/services/maker_webhooks/settings) and write down your webhook `{key}` - anyone with this key can trigger this webhook.

...That's it! Here are some examples to help you get started.

## Examples
To trigger the webhook - you just need to send an http request. I've included examples for [`curl`](https://curl.haxx.se/) and [`python`](https://www.python.org/) but http requests can be sent by many languages.

### GET

The quickest way to trigger your webhook is an http `GET` request. Seriously, navigate to `https://maker.ifttt.com/trigger/{event}/with/key/{key}` in a web-browser. You will recieved a plain html page with the text `Congratulations! You've fired the {event} event` and a mobile notification.

#### Shell
```
curl https://maker.ifttt.com/trigger/{event}/with/key/{key}
```
#### Python
```python
import requests
requests.get(https://maker.ifttt.com/trigger/{event}/with/key/{key})
```

### POST
To give your notifications panache - use an http `POST` request. You can include data in the request body as JSON with keys `value1` `value2` `value3` that map to message ingredients. For example `{"value1":"success}` would subsitute `value1` with "success" in the message template.

#### Shell

```
curl -X POST -H "Content-Type: application/json" \
-d '{data}' \
https://maker.ifttt.com/trigger/{event}/with/key/{key}
```

```
curl -X POST -H "Content-Type: application/json" \
-d '{"value1":"Artwork by Picasso", "value2":"https://bit.ly/1KMoKoN"}' \
https://maker.ifttt.com/trigger/{event}/with/key/{key}
```

#### Python

```python
import requests
address = 'https://maker.ifttt.com/trigger/{event}/with/key/{key}'
requests.post(address, data = {data})
```

```python
import requests
address = 'https://maker.ifttt.com/trigger/{event}/with/key/{key}'
requests.post(address, data = {"value1":"Artwork by Picasso", "value2":"https://bit.ly/1KMoKoN"})
```
