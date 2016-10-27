# Sabae City Community Bus Monitor Demo

## The Data Feed

The data can be gathered by Tsutsuji Bus Location Web API maintained by Sabae City. This demo accesses the realtime vehicle location API through logstash periodically.

### Acknowledgement and License

The data feed by [つつじバスロケーションWEB API](http://www.city.sabae.fukui.jp/users/tutujibus/web-api/web-api.html) licensed under CC-BY .

## How to Run

## Logstash

The logstash configuration file requires the logstash-filter-translate community-maintenance plugin. It is required to convert the route numbers to an appropriate route name. You may install the plugin by running bin/logstash-plugin install logstash-filter-translate or comment out the lines under `translate { ... }`. 

You may also need to adjust the `interval` setting under the `http_poller` input filter. It decides how howten you are going to access the API.

Type in `logstash/bin/logstash -r -f tsutsujibus-logstash.conf` to start receiving the vehicle location data from your Terminal.

### Importing Kibana Visuals and Dashboard

1. Open Kibana and go to Management > Index Patterns. Type in `tsutsujibus` as the index name and create the index pattern.
2. Go to Management > Saved Objects and click on Import, and select `tsutsujibus-kibana.json` by the file chooser.
3. Go to Dashboard and click on Tsutsujibus from the list of the dashboards.
