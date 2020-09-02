---
title: 사용자 지정 디버그 엔진 등록 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9cf06e881034b980b8e40e095779007b3c7fa6f6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703597"
---
# <a name="registering-a-custom-debug-engine"></a>사용자 지정 디버그 엔진 등록
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

디버그 엔진은 COM 규칙에 따라 클래스 팩터리로 등록 하 고 Visual Studio 레지스트리 하위 키를 통해 Visual Studio에 등록 해야 합니다.  
  
> [!NOTE]
> 디버그 엔진을 등록 하는 방법에 대 한 예제는 [자습서: ATL COM을 사용 하 여 디버그 엔진 빌드](https://msdn.microsoft.com/9097b71e-1fe7-48f7-bc00-009e25940c24)의 일부로 빌드된 textinterpreter 샘플에서 찾을 수 있습니다.  
  
## <a name="dll-server-process"></a>DLL 서버 프로세스  
 일반적으로 디버그 엔진은 자체 DLL에서 COM 서버로 구현 됩니다. 즉, 디버그 엔진은 Visual Studio에 액세스 하기 전에 COM을 사용 하 여 클래스 팩터리의 CLSID를 등록 해야 합니다. 그러면 디버그 엔진이 지 원하는 속성 (메트릭이 라고도 함)을 설정 하기 위해 디버그 엔진이 직접 Visual Studio 자체에 등록 해야 합니다. 디버그 엔진의 Visual Studio 레지스트리 하위 키에 기록 되는 메트릭은 디버그 엔진이 지 원하는 기능에 따라 달라 집니다.  
  
 [디버깅을 위한 SDK 도우미](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) 는 디버그 엔진을 등록 하는 데 필요한 레지스트리 위치에 대해서만 설명 합니다. 또한 보다 쉽게 레지스트리를 조작 하는 c + + 개발자를 위한 여러 가지 유용한 함수 및 선언이 포함 된 dbgmetric 라이브러리에 대해 설명 합니다.  
  
### <a name="example"></a>예  
 다음은 `SetMetric` 함수 (dbgmetric에서)를 사용 하 여 Visual Studio에 디버그 엔진을 등록 하는 방법을 보여 주는 일반적인 예제입니다 (TextInterpreter 샘플). 전달 되는 메트릭은 dbgmetric에도 정의 되어 있습니다.  
  
> [!NOTE]
> TextInterpreter 기본 디버그 엔진입니다. 구현 하지 않으므로 다른 모든 기능을 등록 하지 않습니다. 보다 완전 한 디버그 엔진에는 `SetMetric` 디버그 엔진이 지 원하는 각 기능에 대해 하나씩 전체 호출 목록 또는 해당 항목이 있습니다.  
  
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
  
## <a name="see-also"></a>관련 항목  
 [사용자 지정 디버그 엔진 만들기](../../extensibility/debugger/creating-a-custom-debug-engine.md)   
 [디버깅을 위한 SDK 도우미](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [자습서: ATL COM을 사용 하 여 디버그 엔진 빌드](https://msdn.microsoft.com/9097b71e-1fe7-48f7-bc00-009e25940c24)
