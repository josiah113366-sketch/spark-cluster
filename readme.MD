# 프로젝트 구성
```
spark-cluster/
├── docker-compose.yml
├── conf/
│   └── spark-defaults.conf
├── jobs/
│   └── etl_job.py          ← 실행할 PySpark 코드
└── data/
    └── hospital_raw.csv    ← 입력 데이터
```