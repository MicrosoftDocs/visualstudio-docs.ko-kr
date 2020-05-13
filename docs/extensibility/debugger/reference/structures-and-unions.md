---
title: 구조 및 연합 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- structures [Visual Studio SDK]
ms.assetid: 9ff0a8f8-1ee6-4fdd-8b80-206436ff589b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 19d8f547d98488edffc6049be7619e5b5e921d93
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713489"
---
# <a name="structures-and-unions"></a>구조체 및 공용 구조체
다음은 Visual Studio 디버깅 SDK의 구조 및 공용 구조체입니다.

- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) 시스템 ID 또는 GUID일 수 있는 프로세스 ID를 지정합니다.

- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) 중단점이 발사되는 조건을 설명합니다.

- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) 위치, 프로그램 및 스레드를 포함한 오류 중단점의 해결에 대해 설명합니다.

- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) 중단점의 위치를 설명하는 데 사용되는 구조유형을 지정합니다.

- [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) 코드의 주소에서 중단점의 위치를 설명하는 구성 요소를 정의합니다.

- [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) 디버깅 중인 프로그램의 주소에 직접 바인딩되는 중단점의 위치를 설명합니다.

- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) 코드 원본 파일에서 줄에 있는 중단점의 위치를 설명합니다.

- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) 코드의 함수에서 중단점의 오프셋 위치를 설명합니다.

- [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) 사용자가 IDE에서 입력할 수 있는 문자열을 기반으로 코드 중단점을 설정하는 데 사용됩니다.

- [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md) 사용자가 IDE에서 입력할 수 있는 문자열을 기반으로 하는 데이터 중단점을 설정하는 데 사용됩니다.

- [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) 특정 위치에서 중단점의 확인에 대해 설명합니다.

- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) 이전에 통과된 후 중단점이 발생되는 개수와 조건을 설명합니다.

- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) 중단점을 구현하는 데 필요한 정보를 포함합니다.

- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) 중단점을 구현하는 데 필요한 [정보(BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) 구조와 동일하지만 공급업체 GUID, 제약 조건 및 추적 점 정보가 포함됩니다).

- [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) 코드 중단점의 위치를 설명합니다.

- [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) 데이터 중단점 바인딩의 결과를 설명합니다.

- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) 코드 중단점 또는 데이터 중단점에 대한 바인딩된 중단점 정보를 설명합니다.

- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) 중단점 확인 위치의 구조를 지정합니다.

- [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md) 문자열의 배열을 설명합니다.

- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) 메타데이터에서 가져온 필드 유형에 대한 정보를 지정합니다.

- [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) 함수 또는 메서드에 대한 호출에 대해 설명합니다.

- [COMPUTER_INFO](../../../extensibility/debugger/reference/computer-info.md) 디버거가 실행 중인 컴퓨터에 대해 설명합니다.

- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md) GUID 의 목록을 설명합니다.

- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) 메모리 컨텍스트 또는 코드 컨텍스트를 설명합니다.

- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) 디버깅 중인 프로그램의 주소를 설명합니다.

- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) 다양한 종류의 주소 중 하나를 나타냅니다.

- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) 사용자 지정 뷰어 또는 유형 시각화 도우미를 식별합니다.

- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 이름, 형식 및 값이 있는 계층적 특성의 개체를 설명하는 디버그 속성에 대해 설명합니다.

- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) 참조를 설명합니다.

- [디스어셈블리데이터](../../../extensibility/debugger/reference/disassemblydata.md) 디스플레이를 위해 IDE로의 분해에 대해 설명합니다.

- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) 디버깅 중인 프로그램에서 throw된 예외 또는 런타임 오류를 설명합니다.

- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) 로컬 변수, 매개 변수 또는 기타 필드를 설명합니다.

- [프레임 정보](../../../extensibility/debugger/reference/frameinfo.md) 스택 프레임에 대해 설명합니다.

- [GUID_ARRAY](../../../extensibility/debugger/reference/guid-array.md) 사용 가능한 디버그 엔진에 대한 고유 식별자 배열에 대해 설명합니다.

- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) 모듈에 대한 JustMyCode 정보를 설정하는 데 사용됩니다.

- [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) 특정 컴퓨터에 대해 설명합니다.

- [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) 배열 내의 배열 요소를 설명합니다.

- [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) 클래스 또는 구조의 필드의 주소를 설명합니다.

- [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) 범위 내의 로컬 변수(일반적으로 함수 또는 메서드)의 주소를 설명합니다.

- [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) 클래스 메서드의 주소를 설명합니다.

- [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) 메서드 또는 함수의 매개 변수를 설명합니다.

- [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) 메서드 또는 함수의 반환 값을 설명합니다.

- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) 메타데이터에서 가져온 필드 유형에 대해 설명합니다.

- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) 특정 모듈(DLL, EXE 또는 어셈블리)에 대해 설명합니다.

- [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) 검색된 기호 검색 경로에 대한 상태 정보를 설명합니다.

- [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) 네이티브 주소를 설명합니다.

- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) PDB 기호에서 가져온 필드 유형에 대해 설명합니다.

- [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) 코드 위치에 바인딩할 준비가 된 중단점의 상태를 설명합니다.

- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) 프로세스에 대해 설명합니다.

- [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) 프로그램 노드를 나타내는 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 개체 의 목록을 설명합니다.

- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) 컴퓨터에서 실행되는 프로세스에 대해 설명합니다.

- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) 지정된 텍스트의 선 및 열 위치를 설명합니다.

- [스레드 속성](../../../extensibility/debugger/reference/threadproperties.md) 스레드의 속성을 설명합니다.

- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) 필드의 형식을 설명합니다.

- [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) 실제 주소를 설명합니다.

- [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) 포인터(Visual`Me` Basic)를 기준으로 `this` 하는 주소를 설명합니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h, sh.h 또는 ee.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [API 참조](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
