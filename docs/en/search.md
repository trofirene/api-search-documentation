# Product Search

<!-- [RU](../ru/products-search.md) | [EN](products-search.md) -->

## Request Information

| Property  | Value                  |
| --------- | ---------------------- |
| Method    | `GET`                  |
| URL       | `/api/products/search` |
| Form Type | `query`                |
| URL Name  | `products_search`      |

This endpoint allows searching for products using multiple filters: categories, price, weight, dimensions, manufacturers, sellers, rating, and characteristics (variants). It supports pagination and returns detailed information for building filters on the frontend (min/max values, available variants, lists of manufacturers and sellers).

## Request Parameters (Query Parameters)

The request is sent as a JSON object in the body of a `GET` request.

### Main Filters

| Field      | Type     | Description                                                                            |
| ---------- | -------- | -------------------------------------------------------------------------------------- |
| `filters`  | `object` | Object with filtering conditions (see table below).                                    |
| `paginate` | `object` | Object with pagination settings: `page` (page number) and `pp_items` (items per page). |

### `filters` Object Structure

| Field Name                  | Description                                      | Data Type | Required | Example Values / Options                                                             |
| --------------------------- | ------------------------------------------------ | --------- | -------- | ------------------------------------------------------------------------------------ |
| `id`                        | Filter by specific product ID                    | `string`  | No       | `"123"`                                                                              |
| `categories`                | Category IDs for filtering products              | `array`   | No       | `[1, 3, 5]`                                                                          |
| `subscription_exists`       | Filter by subscription availability              | `string`  | No       | `"true"` / `"false"` / `""`                                                          |
| `id_in`                     | Filter by multiple product IDs (comma-separated) | `string`  | No       | `"123,456,789"`                                                                      |
| `is_related_for`            | Product ID to find related products              | `string`  | No       | `"123"`                                                                              |
| `product_group`             | Filter by product groups                         | `array`   | No       | `[2, 4]`                                                                             |
| `search_string`             | Search query by name/description                 | `string`  | No       | `"brooch"`                                                                           |
| `price_from`                | Start of price range                             | `string`  | No       | `"1000"`                                                                             |
| `price_to`                  | End of price range                               | `string`  | No       | `"5000"`                                                                             |
| `price_currency`            | Price currency ID                                | `string`  | No       | `"1"`                                                                                |
| `product_owner`             | Seller IDs                                       | `array`   | No       | `[11, 22]`                                                                           |
| `product_owner_name`        | Search by seller name                            | `string`  | No       | `"John"`                                                                             |
| `product_manufacture`       | Manufacturer IDs                                 | `array`   | No       | `[1, 2]`                                                                             |
| `avg_raiting_from`          | Start of average rating range                    | `string`  | No       | `"4.0"`                                                                              |
| `avg_raiting_to`            | End of average rating range                      | `string`  | No       | `"5.0"`                                                                              |
| `c_aprooved_feedbacks_from` | Minimum number of approved reviews               | `string`  | No       | `"10"`                                                                               |
| `c_aprooved_feedbacks_to`   | Maximum number of approved reviews               | `string`  | No       | `"100"`                                                                              |
| `price_discount_from`       | Minimum discounted price                         | `string`  | No       | `"500"`                                                                              |
| `price_discount_to`         | Maximum discounted price                         | `string`  | No       | `"3000"`                                                                             |
| `weight_search_by`          | Weight search type                               | `string`  | No       | `"exact"` / `"range"`                                                                |
| `weight_from`               | Minimum weight                                   | `string`  | No       | `"100"`                                                                              |
| `weight_to`                 | Maximum weight                                   | `string`  | No       | `"500"`                                                                              |
| `length_search_by`          | Length search type                               | `string`  | No       | `"exact"` / `"range"`                                                                |
| `length_from`               | Minimum length                                   | `string`  | No       | `"10"`                                                                               |
| `length_to`                 | Maximum length                                   | `string`  | No       | `"50"`                                                                               |
| `width_from`                | Minimum width                                    | `string`  | No       | `"5"`                                                                                |
| `width_to`                  | Maximum width                                    | `string`  | No       | `"20"`                                                                               |
| `height_from`               | Minimum height                                   | `string`  | No       | `"2"`                                                                                |
| `height_to`                 | Maximum height                                   | `string`  | No       | `"15"`                                                                               |
| `owner_rating_from`         | Minimum seller rating                            | `string`  | No       | `"4.0"`                                                                              |
| `show_whishlist`            | Show only items from wishlist                    | `string`  | No       | `"true"` / `"false"` / `""`                                                          |
| `only_featured`             | Show only featured products                      | `string`  | No       | `"true"` / `"false"` / `""`                                                          |
| `only_new`                  | Show only new products                           | `string`  | No       | `"true"` / `"false"` / `""`                                                          |
| `with_discount`             | Show only discounted products                    | `string`  | No       | `"true"` / `"false"` / `""`                                                          |
| `is_good_for_promo`         | Products suitable for promotions                 | `string`  | No       | `"true"` / `"false"` / `""`                                                          |
| `from_modal`                | Request from modal window                        | `string`  | No       | `"true"` / `"false"` / `""`                                                          |
| `ordering`                  | Result sorting                                   | `string`  | No       | `"price"`, `"-price"`, `"avg_raiting"`, `"-avg_raiting"`, `"newest"`, `"popularity"` |
| `variant_25`                | Filter by characteristic with ID 25              | `array`   | No       | `[33]`                                                                               |
| `variant_24`                | Filter by characteristic with ID 24              | `array`   | No       | `[31]`                                                                               |
| `variant_13`                | Filter by characteristic with ID 13              | `array`   | No       | `[28]`                                                                               |
| `variant_1`                 | Filter by characteristic with ID 1               | `array`   | No       | `[5, 6, 8]`                                                                          |
| `variant_4`                 | Filter by characteristic with ID 4               | `array`   | No       | `[15, 16]`                                                                           |
| `variant_3`                 | Filter by characteristic with ID 3               | `array`   | No       | `[9, 10, 11, 12, 13]`                                                                |

