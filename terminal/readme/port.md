# zshrc 셋팅

좋은 자동화 아이디어입니다 👍\
`~/.zshrc`에 **함수(function)** 또는 **alias**를 등록하면,\
아래처럼 **포트 번호만 넣어서 바로 종료**할 수 있습니다.

***

### ✅ 추천 방식 (함수) — 가장 깔끔하고 확장성 좋음

#### 1️⃣ `~/.zshrc` 열기

```bash
vi ~/.zshrc
```

***

#### 2️⃣ 아래 함수 추가

```bash
killport() {
  if [ -z "$1" ]; then
    echo "❌ Usage: killport <port>"
    return 1
  fi

  echo "🔍 Killing process on port $1..."
  sudo kill -9 $(sudo lsof -t -i:$1) 2>/dev/null \
    && echo "✅ Port $1 killed" \
    || echo "⚠️ No process found on port $1"
}
```

***

#### 3️⃣ 설정 적용

```bash
source ~/.zshrc
```

***

#### 4️⃣ 사용 방법 🎯

```bash
killport 8000
killport 5500
```

***

### ✅ alias 방식 (짧지만 유연성 ↓)

> **한 개 포트만 고정**하고 싶을 때만 추천

```bash
alias kill8000='sudo kill -9 $(sudo lsof -t -i:8000)'
alias kill5500='sudo kill -9 $(sudo lsof -t -i:5500)'
```

```bash
kill8000
kill5500
```

👉 여러 포트 쓰는 개발 환경에서는 **함수 방식이 훨씬 좋음**

***

### 🔥 보너스: 여러 포트 한 번에 죽이기

```bash
killports() {
  for port in "$@"; do
    echo "🔍 Killing port $port..."
    sudo kill -9 $(sudo lsof -t -i:$port) 2>/dev/null
  done
}
```

```bash
killports 3000 8000 5500
```

***

### ⚠️ 주의사항

* `kill -9`는 **강제 종료(SIGKILL)** → 정상 종료 로직 없음
* 가능하면 개발 중에는 `-15`(SIGTERM) → 필요 시 `-9`

```bash
sudo kill -15 $(sudo lsof -t -i:8000)
```

***

### 💡 추천 최종 형태

> 실무에서 가장 많이 쓰는 형태

```bash
killport 8000
```

원하시면

* `netstat` 버전
* `brew services stop` 연계
* Docker 컨테이너 포트 자동 종료\
  도 같이 정리해 드릴게요 👌



