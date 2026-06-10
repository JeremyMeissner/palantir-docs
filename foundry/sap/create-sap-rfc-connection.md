---
source_url: "https://www.palantir.com/docs/foundry/sap/create-sap-rfc-connection/"
title: "Create an RFC connection"
---
# Create an RFC connection

In this section, an RFC Destination connection is created that will be used to extract data from a remote SAP system. To create an RFC connection, enter the SM59 transaction code. Create a new ABAP connection and select 3 as connection type. In the Technical Settings tab, fill in the Target Host and System Number according to the values for the SAP Source System such as the ECC instance. In the Logon & Security tab, fill in the login credentials and Client number (3-digit number). SAP stores test and production data in the same table and uses a client (MANDT) column to enable different clients (for example, test and production) to retrieve only the relevant client data. For the production environment, enter the Client number for the production client. Save the connection configuration. Authorize the test from the application toolbar and test the connection.
