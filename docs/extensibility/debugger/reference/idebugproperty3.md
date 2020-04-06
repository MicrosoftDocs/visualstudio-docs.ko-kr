---
title: 아이디버그프로퍼티3 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3
helpviewer_keywords:
- IDebugProperty3 interface
ms.assetid: 8f9be68d-4490-4eca-8f6b-8a10ed77e226
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d2819724c204631112fd1a3e827126c4bc176972
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721047"
---
# <a name="idebugproperty3"></a>IDebugProperty3
이 인터페이스는 다음을 지원합니다.

- 속성과 연결된 임의로 긴 문자열을 검색합니다.

- 속성과 고유 ID를 연결합니다.

- 속성에 대한 사용자 지정 뷰어 목록을 검색합니다.

- 결과 오류를 보고할 수 있는 기능을 사용하여 속성 값 설정

## <a name="syntax"></a>구문

```
IDebugProperty3 : IDebugProperty2
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 디버그 엔진(DE)은 긴 문자열, 속성 아이디 및 사용자 지정 뷰어에 대한 지원을 제공하기 위해 [IDebugProperty2를](../../../extensibility/debugger/reference/idebugproperty2.md) 구현하는 동일한 개체에 이 인터페이스를 구현합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 이 인터페이스를 `IDebugProperty2` 얻으려면 인터페이스에서 [QueryInterface를](/cpp/atl/queryinterface) 호출합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 `IDebugProperty3` 인터페이스에서 상속된 `IDebugProperty2`메서드 외에도 다음 메서드를 노출합니다.

|방법|설명|
|------------|-----------------|
|[GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)|속성과 연결된 문자열의 길이를 반환합니다.|
|[GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md)|사용자가 제공한 버퍼에서 문자열을 반환합니다.|
|[CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)|이 속성에 대 한 고유 ID를 만듭니다.|
|[DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)|이 속성의 고유 ID를 삭제합니다.|
|[GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)|이 속성을 볼 수 있는 사용자 지정 뷰어 수를 반환합니다.|
|[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)|이 속성을 볼 수 있는 사용자 지정 뷰어 목록을 반환합니다.|
|[SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)|문제가 발생하면 오류 메시지를 반환하여 이 속성의 값을 설정합니다.|

## <a name="remarks"></a>설명
- [SetValueAsStringWithError는](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) SDM(세션 디버그 관리자)이 속성값을 설정하는 데 선호되는 방법입니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
