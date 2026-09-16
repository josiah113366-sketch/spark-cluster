# 목적 
- 클러스터 환경에서 마스터의 지시에 의해 노드(워커)들에서 `병렬로 etl 작업 처리`

# 프로젝트 구성
```
spark-cluster/
├── docker-compose.yml
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

# 모니터링 및 확인
- 구동 중인 애플리케이션 및 완료 조회 
    - http://127.0.0.1:8080/
- 특정 작업에 대한 조회
    - http://127.0.0.1:8080/app/?appId=app-20260916012237-0000
- 웹 기반 개발 등 관리
    - http://127.0.0.1:8888/lab/workspaces/auto-I?reset
    - 토큰은 직접 로그에서 확인