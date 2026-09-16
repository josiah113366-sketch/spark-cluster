# 목적 
- 클러스터 환경에서 마스터의 지시에 의해 노드(워커)들에서 `병렬로 etl 작업 처리`

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

# 컴포즈 구성
```
docker-compose up -d

docker-compose down
```

# job 제출 -> 작업 시작 
- 차후 airflow에서는 s3에 업로드된 etl_job.py 파일의 경로를 세팅하면 됨 
```
docker exec spark-master /opt/spark/bin/spark-submit --master spark://spark-master:7077 --executor-memory 512m --executor-cores 1 /opt/jobs/etl_job.py
```