# Customer API Reference Document

## Overview

This document provides an overview of the endpoints available in the `CustomerController` for managing worksheet data related to customer installations and other related operations. The API is secured and requires authorization through a secret key.

## Endpoints

### 1. Authorize User
This is a helper function that validates the secret key provided in the request.

**Method:** `private User Authorize(string secret)`

### 2. Get Worksheet by ID
Retrieve the details of a worksheet by its JobNo.

**Endpoint:** `GET /api/customer/{id}`

#### Parameters
- **id** (int): The JobNo of the worksheet to retrieve.
- **secret** (string): The authorization secret key.

#### Response
- **200 OK**: Returns a `WorksheetApiData` object with the worksheet details.
- **401 Unauthorized**: Returns an error message if the authorization fails.
- **404 Not Found**: Returns an error message if the worksheet is not found.

#### Example Request
```http
GET /api/customer/5?secret=api_DE07633C-2EA4-4D89-9DC5-D627EF2D516A
```

#### Example Response
```json
{
    "jobNo": 5,
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
    "antennaName": "Antenna Model",
    "routerName": "Router Model",
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

### 3. Add New Customer
Add a new customer worksheet to the system.

**Endpoint:** `POST /api/customer`

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
POST /api/customer?id=5&secret=api_DE07633C-2EA4-4D89-9DC5-D627EF2D516A
Content-Type: application/json

{
    "jobNo": 5,
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
    "antennaName": "Antenna Model",
    "routerName": "Router Model",
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
{
    "message": "OK"
}
```

### 4. Add Installation
Add an installation to a worksheet.

**Endpoint:** `POST /api/customer/addInstallation`

#### Parameters
- **worksheetId** (int): The ID of the worksheet.
- **mac** (string): The MAC address for the installation.
- **userId** (int): The ID of the user performing the installation.

#### Response
- **200 OK**: Returns a success message if the installation is added successfully.
- **404 Not Found**: Returns an error message if no tickets for the plan are left.

#### Example Request
```http
POST /api/customer/addInstallation
Content-Type: application/json

{
    "worksheetId": 5,
    "mac": "00:1B:44:11:3A:B7",
    "userId": 2
}
```

#### Example Response
```json
{
    "message": "OK"
}
```

## Data Models

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

### User
This class is not fully detailed in the provided code, but it represents the user data model used for authorization.

### Worksheet
This class represents the worksheet data model used to store worksheet details in the database.

### Ticket
This class represents the ticket data model used for managing ticket information related to worksheets.

## Conclusion

This document provides a comprehensive overview of the Customer API, including endpoints, request/response formats, and data models. For further details and updates, please refer to the actual code implementation and comments within the code.
