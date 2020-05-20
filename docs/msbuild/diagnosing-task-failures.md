---
title: 작업 실패 진단 | Microsoft Docs
ms.date: 09/25/2019
ms.topic: troubleshooting
f1_keywords:
- MSBuild.ToolTask.ToolCommandFailed
dev_langs:
- VB
- CSharp
- C++
- jsharp
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 89dcb8bddf2c92406ad5eff952d1f4050d7f9262
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593280"
---
# <a name="diagnosing-task-failures"></a>작업 실패 진단

작업에서 특정 오류를 기록하지 않은 경우 <xref:Microsoft.Build.Utilities.ToolTask> 파생 클래스가 0이 아닌 종료 코드를 반환하는 도구 프로세스를 실행할 때 `MSB6006`이 내보내집니다.

## <a name="identifying-the-failing-task"></a>실패한 작업 확인

작업 오류가 발생하면 첫 번째 단계는 실패한 작업을 식별하는 것입니다.

오류 텍스트는 도구 이름(작업의 <xref:Microsoft.Build.Utilities.ToolTask.ToolName> 구현에서 제공하는 식별 이름 또는 실행 파일의 이름)과 숫자 종료 코드를 지정합니다. 예:

```text
error MSB6006: "custom tool" exited with code 1.
```

도구 이름은 `custom tool`이고 종료 코드는 `1`입니다.

### <a name="command-line-builds"></a>명령줄 빌드

빌드가 요약(기본값)을 포함하도록 구성된 경우 요약은 다음과 같이 표시됩니다.

```text
Build FAILED.

"S:\MSB6006_demo\MSB6006_demo.csproj" (default target) (1) ->
(InvokeToolTask target) ->
  S:\MSB6006_demo\MSB6006_demo.csproj(19,5): error MSB6006: "custom tool" exited with code 1.
```

이 결과는 프로젝트 `S:\MSB6006_demo\MSB6006_demo.csproj`에서 `InvokeToolTask`라는 대상의 파일 `S:\MSB6006_demo\MSB6006_demo.csproj`의 19번 줄에 정의된 작업에서 오류가 발생했음을 나타냅니다.

### <a name="in-visual-studio"></a>Visual Studio에서

`Project`, `File` 및 `Line` 열의 Visual Studio 오류 목록에서 동일한 정보를 사용할 수 있습니다.

## <a name="finding-more-failure-information"></a>추가 실패 정보 찾기

이 오류는 작업이 특정 오류를 기록하지 않은 경우에 내보내집니다. 오류를 기록하는 데 실패하는 것은 작업이 호출하는 도구에서 내보낸 오류 형식을 해석하도록 구성되어 있지 않기 때문입니다.

정상적으로 작동하는 도구는 일반적으로 일부 문맥 또는 오류 정보를 표준 출력 또는 오류 스트림으로 내보내고 작업이 기본적으로 이 정보를 캡처하고 기록합니다. 추가 정보에 대해 오류가 발생하기 전에 로그 항목을 확인합니다. 이 정보를 유지하려면 더 높은 로그 수준으로 빌드를 다시 실행해야 할 수 있습니다.

## <a name="next-steps"></a>다음 단계

로그에서 식별된 추가 컨텍스트나 오류는 문제의 근본 원인을 나타냅니다.

그렇지 않은 경우 실패한 작업에 입력된 속성 및 항목을 검사하여 잠재적인 원인의 범위를 좁혀야 합니다.