### `paginate` Object Structure

| Field Name | Description                | Data Type | Required | Example Value |
| ---------- | -------------------------- | --------- | -------- | ------------- |
| `page`     | Page number for pagination | `integer` | Yes      | `1`           |
| `pp_items` | Number of items per page   | `integer` | Yes      | `15`          |

### Request Example

```json
{
  "filters": {
    "categories": [1, 3],
    "search_string": "brooch",
    "price_from": "1000",
    "price_to": "5000",
    "with_discount": "true",
    "ordering": "-avg_raiting",
    "variant_1": [5, 6],
    "variant_3": [9, 10]
  },
  "paginate": {
    "page": 1,
    "pp_items": 15
  }
}
```

## Response Information

Upon successful execution, an object with search results is returned. The response structure includes aggregated data for building filters on the frontend: minimum and maximum price, weight, and dimension values, available characteristic variants, lists of manufacturers, sellers, and categories, as well as information about discounts and products with high ratings.

| Field             | Description                                              | Example             |
| ----------------- | -------------------------------------------------------- | ------------------- |
| `form_errors`     | Form validation errors. `null` on successful request     | `null`              |
| `success_message` | Success message                                          | `"Success"`         |
| `page_data`       | Main response data object (see detailed structure below) | `{...}`             |
| `exc_stack`       | Error stack trace (empty on success)                     | `""`                |
| `debug`           | Debugging information                                    | `[]`                |
| `user_groups`     | User groups                                              | `""`                |
| `user_perms`      | User permissions                                         | `""`                |
| `spent`           | Server request execution time in seconds                 | `1.5`               |
| `locale`          | Language code used for response localization             | `"en"`              |
| `url_name`        | Technical endpoint name                                  | `"products_search"` |

### Detailed `page_data` Structure

| Field              | Description                                                         |
| ------------------ | ------------------------------------------------------------------- |
| `min_max`          | Minimum and maximum values for price, weight, length, width, height |
| `variants`         | Available product variants (characteristics: color, size, etc.)     |
| `selects`          | Lists of manufacturers, sellers, and categories for filtering       |
| `measures`         | Detailed measurement data (similar to `min_max`)                    |
| `discounts`        | Discount information (number of products with discounts)            |
| `raiting_above_45` | Number of products with rating above 4.5                            |

#### `min_max` / `measures` Structure

The object contains minimum and maximum values for various metrics. Keys (1, 2, 3...) are identifiers for currencies or units of measurement.

| Field        | Description    |
| ------------ | -------------- |
| `max_price`  | Maximum prices |
| `min_price`  | Minimum prices |
| `max_weight` | Maximum weight |
| `min_weight` | Minimum weight |
| `max_length` | Maximum length |
| `min_length` | Minimum length |
| `max_height` | Maximum height |
| `min_height` | Minimum height |
| `max_width`  | Maximum width  |
| `min_width`  | Minimum width  |

Each value contains:

- `transform_value` — formatted value (for display)
- `real_value` — actual value (for calculations)

**Example:**

```json
"max_price": {
  "1": { "transform_value": 26934, "real_value": 26934 }
}
```

**Response Example**

```json
{
  "form_errors": null,
  "success_message": "Success",
  "page_data": {
    "min_max": {
      "max_price": {
        "1": { "transform_value": 26934, "real_value": 26934 }
      },
      "min_price": {
        "1": { "transform_value": 0.91, "real_value": 0.909 }
      }
    },
    "variants": {
      "variant_1": {
        "id": 1,
        "locale": {
          "ru": { "variant_type_name": "Цвет" },
          "en": { "variant_type_name": "Color" }
        },
        "options": [
          {
            "id": 5,
            "locale": { "ru": "Красный" },
            "color": "#f20707",
            "count": 2
          }
        ]
      }
    },
    "selects": {
      "manufacture": [{ "id": 1, "name": "Ksushia", "count": 83 }],
      "categories": [
        { "id": 1, "locale": { "ru": { "cg_name": "Броши" } }, "count": 37 }
      ]
    },
    "discounts": { "any": 15 },
    "raiting_above_45": 5
  },
  "spent": 1.12,
  "locale": "en",
  "url_name": "products_search"
}
```
