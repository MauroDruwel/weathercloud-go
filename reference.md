# Reference
## Auth
<details><summary><code>client.Auth.Login(request) -> error</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Authenticates a user session to allow viewing private indoor sensors (`tempin`, `humin`, `heatin`) for the user's station.
This endpoint expects form urlencoded data and returns a `302 Found` redirect on successful login.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &sdk.LoginAuthRequest{
        LoginFormEntity: "LoginForm[entity]",
        LoginFormPassword: "LoginForm[password]",
    }
client.Auth.Login(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**loginFormEntity:** `string` — Username or email address
    
</dd>
</dl>

<dl>
<dd>

**loginFormPassword:** `string` — Account password
    
</dd>
</dl>

<dl>
<dd>

**loginFormRememberMe:** `*sdk.LoginAuthRequestLoginFormRememberMe` — Keep the user logged in
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## DeviceLive
<details><summary><code>client.DeviceLive.GetValues(DeviceID) -> *sdk.DeviceValues</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns the latest sensor values for a device. **No CSRF token needed.**
This is the primary endpoint for a Home Assistant sensor integration.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &sdk.GetValuesDeviceLiveRequest{
        DeviceID: "5726468552",
    }
client.DeviceLive.GetValues(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**deviceID:** `string` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.DeviceLive.GetStats() -> *sdk.DeviceStats</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns current values plus day/month/year min and max for all sensors.
Each value is a `[unix_timestamp, value]` tuple.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &sdk.GetStatsDeviceLiveRequest{
        Code: "5726468552",
    }
client.DeviceLive.GetStats(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**code:** `string` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.DeviceLive.GetInfo(DeviceID) -> *sdk.DeviceInfo</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Station name, location, elevation, equipment info.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &sdk.GetInfoDeviceLiveRequest{
        DeviceID: "5726468552",
    }
client.DeviceLive.GetInfo(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**deviceID:** `string` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.DeviceLive.GetWindRose() -> *sdk.WindData</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Wind direction distribution data for the wind rose chart.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &sdk.GetWindRoseDeviceLiveRequest{
        Code: "5726468552",
    }
client.DeviceLive.GetWindRose(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**code:** `string` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.DeviceLive.GetUpdateStatus(request) -> *sdk.GetUpdateStatusDeviceLiveResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns seconds since last update and device online status.

> ⚠️ **Requires `X-Requested-With: XMLHttpRequest`** header — without it the server returns an empty 200.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &sdk.GetUpdateStatusDeviceLiveRequest{
        D: "5726468552",
    }
client.DeviceLive.GetUpdateStatus(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**d:** `string` — Device ID
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.DeviceLive.GetOwnerProfile(request) -> *sdk.DeviceProfile</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns observer name, follower count, and device brand/model.

> ⚠️ **Requires `X-Requested-With: XMLHttpRequest`** header — without it the server returns an empty 200.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &sdk.GetOwnerProfileDeviceLiveRequest{
        D: "5726468552",
    }
client.DeviceLive.GetOwnerProfile(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**d:** `string` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## DeviceHistory
<details><summary><code>client.DeviceHistory.GetEvolution(request) -> *sdk.EvolutionResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns hourly aggregated history for a given variable and period.

> ⚠️ **Requires `X-Requested-With: XMLHttpRequest`** header — without it the server returns an empty 200.

**Variable codes:**
| Code | Sensor |
|------|--------|
| 101  | Temperature (°C) |
| 201  | Humidity (%) |
| 541  | Dew point (°C) |
| 641  | Barometric pressure (hPa) |
| 701  | Wind speed (m/s) |
| 6001 | Wind direction (°) |
| 6501 | Wind gust / high speed (m/s) |
| 801  | Rain (mm) |
| 811  | Rain rate (mm/h) |
| 1001 | Solar radiation (W/m²) |
| 1101 | UV index |

**Period values:** `day`, `week`, `month`, `year`
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &sdk.GetEvolutionDeviceHistoryRequest{
        Device: "5726468552",
        Variable: 101,
        Period: sdk.GetEvolutionDeviceHistoryRequestPeriodDay,
    }
client.DeviceHistory.GetEvolution(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**device:** `string` 
    
</dd>
</dl>

<dl>
<dd>

**variable:** `int` 
    
</dd>
</dl>

<dl>
<dd>

**period:** `*sdk.GetEvolutionDeviceHistoryRequestPeriod` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Forecast
<details><summary><code>client.Forecast.GetDaily() -> *sdk.ForecastResponse</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &sdk.GetDailyForecastRequest{
        ID: "5726468552",
    }
client.Forecast.GetDaily(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `string` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Map
<details><summary><code>client.Map.GetDevices(request) -> *sdk.MapDevicesResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns stations visible on the map for a given location bounding box.

> ⚠️ **Requires `X-Requested-With: XMLHttpRequest`** header — without it the server returns an empty 200.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &sdk.GetDevicesMapRequest{}
client.Map.GetDevices(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**user:** `*string` — Filter by user (empty = all)
    
</dd>
</dl>

<dl>
<dd>

**location:** `*string` — lat,lon,zoom format
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Map.GetBackgroundDevices(request) -> *sdk.MapDevicesResponse</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &sdk.GetBackgroundDevicesMapRequest{}
client.Map.GetBackgroundDevices(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**user:** `*string` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Map.GetMetars(request) -> *sdk.GetMetarsMapResponse</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := map[string]any{
        "key": "value",
    }
client.Map.GetMetars(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `map[string]any` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Stations
<details><summary><code>client.Stations.GetNearby(Lat, Lon, Km) -> *sdk.PageDevicesResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns nearby stations as JSON (despite `text/html` content-type header).
All `page/*` endpoints return `PageDevice` objects that include the **station name**.
Values are scaled integers — divide by 10 (e.g. `temp: 281` = 28.1°C).
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &sdk.GetNearbyStationsRequest{
        Lat: 1.1,
        Lon: 1.1,
        Km: 1,
    }
client.Stations.GetNearby(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**lat:** `float64` 
    
</dd>
</dl>

<dl>
<dd>

**lon:** `float64` 
    
</dd>
</dl>

<dl>
<dd>

**km:** `int` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Stations.GetPopular(Country, Period) -> *sdk.PageDevicesResponse</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &sdk.GetPopularStationsRequest{
        Country: "BE",
        Period: sdk.GetPopularStationsRequestPeriodDay,
    }
client.Stations.GetPopular(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**country:** `string` 
    
</dd>
</dl>

<dl>
<dd>

**period:** `*sdk.GetPopularStationsRequestPeriod` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Stations.GetNewest(Country) -> *sdk.PageDevicesResponse</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &sdk.GetNewestStationsRequest{
        Country: "BE",
    }
client.Stations.GetNewest(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**country:** `string` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Stations.GetMostFollowed(Country) -> *sdk.PageDevicesResponse</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &sdk.GetMostFollowedStationsRequest{
        Country: "BE",
    }
client.Stations.GetMostFollowed(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**country:** `string` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Stations.GetLastViews() -> *sdk.PageDevicesResponse</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Stations.GetLastViews(
        context.TODO(),
    )
}
```
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Stations.GetOwn() -> *sdk.PageDevicesResponse</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Stations.GetOwn(
        context.TODO(),
    )
}
```
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Stations.GetStationPage(DeviceID) -> string</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

The station **name** is not available from any JSON API endpoint.
The easiest way to get it is to fetch the station's HTML page and extract
the name from the `<title>` or `og:title` meta tag.

**Example response title:**
```
WeatherStation Skyline - Weathercloud | Global network of weather stations
```

Strip everything from ` - Weathercloud` onward to get the clean station name.

> This is a plain HTML page, not a JSON API. Use it for scraping only.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &sdk.GetStationPageStationsRequest{
        DeviceID: "deviceId",
    }
client.Stations.GetStationPage(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**deviceID:** `string` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Metar
<details><summary><code>client.Metar.GetValues(DeviceID) -> *sdk.DeviceValues</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Most `device/*` routes work identically for METAR (airport) stations by replacing the `device` prefix with `metar`.

METAR station IDs are **ICAO codes** (4 letters), e.g. `EBBR` for Brussels Airport.

**Supported `metar/*` routes (same request/response as their `device/*` counterparts):**
- `GET /metar/values/{icao}` — current readings
- `GET /metar/stats?code={icao}` — statistics
- `GET /metar/wind?code={icao}` — wind rose
- `GET /metar/info/{icao}` — station metadata
- `POST /metar/ajaxupdatedate` — last update time
- `POST /metar/ajaxprofile` — station profile
- `POST /metar/evolution` — time-series history

> **Not supported for METAR:** `/device/ajaxdevicestats`
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &sdk.GetValuesMetarRequest{
        DeviceID: "EBBR",
    }
client.Metar.GetValues(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**deviceID:** `string` — ICAO airport code
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

