# <span style="color: black;"> Sandbox Account </span>

The EasyParcel **sandbox account** is a test environment designed for developers and integrators to simulate real-world usage of EasyParcel's API features without affecting live production data.


## 🔍 Key Highlights

* **Free to use**: The sandbox environment and test credits are completely free.
* **Safe testing**: You can freely test all API operations (like quotations, order submission, cancellation, etc.) without risk to your live account.
* **Test credits available**: You can simulate order submissions with test credits.
* **Live account unaffected**: No changes or charges are applied to your actual EasyParcel account.


## Use cases
### Ideal For

* Testing API integrations before go-live
* QA and staging environments
* Training or demonstrations

For setup instructions, please refer to the [Setup Sandbox Environment](1.Setup%20Demo%20Account.md) guide.

For top up test credits instructions, please refer to the [Top up Sandbox Credit](2.top%20up%20sandbox%20credit.md) guide.

Sandbox Limitation:
refer here for [Sandbox Limitations](3.sandbox%20limitations.md) 


## Demo Account Setup Guide

### Prerequisites
- Existing EasyParcel developer account
- Completed API application registration
- Client ID credentials


### Step-by-Step Demo Account Setup

#### 1. Access Developer Portal
**URL:** [https://api.easyparcel.com](https://api.easyparcel.com)  
![Developer Portal Login](../8.Picture/%202.Create%20Sandbox/login_page.png "EasyParcel Developer Portal Login Interface")


#### 2. Select Application
**Action:** Choose your registered application from the dashboard  
![Application Selection](../8.Picture/%202.Create%20Sandbox/selectappsettings.png "Application Management Dashboard")


#### 3. Navigate to Connections
**Location:** Settings → Connection Management  
![Connection List Interface](../8.Picture/%202.Create%20Sandbox/selectconnectionlist.png "Connection Configuration Section")


#### 4. Add New Connection
**Required:**  
✅ Sandbox environment selection  
✅ Connection name  
![Add Connection Form](../8.Picture/%202.Create%20Sandbox/addconnection.png "New Connection Configuration Panel")


#### 5. Prompt to login
**Required:**  
Login using developers account credentials
![image](https://github.com/user-attachments/assets/010d073d-f191-4225-813e-05d4f5f5e3e5)


#### 6. Allow access request
**Required:**  
Allow the application request to access account credentials and permisions
![image](https://github.com/user-attachments/assets/c19a522f-ed20-4325-a0e0-d79f88180dac)


#### 8. Verify Successful Setup
**Confirmation:** Look for active status indicator  
![Demo Account Success](../8.Picture/%202.Create%20Sandbox/demo_acc_success.png "Successful Connection Creation Notification")


## Top up demo account

1. In the Application settings, connection list, select **Top Up**  
   <p align="center">
   <img src="../8.Picture/%202.Create%20Sandbox/Topup.png" style="width:80%; border-radius:50%">
   </p>

2. Top up the desired amount  
   <p align="center">
   <img src="../8.Picture/%202.Create%20Sandbox/topup.png" style="width:80%; border-radius:50%">
   </p>

3. Top up successful  
   <p align="center">
   <img src="../8.Picture/%202.Create%20Sandbox/topupsuccess.png" style="width:80%; border-radius:50%">
   </p>


## Sandbox Limitations

While the EasyParcel **sandbox environment** allows full API integration testing, there are several limitations compared to the live environment.


### ⚠️ Key Limitations

* **Shipment status will not update**

   Any shipment created in the sandbox will remain static — it will not progress through actual delivery stages.

* **No tracking notifications**

   Add-on features such as SMS, email, and WhatsApp tracking notifications will not be triggered or sent.



Use the sandbox for development and testing purposes. For real transactions and shipment tracking, switch to the production environment.

## Switching to live
You wish to perform live order [live account](../7.References/9.Switching%20to%20live.md)
