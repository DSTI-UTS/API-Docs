# API DOCS UTS

## Endpoint List

### NOTE

Pastikan mengirim headers setiap request:

Headers

```

Accept: application/json
Authorization: Bearer access_token

```

### 1. Autentikasi

-   Token dapat diperoleh dengan mengirimkan request:

Endpoint

```

POST /auth/token

```

Headers

```

Content-Type: application/json

```

Body

```

{
  "email": "johndoe@example.com",
  "password": "password123"
}

```

Response

```

{
  "data" : {
    "access_token": "1000|98rw90er89wncrw9mrwen7yrcwer"
  }
}

```

### 2. profile user

Endpoint

```

POST /auth/user

```

Response

```
{
  "data": {
    "sdm_name": "I MADE WIDIARTA",
    "email": "i.made.widiarta@uts.ac.id",
    "nidn": "0813018701",
    "nip": "0",
    "is_lecturer": true
  }
}

```

### 3. Daftar Mata Kuliah

Endpoint

```
GET /subject
```

Response

```
{
  "data": [
    {
      "id": 1,
      "subject_name": "Dasar pemrograman web",
      "class_name": "SPL-2016-A1",
      "study_program": "Teknik Sipil",
      "semester": "Ganjil 2022/2023",
      "sks": 4,
      "number_of_meetings": 16,
      "sdm_id": 98,
      "sdm_name": "I MADE WIDIARTA",
      "value_sks": "0.50",
      "meetings_completed": 2,
      "meetings_pending": 14
    },
    {
      "id": 2,
      "subject_name": "Matematika diskrit",
      "class_name": "SPL-2016-A1",
      "study_program": "Teknik Sipil",
      "semester": "Ganjil 2022/2023",
      "sks": 4,
      "number_of_meetings": 16,
      "sdm_id": 98,
      "sdm_name": "I MADE WIDIARTA",
      "value_sks": "0.25",
      "meetings_completed": 1,
      "meetings_pending": 15
    }
  ]
}
```

### 4. Mata Kuliah Hari ini

Endpoint

```
GET /subject/today
```

Response

```
{
  "data" : [
    {
      "id": 2,
      "subject_name": "Matematika diskrit",
      "class_name": "SPL-2016-A1",
      "study_program": "Teknik Sipil",
      "semester": "Ganjil 2022/2023",
      "sks": 4,
      "number_of_meetings": 16,
      "sdm_id": 98,
      "sdm_name": "I MADE WIDIARTA",
      "value_sks": "0.25",
      "meetings_completed": 1,
      "meetings_pending": 15
    }
  ]
}
```

### 5. Mata Kuliah By Id

Endpoint

```
GET /subject/{subject_id}
Ex: GET /subject/1
```

Response

```
{
  "data": {
    "id": 1,
    "subject_name": "Dasar pemrograman web",
    "class_name": "SPL-2016-A1",
    "study_program": "Teknik Sipil",
    "semester": "Ganjil 2022/2023",
    "sks": 4,
    "number_of_meetings": 16,
    "sdm_id": 98,
    "sdm_name": "I MADE WIDIARTA",
    "value_sks": "0.50",
    "meetings_completed": 2,
    "meetings_pending": 14
  }
}
```

### 6. Jadwal By Mata Kuliah

Endpoint

```
GET /subject/{subject_id}/meeting
Ex: GET /subject/1/meeting
```

Link dapat dishare ke mahasiswa untuk mahasiswa melakukan absensi

Response

```
{
  "data": [
      {
      "id": 1,
      "meeting_name": "Pertemuan ke 1",
      "date": "2022-12-17T20:23",
      "meeting_start": "2022-12-19 23:21:58",
      "file": "63a08196be9c21671463318download.jfif.jpg",
      "url": {
        "id": 2,
        "meeting_id": 1,
        "link": "/verify?sharer=1?is=63a088969b65b"
      }
    },
    {
      "id": 2, 
      "meeting_name": "Pertemuan ke 2",
      "date": "2022-12-18T13:37",
      "meeting_start": "2022-12-18T13:37",
      "file": "639ea7197d5841671341849download.jfif.jpg",
      "link": null
    },
    ...
     {
      "id": 16,
      "subject_id": 1,
      "meeting_name": "Pertemuan ke 16",
      "date": null,
      "meeting_start": null,
      "file": null,
      "link": null
    }
  ]
}
```

### 7. Absen Mulai Kelas

Endpoint

```
POST /subject/{subject_id}/meeting/{meeting_id}/start
Ex: POST /subject/1/meeting/1/start
```

Body

```
{
    "file": "upload file"
}
```

Response

```
{
  "data": "Meeting dimulai"
} 
```

### 8. List Absensi Kehadiran

Endpoint

```
GET /presence
Ex: GET /presence
```
Response

```
{
  "data": [
    {
      "id": 11,
      "sdm_id": 98,
      "latitude_in": "80",
      "longitude_in": "80",
      "check_in_time": "2022-12-19 12:13:18",
      "check_out_time": "2022-12-19 12:13:36",
      "latitude_out": "80",
      "longitude_out": "80",
  },
  {
      "id": 11,
      "sdm_id": 98,
      "latitude_in": "80",
      "longitude_in": "80",
      "check_in_time": "2022-12-19 12:13:18",
      "check_out_time": "2022-12-19 12:13:36",
      "latitude_out": "80",
      "longitude_out": "80",
    }
  ]
}
```

### 9. Absensi Kehadiran Masuk

Endpoint

```
POST /presence/check-in
Ex: POST /presence/check-in
```
Body

```
{
    "latitude": "80",
    "longitude": "80"
}
```
Response

```
{
  "data": {
    "sdm_id": 98,
    "check_in_time": "2022-12-19 12:13:18",
    "latitude_in": "80",
    "longitude_in": "80",
    "id": 11
  }
}
```

### 10. List Absensi Kehadiran Pulang

Endpoint

```
POST /presence/check-out
Ex: POST /presence/check-out
```
Body

```
{
    "latitude": "80",
    "longitude": "80"
}
```
Response

```
{
  "data": {
    "id": 11,
    "sdm_id": 98,
    "latitude_in": "80",
    "longitude_in": "80",
    "check_in_time": "2022-12-19 12:13:18",
    "check_out_time": "2022-12-19 12:13:36",
    "latitude_out": "80",
    "longitude_out": "80",
  }
}
```

### 10. List Absensi Hari Ini

Endpoint

```
POST /presence/today
Ex: POST /presence/today
```

Response

```
{
  "data": {
    "id": 11,
    "sdm_id": 98,
    "latitude_in": "80",
    "longitude_in": "80",
    "check_in_time": "2022-12-19 12:13:18",
    "check_out_time": "2022-12-19 12:13:36",
    "latitude_out": "80",
    "longitude_out": "80",
  }
}
```
