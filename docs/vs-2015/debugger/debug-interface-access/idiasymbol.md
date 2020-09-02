---
title: IDiaSymbol | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol interface
ms.assetid: 01ad328a-736c-4933-a9f8-c2ded19ddd8c
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7c9b267893bacef8c9126b1a17b4eb444af6a1dd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65692894"
---
# <a name="idiasymbol"></a>IDiaSymbol
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

기호 인스턴스의 속성을 설명 합니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaSymbol : IUnknown  
```  
  
## <a name="methods-in-alphabetical-order"></a>사전순의 메서드  
 다음 표에서는의 메서드를 보여 줍니다 `IDiaSymbol` .  
  
> [!NOTE]
> 기호는 기호 유형에 따라 이러한 메서드 중 일부에 대해서만 의미 있는 데이터를 반환 합니다. 메서드가를 반환 하는 경우 `S_OK` 해당 메서드는 의미 있는 데이터를 반환 합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)|기호의 모든 자식을 검색 합니다.|  
|[IDiaSymbol::findChildrenEx](../../debugger/debug-interface-access/idiasymbol-findchildrenex.md)|기호의 자식을 검색 합니다. 이 메서드는 [IDiaSymbol:: findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)의 확장 된 버전입니다.|  
|[IDiaSymbol::findChildrenExByAddr](../../debugger/debug-interface-access/idiasymbol-findchildrenexbyaddr.md)|지정 된 주소에서 유효한 기호 자식을 검색 합니다.|  
|[IDiaSymbol::findChildrenExByRVA](../../debugger/debug-interface-access/idiasymbol-findchildrenexbyrva.md)|지정 된 RVA (상대 가상 주소)에서 유효한 기호의 자식을 검색 합니다.|  
|[IDiaSymbol::findChildrenExByVA](../../debugger/debug-interface-access/idiasymbol-findchildrenexbyva.md)|지정 된 가상 주소에서 유효한 기호 자식을 검색 합니다.|  
|[IDiaSymbol::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasymbol-findinlineframesbyaddr.md)|클라이언트에서 지정 된 주소의 모든 인라인 프레임을 반복할 수 있도록 하는 열거형을 검색 합니다.|  
|[IDiaSymbol::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasymbol-findinlineframesbyrva.md)|클라이언트에서 지정 된 RVA (상대 가상 주소)의 모든 인라인 프레임을 반복할 수 있도록 하는 열거형을 검색 합니다.|  
|[IDiaSymbol::findInlineFramesByVA](../../debugger/debug-interface-access/idiasymbol-findinlineframesbyva.md)|클라이언트에서 지정 된 VA (가상 주소)의 모든 인라인 프레임을 반복할 수 있도록 하는 열거형을 검색 합니다.|  
|[IDiaSymbol::findInlineeLines](../../debugger/debug-interface-access/idiasymbol-findinlineelines.md)|클라이언트가이 기호에서 직접 또는 간접적으로 인라인 된 모든 함수의 줄 번호 정보를 반복할 수 있도록 하는 열거형을 검색 합니다.|  
|[IDiaSymbol::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasymbol-findinlineelinesbyaddr.md)|클라이언트에서 지정 된 주소 범위 내에서이 기호에 직접 또는 간접적으로 인라인 된 모든 함수의 줄 번호 정보를 반복할 수 있도록 하는 열거형을 검색 합니다.|  
|[IDiaSymbol::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasymbol-findinlineelinesbyrva.md)|클라이언트가 지정 된 RVA (상대 가상 주소) 내에서이 기호에 직접 또는 간접적으로 인라인 된 모든 함수의 줄 번호 정보를 반복할 수 있도록 하는 열거형을 검색 합니다.|  
|[IDiaSymbol::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasymbol-findinlineelinesbyva.md)|클라이언트에서 지정 된 VA (가상 주소) 내의이 기호에서 직접 또는 간접적으로 인라인 된 모든 함수의 줄 번호 정보를 반복할 수 있도록 하는 열거형을 검색 합니다.|  
|[IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasymbol-findsymbolsbyrvaforacceleratorpointertag.md)|해당 태그 값이 지정 된 경우이 메서드는 지정 된 상대 가상 주소에이 스텁 함수에 포함 된 기호의 열거형을 반환 합니다.|  
|[IDiaSymbol::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasymbol-findsymbolsforacceleratorpointertag.md)|C++ AMP 스텁 함수의 액셀러레이터 포인터 태그 수를 반환 합니다.|  
|[IDiaSymbol::get_acceleratorPointerTags](../../debugger/debug-interface-access/idiasymbol-get-acceleratorpointertags.md)|C++ AMP 액셀러레이터 스텁 함수에 해당 하는 액셀러레이터 포인터 태그 값을 모두 반환 합니다.|  
|[IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|클래스 멤버의 액세스 한정자를 검색 합니다.|  
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|주소 위치의 오프셋 부분을 검색 합니다.|  
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|주소 위치의 섹션 부분을 검색 합니다.|  
|[IDiaSymbol::get_addressTaken](../../debugger/debug-interface-access/idiasymbol-get-addresstaken.md)|다른 기호가이 주소를 참조 하는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_age](../../debugger/debug-interface-access/idiasymbol-get-age.md)|프로그램 데이터베이스의 나이 값을 검색 합니다.|  
|[IDiaSymbol::get_arrayIndexType](../../debugger/debug-interface-access/idiasymbol-get-arrayindextype.md)|배열 인덱스 형식의 기호 식별자를 검색 합니다.|  
|[IDiaSymbol::get_arrayIndexTypeId](../../debugger/debug-interface-access/idiasymbol-get-arrayindextypeid.md)|기호의 배열 인덱스 형식 식별자를 검색 합니다.|  
|[IDiaSymbol::get_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|백 엔드 주 버전 번호를 검색 합니다.|  
|[IDiaSymbol::get_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|백 엔드 부 버전 번호를 검색 합니다.|  
|[IDiaSymbol::get_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|백 엔드 빌드 번호를 검색 합니다.|  
|[IDiaSymbol::get_baseDataOffset](../../debugger/debug-interface-access/idiasymbol-get-basedataoffset.md)|기본 데이터 오프셋을 검색 합니다.|  
|[IDiaSymbol::get_baseDataSlot](../../debugger/debug-interface-access/idiasymbol-get-basedataslot.md)|기본 데이터 슬롯을 검색 합니다.|  
|[IDiaSymbol::get_baseSymbol](../../debugger/debug-interface-access/idiasymbol-get-basesymbol.md)|포인터가 기반으로 하는 기호를 검색 합니다.|  
|[IDiaSymbol::get_baseSymbolId](../../debugger/debug-interface-access/idiasymbol-get-basesymbolid.md)|포인터의 기반이 되는 기호 ID를 검색 합니다.|  
|[IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)|단순 형식의 형식 태그를 검색 합니다.|  
|[IDiaSymbol::get_bitPosition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)|위치의 비트 위치를 검색 합니다.|  
|[IDiaSymbol::get_builtInKind](../../debugger/debug-interface-access/idiasymbol-get-builtinkind.md)|HLSL 형식의 기본 제공 종류를 검색 합니다.|  
|[IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)|메서드의 호출 규칙에 대 한 표시기를 반환 합니다.|  
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|기호의 클래스 부모에 대 한 참조를 검색 합니다.|  
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|기호의 클래스 부모 식별자를 검색 합니다.|  
|[IDiaSymbol::get_code](../../debugger/debug-interface-access/idiasymbol-get-code.md)|기호가 코드 주소를 참조 하는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_compilerGenerated](../../debugger/debug-interface-access/idiasymbol-get-compilergenerated.md)|기호가 컴파일러에서 생성 되었는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|[Compiland](../../debugger/debug-interface-access/compiland.md)를 만드는 데 사용 되는 컴파일러의 이름을 검색 합니다.|  
|[IDiaSymbol::get_constructor](../../debugger/debug-interface-access/idiasymbol-get-constructor.md)|사용자 정의 데이터 형식에 생성자가 있는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_container](../../debugger/debug-interface-access/idiasymbol-get-container.md)|이 기호의 포함 하는 기호를 검색 합니다.|  
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|사용자 정의 데이터 형식이 상수 인지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_count](../../debugger/debug-interface-access/idiasymbol-get-count.md)|목록 또는 배열의 항목 수를 검색 합니다.|  
|[IDiaSymbol::get_countLiveRanges](../../debugger/debug-interface-access/idiasymbol-get-countliveranges.md)|로컬 기호와 연결 된 유효한 주소 범위 수를 검색 합니다.|  
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|함수에서 사용자 지정 호출 규칙을 사용 하는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_dataBytes](../../debugger/debug-interface-access/idiasymbol-get-databytes.md)|OEM 기호의 데이터 바이트를 검색 합니다.|  
|[IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)|데이터 기호의 변수 분류를 검색 합니다.|  
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|컴파일된 프로그램 또는 단위의 편집 하며 계속 하기 기능을 설명 하는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|함수에서 far 반환을 사용 하는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|프런트 엔드 주 버전 번호를 검색 합니다.|  
|[IDiaSymbol::get_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|프런트 엔드 부 버전 번호를 검색 합니다.|  
|[IDiaSymbol::get_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|프런트 엔드 빌드 번호를 검색 합니다.|  
|[IDiaSymbol::get_function](../../debugger/debug-interface-access/idiasymbol-get-function.md)|Public 기호가 함수를 참조 하는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_guid](../../debugger/debug-interface-access/idiasymbol-get-guid.md)|기호의 GUID를 검색 합니다.|  
|[IDiaSymbol::get_hasAlloca](../../debugger/debug-interface-access/idiasymbol-get-hasalloca.md)|함수에에 대 한 호출이 포함 되어 있는지 여부를 나타내는 플래그를 검색 `alloca` 합니다.|  
|[IDiaSymbol::get_hasAssignmentOperator](../../debugger/debug-interface-access/idiasymbol-get-hasassignmentoperator.md)|사용자 정의 데이터 형식에 할당 연산자가 정의 되어 있는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_hasCastOperator](../../debugger/debug-interface-access/idiasymbol-get-hascastoperator.md)|사용자 정의 데이터 형식에 캐스트 연산자가 정의 되어 있는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|Compiland에 디버깅 정보가 포함 되어 있는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_hasEH](../../debugger/debug-interface-access/idiasymbol-get-haseh.md)|함수에 c + + 스타일 예외 처리기가 있는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_hasEHa](../../debugger/debug-interface-access/idiasymbol-get-haseha.md)|함수에 비동기 예외 처리기가 있는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_hasInlAsm](../../debugger/debug-interface-access/idiasymbol-get-hasinlasm.md)|함수에 인라인 어셈블리가 있는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_hasLongJump](../../debugger/debug-interface-access/idiasymbol-get-haslongjump.md)|함수가 Cjmp 명령 (C 스타일 예외 처리의 일부)을 포함 하는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|모듈에 관리 되는 코드가 포함 되어 있는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_hasNestedTypes](../../debugger/debug-interface-access/idiasymbol-get-hasnestedtypes.md)|사용자 정의 데이터 형식에 중첩 된 형식 정의가 있는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|[/Gs (Buffer Security Check)](https://msdn.microsoft.com/library/8d8a5ea1-cd5e-42e1-bc36-66e1cd7e731e) 컴파일러 스위치를 통해 함수 또는 compiland에서 컴파일된 보안 검사를 포함 하는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_hasSEH](../../debugger/debug-interface-access/idiasymbol-get-hasseh.md)|함수에 Win32 스타일의 구조적 예외 처리가 있는지를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_hasSetJump](../../debugger/debug-interface-access/idiasymbol-get-hassetjump.md)|함수에 setjmp 명령이 포함 되어 있는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_indirectVirtualBaseClass](../../debugger/debug-interface-access/idiasymbol-get-indirectvirtualbaseclass.md)|사용자 정의 데이터 형식이 간접 가상 기본 클래스 인지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_InlSpec](../../debugger/debug-interface-access/idiasymbol-get-inlspec.md)|함수가 인라인 특성으로 표시 되었는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|함수에 인터럽트 반환 명령이 있는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_intro](../../debugger/debug-interface-access/idiasymbol-get-intro.md)|함수가 기본 클래스 가상 함수 인지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_isAcceleratorGroupSharedLocal](../../debugger/debug-interface-access/idiasymbol-get-isacceleratorgroupsharedlocal.md)|기호가 C++ AMP 액셀러레이터에 대해 컴파일된 코드의 그룹 공유 지역 변수에 해당 하는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_isAcceleratorPointerTagLiveRange](../../debugger/debug-interface-access/idiasymbol-get-isacceleratorpointertagliverange.md)|C++ AMP 액셀러레이터에 대해 컴파일된 코드에서 포인터 변수의 tag 구성 요소에 대 한 *정의 범위 기호와* 해당 기호가 일치 하는지 여부를 나타내는 플래그를 검색 합니다. 정의 범위 기호는 주소 범위에 대 한 변수의 위치입니다.|  
|[IDiaSymbol::get_isAcceleratorStubFunction](../../debugger/debug-interface-access/idiasymbol-get-isacceleratorstubfunction.md)|기호가 호출에 해당 하는 액셀러레이터에 대해 컴파일된 셰이더에 대 한 최상위 함수 기호와 일치 하는지 여부를 나타냅니다 `parallel_for_each` .|  
|[IDiaSymbol::get_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md)|데이터가 여러 기호의 집계에 포함 되는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_isCTypes](../../debugger/debug-interface-access/idiasymbol-get-isctypes.md)|기호 파일에 C 형식이 포함 되어 있는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|모듈이 CIL (공용 중간 언어)에서 네이티브 코드로 변환 되었는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|사용자 정의 데이터 형식의 요소를 특정 경계에 맞출지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_isHLSLData](../../debugger/debug-interface-access/idiasymbol-get-ishlsldata.md)|이 기호가 HLSL (High Level Shader Language) 데이터를 나타내는지 여부를 지정 합니다.|  
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|모듈이 [/hotpatch (핫 패치 가능 이미지 만들기)](https://msdn.microsoft.com/library/aad539b6-c053-4c78-8682-853d98327798) 컴파일러 스위치를 사용 하 여 컴파일 되었는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|관리 되는 compiland이 링커의 LTCG와 연결 되었는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_isMatrixRowMajor](../../debugger/debug-interface-access/idiasymbol-get-ismatrixrowmajor.md)|행렬이 행 주 인지 여부를 지정 합니다.|  
|[IDiaSymbol::get_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|관리 되는 compiland이 .netmodule (메타 데이터만 포함) 인지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_isMultipleInheritance](../../debugger/debug-interface-access/idiasymbol-get-ismultipleinheritance.md)|`this`포인터가 다중 상속이 있는 데이터 멤버를 가리키는지 여부를 지정 합니다.|  
|[IDiaSymbol::get_isNaked](../../debugger/debug-interface-access/idiasymbol-get-isnaked.md)|함수에 [naked](https://msdn.microsoft.com/library/69723241-05e1-439b-868e-20a83a16ab6d) 특성이 있는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_isOptimizedAway](../../debugger/debug-interface-access/idiasymbol-get-isoptimizedaway.md)|변수가 최적화 되어 있는지 여부를 지정 합니다.|  
|[IDiaSymbol::get_isPointerBasedOnSymbolValue](../../debugger/debug-interface-access/idiasymbol-get-ispointerbasedonsymbolvalue.md)|`this`포인터가 기호 값을 기반으로 하는지 여부를 지정 합니다.|  
|[IDiaSymbol::get_isPointerToDataMember](../../debugger/debug-interface-access/idiasymbol-get-ispointertodatamember.md)|이 기호가 데이터 멤버에 대 한 포인터 인지 여부를 지정 합니다.|  
|[IDiaSymbol::get_isPointerToMemberFunction](../../debugger/debug-interface-access/idiasymbol-get-ispointertomemberfunction.md)|이 기호가 멤버 함수에 대 한 포인터 인지 여부를 지정 합니다.|  
|[IDiaSymbol::get_isReturnValue](../../debugger/debug-interface-access/idiasymbol-get-isreturnvalue.md)|변수가 반환 값을 전달 하는지 여부를 지정 합니다.|  
|[IDiaSymbol::get_isSdl](../../debugger/debug-interface-access/idiasymbol-get-issdl.md)|모듈이/SDL 옵션으로 컴파일되는지 여부를 지정 합니다.|  
|[IDiaSymbol::get_isSingleInheritance](../../debugger/debug-interface-access/idiasymbol-get-issingleinheritance.md)|`this`포인터가 단일 상속을 사용 하는 데이터 멤버를 가리키는지 여부를 지정 합니다.|  
|[IDiaSymbol::get_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md)|데이터가 개별 기호의 집계로 분할 되었는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|함수 또는 썽크 계층이 정적 인지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_isStripped](../../debugger/debug-interface-access/idiasymbol-get-isstripped.md)|기호 파일에서 전용 기호를 제거 했는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_isVirtualInheritance](../../debugger/debug-interface-access/idiasymbol-get-isvirtualinheritance.md)|`this`포인터가 가상 상속을 사용 하는 데이터 멤버를 가리키는지 여부를 지정 합니다.|  
|[IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|원본 언어를 검색 합니다.|  
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|이 기호가 나타내는 개체에서 사용 하는 메모리의 바이트 수를 검색 합니다.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|기호의 어휘 부모에 대 한 참조를 검색 합니다.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|기호의 어휘 부모 식별자를 검색 합니다.|  
|[IDiaSymbol::get_libraryName](../../debugger/debug-interface-access/idiasymbol-get-libraryname.md)|개체가 로드 된 라이브러리나 개체 파일의 파일 이름을 검색 합니다.|  
|[IDiaSymbol::get_liveRangeLength](../../debugger/debug-interface-access/idiasymbol-get-liverangelength.md)|로컬 기호가 유효한 주소 범위의 길이를 반환 합니다.|  
|[IDiaSymbol::get_liveRangeStartAddressSection](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddresssection.md)|로컬 기호가 유효한 시작 주소 범위의 부분을 반환 합니다.|  
|[IDiaSymbol::get_liveRangeStartAddressOffset](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddressoffset.md)|로컬 기호가 유효한 시작 주소 범위의 오프셋 부분을 반환 합니다.|  
|[IDiaSymbol::get_liveRangeStartRelativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-liverangestartrelativevirtualaddress.md)|로컬 기호가 유효한 주소 범위의 시작을 반환 합니다.|  
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|데이터 기호의 위치 유형을 검색 합니다.|  
|[IDiaSymbol::get_lowerBound](../../debugger/debug-interface-access/idiasymbol-get-lowerbound.md)|포트란 배열 차원의 하 한을 검색 합니다.|  
|[IDiaSymbol::get_lowerBoundId](../../debugger/debug-interface-access/idiasymbol-get-lowerboundid.md)|포트란 배열 차원의 하 한에 대 한 기호 식별자를 검색 합니다.|  
|[IDiaSymbol::get_machineType](../../debugger/debug-interface-access/idiasymbol-get-machinetype.md)|대상 CPU의 형식을 검색 합니다.|  
|[IDiaSymbol::get_managed](../../debugger/debug-interface-access/idiasymbol-get-managed.md)|기호가 관리 코드를 참조 하는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_memorySpaceKind](../../debugger/debug-interface-access/idiasymbol-get-memoryspacekind.md)|메모리 공간 종류를 검색 합니다.|  
|[IDiaSymbol::get_msil](../../debugger/debug-interface-access/idiasymbol-get-msil.md)|기호가 MSIL (Microsoft 중간 언어) 코드를 참조 하는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|기호의 이름을 검색 합니다.|  
|[IDiaSymbol::get_nested](../../debugger/debug-interface-access/idiasymbol-get-nested.md)|사용자 정의 데이터 형식이 중첩 되어 있는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|함수가 [noinline](https://msdn.microsoft.com/library/f259d55b-dec7-4bde-8cf9-14521e4fdc42) 특성으로 표시 되어 있는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|[Noreturn](https://msdn.microsoft.com/library/9c6517e5-22d7-4051-9974-3d2200ae4d1d) 특성을 사용 하 여 함수가 선언 되었는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_noStackOrdering](../../debugger/debug-interface-access/idiasymbol-get-nostackordering.md)|스택 버퍼 검사의 일부로 스택 순서를 수행할 수 없는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|함수 또는 레이블에 도달 하지 않는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_numberOfAcceleratorPointerTags](../../debugger/debug-interface-access/idiasymbol-get-numberofacceleratorpointertags.md)|C++ AMP 스텁 함수의 액셀러레이터 포인터 태그 수를 반환 합니다.|  
|[IDiaSymbol::get_numberOfModifiers](../../debugger/debug-interface-access/idiasymbol-get-numberofmodifiers.md)|원래 형식에 적용 되는 한정자 수를 검색 합니다.|  
|[IDiaSymbol::get_numberOfRegisterIndices](../../debugger/debug-interface-access/idiasymbol-get-numberofregisterindices.md)|레지스터 인덱스 수를 검색 합니다.|  
|[IDiaSymbol::get_numberOfRows](../../debugger/debug-interface-access/idiasymbol-get-numberofrows.md)|행렬의 행 수를 검색 합니다.|  
|[IDiaSymbol::get_numberOfColumns](../../debugger/debug-interface-access/idiasymbol-get-numberofcolumns.md)|행렬의 열 수를 검색 합니다.|  
|[IDiaSymbol::get_objectFileName](../../debugger/debug-interface-access/idiasymbol-get-objectfilename.md)|개체 파일 이름을 검색 합니다.|  
|[IDiaSymbol::get_objectPointerType](../../debugger/debug-interface-access/idiasymbol-get-objectpointertype.md)|클래스 메서드에 대 한 개체 포인터의 형식을 검색 합니다.|  
|[IDiaSymbol::get_oemId](../../debugger/debug-interface-access/idiasymbol-get-oemid.md)|기호 값을 검색 `oemId` 합니다.|  
|[IDiaSymbol::get_oemSymbolId](../../debugger/debug-interface-access/idiasymbol-get-oemsymbolid.md)|기호 값을 검색 `oemSymbolId` 합니다.|  
|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|기호 위치의 오프셋을 검색 합니다.|  
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|함수 또는 레이블에 디버그 정보를 비롯 하 여 최적화 된 코드가 포함 되어 있는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_overloadedOperator](../../debugger/debug-interface-access/idiasymbol-get-overloadedoperator.md)|사용자 정의 데이터 형식에 오버 로드 된 연산자가 있는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_packed](../../debugger/debug-interface-access/idiasymbol-get-packed.md)|사용자 정의 데이터 형식이 압축 되었는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|프로그램 또는 compiland 컴파일된 플랫폼 형식을 검색 합니다.|  
|[IDiaSymbol::get_pure](../../debugger/debug-interface-access/idiasymbol-get-pure.md)|함수가 순수 가상 함수 인지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_rank](../../debugger/debug-interface-access/idiasymbol-get-rank.md)|포트란 다차원 배열의 순위를 검색 합니다.|  
|[IDiaSymbol::get_reference](../../debugger/debug-interface-access/idiasymbol-get-reference.md)|포인터 형식이 참조 인지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)|위치의 등록 지정자를 검색 합니다.|  
|[IDiaSymbol::get_registerType](../../debugger/debug-interface-access/idiasymbol-get-registertype.md)|레지스터 형식을 검색 합니다.|  
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|위치의 RVA (상대 가상 주소)를 검색 합니다.|  
|[IDiaSymbol::get_restrictedType](../../debugger/debug-interface-access/idiasymbol-get-restrictedtype.md)|포인터가 제한으로 플래그 지정 되는지 여부를 지정 합니다 `this` .|  
|[IDiaSymbol::get_samplerSlot](../../debugger/debug-interface-access/idiasymbol-get-samplerslot.md)|샘플러 슬롯을 검색 합니다.|  
|[IDiaSymbol::get_scoped](../../debugger/debug-interface-access/idiasymbol-get-scoped.md)|사용자 정의 데이터 형식이 비전역 어휘 범위에 나타나는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_signature](../../debugger/debug-interface-access/idiasymbol-get-signature.md)|기호의 서명 값을 검색 합니다.|  
|[IDiaSymbol::get_sizeInUdt](../../debugger/debug-interface-access/idiasymbol-get-sizeinudt.md)|사용자 정의 형식의 멤버 크기를 검색 합니다.|  
|[IDiaSymbol::get_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)|위치의 슬롯 번호를 검색 합니다.|  
|[IDiaSymbol::get_sourceFileName](../../debugger/debug-interface-access/idiasymbol-get-sourcefilename.md)|소스 파일의 파일 이름을 검색 합니다.|  
|[IDiaSymbol::getSrcLineOnTypeDefn](../../debugger/debug-interface-access/idiasymbol-getsrclineontypedefn.md)|지정 된 사용자 정의 형식이 정의 된 위치를 나타내는 소스 파일 및 줄 번호를 검색 합니다.|  
|[IDiaSymbol::get_stride](../../debugger/debug-interface-access/idiasymbol-get-stride.md)|행렬 또는 strided 배열의 스트라이드를 검색 합니다.|  
|[IDiaSymbol::get_subType](../../debugger/debug-interface-access/idiasymbol-get-subtype.md)|하위 형식을 검색 합니다.|  
|[IDiaSymbol::get_subTypeId](../../debugger/debug-interface-access/idiasymbol-get-subtypeid.md)|하위 유형 ID를 검색 합니다.|  
|[IDiaSymbol::get_symbolsFileName](../../debugger/debug-interface-access/idiasymbol-get-symbolsfilename.md)|기호가 로드 된 파일의 이름을 검색 합니다.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|고유 기호 식별자를 검색 합니다.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|기호 형식 분류자를 검색 합니다.|  
|[IDiaSymbol::get_targetOffset](../../debugger/debug-interface-access/idiasymbol-get-targetoffset.md)|썽크 대상의 오프셋 섹션을 검색 합니다.|  
|[IDiaSymbol::get_targetRelativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetrelativevirtualaddress.md)|썽크 대상의 RVA (상대 가상 주소)를 검색 합니다.|  
|[IDiaSymbol::get_targetSection](../../debugger/debug-interface-access/idiasymbol-get-targetsection.md)|썽크 대상의 주소 섹션을 검색 합니다.|  
|[IDiaSymbol::get_targetVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetvirtualaddress.md)|썽크 대상의 VA (가상 주소)를 검색 합니다.|  
|[IDiaSymbol::get_textureSlot](../../debugger/debug-interface-access/idiasymbol-get-textureslot.md)|질감 슬롯을 검색 합니다.|  
|[IDiaSymbol::get_thisAdjust](../../debugger/debug-interface-access/idiasymbol-get-thisadjust.md)|`this`메서드에 대 한 논리적 adjustor를 검색 합니다.|  
|[IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)|함수의 썽크 형식을 검색 합니다.|  
|[IDiaSymbol::get_timeStamp](../../debugger/debug-interface-access/idiasymbol-get-timestamp.md)|기본 실행 파일의 타임 스탬프를 검색 합니다.|  
|[IDiaSymbol::get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|관리 되는 함수 또는 변수의 메타 데이터 토큰을 검색 합니다.|  
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|함수 서명에 대 한 참조를 검색 합니다.|  
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|기호의 형식 식별자를 검색 합니다.|  
|[IDiaSymbol::get_types](../../debugger/debug-interface-access/idiasymbol-get-types.md)|이 기호에 대 한 컴파일러 관련 형식 값의 배열을 검색 합니다.|  
|[IDiaSymbol::get_typeIds](../../debugger/debug-interface-access/idiasymbol-get-typeids.md)|이 기호에 대 한 컴파일러 관련 형식 식별자 값의 배열을 검색 합니다.|  
|[IDiaSymbol::get_uavSlot](../../debugger/debug-interface-access/idiasymbol-get-uavslot.md)|Uav 슬롯을 검색 합니다.|  
|[IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)|여러 UDT (사용자 정의 형식)를 검색 합니다.|  
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|사용자 정의 데이터 형식이 정렬 되지 않는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_undecoratedName](../../debugger/debug-interface-access/idiasymbol-get-undecoratedname.md)|데코레이팅된 c + + 또는 링크 이름에 대해 데코레이팅되지 않은 이름을 검색 합니다.|  
|[IDiaSymbol::get_undecoratedNameEx](../../debugger/debug-interface-access/idiasymbol-get-undecoratednameex.md)|`get_undecoratedName`확장 필드의 값을 기반으로 데코레이팅되지 않은 이름을 검색 하는 메서드의 확장입니다.|  
|[IDiaSymbol::get_unmodifiedTypeId](../../debugger/debug-interface-access/idiasymbol-get-unmodifiedtypeid.md)|수정 되지 않은 원래 형식의 ID를 검색 합니다.|  
|[IDiaSymbol::get_upperBound](../../debugger/debug-interface-access/idiasymbol-get-upperbound.md)|포트란 배열 차원의 상한을 검색 합니다.|  
|[IDiaSymbol::get_upperBoundId](../../debugger/debug-interface-access/idiasymbol-get-upperboundid.md)|포트란 배열 차원의 상한에 대 한 기호 식별자를 검색 합니다.|  
|[IDiaSymbol::get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|상수 값을 검색 합니다.|  
|[IDiaSymbol::get_virtual](../../debugger/debug-interface-access/idiasymbol-get-virtual.md)|함수가 가상 함수 인지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|위치의 VA (가상 주소)를 검색 합니다.|  
|[IDiaSymbol::get_virtualBaseClass](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseclass.md)|사용자 정의 데이터 형식이 가상 기본 클래스 인지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_virtualBaseDispIndex](../../debugger/debug-interface-access/idiasymbol-get-virtualbasedispindex.md)|가상 기본 치환 테이블의 인덱스를 검색 합니다.|  
|[IDiaSymbol::get_virtualBaseOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseoffset.md)|가상 함수의 가상 함수 테이블에서 오프셋을 검색 합니다.|  
|[IDiaSymbol::get_virtualBasePointerOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbasepointeroffset.md)|가상 기본 포인터의 오프셋을 검색 합니다.|  
|[IDiaSymbol::get_virtualBaseTableType](../../debugger/debug-interface-access/idiasymbol-get-virtualbasetabletype.md)|가상 기본 테이블 포인터의 형식을 검색 합니다.|  
|[IDiaSymbol::get_virtualTableShape](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshape.md)|사용자 정의 형식에 대 한 가상 테이블 형식의 기호 인터페이스를 검색 합니다.|  
|[IDiaSymbol::get_virtualTableShapeId](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshapeid.md)|기호의 가상 테이블 셰이프 식별자를 검색 합니다.|  
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|사용자 정의 데이터 형식이 휘발성 인지 여부를 나타내는 플래그를 검색 합니다.|  
  
## <a name="remarks"></a>설명  
  
## <a name="notes-for-callers"></a>호출자 참고 사항  
 다음 메서드 중 하나를 호출 하 여이 인터페이스를 가져옵니다.  
  
- [IDiaEnumSymbols::Item](../../debugger/debug-interface-access/idiaenumsymbols-item.md)  
  
- [IDiaEnumSymbols::Next](../../debugger/debug-interface-access/idiaenumsymbols-next.md)  
  
- [IDiaEnumSymbolsByAddr::Next](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-next.md)  
  
- [IDiaEnumSymbolsByAddr::Prev](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-prev.md)  
  
- [IDiaEnumSymbolsByAddr::symbolByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyaddr.md)  
  
- [IDiaEnumSymbolsByAddr::symbolByRVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyrva.md)  
  
- [IDiaEnumSymbolsByAddr::symbolByVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyva.md)  
  
- [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)  
  
- [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)  
  
- [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)  
  
- [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)  
  
- [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)  
  
- [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)  
  
- [IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)  
  
- [IDiaStackWalkHelper::symbolForVA](../../debugger/debug-interface-access/idiastackwalkhelper-symbolforva.md)  
  
- [IDiaSymbol::get_types](../../debugger/debug-interface-access/idiasymbol-get-types.md)  
  
## <a name="example"></a>예  
 이 예제에서는 지정 된 상대 가상 주소에서 함수에 대 한 지역 변수를 표시 하는 방법을 보여 줍니다. 또한 다양 한 형식의 기호가 서로 관련 되는 방식을 보여 줍니다.  
  
> [!NOTE]
> `CDiaBSTR` 는를 래핑하고 `BSTR` 인스턴스화가 범위를 벗어날 때 문자열 해제를 자동으로 처리 하는 클래스입니다.  
  
```cpp#  
void DumpLocalVars( DWORD rva, IDiaSession *pSession )  
{  
    CComPtr< IDiaSymbol > pBlock;  
    if ( FAILED( psession->findSymbolByRVA( rva, SymTagBlock, &pBlock ) ) )  
    {  
        Fatal( "Failed to find symbols by RVA" );  
    }  
    CComPtr< IDiaSymbol > pscope;  
    for ( ; pBlock != NULL; )  
    {  
        CComPtr< IDiaEnumSymbols > pEnum;  
        // local data search  
        if ( FAILED( pBlock->findChildren( SymTagNull, NULL, nsNone, &pEnum ) ) )  
        {  
            Fatal( "Local scope findChildren failed" );  
        }  
        CComPtr< IDiaSymbol > pSymbol;  
        DWORD tag;  
        DWORD celt;  
        while ( pEnum != NULL &&  
                SUCCEEDED( pEnum->Next( 1, &pSymbol, &celt ) ) &&  
                celt == 1)  
        {  
            pSymbol->get_symTag( &tag );  
            if ( tag == SymTagData )  
            {  
                CDiaBSTR name;  
                DWORD    kind;  
                pSymbol->get_name( &name );  
                pSymbol->get_dataKind( &kind );  
                if ( name != NULL )  
                    wprintf_s( L"\t%s (%s)\n", name, szDataKinds[ kind ] );  
            }  
            else if ( tag == SymTagAnnotation )  
            {  
                CComPtr< IDiaEnumSymbols > pValues;  
                // local data search  
                wprintf_s( L"\tAnnotation:\n" );  
                if ( FAILED( pSymbol->findChildren( SymTagNull, NULL, nsNone, &pValues ) ) )  
                    Fatal( "Annotation findChildren failed" );  
                pSymbol = NULL;  
                while ( pValues != NULL &&  
                        SUCCEEDED( pValues->Next( 1, &pSymbol, &celt ) ) &&  
                        celt == 1 )  
                {  
                    CComVariant value;  
                    if ( pSymbol->get_value( &value ) != S_OK )  
                        Fatal( "No value for annotation data." );  
                    wprintf_s( L"\t\t%ws\n", value.bstrVal );  
                    pSymbol = NULL;  
                }  
            }  
            pSymbol = NULL;  
        }  
        pBlock->get_symTag( &tag );   
        if ( tag == SymTagFunction )    // stop when at function scope  
            break;  
        // move to lexical parent  
        CComPtr< IDiaSymbol > pParent;  
        if ( SUCCEEDED( pBlock->get_lexicalParent( &pParent ) )  
            && pParent != NULL ) {  
            pBlock = pParent;  
        }  
        else  
        {  
            Fatal( "Finding lexical parent failed." );  
        }  
    };  
}  
```  
  
## <a name="requirements"></a>요구 사항  
 `Header:` Dia2.h  
  
 라이브러리: diaguids  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>관련 항목  
 [인터페이스 (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [기호 형식의 클래스 계층 구조](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [기호 및 기호 태그](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)   
 [컴파일 대상](../../debugger/debug-interface-access/compiland.md)
