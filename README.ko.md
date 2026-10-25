# 식탁보 Windows Sandbox 스킬

[English](README.md)

2026년 10월 25일 기준으로 이 패키지는 [식탁보 커밋 f91a83d](https://github.com/yourtablecloth/TableCloth/tree/f91a83daac158130afdd24b261ad35de3d5f42cf)의 Windows Sandbox 지침을 그대로 제공합니다. 식탁보의 호스트 연결 기능이 전달한 로컬 실행 결과를 설명합니다.

설치, 호스트 연결, 자격 증명, 지원 작업과 라이선스 순서로 살펴보겠습니다. 지침을 설치해도 Windows Sandbox 기능이나 Codex의 셸 접근을 활성화하지 않습니다.

## 저장소 루트의 스킬 설치

카탈로그에 등록한 뒤 식탁보의 스킬 마켓플레이스에서 설치하거나 설치된 스킬 화면에서 이 폴더를 가져올 수 있습니다. [SKILL.md](SKILL.md)를 저장소 루트에 두므로 카탈로그는 고정 커밋과 `Source.Path="."`를 사용합니다. 폴더와 스킬 이름은 `tablecloth-windows-sandbox`를 사용합니다.

## 식탁보 호스트가 전달하는 실행 결과

[Sandbox 호스트 연결 기능](https://github.com/yourtablecloth/TableCloth/blob/f91a83daac158130afdd24b261ad35de3d5f42cf/src/TableCloth.App/ManagedAi/ManagedAiSandboxBridge.cs)을 제공하는 식탁보 빌드와 호환되는 Windows 환경에서 사용합니다. 호스트가 허용 목록의 `wsb.exe` 명령을 실행하고 현재 AI 대화에 `LOCAL_WINDOWS_SANDBOX_REPORT`를 전달합니다. Codex는 명령을 직접 실행하지 않습니다. 보고서가 없으면 로컬 작업의 실행이나 성공을 주장할 수 없습니다.

## 추가 서비스 자격 증명 없는 사용

이 스킬은 추가 API 키, 토큰이나 클라이언트 시크릿을 요구하지 않으며 실행 스크립트나 외부 패키지를 포함하지 않습니다. 식탁보 AI의 기존 계정 연결과 실행 권한은 별도로 적용합니다. [SKILL.md](SKILL.md)를 설치해도 `wsb.exe`를 설치하거나 Windows Sandbox 기능을 활성화하지 않습니다.

## 허용한 작업과 실제 결과로 제한한 설명

호스트는 `list`, 기본 `start`, `stop`, `connect`, `ip`를 지원합니다. 세션이 필요한 작업에는 사용자가 지정한 Sandbox GUID나 목록의 유일한 ID를 사용합니다. 세션이 여러 개이면 사용자에게 선택을 요청합니다. `stop`은 Sandbox 상태를 폐기합니다. 기본 `start`는 식탁보 Catalog나 Spork 구성을 적용하지 않은 일반 Sandbox를 만듭니다. 임의 명령 실행, `exec`, `share`, 폴더 접근과 사용자 지정 구성은 [지원 범위](SKILL.md)에 포함하지 않습니다.

## 원본 저작권과 라이선스 보존

[원본 저작권 및 라이선스 안내](https://github.com/yourtablecloth/TableCloth/blob/f91a83daac158130afdd24b261ad35de3d5f42cf/README.md#법적-고지)는 저작권자 남정현과 다음 문구를 명시합니다.

> Copyright 2021-2026 rkttu.com. All rights reserved.

여기까지 정리하면 이 패키지는 원본 지침과 [AGPL-3.0 전문](LICENSE-AGPL), [상용 라이선스 문의 안내](LICENSE-COMMERCIAL)를 원문 그대로 보존합니다. 상용 문의 안내는 Jung Hyun, Nam을 연락 대상으로 명시하며 이번 분리는 새 라이선스를 부여하지 않습니다.

Windows Sandbox 기능과 호스트의 실제 실행 결과가 사용할 수 있는 작업 범위를 결정합니다. 지침만 설치한 환경에서는 로컬 실행 상태를 확인할 수 없습니다.
