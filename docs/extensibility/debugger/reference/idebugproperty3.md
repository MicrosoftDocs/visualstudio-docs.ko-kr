---
title: IDebugProperty3 | Microsoft Docs
description: 이 인터페이스는 속성과 연결 된 임의의 긴 문자열을 검색 하 고, 고유 ID를 속성과 연결 하 고, 속성에 대 한 사용자 지정 뷰어 목록을 검색 하 고, 결과 오류를 보고할 수 있는 기능으로 속성 값을 설정 하는 기능을 제공 합니다.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3
helpviewer_keywords:
- IDebugProperty3 interface
ms.assetid: 8f9be68d-4490-4eca-8f6b-8a10ed77e226
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 65da477c47e88699cc479f632843f839b3d02f9d
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102469777"
---
# <a name="idebugproperty3"></a>IDebugProperty3
이 인터페이스는 다음에 대 한 지원을 제공 합니다.

- 속성과 연결 된 임의의 긴 문자열을 검색 합니다.

- 고유 ID를 속성과 연결 합니다.

- 속성에 대 한 사용자 지정 뷰어 목록을 검색 합니다.

- 결과 오류를 보고할 수 있는 기능을 사용 하 여 속성 값 설정

## <a name="syntax"></a>구문

```
IDebugProperty3 : IDebugProperty2
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 DE (디버그 엔진)는 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 을 구현 하는 동일한 개체에서이 인터페이스를 구현 하 여 긴 문자열, 속성 id 및 사용자 지정 뷰어를 지원 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 인터페이스에서 [QueryInterface](/cpp/atl/queryinterface) `IDebugProperty2` 를 호출 하 여이 인터페이스를 가져옵니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 에서 상속 된 메서드 외에도 `IDebugProperty2` 인터페이스는 `IDebugProperty3` 다음 메서드를 노출 합니다.

|방법|Description|
|------------|-----------------|
|[GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)|속성과 연결 된 문자열의 길이를 반환 합니다.|
|[GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md)|사용자가 제공한 버퍼의 문자열을 반환 합니다.|
|[CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)|이 속성에 대 한 고유 ID를 만듭니다.|
|[DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)|이 속성의 고유 ID를 소멸 시킵니다.|
|[GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)|이 속성을 볼 수 있는 사용자 지정 뷰어 수를 반환 합니다.|
|[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)|이 속성을 볼 수 있는 사용자 지정 뷰어 목록을 반환 합니다.|
|[SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)|오류가 발생 한 경우 오류 메시지를 반환 하 여이 속성의 값을 설정 합니다.|

## <a name="remarks"></a>설명
- [Setvalueasstringwitherror](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) 는 SDM (세션 디버그 관리자)이 속성의 값을 설정 하는 데 선호 되는 방법입니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고 항목
- [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
