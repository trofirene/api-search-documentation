# Getting List of Countries and Addresses

<!-- [RU](../ru/POST.md) | [EN](POST.md) -->

# Screenshot 1

<img src="../images/screen.png" width="300" alt="screen1">

# Screenshot 2

<img src="../images/screen2.png" width="300" alt="screen2">

# Screenshot 3

<img src="../images/screen3.png" width="300" alt="screen3">

## Request Information

| Property         | Value                |
| :--------------- | :------------------- |
| **Method**       | `POST`               |
| **URL**          | `/api/addresses/get` |
| **Content Type** | `application/json`   |
| **URL Name**     | `address_get`        |

This endpoint provides reference information about countries and user addresses. Returns a list of countries with their codes and localized names, as well as a list of saved addresses for the current user.

---

## Request Parameters (Request Body)

### Main Fields

| Field      | Type     | Required | Description                      |
| :--------- | :------- | :------: | :------------------------------- |
| `filters`  | `object` |    ❌    | Object with filtering conditions |
| `paginate` | `object` |    ✅    | **Pagination settings**          |

### Detailed Structure

#### `filters` Object

| Field  | Type     | Required | Description                                                                  | Example |
| :----- | :------- | :------: | :--------------------------------------------------------------------------- | :------ |
| _none_ | `object` |    ❌    | Filtering is not supported in the current version. Pass an empty object `{}` | `{}`    |

> 💡 **For future use:** The structure allows for adding filters in the future. Keep an eye on documentation updates.

#### `paginate` Object

| Field      | Type      | Required | Description                   | Example |
| :--------- | :-------- | :------: | :---------------------------- | :------ |
| `page`     | `integer` |    ✅    | Page number (starting from 1) | `1`     |
| `pp_items` | `integer` |    ✅    | Number of items per page      | `10`    |

---

### Request Example

```json
{
  "filters": {},
  "paginate": {
    "page": 1,
    "pp_items": 10
  }
}
```
