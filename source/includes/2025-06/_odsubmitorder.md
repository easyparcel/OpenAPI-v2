# OnDemand Order Submission

This guide explains how to submit an on-demand shipment order with and without applying a coupon, and the structure of the response received.

## HTTP Request (Ondemand Submit Order)

`POST https://api.easyparcel.com/ondemand/order`

## 📥 Request Parameters

### 📦 Request Sample

```json
{ 
    "coupon_codes":["a186f575-8481-4cf0-80e6-909871eb7e97"],
    "origin_country": "MY",
    "ondemand_service_id": "EP-CS09",
    "schedule_pickup_date": "2024-12-10",
    "schedule_pickup_time": "17:35:15",
    "time_zone": "Asia/Kuala_Lumpur",
    "metadata": {
        "quotationId": "3114850556997669249"
    },
    "waypoint": [
        {
            "point": 0,
            "type": "pickup",
            "remark": "1",
            "coordinates": {
                "latitude": 5.342720241204454,
                "longitude": 100.28204988381822
            },
            "item": [
                {
                    "quantity": "1",
                    "description": "1",
                    "dimensions": {
                        "height": "1",
                        "width": "1",
                        "length": "1",
                        "weight": "1"
                    }
                }
            ],
            "shipment_info": {
                "phone_number_country_code": "MY",
                "phone_number": "1278491622",
                "address": "L1 Lobby, Suntec City Tower 1 & 2, 7 Temasek Boulevard, Singapore, 038987",
                "name": "111",
                "email": "as@as.as"
            }
        },
        {
            "point": 1,
            "type": "dropoff",
            "remark": "222",
            "coordinates": {
                "latitude": 5.325513957,
                "longitude": 100.2862732
            },
            "item": [
                {
                    "quantity": "2",
                    "description": "2",
                    "dimensions": {
                        "height": "2",
                        "width": "2",
                        "length": "2",
                        "weight": "2"
                    }
                }
            ],
            "shipment_info": {
                "name": "222",
                "email": "as@as.as",
                "phone_number_country_code": "MY",
                "phone_number": "127491622",
                "address": "Terminal 1 Departure - Changi Airport, 80 Airport Boulevard, Singapore, 819642"
            }
        }
    ]
}
```


| Parameter                                                 | Type    | Required | Description                                    |
| --------------------------------------------------------- | ------- | -------- | ---------------------------------------------- |
| coupon_codes                                              | string  | Optional | Apply coupon codes to get further discount     |
| ondemand\_service\_id                                     | string  | Yes      | ID of the selected on-demand service           |
| origin\_country                                           | string  | Yes      | ISO 3166-1 alpha-2 country code                |
| schedule\_pickup\_date                                    | string  | Optional | Date of pickup (YYYY-MM-DD)                    |
| schedule\_pickup\_time                                    | string  | Optional | Time of pickup (HH\:MM\:SS)                    |
| time\_zone                                                | string  | Optional | Time zone of the pickup schedule               |
| metadata                                                  | object  | Yes      | Additional metadata, e.g. quotationId          |
| waypoint                                                  | array   | Yes      | Array of pickup and dropoff points             |
| waypoint\[\*].point                                       | numeric | Yes      | Sequence index (e.g., 0 = pickup, 1 = dropoff) |
| waypoint\[\*].type                                        | string  | Yes      | Type of stop; must be "pickup" or "dropoff"    |
| waypoint\[\*].coordinates.latitude                        | numeric | Yes      | Latitude of the location                       |
| waypoint\[\*].coordinates.longitude                       | numeric | Yes      | Longitude of the location                      |
| waypoint\[\*].item                                        | array   | Yes      | Items associated with the waypoint             |
| waypoint\[*].item\[*].quantity                            | string  | Yes      | Quantity of the item                           |
| waypoint\[*].item\[*].description                         | string  | Optional | Description of the item                        |
| waypoint\[*].item\[*].dimensions.height                   | string  | Yes      | Height of the item (in cm)                     |
| waypoint\[*].item\[*].dimensions.width                    | string  | Yes      | Width of the item (in cm)                      |
| waypoint\[*].item\[*].dimensions.length                   | string  | Yes      | Length of the item (in cm)                     |
| waypoint\[*].item\[*].dimensions.weight                   | string  | Yes      | Weight of the item (in kg)                     |
| waypoint\[\*].shipment\_info.name                         | string  | Yes      | Name of the sender/receiver                    |
| waypoint\[\*].shipment\_info.email                        | string  | Optional | Email address                                  |
| waypoint\[\*].shipment\_info.phone\_number\_country\_code | string  | Yes      | Phone number country code (e.g., MY)           |
| waypoint\[\*].shipment\_info.phone\_number                | string  | Yes      | Phone number                                   |
| waypoint\[\*].shipment\_info.address                      | string  | Yes      | Full address                                   |
| waypoint\[\*].remark                                      | string  | Optional | Any additional notes or instructions           |



