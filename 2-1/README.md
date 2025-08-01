# 🔐 door_hacking.py - Emergency Storage Password Cracker

## 📖 프로젝트 설명

화성 기지의 `emergency_storage_key.zip` 파일이 암호로 잠겨 있습니다.  
비밀번호는 **숫자와 소문자 알파벳으로 구성된 6자리 문자열**입니다.  
이 프로젝트는 **브루트포스(무차별 대입) 알고리즘**을 통해 암호를 해제하고, 성공 시 비밀번호를 `password.txt`에 저장합니다.

---

## 📝 기능 요약
- **`door_hacking.py`**  
  - 단일 프로세스 기반 무차별 대입
  - 진행 상황(시도 횟수, 경과 시간) 출력
  - 성공 시 `password.txt` 파일에 저장

- **`door_hacking_fast.py`** (보너스 과제)
  - **멀티프로세싱**을 활용하여 CPU 병렬 연산 지원
  - 단일 프로세스 대비 최대 **4~8배 성능 향상** (코어 수에 따라 다름)

- **`door_hacking_threaded.py`** (보너스 과제)
  - **멀티스레딩 기반** 병렬 시도
  - `zipfile` 중심의 I/O 작업을 다중 스레드로 병렬 처리
  - **지연 생성(generator)** + **작업 큐(queue)** 구조로 **메모리 최적화**
  - 💡 전체 21억개의 비밀번호를 한 번에 생성하지 않고 순차적으로 처리함

---

## 📂 파일 구성

```
door_hacking/
│
├── README.md                      # 본 문서
├── door_hacking.py                # 기본 브루트포스 코드
├── door_hacking_fast.py           # 멀티프로세싱 최적화 버전
├── door_hacking_threaded.py       # 멀티스레딩 최적화 버전 (+지연 생성 적용)
├── emergency_storage_key.zip      # 암호화된 ZIP 파일
└── password.txt                   # 성공 시 비밀번호 저장 파일
```

---

## ⚙️ 실행 방법

### 1. 기본 실행

```bash
python door_hacking.py
```

### 2. 멀티프로세싱 버전

```bash
python door_hacking_fast.py
```

### 3. 멀티스레딩 버전 (+지연 생성 적용)

```bash
python door_hacking_threaded.py
```

---

## 💡 제약 사항

- python에서 기본 제공되는 명령어 이외의 별도의 라이브러리나 패키지를 사용해서는 안된다.
- 단, zip 파일을 다루는 부분은 외부 라이브러리 사용 가능하다.
- 파일을 다루는 부분은 예외처리가 되어있어야 한다.
- 경고 메시지 없이 모든 코드는 실행 되어야 한다.

---

## 🧠 참고

- 비밀번호는 총 36^6 = 약 21억개 조합이므로, 브루트포스는 시간이 많이 소요될 수 있음.
- 시스템 사양에 따라 멀티스레딩이 빠를 수도, 멀티프로세싱이 유리할 수도 있음.
- 실제 실행 시 thread_count 또는 processes 수는 시스템 코어 수에 맞게 조절 필요.

---

## 출력 결과
- ✅ 비밀번호 해제 성공! → mars06
- 🔢 총 시도 횟수: 726411561
- ⏱️ 총 소요 시간: 52773.37초

---