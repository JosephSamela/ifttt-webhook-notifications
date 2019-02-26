# IFTTT Webhook Notifications

`{event}` Name of applet 

`{key}` Unique webook key

`{data}` JSON formatted data containing `value1`, `value2` `value3`

## GET

### Shell
```shell
curl https://maker.ifttt.com/trigger/{event}/with/key/{key}
```
### Python
```python
import requests
requests.get(https://maker.ifttt.com/trigger/{event}/with/key/{key})
```

### Web-Browser
Alternatively, navigate to `https://maker.ifttt.com/trigger/{event}/with/key/{key}` in a web-browser. You will recieved a plain html page with the text `Congratulations! You've fired the {event} event`.

## POST

### Shell

```shell
curl -X POST -H "Content-Type: application/json" -d '{data}' https://maker.ifttt.com/trigger/{event}/with/key/{key}
```

```shell
curl -X POST -H "Content-Type: application/json" -d '{"value1":"Artwork by Picasso", "value2":"https://bit.ly/1KMoKoN"}' https://maker.ifttt.com/trigger/{event}/with/key/{key}
```

### Python

```python
import requests
requests.post('https://maker.ifttt.com/trigger/{event}/with/key/{key}', data = {data})
```

```python
import requests
requests.post('https://maker.ifttt.com/trigger/{event}/with/key/{key}', data = {"value1":"Artwork by Picasso", "value2":"https://bit.ly/1KMoKoN"})
```