## 🧾 Ondemand Submit Order Response Parameters

### Sample Response

```json
{
    "status_code": 200,
    "message": "Success",
    "data": {
        "booking_id": "EOD-350",
        "ondemand_service_id": "EP-CS09",
        "order_number": "3231209862956724576",
        "tracking_url": "https://share.sandbox.lalamove.com?MY100250516151601363420020075208941&lang=en_MY&sign=b09efebbf9f9d1e287dc61a8bb22fdc4&source=api_wrapper",
        "courier": {
            "service_id": 5,
            "courier_name": "Lalamove",
            "img_courier": "https://s3-ap-southeast-1.amazonaws.com/easyparcel/Public/source/general/img/couriers/lalamove.svg"
        },
        "pricing_breakdown": {
            "currency_code": "MYR",
            "total_order_amount": "9.61",
            "total_paid_amount": "6.79",
            "shipment_amount": "9.41",
            "tax_amount": "0.20",
            "coupon_redeemed": "2.82"
        },
        "shipment": {
            "coupon_codes": [
                "a186f575-8481-4cf0-80e6-909871eb7e97"
            ],
            "origin_country": "MY",
            "ondemand_service_id": "EP-CS09",
            "schedule_pickup_date": "2024-12-10",
            "schedule_pickup_time": "17:35:15",
            "time_zone": "Asia/Kuala_Lumpur",
            "metadata": {
                "quotationId": "3114850556997669249"
            },
            "waypoint": [
                {
                    "point": 0,
                    "type": "pickup",
                    "remark": "1",
                    "coordinates": {
                        "latitude": 5.342720241204454,
                        "longitude": 100.28204988381822
                    },
                    "item": [
                        {
                            "quantity": "1",
                            "description": "1",
                            "dimensions": {
                                "height": "1",
                                "width": "1",
                                "length": "1",
                                "weight": "1"
                            }
                        }
                    ],
                    "shipment_info": {
                        "phone_number_country_code": "MY",
                        "phone_number": "1278491622",
                        "address": "L1 Lobby, Suntec City Tower 1 & 2, 7 Temasek Boulevard, Singapore, 038987",
                        "name": "111",
                        "email": "as@as.as"
                    }
                },
                {
                    "point": 1,
                    "type": "dropoff",
                    "remark": "222",
                    "coordinates": {
                        "latitude": 5.325513957,
                        "longitude": 100.2862732
                    },
                    "item": [
                        {
                            "quantity": "2",
                            "description": "2",
                            "dimensions": {
                                "height": "2",
                                "width": "2",
                                "length": "2",
                                "weight": "2"
                            }
                        }
                    ],
                    "shipment_info": {
                        "name": "222",
                        "email": "as@as.as",
                        "phone_number_country_code": "MY",
                        "phone_number": "127491622",
                        "address": "Terminal 1 Departure - Changi Airport, 80 Airport Boulevard, Singapore, 819642"
                    }
                }
            ]
        }
    }
}
```

### Main Response

| Parameter    | Type   | Description                                |
| ------------ | ------ | ------------------------------------------ |
| status\_code | int    | HTTP status code (e.g., 200)               |
| message      | string | Success or error message                   |
| data         | object | Contains booking details and shipment info |

### Data Object

