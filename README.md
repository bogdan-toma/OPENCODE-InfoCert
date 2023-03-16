

## OpenCode InfoCert integration API

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
> | cuiReg      |  required | String   | Company registration number  |
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
    "cuiReg":  "J40/12446/2013",
    "documentType":  "Furnizare informatii",
    "documentScope":  "Informare",
    "priority":  "High",
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

#### Query Request Status

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
> | docUri      |   String   | Direct download URI for generated document (present only if generated)  |

###### Example
```json
{
"partnerRef":  "d5f3af8e",
"requestStatus":  "Finalised",
"docUri":  "https://storage.googleapis.com/download/storage/v1/b/certificatconstatator-dev.appspot.com/o/_data1_portal_ccfil_certificate_2023_3_6_certificat0000-0000Q.pdf?generation=1678138325733513&alt=media"
}
```

</details>

------------------------------------------------------------------------------------------
#### Value Lists
<details>
 <summary>documentType</summary>
 
 ```javascript
 "Furnizare informatii"
 "Certificat constatator de bază"
 "Certificat constatator fonduri IMM"
 "Certificat constatator pentru insolvență"
 ```
</details>

<details>
 <summary>documentScope</summary>
 
 <blockquote>
 
 <details>
	 <summary>documentType = <code>"Furnizare informatii"</code></summary>
  <blockquote>
  <code>"Informare"</code>
	</details>
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
</details>
<details>
 <summary>requestStatus</summary>
 
> | Option   |  Description                                                           |
> |----------|----------------------------------------------------------------|
> | Created      | Request received and loaded to backend systems  |
> | SendingToONRC      | RPA in progress to create ONRC request - first try |
> | RetrySendToONRC | Subsequent RPA tries to create ONRC request |
> | SentToONRC | Request is sent to ONRC and waiting for document |
> | DownloadONRC | First check if document is generated |
> | RetryDownloadONRC | Subsequent checks for document generation |
> | DoneONRC | Document is generated and available |
> | Finalised | Request is finalised |

</details>
