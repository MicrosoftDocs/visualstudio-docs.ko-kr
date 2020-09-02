---
title: 'IDebugProperty2:: GetExtendedInfo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetExtendedInfo
helpviewer_keywords:
- IDebugProperty2::GetExtendedInfo
ms.assetid: 0c9c0b2b-7540-4424-adb5-fce7aa37a026
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 74810aab2f47a36c716891fd45b7424eb737b142
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164984"
---
# <a name="idebugproperty2getextendedinfo"></a>IDebugProperty2::GetExtendedInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

속성에 대 한 확장 정보를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
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
  
#### <a name="parameters"></a>매개 변수  
 `guidExtendedInfo`  
 진행 검색할 확장 정보의 유형을 결정 하는 GUID입니다. 자세한 내용은 설명 부분을 참조 하십시오.  
  
 `pExtendedInfo`  
 제한이 `VARIANT` 확장 속성 정보를 검색 하는 데 사용할 수 있는 (c + +) 또는 개체 (c #)를 반환 합니다. 예를 들어이 매개 변수는 `IUnknown` [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) 인터페이스에 대해 쿼리할 수 있는 인터페이스를 반환할 수 있습니다. 자세한 내용은 설명 부분을 참조 하십시오.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다. `S_GETEXTENDEDINFO_NO_EXTENDEDINFO`검색할 확장 정보가 없으면를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 이 메서드는 [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 메서드를 호출 하 여 자신을 검색 하지 않는 정보를 검색 하기 위해 존재 합니다.  
  
 다음 Guid는 일반적으로이 메서드에서 인식 됩니다. GUID 값은 모든 어셈블리에서 사용할 수 없기 때문에 c #에 대해 지정 됩니다. 내부 사용을 위해 Guid를 추가로 만들 수 있습니다.  
  
|Name|GUID|설명|  
|----------|----------|-----------------|  
|guidDocument|{3f98de84-fee9-11d0-b47f-00a0244a1dd2}|`IUnknown`문서에 대 한 인터페이스를 반환 합니다. 일반적으로이 인터페이스에서 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) 인터페이스를 가져올 수 있습니다 `IUnknown` .|  
|guidCodeContext|{e2fc65e-56ce-11d1-b528-00aax004a8797}|`IUnknown`문서 컨텍스트에 대 한 인터페이스를 반환 합니다. 일반적으로이 인터페이스에서 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) 인터페이스를 가져올 수 있습니다 `IUnknown` .|  
|guidCustomViewerSupported|{d9c9da31-ffbe-4eeb-9186-23121e3c088c}|일반적으로 식 계산기에 의해 구현 되는 사용자 지정 뷰어의 CLSID를 포함 하는 문자열을 반환 합니다.|  
|guidExtendedInfoSlot|{6df235ad-82c6-4292-9c97-7389770bc42f}|이 속성이 관리 코드 로컬 주소를 나타내는 경우 원하는 슬롯 번호를 나타내는 32 비트 숫자를 반환 합니다.|  
|guidExtendedInfoSignature|{b5fb6d46-f805-417f-96a3-8ba737073ffd}|Property 개체와 연결 된 변수의 시그니처를 포함 하는 문자열을 반환 합니다.|  
  
## <a name="see-also"></a>관련 항목  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
