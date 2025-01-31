# SpringBoot Kafka Practice

## 🚀 Kafka CLI 테스트

### 1. Kafka 토픽 생성
**Kafka에서 test-topic이라는 토픽을 생성한다.**

> docker exec -it kafka-1 kafka-topics --create \
--topic test-topic \
--bootstrap-server kafka-1:9092 \
--partitions 3 \
--replication-factor 2

- `--topic test-topic`: 생성할 토픽 이름
- `--partitions 3`: 3개의 파티션으로 구성
- `--replication-factor 2`: 2개의 복제본 유지

**토픽이 정상적으로 생성되었는지 확인한다.**
> docker exec -it kafka-1 kafka-topics --list --bootstrap-server kafka-1:9092


### 2. 메시지 전송 (Producer)
**생성한 test-topic에 메시지를 전송한다.**

> docker exec -it kafka-1 kafka-console-producer --topic test-topic --bootstrap-server kafka-1:9092

**실행 후 메시지를 입력하면 Kafka 토픽에 전송된다.**

> Hello Kafka!
> Welcome to Kafka Testing!

### 3. 메시지 소비 (Consumer)

**Producer에서 보낸 메시지를 Consumer로 확인한다.**

> docker exec -it kafka-2 kafka-console-consumer --topic test-topic --bootstrap-server kafka-2:9093 --from-beginning

실행 결과 예시:

Hello Kafka!
Welcome to Kafka Testing!
