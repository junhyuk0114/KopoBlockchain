# KopoBlockchain
Python Blockchain Implementation for educational purposes (Dept. of Smart Finance of Korea Polytechnics)

### YOU MUST RUN BLOCKCHAIN SERVER BEFORE FOLLOWING THESE INSTRUCTIONS BELOW !!!

---

## 🛠️ 1. 환경 구축 및 의존성 설치

프로젝트 실행에 필요한 파이썬 패키지를 설치합니다.
```bash
pip install -r requirements.txt
```

## 🚀 2. 서버 실행 방법 (Port 및 Peer 설정)

 `--port`와 `--peers` 인자를 사용하여 노드 서버를 실행할 수 있습니다.
```bash
python myBlockChain.py --port 8666 --peers 127.0.0.1:8668
```

---

## 📖 3. Contents

- [getBlockData](#-getBlockData)
- [generateBlock](#-generateBlock)
- [newBlock](#-newBlock)
- [newTx](#-newTx-post)
- [validateBlock](#-validateBlock)
- [Diagrams](#-Diagrams)

---

## 🧱 getBlockData

You can get Block data by link down below. (GET Method)
You MUST run myBlockChain.py before clicking this link.

http://localhost:8666/block/getBlockData

### 🔍 범위 지정 블록 조회 (`from`, `end`) 추가 기능
전체 블록 중 원하는 구간의 블록만 골라서 조회할 수 있습니다. (예: 1번부터 3번 블록 조회)
```
http://localhost:8666/block/getBlockData?from=1&end=3
```

#### * This is Example Request for getBlockData (curl)
전체 조회:
```bash
curl --location --request GET 'http://localhost:8666/block/getBlockData'
```
범위 지정 조회:
```bash
curl --location --request GET 'http://localhost:8666/block/getBlockData?from=1&end=3'
```

---

## 💡 generateBlock
You should write tx before generate a new block. if you don't write new tx, mining will be aborted.

You can write new tx here -> [newTx](#-newTx-post)

You can generate a new block by link down below.
It uses GET method to run this function.

http://localhost:8666/block/generateBlock

#### * This is Example Request for generateBlock (curl)
```bash
curl --location --request GET 'http://localhost:8666/block/generateBlock'
```

---

## ⛏ newBlock

You can mine a new block by link down below.
It also uses GET method to run this function.

http://localhost:8666/block/mineNewBlock

#### * This is Example Request for newBlock (curl)
```bash
curl --location --request GET 'http://localhost:8666/block/mineNewBlock'
```

---

## 💵 newtx (POST)
Please use Post Method for this Example request.

You have to fill out Headers and Body before when you send requests.
(Content-Type(KEY) : application/json(VALUE), Body = raw, json)

#### * This is Example Request for newTx (curl, POST Method)
```bash
curl --location --request POST 'http://localhost:8666/block/newtx' \
--header 'Content-Type: application/json' \
--data-raw '[{
    "sender" : "sender_name",
    "amount" : "number_of_amounts",
    "receiver" : "receiver_name"
}]'
```

---

## 🔎 validateBlock
You can check that new block is valid or not.

You have to figure out "currentHash", "data", "index", "previousHash", "proof", "timestamp" before validate new block.
Use POST Method same as newTx before.

#### * This is Example Request for validateBlock (curl, POST Method)

```bash
curl --location --request POST 'http://localhost:8666/block/validateBlock' \
--data-raw '[
    {
        "currentHash": "aad22d5f3bb41eaacda9883106e8770cf9818a710cba5309e11bfd4721dfee6f",
        "data": "Genesis Block",
        "index": "0",
        "previousHash": "0",
        "proof": "0",
        "timestamp": "1654828634.695756"
    }
]'
```
# 💎 Diagrams
## 🌊 Flow chart Image for generateBlock
![initial](https://github.com/SunghwanNam/KopoBlockchain/blob/283eac7a1299875d4ff556ae97afd2aae0e8186b/generateBlock.png)

## 🌊 Flow chart Image for getBlockData
![initial](https://github.com/SunghwanNam/KopoBlockchain/blob/283eac7a1299875d4ff556ae97afd2aae0e8186b/getBlockData.png)

## 🌊 Flow chart Image for addNodeData
![Untitled Diagram-Page-8 drawio](https://user-images.githubusercontent.com/103026653/174598167-26169227-3869-4c40-9fb2-385ac397b23a.png)