| Parameter             | Type   | Description                           |
| --------------------- | ------ | ------------------------------------- |
| booking\_id           | string | Booking ID for the on-demand shipment |
| ondemand\_service\_id | string | ID of the selected on-demand service  |
| order\_number         | string | Unique order number                   |
| tracking\_url         | string | URL to track the delivery             |
| courier               | object | Courier service information           |
| pricing\_breakdown    | object | Price breakdown of the order          |
| shipment              | object | Submitted shipment details            |

### Courier Object

| Parameter     | Type   | Description             |
| ------------- | ------ | ----------------------- |
| service\_id   | int    | Courier's service ID    |
| courier\_name | string | Name of the courier     |
| img\_courier  | string | Logo URL of the courier |

### Pricing Breakdown

| Parameter            | Type   | Description                        |
| -------------------- | ------ | ---------------------------------- |
| currency\_code       | string | Currency used (e.g., MYR)          |
| total\_order\_amount | string | Final amount before any coupon     |
| total\_paid\_amount  | string | Amount paid after coupon applied   |
| shipment\_amount     | string | Delivery cost without tax          |
| tax\_amount          | string | Tax applied to the shipment        |
| coupon\_redeemed     | string | Amount discounted using the coupon |

### Shipment Object

| Parameter              | Type   | Description                             |
| ---------------------- | ------ | --------------------------------------- |
| coupon\_codes          | array  | Applied coupon codes (if any)           |
| origin\_country        | string | Country code of the shipment origin     |
| ondemand\_service\_id  | string | Service ID used                         |
| schedule\_pickup\_date | string | Scheduled pickup date                   |
| schedule\_pickup\_time | string | Scheduled pickup time                   |
| time\_zone             | string | Time zone of the schedule               |
| metadata               | object | Additional metadata (e.g., quotationId) |
| waypoint               | array  | Pickup and dropoff location details     |

### Waypoint Object

| Parameter      | Type   | Description                          |
| -------------- | ------ | ------------------------------------ |
| point          | int    | Sequence point (0=pickup, 1=dropoff) |
| type           | string | Type of point ('pickup'/'dropoff')   |
| remark         | string | Remark or notes for the waypoint     |
| coordinates    | object | Latitude and longitude               |
| item           | array  | Items associated with this stop      |
| shipment\_info | object | Sender or receiver contact details   |



## 📂 Code Implementation Examples

### JavaScript (Fetch API) | PHP (cURL) | Python (Requests)

```javascript
fetch("https://api.easyparcel.com/ondemand/order", {
    method: "POST",
    headers: {
        "Content-Type": "application/json",
        "Authorization": "Bearer YOUR_ACCESS_TOKEN"
    },
    body: JSON.stringify({ ... })
})
.then(res => res.json())
.then(data => console.log(data))
.catch(err => console.error(err));
```


```php
<?php
$ch = curl_init("https://api.easyparcel.com/ondemand/order");
$data = [ ... ];
curl_setopt($ch, CURLOPT_HTTPHEADER, [
    'Content-Type: application/json',
    'Authorization: Bearer YOUR_ACCESS_TOKEN'
]);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
curl_setopt($ch, CURLOPT_POSTFIELDS, json_encode($data));
$response = curl_exec($ch);
curl_close($ch);
echo $response;
?>
```


```python
import requests

url = "https://api.easyparcel.com/ondemand/order"
headers = {
    "Content-Type": "application/json",
    "Authorization": "Bearer YOUR_ACCESS_TOKEN"
}
data = { ... }
response = requests.post(url, json=data, headers=headers)
print(response.json())
```

## 📄 Best Practices for Ondemand Submit Order

* **Validate your data** before sending the request, especially coordinates and item dimensions.
* **Use quotationId** from the Get Quotation API in `metadata` to ensure pricing consistency.
* **Respect rate limits** by not firing too many requests in a short time.
* **Ensure date and time format** follow `YYYY-MM-DD` and `HH:MM:SS` standards.
* **Always include proper contact details** to avoid delivery failure.
* **Secure your access token** and never expose it in public repositories.
* **Use sandbox/test environment** for testing before going live.

---
