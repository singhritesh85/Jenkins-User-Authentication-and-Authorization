# Jenkins-User-Authentication-and-Authorization

For Jenkins User Authentication I am explaining
1. LDAP
2. Jenkins own user database

For Authorization I am explaining 
1. Matrix based security
2. Project-based Matrix authorization strategy

### Authentication
1. LDAP

I am using open LDAP and created three users dexter who has administrative privileges and user1 and user2 who are normal users whose access I will restrict.

![image](https://github.com/user-attachments/assets/cfda0bc5-87c8-49bf-bfa9-6f3a9525abcd)

I logged-in with user dexter who has administrative privilege
![image](https://github.com/user-attachments/assets/1f1d80ba-f768-4aca-8e72-7caaf70b3f16)

Go to **Manage Jenkins** > **Security** as shown in the screenshot attached below.

![image](https://github.com/user-attachments/assets/f8c5c7d1-c99a-4d52-9a30-abac8d68b72b)
![image](https://github.com/user-attachments/assets/f79e2f13-23cc-4f17-a0cb-7372314e829c)
![image](https://github.com/user-attachments/assets/24a3500e-1331-41bb-875c-d46538f26963)

First of all I am using **Matrix based security** as shown in the screenshot attached below.

For Authenticated users I had provided overall Read permission and for user1 I had provided only Read permission at Job level. For user2 I had provided Read and Build permission as Job level as shown in the screenshot attached below.
![image](https://github.com/user-attachments/assets/d4e10973-1944-490e-b1cd-eedb56864282)

When login with user1 can only read the job but can not build the job as the user don't have build access, shown in the screenshot attached below.

![image](https://github.com/user-attachments/assets/241b9697-c20d-45ef-82b9-91d1ec4838d2)
![image](https://github.com/user-attachments/assets/eb9fe1f2-1417-42e0-bb65-40b35e839f73)

When login with user2 can read and build the job as shown in the screenshot attached below.
![image](https://github.com/user-attachments/assets/4c5729b7-452a-4181-b46a-3b719b118147)
![image](https://github.com/user-attachments/assets/dade448a-0b9f-47eb-b4a2-80049e19d286)
![image](https://github.com/user-attachments/assets/e25660ee-f3d3-4c71-acd0-c01f2c43e500)

Now I am using **Project-based Matrix authorization strategy** and provided overall Read and Build access to the user2 as shown in the screenshot attached below.

![image](https://github.com/user-attachments/assets/32490025-1090-4fab-bd56-78d3080fda36)

Go to **Manage Jenkins** > **Security** as shown in the screenshot attached below.
![image](https://github.com/user-attachments/assets/4d078713-38b3-4395-9f2a-da1939217e4b)

In Jenkins Job test-2 I did not enable project based security while in Jenkins Job test-1 I enabled project based security with the condition of **Inherit permissions from parent ACL** as shown in the screenshot attached below. In test-1 Jenkins Job user1 has Job based Read access as shown in the screenshot attached below.

![image](https://github.com/user-attachments/assets/0209f806-da96-47e7-8ed2-f75a99769db3)
![image](https://github.com/user-attachments/assets/b2fdec5c-967e-4691-ac9d-63eafb379175)

I can conclude that the user1 can only read test-1 jenkins job and can not read jenkins job test-2 as shown in the screenshot attached below.

![image](https://github.com/user-attachments/assets/b9ec95c3-5330-40f8-aed7-7db83edd559e)
![image](https://github.com/user-attachments/assets/bf9baf8f-1049-47c4-b49c-471f325e0105)

However user2 can Read and Build both the jenkins job test-1 and test-2 as shown in the screenshot attached below.

![image](https://github.com/user-attachments/assets/61e0d417-5e1c-45e6-b4ab-613d570db8eb)
![image](https://github.com/user-attachments/assets/6ba6512d-63af-4ba3-9797-a479e3a9f478)
![image](https://github.com/user-attachments/assets/3431610f-c056-4d2e-b27c-ce78f716365d)
