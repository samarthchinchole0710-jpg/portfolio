# WeatherPulse API Reference (Excerpt)

**Document type:** API Reference
**Audience:** Software developers integrating a REST API
**Why this sample:** Demonstrates developer-facing documentation — clear endpoint definitions, parameter tables, and complete request/response examples.

---

## Overview

The WeatherPulse API provides current conditions and 5-day forecasts for a given location. All endpoints return JSON and require an API key.

**Base URL:** `https://api.weatherpulse.example.com/v1`

## Authentication

Include your API key as a query parameter on every request:

```
?api_key=YOUR_API_KEY
```

Requests without a valid key return a `401 Unauthorized` response.

## Endpoint: Get Current Conditions

```
GET /current
```

Returns current weather conditions for a specified location.

### Parameters

| Parameter | Type | Required | Description |
|---|---|---|---|
| `lat` | float | Yes | Latitude of the location, in decimal degrees |
| `lon` | float | Yes | Longitude of the location, in decimal degrees |
| `units` | string | No | `metric` (default) or `imperial` |
| `api_key` | string | Yes | Your API key |

### Example Request

```bash
curl "https://api.weatherpulse.example.com/v1/current?lat=28.6&lon=77.2&units=metric&api_key=YOUR_API_KEY"
```

### Example Response

```json
{
  "location": {
    "lat": 28.6,
    "lon": 77.2
  },
  "current": {
    "temperature": 34.2,
    "condition": "Partly Cloudy",
    "humidity": 41,
    "wind_speed": 12.4,
    "observed_at": "2026-08-02T10:30:00Z"
  }
}
```

### Response Fields

| Field | Type | Description |
|---|---|---|
| `current.temperature` | float | Temperature in the requested units |
| `current.condition` | string | Short text description of conditions |
| `current.humidity` | integer | Relative humidity, as a percentage |
| `current.wind_speed` | float | Wind speed in km/h (metric) or mph (imperial) |
| `current.observed_at` | string | ISO 8601 timestamp of the observation |

### Error Responses

| Status Code | Meaning | Common Cause |
|---|---|---|
| `400` | Bad Request | Missing or invalid `lat`/`lon` |
| `401` | Unauthorized | Missing or invalid `api_key` |
| `404` | Not Found | No data available for the given coordinates |
| `429` | Too Many Requests | Rate limit exceeded (see Rate Limits below) |

**Error response body:**

```json
{
  "error": {
    "code": 400,
    "message": "Parameter 'lat' must be between -90 and 90."
  }
}
```

## Rate Limits

The free tier allows 60 requests per minute. The current rate limit status is returned in response headers:

| Header | Description |
|---|---|
| `X-RateLimit-Limit` | Maximum requests allowed per minute |
| `X-RateLimit-Remaining` | Requests remaining in the current window |
| `X-RateLimit-Reset` | Unix timestamp when the limit resets |

---

*This is a portfolio writing sample built around a fictional API. It is not connected to a real service.*
