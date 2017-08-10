# NDC Segment

Go API for event tracking.

## Prerequisites

Following is required to build and deploy.

* [Go 1.8](https://blog.golang.org/go1.8) or higher

## Getting started

Make sure your go environment is setup.

### Build

Compile go code:

```
$ go get && go build
```

### Run

Run the api locally.

```
$ go run main.go
2017/08/10 13:57:50 Loading model ../ndc_scraper/model.bin
2017/08/10 13:57:53 Model loaded in 2.928797763s
2017/08/10 13:57:53 NDC Predict API 1.0.0 listening on: :3002
```

### Testing

Test the API with curl.

```
$ curl -H "Content-Type: application/json" -d @talk.json -X POST http://localhost:3002/predict
{"prob":0.42578128,"label":"__label__microsoft"}
```

Load test with [hey](https://github.com/rakyll/hey) for 100 concurrent users with ~10ms latency.

```
$ hey -n 10000 -c 100 -H "Content-Type: application/json" -D ./talk.json -m POST http://localhost:3002/predict

Summary:
  Total:	1.7166 secs
  Slowest:	0.1217 secs
  Fastest:	0.0002 secs
  Average:	0.0166 secs
  Requests/sec:	5825.4925
  Total data:	490000 bytes
  Size/request:	49 bytes

Detailed Report:

	DNS+dialup:
  		Average:	0.0002 secs
  		Fastest:	0.0000 secs
  		Slowest:	0.0394 secs

	DNS-lookup:
  		Average:	0.0001 secs
  		Fastest:	0.0000 secs
  		Slowest:	0.0118 secs

	Request Write:
  		Average:	0.0010 secs
  		Fastest:	0.0000 secs
  		Slowest:	0.0863 secs

	Response Wait:
  		Average:	0.0095 secs
  		Fastest:	0.0001 secs
  		Slowest:	0.0458 secs

	Response Read:
  		Average:	0.0056 secs
  		Fastest:	0.0000 secs
  		Slowest:	0.0890 secs

Status code distribution:
  [200]	10000 responses

Response time histogram:
  0.000 [1]	|
  0.012 [4137]	|∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎
  0.025 [4156]	|∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎
  0.037 [1065]	|∎∎∎∎∎∎∎∎∎∎
  0.049 [394]	|∎∎∎∎
  0.061 [158]	|∎∎
  0.073 [40]	|
  0.085 [28]	|
  0.097 [13]	|
  0.110 [2]	|
  0.122 [6]	|

Latency distribution:
  10% in 0.0048 secs
  25% in 0.0097 secs
  50% in 0.0139 secs
  75% in 0.0201 secs
  90% in 0.0310 secs
  95% in 0.0396 secs
  99% in 0.0599 secs
```

## Authors

* Julian Bright - [brightsparc](https://github.com/brightsparc/)

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details