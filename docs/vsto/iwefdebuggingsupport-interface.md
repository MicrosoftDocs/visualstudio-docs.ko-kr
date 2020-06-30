---
title: IWefDebuggingSupport 인터페이스
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0a4883d36c1833c66a2539380184521b070f5c2a
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544731"
---
# <a name="iwefdebuggingsupport-interface"></a>IWefDebuggingSupport 인터페이스
  Office 용 응용 프로그램의 디버깅을 용이 하 게 하기 위해 Visual Studio와 같은 디버깅 환경에 의해 구현 됩니다. Word 또는 Excel과 같은 Office 응용 프로그램은 Visual Studio에서이 인터페이스를 가져온 다음 디버깅 세션 중 특정 지점에서 인터페이스의 메서드를 호출 합니다.

## <a name="syntax"></a>구문

```csharp
[
    uuid(ccaf1a90-ce1c-4199-9cd6-b40c5c57a671),
    oleautomation
]
interface IWefDebuggingSupport : IUnknown
{
    HRESULT SetWefProcessId(
        [in] DWORD dwProcessId);
    HRESULT GetAutoInsertExtensions(
        [out, retval] SAFEARRAY(BSTR)* psaExtensionNames);
}
```

## <a name="methods"></a>메서드
 다음 표에서는 IWefDebuggingSupport 인터페이스가 정의 하는 메서드를 보여 줍니다.

|Name|설명|
|----------|-----------------|
|[GetAutoInsertExtensions 메서드](../vsto/getautoinsertextensions-method.md)|디버깅 하는 동안 자동으로 삽입 되는 Office 용 앱에 대 한 정보를 가져옵니다.|
|[SetWefProcessId 메서드](../vsto/setwefprocessid-method.md)|WEF (웹 확장 프레임 워크) 콘텐츠를 실행 하는 프로세스 식별자를 제공 합니다.|
