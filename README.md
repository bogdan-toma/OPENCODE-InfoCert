

## ONRC InfoCert integration API - by OpenCode S.R.L.

------------------------------------------------------------------------------------------

#### Create a new request

<details>
 <summary><code>POST</code> <code><b>{uri}/api/partners/submitRequest</b></code> <code>(creates a new request)</code></summary>

##### Endpoint

> | Key      | Value               | description                                                           |
> |-----------|-------------------------|-----------------------------------------------------------------------|
> | uri      | String  | Provided by OpenCode (STAGING / PROD)  |

##### Headers

> | Key      | Value               | description                                                           |
> |-----------|-------------------------|-----------------------------------------------------------------------|
> | Authorization      | Basic Auth   | Provided by OpenCode  |
> | X-OCD-Partner      | String   | Provided by OpenCode  |

##### Body

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | cui      |  required | String   | Company identifier (without "RO")  |
> | documentType      |  required | String   | From value list  |
> | documentScope      |  required | String   | From value list  |
> | priority      |  required | String   | Low / High  |
> | partnerRef      |  required | String   | Partner's unique internal ID of request  |

###### Example
```bash
curl -L 'https://$uri/api/partners/submitRequest' \
-u '$user:$password' \
-H 'X-OCD-Partner: $partnerId' \
-H 'Content-Type: application/json' \
-d '{
    "cui":  "32332105",
    "documentType":  "Furnizare informatii",
    "documentScope":  "Informare",
    "priority":  "Low",
    "partnerRef":  "d5f3af8e"
}'
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
```json
{
"requestId":  "jrurF1FhZ7nuyYAdy6Xm"
}
```

</details>

------------------------------------------------------------------------------------------

#### Cancel request

<details>
 <summary><code>POST</code> <code><b>{uri}/api/partners/cancelRequest</b></code> <code>(cancels a request - only from Created or RetrySendToONRC)</code></summary>

##### Endpoint

> | Key      | Value               | description                                                           |
> |-----------|-------------------------|-----------------------------------------------------------------------|
> | uri      | String  | Provided by OpenCode (STAGING / PROD)  |

##### Headers

> | Key      | Value               | description                                                           |
> |-----------|-------------------------|-----------------------------------------------------------------------|
> | Authorization      | Basic Auth   | Provided by OpenCode  |
> | X-OCD-Partner      | String   | Provided by OpenCode  |

##### Body

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | requestId      |  required | String   | Internal request ID  |

###### Example
```bash
curl -L 'https://$uri/api/partners/cancelRequest' \
-u '$user:$password' \
-H 'X-OCD-Partner: $partnerId' \
-H 'Content-Type: application/json' \
-d '{
    "requestId": "jrurF1FhZ7nuyYAdy6Xm"
}'
```

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `200`         | `application/json`        | object (JSON)    |
> | `400`         | `text/html;charset=utf-8` | None   |
> | `401`         | `text/html;charset=utf-8`         | None  |
> | `404`         | `text/html;charset=utf-8`         | None  |
> | `409`         | `text/html;charset=utf-8`         | None  |


##### Response Body

> | name      |   data type               | description                   |
> |-----------|-----------|-------------------------|
> | requestId      |   String   | Internal request ID  |
> | requestStatus      |   String   | Request Status - Cancelled  |

###### Example
```json
{
"requestId":  "jrurF1FhZ7nuyYAdy6Xm",
"requestStatus": "Cancelled"
}
```

</details>

------------------------------------------------------------------------------------------

#### Query request status

<details>
 <summary><code>POST</code> <code><b>{uri}/api/partners/queryRequestStatus</b></code> <code>(query request status)</code></summary>

##### Endpoint

> | Key      | Value               | description                                                           |
> |-----------|-------------------------|-----------------------------------------------------------------------|
> | uri      | String  | Provided by OpenCode (STAGING / PROD)  |


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
```bash
curl -L 'https://$uri/api/partners/queryRequestStatus' \
-u '$user:$password' \
-H 'X-OCD-Partner: $partnerId' \
-H 'Content-Type: application/json' \
-d '{
    "requestId": "jrurF1FhZ7nuyYAdy6Xm"
}'
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
> | requestStatus      |   String   | Request Status  |
> | onrcPortalNo | String | ONRC Portal Number |
> | docUri      |   String   | Direct download URI for generated document (present only if generated)  |
> | onrcInvoiceUri | String | Direct download URI for ONRC invoice (only for partners with self-invoice |

###### Example
```json
{
"partnerRef":  "d5f3af8e",
"requestStatus":  "Finalised",
"onrcPortalNo": "856012",
"docUri":  "https://storage.googleapis.com/download/storage/v1/b/certificatconstatator-dev.appspot.com/o/_data1_portal_ccfil_certificate_2023_3_6_certificat0000-0000Q.pdf?generation=1678138325733513&alt=media",
"onrcInvoiceUri":  "https://storage.googleapis.com/download/storage/v1/b/certificatconstatator-dev.appspot.com/o/_data1_portal_ccfil_certificate_2023_3_6_certificat0000-0000Q.pdf?generation=1678138325733513&alt=media"
}
```

</details>

------------------------------------------------------------------------------------------

#### Query ONRC status

<details>
 <summary><code>POST</code> <code><b>{uri}/api/partners/queryOnrcStatus</b></code> <code>(query ONRC status)</code></summary>

##### Endpoint

> | Key      | Value               | description                                                           |
> |-----------|-------------------------|-----------------------------------------------------------------------|
> | uri      | String  | Provided by OpenCode (STAGING / PROD)  |


##### Headers

> | Key      | Value               | description                                                           |
> |----------|---------------------|-----------------------------------------------------------------------|
> | Authorization      | Basic Auth   | Provided by OpenCode  |
> | X-OCD-Partner      | String   | Provided by OpenCode  |


###### Example
```bash
curl -L 'https://$uri/api/partners/queryOnrcStatus' \
-u '$user:$password' \
-H 'X-OCD-Partner: $partnerId' 
```

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `200`         | `application/json`        | object (JSON)    |
> | `401`         | `text/html;charset=utf-8`         | None  |


##### Response Body

> | name        |   data type  | description                                       |
> |-------------|--------------|---------------------------------------------------|
> | isInfoCertActive      |   String   | "true" / "false" string values  |

###### Example
```json
{
"isInfoCertActive": "true"
}
```

</details>

------------------------------------------------------------------------------------------
#### Value Lists
<details>
 <summary>documentType</summary>
 
 ```javascript
 "Certificat constatator de bază"
 "Certificat constatator fonduri IMM"
 "Certificat constatator pentru insolvență"
 "InfoRBR - Situatie la zi"
 "InfoRBR - Raport istoric"
 ```
</details>

<details>
 <summary>documentScope</summary>
 
 <blockquote>
 
 <details>
	 <summary>documentType = <code>"Certificat constatator de bază"</code></summary>
  <blockquote>
  <code>"Informare"
"Accesare Fonduri"
"Accesare Fonduri Europene"
"Administratia financiara"
"Administraţia Fondului pentru Mediu"
"Administrația Finanțelor Publice"
"Agenţia pentru Finanţarea Investiţiilor Rurale (AFIR)"
"Agenția de Plăți și Intervenții în Agricultură"
"Agenția Națională de Administrare Fiscală"
"Agenția Națională pentru Ocuparea Forței de Muncă"
"Agenția Națională pentru Protecția Mediului"
"Agenția Națională pentru Resurse Minerale"
"Ambasadă"
"Atestare ANRE"
"Autoritatea Rutieră Română"
"Autorizare"
"Banca Națională a României"
"Bancă"
"Birou notar public"
"Casa Națională de Asigurări de Sănătate"
"Casa Națională de Pensii"
"Direcţia Generală a Vămilor"
"Eliberare cazier judiciar"
"Fonduri SAPARD"
"Insolvență"
"Inspectoratul General pentru Imigrări"
"Instanță"
"Leasing"
"Licitație"
"Ministerul Economiei, Energiei și Mediului de Afaceri"
"Ministerul Muncii și Justiţiei Sociale"
"Obținere viză"
"Oficiul de Cadastru și Publicitate Imobiliară"
"Parchet"
"Poliție"
"Primãrie"
"PSIPAN"
"Registrul Auto Român"
"Registrul Operatorilor Intracomunitari"
"Înregistrare în scopuri de TVA"</code>
	</details>
 <details>
	 <summary>documentType = <code>"Certificat constatator fonduri IMM"</code></summary>
  <blockquote>
  <code>"Accesare Fonduri"
"Accesare Fonduri Europene"
"Agenţia pentru Finanţarea Investiţiilor Rurale (AFIR)"
"Agenția de Plăți și Intervenții în Agricultură"
"Fonduri IMM"
"Fonduri SAPARD"
"MINIMIS"
"Ministerul Economiei, Energiei și Mediului de Afaceri"
"Ministerul Muncii și Justiţiei Sociale"
"Primãrie"</code>
	</details>
 <details>
	 <summary>documentType = <code>"Certificat constatator pentru insolvență"</code></summary>
  <blockquote>
<code>"Birou notar public"
"Licitație"
"Procedura de insolventa"
"Tribunal"</code>
	</details>
<details>
	<summary>documentType = <code>"InfoRBR - Situatie la zi"</code></summary>
  <blockquote>
  <code>"Informare"</code>
</details>
<details>
	<summary>documentType = <code>"InfoRBR - Raport istoric"</code></summary>
  <blockquote>
  <code>"Informare"</code>
</details>
</details>

<details>
 <summary>requestStatus</summary>
 
> | Option   |  Description                                                           |
> |----------|----------------------------------------------------------------|
> | Created      | Request received and loaded to backend systems  |
> | Cancelled | Request cancelled by partner |
> | SendingToONRC      | In progress - API create ONRC request |
> | RetrySendToONRC | Postponed - API create ONRC request |
> | SentToONRC | Request is sent to ONRC and waiting for document |
> | DownloadONRC | In progress - check ONRC for document generation |
> | RetryDownloadONRC | Postponed - check ONRC for document generation |
> | DoneONRC | Document is generated and available |
> | InvoiceGeneratedONRC | ONRC invoice is generated and available |
> | Finalised | Request is finalised |

</details>
