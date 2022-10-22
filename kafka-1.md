# Kafka 명령어

**토픽 리스트 확인**

```
kafka-topics.sh --list --bootstrap-server localhost:9092
```

**토픽 생성**

```
# test 이름의 토픽, 리플리케이션 1개, 파티션 1개
kafka-topics.sh --create --bootstrap-server localhost:9092 --replication-factor 1 --partitions 1 --topic test
```

**토픽 생성(크기가 큰 데이터를 받기 위한 추가 설정)**

```
kafka-topics.sh --bootstrap-server localhost:9092 --create --topic test --partitions 1 --replication-factor 1 --config max.message.bytes=20971520
```

**토픽 안의 데이터 확인**

```
# test라는 이름의 토픽의 데이터를 첫번째 레코드부터 모두 확인
kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic test --from-beginning
```

**토픽 삭제**

```
kafka-topics.sh --delete --bootstrap-server localhost:9092 --topic test
```

**컨슈머 그룹 리스트 확인**

```
kafka-consumer-groups.sh --list --bootstrap-server localhost:9092
```

**컨슈머 그룹 생성**

```
# test라는 토픽을 구독하는 test_group 이름의 컨슈머 그룹 생성
kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic test --from-beginning --group test_group
```

**컨슈머 그룹 상세보기**

```
# test_group이라는 이름의 컨슈머 그룹 상세보기
kafka-consumer-groups.sh --describe --group test_group --bootstrap-server localhost:9092
```
