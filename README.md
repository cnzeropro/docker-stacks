# docker-stacks

本机开发用的 Docker Compose 服务栈集合：**17 个**常用中间件 / 应用的现成 compose 配置（共 27 个 `docker-compose*.yml`），克隆后按需起服务。

## 服务栈一览

| 栈 | 目录 | 变体与配置 |
| --- | --- | --- |
| Apollo | `compose/apollo/apollo-quick-start/` | 快速启动，含 MySQL 初始化 SQL（apolloconfigdb / apolloportaldb） |
| Blog | `compose/blog/` | 博客应用（`.env` + compose） |
| ClickHouse | `compose/clickhouse/` | 单节点，含 `config.xml` / `users.xml` 自定义 |
| Elasticsearch | `compose/elasticsearch/` | 单节点 + 多节点两套；单节点含 `conf/`（`elasticsearch.yml`、`jvm.options`、`certs/`） |
| Grafana | `compose/grafana/` | 含 `grafana.ini` / `ldap.toml` |
| Kibana | `compose/kibana/` | 含 `kibana.yml` |
| Logstash | `compose/logstash/` | 含 `pipelines.yml` / `logstash.yml` / `jvm.options` |
| Loki | `compose/loki/` | 含 `local-config.yaml` |
| MySQL | `compose/mysql/mysql-single/` | 单节点，含 `my.cnf` |
| Nacos | `compose/nacos-cluster/` | 集群，提供 hostname / ip / 嵌入式 / MySQL 多种 env 与 `cluster-hostname.yaml` |
| Oracle | `compose/oracle/` | `tnsnames.ora` |
| Prometheus | `compose/prometheus/` | 含 `prometheus.yml` |
| Promtail | `compose/promtail/` | 含 `config.yml` |
| RabbitMQ | `compose/rabbitmq/rabbitmq-classic-cluster/` | 3 节点经典集群 |
| Redis | `compose/redis/` | 集群两套：原生 6 节点、Bitnami |
| RocketMQ | `compose/rocketmq/` | nameserver / broker / proxy / dashboard，含单机、多主、多主多从（本地与集群）多种拓扑 |
| ZooKeeper | `compose/zookeeper/` | 单节点 + 3 节点集群 |

## 用法

```bash
cd compose/<栈>/<变体>
docker compose up -d
```

- 端口、账号密码集中在各栈的 `.env` / `*.env` 与 `docker-compose*.yml` 中
- 各栈的 `conf/` 均为可挂载的真实配置，按需改完重启容器即可
- 集群类栈（ES / Redis / RocketMQ / RabbitMQ / ZooKeeper / Nacos）的节点配置为本地示例，端口与卷路径请按本机情况调整

## 说明

- 仓库只跟踪 `compose/` 下的配置，`.idea/` 由 `.gitignore` 忽略
- 全部栈面向**本机开发调试**，未做生产加固（无资源限制、无高可用保障）
