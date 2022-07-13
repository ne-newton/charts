```mermaid
  flowchart TD
    subgraph GitHub
      subgraph Book Repo 1
        A1[Content Version 1]
        A2[Content Version ..n]
      end
      subgraph Book Repo ..n
        A3[Content Version 1]
        A4[Content Version ..n]
      end
      A5[Approved Books List]
    end
    subgraph Concourse
      subgraph Pipeline 1
        B1[Feeder] -->|Informs of ABL change| B2[Bakery]
      end
      subgraph Pipeline ..n
        B3[Feeder] -->|Informs of ABL change| B4[Bakery]
      end
    end
    subgraph AWS
      C1[Old S3 Bucket]
      C2[S3 Bucket 1]
      C3[S3 Bucket ..n]
    end
    A2 --> A5
    A4 --> A5
    A2 --> B2
    A2 --> B4
    A4 --> B2
    A4 --> B4
    B2 --> C2
    B4 --> C3
    B1 -.-> A5
    B3 -.-> A5
    C3 --> D1[REX]
    D1 -.-> A5
```