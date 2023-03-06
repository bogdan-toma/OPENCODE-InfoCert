
## OpenCode InfoCert integration API

------------------------------------------------------------------------------------------

#### Create a new request

<details>
 <summary><code>POST</code> <code><b>/api/partners/submitRequest</b></code> <code>(creates a new request)</code></summary>

##### Headers

> | Key      | Value               | description                                                           |
> |-----------|-------------------------|-----------------------------------------------------------------------|
> | Authorization      | Basic Auth   | Provided by OpenCode  |
> | X-OCD-Partner      | String   | Provided by OpenCode  |

##### Body

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | cui      |  required | String   | Company identifier (without "RO")  |
> | cuiReg      |  required | String   | Company registration number  |
> | documentType      |  required | String   | From value list  |
> | documentScope      |  required | String   | From value list  |
> | priority      |  required | String   | Low / High  |
> | partnerRef      |  required | String   | Partner's unique internal ID of request  |

###### Example
```javascript
{
"cui":  "32332105",
"cuiReg":  "J40/12446/2013",
"documentType":  "Furnizare informatii",
"documentScope":  "Informare",
"priority":  "High"
"partnerRef":  "d5f3af8e"
}
```

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `200`         | `application/json`        | object (JSON)                             |
> | `400`         | `text/html;charset=utf-8` | None   |
> | `401`         | `text/html;charset=utf-8`         | None                                   |


##### Response Body

> | name      |   data type               | description                   |
> |-----------|-----------|-------------------------|
> | requestId      |   String   | Internal request ID  |

###### Example
```javascript
{
"requestId":  "jrurF1FhZ7nuyYAdy6Xm"
}
```

</details>

------------------------------------------------------------------------------------------

#### Query Request Status

<details>
 <summary><code>POST</code> <code><b>/api/partners/queryRequestStatus</b></code> <code>(query request status)</code></summary>


##### Headers

> | Key      | Value               | description                                                           |
> |----------|---------------------|-----------------------------------------------------------------------|
> | Authorization      | Basic Auth   | Provided by OpenCode  |
> | X-OCD-Partner      | String   | Provided by OpenCode  |

##### Body

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | requestId      |  required | String   | Internal request ID  |

###### Example
```javascript
{
"requestId":  "jrurF1FhZ7nuyYAdy6Xm"
}
```

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `200`         | `application/json`        | object (JSON)    |
> | `400`         | `text/html;charset=utf-8` | None   |
> | `401`         | `text/html;charset=utf-8`         | None  |
> | `404`         | `text/html;charset=utf-8`         | None  |


##### Response Body

> | name        |   data type  | description                                       |
> |-------------|--------------|---------------------------------------------------|
> | partnerRef      |   String   | Partner's unique internal ID of request  |
> | requestStatus      |   String   | Internal request ID  |
> | docUri      |   String   | Direct download URI for generated document (present only if generated)  |

###### Example
```javascript
{
"partnerRef":  "d5f3af8e",
"requestStatus":  "Finalised",
"docUri":  "https://storage.googleapis.com/download/storage/v1/b/certificatconstatator-dev.appspot.com/o/_data1_portal_ccfil_certificate_2023_3_6_certificat0000-0000Q.pdf?generation=1678138325733513&alt=media"
}
```

</details>

------------------------------------------------------------------------------------------
