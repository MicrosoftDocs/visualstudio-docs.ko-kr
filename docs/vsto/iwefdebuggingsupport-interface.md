---
title: IWefDebuggingSupport 인터페이스
description: Visual Studio와 같은 디버깅 환경을 사용 하 여 Microsoft Office 응용 프로그램의 디버깅을 용이 하 게 하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 6a818973bdc2f62194d6ed0026c0798806fe5f2a
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525319"
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

|이름|Description|
|----------|-----------------|
|[GetAutoInsertExtensions 메서드](../vsto/getautoinsertextensions-method.md)|디버깅 하는 동안 자동으로 삽입 되는 Office 용 앱에 대 한 정보를 가져옵니다.|
|[SetWefProcessId 메서드](../vsto/setwefprocessid-method.md)|WEF (웹 확장 프레임 워크) 콘텐츠를 실행 하는 프로세스 식별자를 제공 합니다.|
