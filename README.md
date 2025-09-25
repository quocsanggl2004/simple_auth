Simple Authentication Examples - POSTMAN TEST

Muc dich: Test tat ca truong hop bang Postman

SETUP:
1. Chay server Basic Auth: node basic_auth.js (port 3000)
2. Chay server Cookie Auth: node cookie_auth.js (port 3001)
3. Mo Postman

PHAN 1: BASIC AUTH TEST TREN POSTMAN

Buoc 1: Test public route 1
Method: GET
URL: http://localhost:3000/
Authorization: No Auth
Ket qua: Welcome! Visit first public resource.
Status: 200
![alt text](public/img/1.png)

Buoc 2: Test public route 2
Method: GET
URL: http://localhost:3000/public
Authorization: No Auth
Ket qua: Welcome! Visit second public resource.
Status: 200
![alt text](public/img/2.png)

Buoc 3: Test protected route - KHONG CO AUTH
Method: GET
URL: http://localhost:3000/secure
Authorization: No Auth
Ket qua: Authentication required.
Status: 401
![alt text](public/img/3.png)

Buoc 4: Test protected route - SAI USERNAME
Method: GET
URL: http://localhost:3000/secure
Authorization: Basic Auth
Username: wronguser
Password: 12345
Ket qua: Access denied.
Status: 403
![alt text](public/img/4.png)

Buoc 5: Test protected route - SAI PASSWORD
Method: GET
URL: http://localhost:3000/secure
Authorization: Basic Auth
Username: admin
Password: wrongpass
Ket qua: Access denied.
Status: 403
![alt text](public/img/5.png)

Buoc 6: Test protected route - DUNG CREDENTIALS
Method: GET
URL: http://localhost:3000/secure
Authorization: Basic Auth
Username: admin
Password: 12345
Ket qua: You have accessed a protected resource
Status: 200
![alt text](public/img/6.png)

PHAN 2: COOKIE AUTH TEST TREN POSTMAN

Buoc 7: Test login SAI CREDENTIALS
Method: POST
URL: http://localhost:3001/login
Headers: Content-Type: application/json
Body (raw JSON):
{
  "username": "wrong",
  "password": "wrong"
}
Ket qua: Invalid credentials
Status: 401
![alt text](public/img/7.png)

Buoc 8: Test login DUNG CREDENTIALS
Method: POST
URL: http://localhost:3001/login
Headers: Content-Type: application/json
Body (raw JSON):
{
  "username": "admin",
  "password": "12345"
}
Ket qua: Logged in!
Status: 200
CHU Y: Postman tu dong luu cookie
![alt text](public/img/8.png)

Buoc 9: Kiem tra cookie trong Postman
Vao tab Cookies (duoi URL bar)
Xem cookie auth_cookie_token
![alt text](public/img/9.png)

Buoc 10: Test protected route KHONG CO COOKIE
Method: GET
URL: http://localhost:3001/profile
Mo tab o an danh (Incognito) hoac xoa cookie
Ket qua: No cookie found
Status: 401
![alt text](public/img/10.png)

Buoc 11: Test protected route CO COOKIE
Method: GET
URL: http://localhost:3001/profile
CHU Y: Dung cung Postman window da login
Ket qua: Welcome user 1, your cookie is valid.
Status: 200
![alt text](public/img/11.png)

Buoc 12: Test logout
Method: POST
URL: http://localhost:3001/logout
Khong can Body
Ket qua: Logged out.
Status: 200
![alt text](public/img/12.png)


Buoc 13: Test sau logout
Method: GET
URL: http://localhost:3001/profile
Ket qua: Invalid or expired cookie
Status: 401
![alt text](public/img/13.png)

