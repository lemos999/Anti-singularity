# Anti-singularity ✅

## 뭐하는 확장이야?

**AI가 "이거 해도 돼?" 물어볼 때, 자동으로 "응 해!" 눌러주는 확장이야.**

Cursor나 Antigravity 같은 AI 코딩 도구 쓰다 보면, AI가 뭔가 할 때마다 "Accept" 버튼 눌러달라고 하잖아?

그거 매번 누르기 귀찮지 않아? 🥱

**Anti-singularity가 대신 눌러줄게!**

---

## 📋 DETAILS (상세 설명)

### ⚠️ 중요! 처음 설치 후 꼭 해야 할 것

**이 확장이 작동하려면 "CDP"라는 걸 켜줘야 해.**

CDP가 뭐냐면, 확장이 브라우저(IDE)랑 대화할 수 있게 해주는 통로야.
이걸 안 켜면 확장이 버튼을 못 눌러!

#### 🪟 Windows 사용자 (PowerShell로 설정)

**1. PowerShell을 "관리자 권한으로" 열어야 해!**

> 1. Windows 키 누르기
> 2. "PowerShell" 입력
> 3. "Windows PowerShell" 우클릭
> 4. **"관리자 권한으로 실행"** 클릭 ⬅️ 이거 중요!

**2. 아래 명령어를 복사해서 붙여넣고 Enter!**

```powershell
# Cursor 사용자용 (Cursor 쓰면 이거!)
$WshShell = New-Object -ComObject WScript.Shell
$searchLocations = @(
    [Environment]::GetFolderPath('Desktop'),
    "$env:USERPROFILE\Desktop",
    "$env:APPDATA\Microsoft\Windows\Start Menu\Programs"
)
$foundShortcuts = @()
foreach ($location in $searchLocations) {
    if (Test-Path $location) {
        $shortcuts = Get-ChildItem -Path $location -Recurse -Filter "*.lnk" -ErrorAction SilentlyContinue | Where-Object { $_.Name -like "*Cursor*" }
        $foundShortcuts += $shortcuts
    }
}
foreach ($shortcutFile in $foundShortcuts) {
    $shortcut = $WshShell.CreateShortcut($shortcutFile.FullName)
    $shortcut.Arguments = "--remote-debugging-port=9000 " + $shortcut.Arguments
    $shortcut.Save()
    Write-Host "Updated: $($shortcutFile.Name)" -ForegroundColor Green
}
Write-Host "Done! Now restart Cursor completely." -ForegroundColor Cyan
```

```powershell
# Antigravity 사용자용 (Antigravity 쓰면 이거!)
$WshShell = New-Object -ComObject WScript.Shell
$searchLocations = @(
    [Environment]::GetFolderPath('Desktop'),
    "$env:USERPROFILE\Desktop",
    "$env:APPDATA\Microsoft\Windows\Start Menu\Programs"
)
$foundShortcuts = @()
foreach ($location in $searchLocations) {
    if (Test-Path $location) {
        $shortcuts = Get-ChildItem -Path $location -Recurse -Filter "*.lnk" -ErrorAction SilentlyContinue | Where-Object { $_.Name -like "*Antigravity*" }
        $foundShortcuts += $shortcuts
    }
}
foreach ($shortcutFile in $foundShortcuts) {
    $shortcut = $WshShell.CreateShortcut($shortcutFile.FullName)
    $shortcut.Arguments = "--remote-debugging-port=9000 " + $shortcut.Arguments
    $shortcut.Save()
    Write-Host "Updated: $($shortcutFile.Name)" -ForegroundColor Green
}
Write-Host "Done! Now restart Antigravity completely." -ForegroundColor Cyan
```

**3. IDE 완전히 껐다가 다시 켜기**

> ❌ 그냥 탭 닫기 = 안 됨  
> ✅ 프로그램 완전히 종료 후 다시 시작 = 됨

---

#### 🍎 Mac 사용자

터미널에서 이렇게 실행:

```bash
open -n -a "Cursor" --args --remote-debugging-port=9000
```

또는 Antigravity면:

```bash
open -n -a "Antigravity" --args --remote-debugging-port=9000
```

---

### 이게 왜 필요해?

AI 에이전트가 코드 작성할 때 이런 일들이 생겨:

1. 파일 수정할 때 → "이 파일 수정해도 돼?" → **Accept 클릭 필요**
2. 터미널 명령어 실행할 때 → "이 명령어 실행해도 돼?" → **Accept 클릭 필요**
3. 뭔가 막혔을 때 → "다시 시도할까?" → **Retry 클릭 필요**

**한 시간에 수십 번** 이런 일이 생겨.

Anti-singularity가 이걸 **자동으로 처리**해줘서, 너는 다른 일 하고 있어도 돼!

### 얼마나 안전해?

