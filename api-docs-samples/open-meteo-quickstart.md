# Open-Meteo Weather API: Quickstart

> **Note:** This is an unofficial documentation sample written for
> portfolio purposes. It is not affiliated with Open-Meteo.
> Official docs: https://open-meteo.com/en/docs

## Overview
The Open-Meteo Forecast API returns current weather and forecasts for any
location, based on latitude and longitude. It is free for non-commercial
use and does not require an API key.

## Before you begin
- A web browser or any tool that can send HTTP GET requests
- The latitude and longitude of your location

## Make your first request
Send a GET request to this endpoint:

`https://api.open-meteo.com/v1/forecast`

Example request, for current conditions in Kolkata:

https://api.open-meteo.com/v1/forecast?latitude=22.57&longitude=88.36&current=temperature_2m,wind_speed_10m,relative_humidity_2m

Example response:

```json
{"latitude":22.601053,"longitude":88.31776,"generationtime_ms":0.316619873046875,"utc_offset_seconds":0,"timezone":"GMT","timezone_abbreviation":"GMT","elevation":12.0,"current_units":{"time":"iso8601","interval":"seconds","temperature_2m":"°C","wind_speed_10m":"km/h","relative_humidity_2m":"%"},"current":{"time":"2026-10-27T09:15","interval":900,"temperature_2m":27.9,"wind_speed_10m":2.4,"relative_humidity_2m":78}}
```

## Request parameters
| Parameter | Required | Description | Example |
|---|---|---|---|
| latitude | Yes | Latitude of the location | 22.57 |
| longitude | Yes | Longitude of the location | 88.36 |
| current | No | Comma-separated list of current weather values to return | temperature_2m,wind_speed_10m |
| timezone | No | Timezone for returned times | Asia/Kolkata |

## Reading the response
| Field | Meaning | Unit |
|---|---|---|
| temperature_2m | Air temperature at 2 metres above ground | °C |
| wind_speed_10m | Wind speed at 10 metres above ground | km/h |
| relative_humidity_2m | Relative humidity at 2 metres | % |

[Check each unit against your real response, under "current_units".]

## Errors
| What went wrong | What you see | How to fix it |
|---|---|---|
| Missing longitude | {"reason":"Parameter 'latitude' and 'longitude' must have the same number of elements","error":true} | Add the longitude parameter |
| Latitude out of range | {"reason":"Latitude must be in range of -90 to 90°. Given: 999.0.","error":true} | Use a latitude between -90 and 90 |

## Troubleshooting tips
- If you see no data, check that your latitude and longitude are not swapped.
- If a value is missing, check the spelling of the parameter name.
