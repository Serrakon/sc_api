# Customer API Reference Document

## Endpoints

### 1. Get Customer Worksheet by JobNo
Retrieve the details of a worksheet by its JobNo.

**Endpoint:** `GET /api/customer/{id}?secret=1234567890`

#### Parameters
- **id** (int): The JobNo of the worksheet to retrieve.
- **secret** (string): The authorization secret key.

#### Response
- **200 OK**: Returns a `WorksheetApiData` object with the worksheet details.
- **401 Unauthorized**: Returns an error message if the authorization fails.
- **404 Not Found**: Returns an error message if the worksheet is not found.

#### Example Request
```http
GET /api/customer/9999?secret=1234567890
```

#### Example Response
```json
{
    "jobNo": 9999,
    "name": "Customer Name",
    "location": "Location",
    "city": "City",
    "telephone": "123-456-7890",
    "nationality": "Nationality",
    "email": "email@example.com",
    "refferedBy": "Referred By",
    "subscriptionPrice": 99.99,
    "installPrice": 49.99,
    "depositPrice": 20.00,
    "antennaMac": "00:1B:44:11:3A:B7",
    "baseStation": "Base Station",
    "installedBy": "Installer Name",
    "moneyReceivedBy": "Receiver Name",
    "completionDate": "27/06/2024 14:30:00",
    "antennaName": "Antenna",
    "routerName": "Router",
    "tvMac": "00:1B:44:11:3A:B8",
    "routerMac": "00:1B:44:11:3A:B9",
    "radioName": "Radio Model",
    "antennaCustomer": true,
    "paid": true,
    "commisionDue": false,
    "supportNotes": "Support notes here",
    "technicianNotes": "Technician notes here",
    "planId": null,
    "count": null
}
```

### 2. Add New Customer
Add a new customer worksheet to the system.

**Endpoint:** `POST /api/customer?secret=1234567890`

#### Parameters
- **id** (int): An identifier for the new customer.
- **secret** (string): The authorization secret key.
- **order** (WorksheetApiData): The data for the new worksheet.

#### Response
- **200 OK**: Returns a success message if the worksheet is added successfully.
- **401 Unauthorized**: Returns an error message if the authorization fails.
- **409 Conflict**: Returns an error message if a worksheet with the same name already exists.

#### Example Request
```http
POST /api/customer?secret=1234567890
Content-Type: application/json

{
    "jobNo": 99991,
    "name": "Customer Name",
    "location": "Location",
    "city": "City",
    "telephone": "123-456-7890",
    "nationality": "Nationality",
    "email": "email@example.com",
    "refferedBy": "Referred By",
    "subscriptionPrice": 99.99,
    "installPrice": 49.99,
    "depositPrice": 20.00,
    "antennaMac": "00:1B:44:11:3A:B7",
    "baseStation": "Base Station",
    "installedBy": "Installer Name",
    "moneyReceivedBy": "Receiver Name",
    "completionDate": "27/06/2024 14:30:00",
    "antennaName": "Antenna",
    "routerName": "Router",
    "tvMac": "00:1B:44:11:3A:B8",
    "routerMac": "00:1B:44:11:3A:B9",
    "radioName": "Radio Model",
    "antennaCustomer": true,
    "paid": true,
    "commisionDue": false,
    "supportNotes": "Support notes here",
    "technicianNotes": "Technician notes here",
    "planId": 1,
    "count": 2
}
```

#### Example Response
```json
"OK"
```

## C# Data Models

### WorksheetApiData
```csharp
public class WorksheetApiData
{
    public int jobNo;
    public string name;
    public string location;
    public string city;
    public string telephone;
    public string nationality;
    public string email;
    public string refferedBy;

    public double subscriptionPrice;
    public double installPrice;
    public double depositPrice;
    public string antennaMac;
    public string baseStation;
    public string installedBy;
    public string moneyReceivedBy;

    public string completionDate;
    public string antennaName;
    public string routerName;
    public string tvMac;
    public string routerMac;
    public string radioName;
    public bool antennaCustomer;
    public bool paid;
    public bool commisionDue;

    public string supportNotes;
    public string technicianNotes;

    public int? planId;
    public int? count;
}
```