- 위험한 명령어는 **절대 자동 실행 안 함** (예: `rm -rf /` 같은 거)
- 어떤 명령어를 막을지 **직접 설정** 가능
- 언제든 **끌 수 있음**

---

## ⭐ FEATURES (기능)

### 1. 자동 승인 ✅
AI가 물어보면 자동으로 "OK" 눌러줘.
- 파일 수정 → 자동 승인
- 터미널 명령어 → 자동 승인
- 재시도 버튼 → 자동 클릭

---

### 2. 백그라운드 모드 🌍 (핵심 기능!)

#### 백그라운드 모드가 뭐야?

**안 보고 있는 탭에서도 자동 승인이 되는 기능이야!**

#### 없으면 어떻게 돼?

백그라운드 모드 **끄면**:
- 지금 보고 있는 탭에서만 자동 승인이 돼
- 다른 탭으로 가면 그 탭은 승인 안 됨
- 탭마다 일일이 확인해야 함 😓

#### 켜면 어떻게 돼?

백그라운드 모드 **켜면**:
- **모든 탭**에서 자동 승인이 돼!
- 네가 뭘 보고 있든 상관없어
- AI 3개가 동시에 일해도 다 처리됨! 🚀

#### 예시로 설명할게

**상황**: AI 에이전트 탭 3개 열어놓음

| | 백그라운드 OFF | 백그라운드 ON |
|---|---|---|
| 탭 1 (보고 있음) | ✅ 자동 승인 | ✅ 자동 승인 |
| 탭 2 (안 보고 있음) | ❌ 멈춤 | ✅ 자동 승인 |
| 탭 3 (안 보고 있음) | ❌ 멈춤 | ✅ 자동 승인 |

**백그라운드 모드 = 3개 다 동시에 돌아감!**

#### 어떻게 작동해?

1. 확장이 모든 열린 탭을 감시해
2. 어떤 탭에서든 "Accept" 버튼이 나타나면
3. 그 탭으로 잠깐 갔다가 버튼 누르고 돌아옴
4. 이걸 아주 빠르게 반복함 (0.5~1초마다)

**너는 유튜브 보고 있어도 되고, 밥 먹으러 가도 돼.**
**돌아오면 AI가 다 해놨어!** 🎉

#### 어떻게 켜?

1. 상태바에서 `Anti-singularity: ON` 확인
2. 옆에 `Background: OFF` 클릭
3. `Background: ON`으로 바뀌면 성공!

---

### 3. 위험 명령어 차단 🛡️

```
rm -rf /     ← 컴퓨터 다 날림 → 자동 차단!
format c:    ← 하드 포맷 → 자동 차단!
del /f /s /q ← 전체 삭제 → 자동 차단!
```

컴퓨터 날려먹는 명령어는 **자동으로 막아줘.**

설정에서 어떤 명령어를 막을지 직접 추가할 수도 있어.

---

### 4. 실시간 상태 표시 📊

화면 아래 상태바에서 확인 가능:

| 표시 | 의미 |
|---|---|
| `Anti-singularity: ON` | 작동 중 |
| `Anti-singularity: OFF` | 꺼져 있음 |
| `Background: ON` | 백그라운드 모드 켜짐 |
| `Background: OFF` | 백그라운드 모드 꺼짐 |

---

## 🚀 빠른 시작 요약

1. ✅ 확장 설치 (이미 함)
2. ⚙️ PowerShell 관리자 권한으로 열기
3. 📋 위의 스크립트 복사해서 붙여넣기
4. 🔄 IDE 완전히 재시작
5. 🎉 끝! 상태바에서 ON 확인

---

## ❓ 자주 묻는 질문

**Q: 안전해?**
A: 응! 위험한 명령어는 자동으로 막아. 그리고 언제든 끌 수 있어.

**Q: 무료야?**
A: **완전 무료!** 모든 기능 다 쓸 수 있어.

**Q: 어떤 IDE에서 돼?**
A: Cursor, Antigravity, VS Code 다 돼.

**Q: 백그라운드 모드 안 되는데?**
A: CDP 설정 했어? 위에 PowerShell 명령어 실행하고 IDE 재시작해봐.

**Q: PowerShell 스크립트가 안 돼요**
A: "관리자 권한으로 실행" 했어? 일반 모드면 권한 없어서 안 될 수 있어.

---

## 💡 팁

- 상태바 클릭하면 켜고 끌 수 있어
- 설정(⚙️) 누르면 차단할 명령어 추가할 수 있어
- 처음엔 지켜보다가, 믿음이 생기면 백그라운드 모드 켜!
- 여러 AI 돌릴 거면 **반드시 백그라운드 모드 켜!**

---

**만든 이유:** AI 에이전트가 일하는 동안 Accept 버튼 누르느라 시간 낭비하지 마! 🎮
