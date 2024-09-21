# File with heading

Project pembelajaran dan sekalian untuk django template auth + restful CRUD

Cara menjalankan project ini:

A. Requirement

- pastikan sudah menginstall python3-pip dan python3-venv
- buat venv dengan nama env

```
python3 -m venv env
```

- aktivasi venv tersebut

```
source env/bin/activate (untuk keluar deactivate)
```

- install library yang diperlukan 

```
pip install -r requirements.txt
```

B. Start Project

- jalankan project

```
python3 manage.py runserver
```

- cek pada localhost

```
http://127.0.0.1:8000/api/v1/movies/
```

- anda akan mendapatkan error, karena belum login

C. Auth

- Buat User 

```
http POST http://127.0.0.1:8000/api/v1/auth/register/ email="helmi@gmail.com" username="HELMI" password="123helmi123" password2="123helmi123"
```

- Login dengan akun yang diubah

```
http http://127.0.0.1:8000/api/v1/auth/token/ username="HELMI" password="123helmi123"
```

- Mendapatkan accessToken dan RefreshToken
- Token akan expired setelah beberapa waktu, untuk mendapatkan token baru, gunakan

```
http http://127.0.0.1:8000/api/v1/auth/token/refresh/ refresh="Ganti-dengan-refresh-token"
```

- Sertakan Setiap permintaan dengan accesToken -> "Authorization: Bearer {ACCESS_TOKEN}"

D. Daftar Endpoint

1. CRUD

- Get all movies

```
http http://127.0.0.1:8000/api/v1/movies/ "Authorization: Bearer {YOUR_TOKEN}" 
```

- Get a single movie

```
http GET http://127.0.0.1:8000/api/v1/movies/{movie_id}/ "Authorization: Bearer {YOUR_TOKEN}" 
```

- Create a new movie

```
http POST http://127.0.0.1:8000/api/v1/movies/ "Authorization: Bearer {YOUR_TOKEN}" title="Ant Man and The Wasp" genre="Action" year=2018 
```

- Full update a movie

```
http PUT http://127.0.0.1:8000/api/v1/movies/{movie_id}/ "Authorization: Bearer {YOUR_TOKEN}" title="AntMan and The Wasp" genre="Action" year=2018
```

- Partial update a movie

```
http PATCH http://127.0.0.1:8000/api/v1/movies/{movie_id}/ "Authorization: Bearer {YOUR_TOKEN}" title="AntMan and The Wasp" 
```

- Delete a movie

```
http DELETE http://127.0.0.1:8000/api/v1/movies/{movie_id}/ "Authorization: Bearer {YOUR_TOKEN}"
```

2. Pagination

```
http http://127.0.0.1:8000/api/v1/movies/?page=1 "Authorization: Bearer {YOUR_TOKEN}"
http http://127.0.0.1:8000/api/v1/movies/?page=3 "Authorization: Bearer {YOUR_TOKEN}"
http http://127.0.0.1:8000/api/v1/movies/?page=3&page_size=15 "Authorization: Bearer {YOUR_TOKEN}"
```

3. Filter

```
http http://127.0.0.1:8000/api/v1/movies/?title="AntMan" "Authorization: Bearer {YOUR_TOKEN}"
http http://127.0.0.1:8000/api/v1/movies/?year=2020 "Authorization: Bearer {YOUR_TOKEN}"
http http://127.0.0.1:8000/api/v1/movies/?year__gt=2019&year__lt=2022 "Authorization: Bearer {YOUR_TOKEN}"
http http://127.0.0.1:8000/api/v1/movies/?genre="Action" "Authorization: Bearer {YOUR_TOKEN}"
http http://127.0.0.1:8000/api/v1/movies/?creator__username="myUsername" "Authorization: Bearer {YOUR_TOKEN}"
```