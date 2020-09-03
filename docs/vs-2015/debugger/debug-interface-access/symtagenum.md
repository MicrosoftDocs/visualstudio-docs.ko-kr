---
title: SymTagEnum | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- SymTagEnum enumeration
ms.assetid: 528a50cf-e13d-46ec-a98c-323d5d047de9
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1578d88265769414f68964e28d3426ffcc62f9e8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193509"
---
# <a name="symtagenum"></a>SymTagEnum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

기호의 유형을 지정 합니다.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum SymTagEnum {   
   SymTagNull,  
   SymTagExe,  
   SymTagCompiland,  
   SymTagCompilandDetails,  
   SymTagCompilandEnv,  
   SymTagFunction,  
   SymTagBlock,  
   SymTagData,  
   SymTagAnnotation,  
   SymTagLabel,  
   SymTagPublicSymbol,  
   SymTagUDT,  
   SymTagEnum,  
   SymTagFunctionType,  
   SymTagPointerType,  
   SymTagArrayType,   
   SymTagBaseType,   
   SymTagTypedef,   
   SymTagBaseClass,  
   SymTagFriend,  
   SymTagFunctionArgType,   
   SymTagFuncDebugStart,   
   SymTagFuncDebugEnd,  
   SymTagUsingNamespace,   
   SymTagVTableShape,  
   SymTagVTable,  
   SymTagCustom,  
   SymTagThunk,  
   SymTagCustomType,  
   SymTagManagedType,  
   SymTagDimension,  
   SymTagCallSite,  
   SymTagInlineSite,  
   SymTagBaseInterface,  
   SymTagVectorType,  
   SymTagMatrixType,  
   SymTagHLSLType  
};  
```  
  
## <a name="elements"></a>요소  
 `SymTagNull`  
 기호에 형식이 없음을 나타냅니다.  
  
 `SymTagExe`  
 기호가 .exe 파일 임을 나타냅니다. 기호 `SymTagExe` 저장소 당 하나의 기호만 있습니다. 전역 범위 역할을 하며 어휘 부모를 포함 하지 않습니다.  
  
 `SymTagCompiland`  
 기호 저장소의 각 compiland 구성 요소에 대 한 compiland 기호를 나타냅니다. 네이티브 응용 프로그램의 경우 `SymTagCompiland` 기호는 이미지에 연결 된 개체 파일에 해당 합니다. 일부 종류의 MSIL (Microsoft 중간 언어) 이미지의 경우 클래스 마다 하나의 compiland 있습니다.  
  
 `SymTagCompilandDetails`  
 기호에 compiland 확장 특성이 포함 되어 있음을 나타냅니다. 이러한 속성을 검색 하려면 compiland 기호를 로드 해야 할 수 있습니다.  
  
 `SymTagCompilandEnv`  
 기호가 compiland에 대해 정의 된 환경 문자열 임을 나타냅니다.  
  
 `SymTagFunction`  
 기호가 함수 임을 나타냅니다.  
  
 `SymTagBlock`  
 기호가 중첩 된 블록 임을 나타냅니다.  
  
 `SymTagData`  
 기호가 데이터 임을 나타냅니다.  
  
 `SymTagAnnotation`  
 코드 주석에 대해 기호가 임을 나타냅니다. 이 기호의 자식은 상수 데이터 문자열 ( `SymTagData` , `LocIsConstant` , `DataIsConstant` )입니다. 대부분의 클라이언트는이 기호를 무시 합니다.  
  
 `SymTagLabel`  
 기호가 레이블 임을 나타냅니다.  
  
 `SymTagPublicSymbol`  
 기호가 공용 기호 임을 나타냅니다. 네이티브 응용 프로그램의 경우이 기호는 이미지를 연결 하는 동안 발견 된 COFF 외부 기호입니다.  
  
 `SymTagUDT`  
 기호가 사용자 정의 형식 (구조체, 클래스 또는 공용 구조체) 임을 나타냅니다.  
  
 `SymTagEnum`  
 기호가 열거형 임을 나타냅니다.  
  
 `SymTagFunctionType`  
 기호가 함수 시그니처 형식 임을 나타냅니다.  
  
 `SymTagPointerType`  
 기호가 포인터 형식 임을 나타냅니다.  
  
 `SymTagArrayType`  
 기호가 배열 형식 임을 나타냅니다.  
  
 `SymTagBaseType`  
 기호가 기본 형식 임을 나타냅니다.  
  
 `SymTagTypedef`  
 기호가 `typedef` 또 다른 형식의 별칭인 임을 나타냅니다.  
  
 `SymTagBaseClass`  
 기호가 사용자 정의 형식의 기본 클래스 임을 나타냅니다.  
  
 `SymTagFriend`  
 기호가 사용자 정의 형식의 friend 임을 나타냅니다.  
  
 `SymTagFunctionArgType`  
 기호가 함수 인수 임을 나타냅니다.  
  
 `SymTagFuncDebugStart`  
 기호가 함수 프롤로그 코드의 끝 위치 임을 나타냅니다.  
  
 `SymTagFuncDebugEnd`  
 기호가 함수의 에필로그 코드 시작 위치 임을 나타냅니다.  
  
 `SymTagUsingNamespace`  
 기호가 현재 범위에서 활성 상태인 네임 스페이스 이름 임을 나타냅니다.  
  
 `SymTagVTableShape`  
 기호가 가상 테이블 설명 임을 나타냅니다.  
  
 `SymTagVTable`  
 기호가 가상 테이블 포인터 임을 나타냅니다.  
  
 `SymTagCustom`  
 기호가 사용자 지정 기호 이며 DIA에서 해석 되지 않음을 나타냅니다.  
  
 `SymTagThunk`  
 기호가 16 비트 코드와 32 비트 코드 간에 데이터를 공유 하는 데 사용 되는 썽크 임을 나타냅니다.  
  
 `SymTagCustomType`  
 기호가 사용자 지정 컴파일러 기호 임을 나타냅니다.  
  
 `SymTagManagedType`  
 기호가 메타 데이터에 있음을 나타냅니다.  
  
 `SymTagDimension`  
 기호가 포트란 다차원 배열 임을 나타냅니다.  
  
 `SymTagCallSite`  
 기호가 호출 사이트 임을 나타냅니다.  
  
 `SymTagInlineSite`  
 기호가 인라인 사이트 임을 나타냅니다.  
  
 `SymTagBaseInterface`  
 기호가 기본 인터페이스 임을 나타냅니다.  
  
 `SymTagVectorType`  
 기호가 벡터 형식 임을 나타냅니다.  
  
 `SymTagMatrixType`  
 기호가 행렬 형식 임을 나타냅니다.  
  
 `SymTagHLSLType`  
 기호가 높은 수준의 셰이더 언어 형식 임을 나타냅니다.  
  
## <a name="remarks"></a>설명  
 디버그 파일 내의 모든 기호에는 기호 형식을 지정 하는 식별 태그가 있습니다.  
  
 이 열거형의 값은 [IDiaSymbol:: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) 메서드를 호출 하 여 반환 됩니다.  
  
 이 열거형의 값은 검색 범위를 특정 기호 형식으로 제한 하기 위해 다음 메서드에 전달 됩니다.  
  
- [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)  
  
- [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)  
  
- [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)  
  
- [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)  
  
- [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)  
  
- [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)  
  
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## <a name="requirements"></a>요구 사항  
 헤더: cvconst  
  
## <a name="see-also"></a>관련 항목  
 [열거형 및 구조체](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [기호 형식의 어휘 계층 구조](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [IDiaSession:: Find기호 Byaddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)   
 [IDiaSession:: Find기호 Byrva](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)   
 [IDiaSession:: findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)   
 [IDiaSession:: Find기호 Bytoken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)   
 [IDiaSession:: Find기호 Byva](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)   
 [IDiaSession:: findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)   
 [IDiaSession:: findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
