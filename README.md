

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
```json
{
"cui":  "32332105",
"cuiReg":  "J40/12446/2013",
"documentType":  "Furnizare informatii",
"documentScope":  "Informare",
"priority":  "High",
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
```json
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
```json
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
 "Certificat constatator de baz??"
 "Certificat constatator fonduri IMM"
 "Certificat constatator pentru insolven????"
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
	 <summary>documentType = <code>"Certificat constatator de baz??"</code></summary>
  <blockquote>
  <code>"Informare"
"Accesare Fonduri"
"Accesare Fonduri Europene"
"Administratia financiara"
"Administra??ia Fondului pentru Mediu"
"Administra??ia Finan??elor Publice"
"Agen??ia pentru Finan??area Investi??iilor Rurale (AFIR)"
"Agen??ia de Pl????i ??i Interven??ii ??n Agricultur??"
"Agen??ia Na??ional?? de Administrare Fiscal??"
"Agen??ia Na??ional?? pentru Ocuparea For??ei de Munc??"
"Agen??ia Na??ional?? pentru Protec??ia Mediului"
"Agen??ia Na??ional?? pentru Resurse Minerale"
"Ambasad??"
"Atestare ANRE"
"Autoritatea Rutier?? Rom??n??"
"Autorizare"
"Banca Na??ional?? a Rom??niei"
"Banc??"
"Birou notar public"
"Casa Na??ional?? de Asigur??ri de S??n??tate"
"Casa Na??ional?? de Pensii"
"Direc??ia General?? a V??milor"
"Eliberare cazier judiciar"
"Fonduri SAPARD"
"Insolven????"
"Inspectoratul General pentru Imigr??ri"
"Instan????"
"Leasing"
"Licita??ie"
"Ministerul Economiei, Energiei ??i Mediului de Afaceri"
"Ministerul Muncii ??i Justi??iei Sociale"
"Ob??inere viz??"
"Oficiul de Cadastru ??i Publicitate Imobiliar??"
"Parchet"
"Poli??ie"
"Prim??rie"
"PSIPAN"
"Registrul Auto Rom??n"
"Registrul Operatorilor Intracomunitari"
"??nregistrare ??n scopuri de TVA"</code>
	</details>
 <details>
	 <summary>documentType = <code>"Certificat constatator fonduri IMM"</code></summary>
  <blockquote>
  <code>"Accesare Fonduri"
"Accesare Fonduri Europene"
"Agen??ia pentru Finan??area Investi??iilor Rurale (AFIR)"
"Agen??ia de Pl????i ??i Interven??ii ??n Agricultur??"
"Fonduri IMM"
"Fonduri SAPARD"
"MINIMIS"
"Ministerul Economiei, Energiei ??i Mediului de Afaceri"
"Ministerul Muncii ??i Justi??iei Sociale"
"Prim??rie"</code>
	</details>
 <details>
	 <summary>documentType = <code>"Certificat constatator pentru insolven????"</code></summary>
  <blockquote>
<code>"Birou notar public"
"Licita??ie"
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
