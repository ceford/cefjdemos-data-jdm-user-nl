<!-- Filename: Localhost / Display title: Schema.org - Aangepast -->

## Doel

De Custom schema-plugin wordt gebruikt om aangepaste informatie in raw JSON-LD-formaat in te voeren. Het is geen Schema Org-type.

Open een artikelbewerkingsformulier en selecteer het Schema-tabblad om een Schema-type te selecteren en de gegevens voor dat type in te stellen. Als een Schema-type niet in de lijst voorkomt, kan zijn Plugin zijn uitgeschakeld. De in te voeren waarden in elk veld zijn meestal vanzelfsprekend.

Dit is een voorbeeld van een handgemaakt rijk fragment:

```json
{
  "@context": "https://schema.org",
  "@type": "WebPage",
  "name": "Your Article Title",
  "description": "A brief description of the article.",
  "timeRequired": "PT5M"
}
```

De eigenschap *timeRequired* vertegenwoordigt de geschatte leestijd in ISO 8601 duurformaat. In dit geval betekent PT5M *5 minuten*.

## Voorbeeld Screenshot

Hieronder staat een voorbeeld van een Aangepast schema-veld in een Artikelbewerkingsformulier.

![A custom schema edit form](../../../en/images/schemas/edit-schema-custom.png)

*Vertaald door openai.com*

