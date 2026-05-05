**Automating Entra ID User Inventory with Microsoft Graph PowerShell**

**Screenshot 1 — Connecting to Microsoft Graph**

Note: Tenant ID has been redacted for security purposes.

Using Connect-MgGraph -Scopes "User.Read.All" to authenticate to the Entra ID tenant. The -Scopes parameter requests only the permissions needed for this task — User.Read.All is the appropriate scope for a read-only audit, following the principle of least privilege. Using User.ReadWrite.All in this context would be over-permissioned since no write operations are performed.



<img width="2884" height="1822" alt="1" src="https://github.com/user-attachments/assets/68ee65cb-17e6-4a6f-9c86-57d196a5ba38" />



<img width="2880" height="1658" alt="2" src="https://github.com/user-attachments/assets/e01417b8-60b2-457f-9b03-ff86c5065963" />



<img width="2880" height="1656" alt="3" src="https://github.com/user-attachments/assets/8c55728c-5894-42d1-918a-4e71ea9265d6" />




<img width="2882" height="1654" alt="4" src="https://github.com/user-attachments/assets/a5854a85-a2b9-4339-b288-34942e9cdc41" />
