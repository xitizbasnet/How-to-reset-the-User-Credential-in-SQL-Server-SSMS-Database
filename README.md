# How to reset the User Credential in SQL Server(SSMS) Database

This document provides a step-by-step guide for **managing access and resetting credentials** for the `Testhealth` SQL user hosted on the SQL Server instance at:

* **SQL Server IP:** `10.160.100.34`

The guide covers:

* Secure Remote Desktop access
* SQL Server Management Studio (SSMS) navigation
* Assigning database-level permissions
* Resetting SQL login credentials
* Accessing the On-Premises Data Gateway

> ⚠️ **Audience:** IT Administrators / Database Administrators
> 🔐 **Access Level Required:** Windows & SQL administrative privileges

---

## 🖥️ Remote Desktop Access

Follow the steps below to access the SQL Server host machine.

### Steps

1. Press **`Win + R`**
2. Type the following command:

   ```bash
   mstsc /admin
   ```
3. Enter the server credentials:

| Field        | Value           |
| ------------ | --------------- |
| **Username** | `admin`         |
| **Password** | `********`      |

> ✅ You are now logged into the SQL Server host (`10.160.100.34`)

---

## 🗄️ Accessing SQL Server Management Studio (SSMS)

### Steps

1. Open the **Windows Search Bar**
2. Search for **SQL Server Management Studio**
3. Launch the application

### Connection Details

Fill in the connection dialog as follows:

| Setting            | Value                     |
| ------------------ | ------------------------- |
| **Server Type**    | Database Engine           |
| **Server Name**    | `SQLSERVER2\MSSQLSERVER2` |
| **Authentication** | Windows Authentication    |

4. Click **Connect**

> 🟢 Successful connection opens the SSMS Object Explorer dashboard

---

## 🧭 Navigating to the testhealth Database

Once connected to SSMS:

1. Expand **Databases**
2. Locate and expand **`testhealth`**
3. Navigate to:

   ```
   testhealth
   └── Security
       └── Users
   ```
4. Locate the database user:

   ```
   testhealth
   ```

> 📌 This is the database-level user associated with the SQL login

---

## 🔐 Assigning Read-Only Access

To grant **read-only access** to the `testhealth` user:

### Steps

1. Right-click on **testhealth**
2. Select **Properties**
3. Open the **Membership** tab
4. Enable the following role:

   * ✅ `db_datareader`
5. Click **OK** to save changes

> 🧾 This ensures the user can **read data only** without modification privileges

---

## 🔑 Resetting testhealth User Credentials

To reset the SQL login password:

### Steps

1. In SSMS, navigate to:

   ```
   Security
   └── Logins
       └── testhealth
   ```
2. Double-click **testhealth**
3. In the login properties window:

   * Enter **New Password**
   * Confirm **New Password**
4. Click **OK**

> ⚠️ Ensure the updated credentials are securely stored and shared only with authorized users

---

## 🔄 Accessing the On-Premises Data Gateway

The On-Premises Data Gateway is hosted on a separate server:

* **Gateway Server IP:** `10.160.100.36`

### Steps

1. Log in to the gateway server
2. Open **On-Premises Data Gateway**
3. Sign in using authorized credentials
4. Confirm successful connection

> 🔗 This gateway enables secure data connectivity for reporting and client integrations

---

## ✅ Conclusion

This guide provides a standardized and secure approach to:

* Managing SQL Server user permissions
* Resetting database credentials
* Ensuring controlled read-only access
* Maintaining connectivity via the On-Premises Data Gateway

By following these procedures, administrators can ensure:

* 🔐 **Data security**
* 📊 **Operational continuity**
* 🛠️ **Audit-ready documentation**

---
