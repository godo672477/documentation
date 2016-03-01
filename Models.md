## Models

### `SafeUUID`

### `Option`

### `DateTime`

### `LocalDate`

### Agency

case class Agency(agencyUid: SafeAgencyUid,
                     name: String,
                     extName: Option[String],
                     address: Option[Address],
                     phones: List[String],
                     fax: Option[String],
                     emails: List[String])
