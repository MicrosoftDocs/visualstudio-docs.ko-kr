---
title: 사용자 지정 디버그 엔진 등록 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a664385594f139e2c3c5a18a0d8a59e23c13df0a
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90011842"
---
# <a name="register-a-custom-debug-engine"></a>사용자 지정 디버그 엔진 등록
디버그 엔진은 visual Studio 레지스트리 하위 키를 통해 Visual Studio에 등록 하는 것은 물론 COM 규칙에 따라 자신을 클래스 팩터리로 등록 해야 합니다.

> [!NOTE]
> 디버깅 엔진을 등록 하는 방법에 대 한 예제는 [자습서: ATL COM을 사용 하 여 디버그 엔진 빌드](/previous-versions/bb147024(v=vs.90))의 일부로 빌드된 textinterpreter 샘플에서 찾을 수 있습니다.

## <a name="dll-server-process"></a>DLL 서버 프로세스
 디버그 엔진은 일반적으로 자체 DLL에 COM 서버로 설정 됩니다. 따라서 디버그 엔진은 Visual Studio에서이 클래스에 액세스할 수 있으려면 해당 클래스 팩터리의 CLSID를 COM에 등록 해야 합니다. 그런 다음 디버그 엔진은 디버그 엔진이 지 원하는 속성 (즉, 메트릭이 라고도 함)을 설정 하기 위해 Visual Studio에 자신을 등록 해야 합니다. Visual Studio 레지스트리 하위 키에 작성 된 메트릭의 선택은 디버그 엔진이 지 원하는 기능에 따라 달라 집니다.

 [디버깅을 위한 SDK 도우미](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) 는 디버그 엔진을 등록 하는 데 필요한 레지스트리 위치에 대해서만 설명 합니다. 또한 보다 쉽게 레지스트리를 조작 하는 c + + 개발자를 위한 여러 가지 유용한 함수 및 선언이 포함 된 *dbgmetric* 라이브러리에 대해 설명 합니다.

### <a name="example"></a>예
 다음 예제 (TextInterpreter 샘플에서)는 `SetMetric` 함수 ( *dbgmetric*)를 사용 하 여 디버그 엔진을 Visual Studio에 등록 하는 방법을 보여 줍니다. 전달 되는 메트릭은 *dbgmetric*에도 정의 되어 있습니다.

> [!NOTE]
> TextInterpreter 기본 디버그 엔진입니다. 설정 되지 않으므로 다른 기능이 등록 되지 않습니다. 보다 완전 한 디버그 엔진에는 `SetMetric` 디버그 엔진이 지 원하는 각 기능에 대해 하나씩 전체 호출 목록 또는 해당 항목이 있습니다.

```
// Define base registry subkey to Visual Studio.
static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0";

HRESULT CTextInterpreterModule::RegisterServer(BOOL bRegTypeLib, const CLSID * pCLSID)
{
    SetMetric(metrictypeEngine, __uuidof(Engine), metricName, L"Text File", false, strRegistrationRoot);
    SetMetric(metrictypeEngine, __uuidof(Engine), metricCLSID, CLSID_Engine, false, strRegistrationRoot);
    SetMetric(metrictypeEngine, __uuidof(Engine), metricProgramProvider, CLSID_MsProgramProvider, false, strRegistrationRoot);

    return base::RegisterServer(bRegTypeLib, pCLSID);
}
```

## <a name="see-also"></a>참고 항목
- [사용자 지정 디버그 엔진 만들기](../../extensibility/debugger/creating-a-custom-debug-engine.md)
- [디버깅을 위한 SDK 도우미](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [자습서: ATL COM을 사용 하 여 디버그 엔진 빌드](/previous-versions/bb147024(v=vs.90))