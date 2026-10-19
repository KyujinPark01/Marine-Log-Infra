# Marine-Log-Infra

Marine-Log 실행/배포 설정 레포


- Backend: [Marine-Log-backend](https://github.com/KyujinPark01/Marine-Log-backend) → `marinelog-backend`
- Frontend: [Marine-Log-frontend](https://github.com/KyujinPark01/Marine-Log-frontend) → `marinelog-frontend`

## 구성

| 서비스 | 이미지 | 포트 |
| --- | --- | --- |
| frontend | marinelog-frontend (nginx) | 5173 → 80 |
| backend | marinelog-backend (Spring Boot) | 8080 |
| db | postgis/postgis:16-3.4 | - |
| redis | redis:7-alpine | - |


```bash
# backend
cd Marine-Log-backend
docker build -t marinelog-backend .

# frontend
cd Marine-Log-frontend
docker build -t marinelog-frontend --build-arg VITE_API_BASE_URL=http://localhost:8080 .
```

```bash
cp .env.example .env
docker compose up -d
docker compose logs -f backend
```

- Front: http://localhost:5173
- Swagger: http://localhost:8080/swagger-ui/index.html


