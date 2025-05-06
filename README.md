# Vector.dev 파이프라인 구성



## 디렉토리 구조

```
base/
├── agent/
│   └── vector.yaml
│   └── logs/
|       ├── test.log
│       └── ...
│
├── aggregator/
│   └── vector.yaml
│
└── test/
    └── vector.yaml

```

## 아키텍처 다이어그램


```
      ┌────────────┐          ┌────────────┐
      │ vector-test│          │vector-agent│
      └─────┬──────┘          └─────┬──────┘
            │                       │
            └──────────┬────────────┘
                       ▼
             ┌───────────────────┐
             │ vector-aggregator │
             └───────────────────┘
```

- **base/agent/logs/**: `vector-agent`가 수집할 샘플 로그 파일들이 위치한 디렉토리입니다.
- **/basetest/vector.yaml**: `demo_log` 소스를 사용해 임의 로그를 생성하여 `vector-aggregator`로 전송하는 설정 파일입니다.
- **/base/agent/vector.yaml**: `logs/*.log` 경로에서 로그 파일을 읽어 `vector-aggregator`로 전송하는 설정 파일입니다.
- **/base/aggregator/vector.yaml**: Vector-aggregator가 수신한 이벤트를 콘솔에 출력하는 설정 파일입니다.
