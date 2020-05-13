---
title: 아이디버그프로퍼티2::겟확장정보 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetExtendedInfo
helpviewer_keywords:
- IDebugProperty2::GetExtendedInfo
ms.assetid: 0c9c0b2b-7540-4424-adb5-fce7aa37a026
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 34d6cd880ccae520bf000ad01b52223857f4f10f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721493"
---
# <a name="idebugproperty2getextendedinfo"></a>IDebugProperty2::GetExtendedInfo
속성에 대한 확장 정보를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetExtendedInfo ( 
   REFGUID* guidExtendedInfo,
   VARIANT* pExtendedInfo
);
```

```csharp
int GetExtendedInfo ( 
   ref Guid guidExtendedInfo,
   out object pExtendedInfo
);
```

## <a name="parameters"></a>매개 변수
`guidExtendedInfo`\
【인】 검색할 확장 정보의 유형을 결정하는 GUID입니다. 자세한 내용은 비고를 참조하십시오.

`pExtendedInfo`\
【아웃】 확장 `VARIANT` 속성 정보를 검색하는 데 사용할 수 있는 (C++) 또는 개체(C#)를 반환합니다. 예를 들어 이 매개 `IUnknown` 변수는 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) 인터페이스에 대해 쿼리할 수 있는 인터페이스를 반환할 수 있습니다. 자세한 내용은 비고를 참조하십시오.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다. 검색할 확장 정보가 없는 경우 반환합니다. `S_GETEXTENDEDINFO_NO_EXTENDEDINFO`

## <a name="remarks"></a>설명
 이 메서드는 [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 메서드를 호출 하 여 검색 되 고 자신을 빌려 하지 않는 정보를 검색 하기 위한 목적으로 존재 합니다.

 다음 GUID는 일반적으로 이 메서드에서 인식됩니다(GUID 값은 C#에 대해 지정되므로 어셈블리에서 이름을 사용할 수 없습니다). 내부 사용을 위해 추가 GUID를 만들 수 있습니다.

|이름|GUID|설명|
|----------|----------|-----------------|
|guidDocument|{3f98de84-fee9-11d0-b47f-00a0244a1dd2}|문서에 `IUnknown` 인터페이스를 반환합니다. 일반적으로 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) 인터페이스는 이 `IUnknown` 인터페이스에서 가져올 수 있습니다.|
|guidCode컨텍스트|{e2fc65e-56ce-11d1-b528-00ax004a8797}|문서 `IUnknown` 컨텍스트에 인터페이스를 반환합니다. 일반적으로 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) 인터페이스는 이 `IUnknown` 인터페이스에서 가져올 수 있습니다.|
|guid사용자 정의 뷰어 지원|{d9c9da31-ffbe-4eeb-9186-23121e3c08c}|일반적으로 식 계산기에서 구현되는 사용자 지정 뷰어의 CLSID를 포함하는 문자열을 반환합니다.|
|guidExtendedInfo슬롯|{6df235ad-82c6-4292-9c97-7389770bc42f}|이 속성이 관리 코드 로컬 주소를 나타내는 경우 원하는 슬롯 번호를 나타내는 32비트 번호를 반환합니다.|
|guidExtendedInfo서명|{b5fb6d46-f805-417f-96a3-8ba737073ffd}|속성 개체와 연결된 변수의 서명을 포함하는 문자열을 반환합니다.|

## <a name="see-also"></a>참조
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
