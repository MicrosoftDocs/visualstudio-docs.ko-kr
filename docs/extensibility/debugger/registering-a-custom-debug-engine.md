---
title: 사용자 지정 디버그 엔진 등록 | 마이크로 소프트 문서
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
ms.openlocfilehash: fe6fb916810bc8a7e960a4723a6a7c7a6f0c1410
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713218"
---
# <a name="register-a-custom-debug-engine"></a>사용자 지정 디버그 엔진 등록
디버그 엔진은 COM 규칙에 따라 클래스 팩터리로 등록하고 Visual Studio 레지스트리 하위 키를 통해 Visual Studio에 등록해야 합니다.

> [!NOTE]
> [자습서: ATL COM을 사용하여 디버그 엔진 빌드의](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)일부로 빌드된 TextInterpreter 샘플에서 디버그 엔진을 등록하는 방법의 예를 찾을 수 있습니다.

## <a name="dll-server-process"></a>DLL 서버 프로세스
 디버그 엔진은 일반적으로 자체 DLL에서 COM 서버로 설정됩니다. 따라서 디버그 엔진은 Visual Studio에서 액세스하려면 먼저 동급 팩터리의 CLSID를 COM에 등록해야 합니다. 그런 다음 디버그 엔진이 Visual Studio에 등록하여 디버그 엔진이 지원하는 모든 속성(메트릭이라고도 함)을 설정해야 합니다. Visual Studio 레지스트리 하위 키에 기록된 메트릭의 선택은 디버그 엔진이 지원하는 기능에 따라 다릅니다.

 [디버깅을 위한 SDK 도우미는](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) 디버그 엔진을 등록하는 데 필요한 레지스트리 위치뿐만 아니라 설명합니다. 또한 레지스트리를 보다 쉽게 조작할 수 있도록 하는 C++ 개발자를 위한 유용한 함수와 선언이 포함된 *dbgmetric.lib* 라이브러리에 대해서도 설명합니다.

### <a name="example"></a>예제
 다음 예제(TextInterpreter 샘플)에서는 `SetMetric` *함수(dbgmetric.lib)를*사용하여 디버그 엔진을 Visual Studio에 등록하는 방법을 보여 주습니다. 전달되는 메트릭은 *dbgmetric.lib에도*정의됩니다.

> [!NOTE]
> TextInterpreter는 기본 디버그 엔진입니다. 설정되지 않으므로 다른 기능을 등록하지 않습니다. 보다 완전한 디버그 엔진에는 디버그 `SetMetric` 엔진이 지원하는 각 기능에 대해 전체 호출 또는 그에 상응하는 호출 목록이 하나씩 있습니다.

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

## <a name="see-also"></a>참조
- [사용자 지정 디버그 엔진 만들기](../../extensibility/debugger/creating-a-custom-debug-engine.md)
- [디버깅을 위한 SDK 도우미](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [자습서: ATL COM을 사용하여 디버그 엔진 구축](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)
