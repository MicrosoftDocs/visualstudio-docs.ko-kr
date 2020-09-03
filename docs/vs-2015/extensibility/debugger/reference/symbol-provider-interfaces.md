---
title: 기호 공급자 인터페이스 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- interfaces, symbol handler
- symbol handler, interfaces
- symbol handler, evaluating variables
ms.assetid: 4201f10e-c9f7-4b38-bb45-40fe0082d5bf
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c409175fb39207bc0e83a521577ad6d641731691
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204863"
---
# <a name="symbol-provider-interfaces"></a>기호 공급자 인터페이스
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

다음은에 대 한 기호 처리 인터페이스 [!INCLUDE[vsipsdk](../../../includes/vsipsdk-md.md)] 입니다.  
  
## <a name="discussion"></a>토론(Discussion)  
 이러한 인터페이스는 중단 모드에서 호출 스택의 변수를 평가 하는 데 사용 됩니다. 공용 언어 런타임 기호 공급자 (SP)에 대해서만 구현 됩니다.  
  
|인터페이스|구현 방법|설명|  
|---------------|--------------------|-----------------|  
|[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)|SP|항목의 주소를 나타냅니다.|  
|[IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)|SP|프로세스 ID에 대 한 액세스를 제공 하는 항목의 주소를 나타냅니다.|  
|[IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)|SP|배열 기호 또는 배열 형식을 나타냅니다.|  
|[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)|SP|클래스 기호 또는 클래스 형식을 나타냅니다.|  
|[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)|SP|관리 코드와 관련 된 메서드를 사용 하 여 COM + 기호 공급자를 나타냅니다.|  
|[IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)|SP|관리 코드와 관련 된 메서드를 사용 하 여 **IDebugComPlusSymbolProvider**를 확장 하는 com + 기호 공급자를 나타냅니다.|  
|[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)|SP|다른 기호 또는 형식에 대 한 컨테이너인 기호 또는 형식을 나타냅니다.|  
|[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)|SP|기호에 연결할 수 있는 사용자 지정 특성을 나타냅니다.|  
|[IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)|SP|메서드 또는 형식에 대 한 사용자 지정 특성에 대 한 쿼리를 나타냅니다.|  
|[IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)|SP|기호에 대 한 사용자 지정 특성에 대 한 액세스를 제공 합니다.|  
|[IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)|SP|런타임에 확인할 수 있는 모든 형식에 대 한 기본 인터페이스입니다.|  
|[IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)|SP|[Idebugbinder](../../../extensibility/debugger/reference/idebugbinder.md) 개체의 동적 필드를 나타냅니다.|  
|[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)|SP|열거형 형식을 나타냅니다.|  
|[IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)|Sp-2|관리 코드 제네릭을 지원 하도록 사용 가능한 필드의 형식을 확장 합니다.|  
|[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)|SP|모든 필드에 대 한 기본 클래스입니다. 기호 또는 형식에 대 한 설명을 나타냅니다.|  
|[IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)|SP|관리 코드 제네릭 형식에 대 한 필드의 정의를 나타냅니다.|  
|[IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)|SP|관리 코드 제네릭 형식에 대 한 필드의 인스턴스를 나타냅니다.|  
|[IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)|SP|관리 코드 제네릭 형식에 대 한 매개 변수를 나타냅니다.|  
|[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)|SP|메서드를 나타냅니다.|  
|[IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)|SP|Debug 선택적 한정자를 나타냅니다.|  
|[IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)|SP|포인터를 나타냅니다.|  
|[IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)|SP|[Idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 인터페이스의 기본 형식 열거형 값을 나타냅니다.|  
|[IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)|SP|가져오거나 설정할 수 있는 관리 되는 코드 클래스의 속성을 나타냅니다.|  
|[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)|SP|기호 및 형식을 제공 하는 기호 공급자를 나타냅니다.|  
|[IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)|SP|메타 데이터 및 핵심 기호 인터페이스에 직접 액세스할 수 있는 기호 공급자를 나타냅니다.|  
|[IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)|SP|형식을 나타내는 필드를 만드는 기능을 나타냅니다.|  
|[IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)|SP|배열 형식을 만들 수 있도록 **Idebugtypefieldbuilder** 를 확장 합니다.|  
|[IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)|SP|[Idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md) 개체의 컬렉션을 나타냅니다.|  
|[IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)|SP|[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) 개체의 컬렉션을 나타냅니다.|  
|[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)|SP|[Idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 개체의 컬렉션을 나타냅니다.|  
  
## <a name="see-also"></a>관련 항목  
 [API 참조](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
