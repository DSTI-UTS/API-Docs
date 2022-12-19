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
    "id": 98,
    "sdm_id": "5ded2223-3d3d-4cd4-bbab-8e041f1aec6c",
    "sdm_name": "I MADE WIDIARTA",
    "email": "i.made.widiarta@uts.ac.id",
    "email_verified_at": null,
    "nidn": "0813018701",
    "nip": "0",
    "active_status_name": "Aktif",
    "employee_status": "NON PNS",
    "sdm_type": "Dosen",
    "is_sister_exist": 1,
    "structure_id": 2,
    "created_at": "2022-12-10T12:45:41.000000Z",
    "updated_at": "2022-12-10T18:11:35.000000Z"
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
      "subject": "Dasar pemrograman web",
      "class_id": 2,
      "sks": 4,
      "number_of_meetings": 16,
      "sdm_id": 98,
      "value_sks": "0.50",
      "meetings_completed": 2,
      "meetings_pending": 14,
      "human_resource": {
        "id": 98,
        "sdm_name": "I MADE WIDIARTA"
      },
      "class": {
        "id": 2,
        "class": "SPL-2016-A1",
        "structure_id": 21,
        "structure": {
          "id": 21,
          "role": "Teknik Sipil"
        }
      }
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
      "id": 1,
      "subject": "Dasar pemrograman web",
      "class_id": 2,
      "sks": 4,
      "number_of_meetings": 16,
      "sdm_id": 98,
      "value_sks": "0.50",
      "meetings_completed": 2,
      "meetings_pending": 14,
      "human_resource": {
        "id": 98,
        "sdm_name": "I MADE WIDIARTA"
      },
      "class": {
        "id": 2,
        "class": "SPL-2016-A1",
        "structure_id": 21,
        "structure": {
          "id": 21,
          "role": "Teknik Sipil"
        }
      }
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
    "subject": "Dasar pemrograman web",
    "class_id": 2,
    "sks": 4,
    "number_of_meetings": 16,
    "sdm_id": 98,
    "value_sks": "0.50",
    "meetings_completed": 2,
    "meetings_pending": 14,
    "human_resource": {
      "id": 98,
      "sdm_name": "I MADE WIDIARTA"
    },
    "class": {
      "id": 2,
      "class": "SPL-2016-A1",
      "structure_id": 21,
      "structure": {
        "id": 21,
        "role": "Teknik Sipil"
      }
    }
  }
}
```

### 6. Jadwal By Mata Kuliah

Endpoint

```
GET /subject/{subject_id}/meeting
Ex: GET /subject/1/meeting
```

Response

```
{
  "data": [
      {
      "id": 1,
      "subject_id": 1,
      "meeting_name": "Pertemuan ke 1",
      "date": "2022-12-17T20:23",
      "meeting_start": "2022-12-17T20:23",
      "file": null
    },
    {
      "id": 2,
      "subject_id": 1,
      "meeting_name": "Pertemuan ke 2",
      "date": "2022-12-18T13:37",
      "meeting_start": "2022-12-18T13:37",
      "file": "639ea7197d5841671341849download.jfif.jpg"
    },
    ...
     {
      "id": 16,
      "subject_id": 1,
      "meeting_name": "Pertemuan ke 16",
      "date": null,
      "meeting_start": null,
      "file": null
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
  "data":  {
      "id": 1,
      "subject_id": 1,
      "meeting_name": "Pertemuan ke 1",
      "date": "2022-12-10T20:50",
      "meeting_start": "2022-12-11 06:46:09",
      "meeting_end": null,
      "file_start": "63957cb1577431670741169-156.png",
      "file_end": null
  }
}
```

### 8. List Absensi Kehadiran

Endpoint

```
POST /presence
Ex: POST /presence
```
Response

```
{
  "data": {
      "id": 1,
      "subject_id": 1,
      "meeting_name": "Pertemuan ke 1",
      "date": "2022-12-10T20:50",
      "meeting_start": "2022-12-11 06:46:09",
      "meeting_end": "2022-12-11 06:47:34",
      "file_start": "63957cb1577431670741169-156.png",
      "file_end": "63957d065151c1670741254-156.png"
  }
}
```
