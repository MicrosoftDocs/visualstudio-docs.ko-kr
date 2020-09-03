---
title: 'IPropertyProxyProvider:: GetPropertyProxy | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IPropertyProxyProvider::GetPropertyProxy
helpviewer_keywords:
- IPropertyProxyProvider::GetPropertyProxy
ms.assetid: 3ebb7515-5bfe-48f4-9b8d-721b8f664eb6
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cc505799a0ea7571ccff41057ba9852018ddbb3e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199471"
---
# <a name="ipropertyproxyprovidergetpropertyproxy"></a>IPropertyProxyProvider::GetPropertyProxy
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

지정 된 프록시 ID에 대 한 속성 프록시 인터페이스를 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT GetPropertyProxy(  
   DWORD                  dwID,  
   IPropertyProxyEESide** proxy  
);  
```  
  
```csharp  
int GetPropertyProxy(  
   uint                     dwID,  
   out IPropertyProxyEESide proxy  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `dwID`  
 진행 원하는 속성 프록시의 ID입니다.  
  
 `proxy`  
 제한이 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) 개체를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 외부 형식 시각화 도우미를 지원 하기 위해이 메서드는 일반적으로 [Getpropertyproxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md) 메서드에 대 한 호출을 전달 합니다. IEEVisualizerService를 가져오는 방법에 대 한 자세한 내용은 [데이터 시각화 및 보기](../../../extensibility/debugger/visualizing-and-viewing-data.md) 를 참조 하세요.  
  
## <a name="see-also"></a>관련 항목  
 [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)   
 [데이터 시각화 및 보기](../../../extensibility/debugger/visualizing-and-viewing-data.md)
