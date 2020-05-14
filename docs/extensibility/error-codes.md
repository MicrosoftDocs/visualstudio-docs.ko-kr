---
title: 오류 코드 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- error codes, source control plug-ins
- source control plug-ins, error codes
- errors [Visual Studio SDK]
ms.assetid: d9cbd1c4-719b-467a-8100-333c1e146d3b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34072f6ddbd632f83dd308c6cb63427e02bb110b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711836"
---
# <a name="error-codes"></a>오류 코드
소스 제어 플러그인 API 함수가 오류를 반환하면 다음 오류 코드 중 하나가 될 것으로 예상됩니다. 모든 오류는 음수, 경고 또는 정보 오류 코드는 양수, 성공은 0입니다.

|오류 코드|값|Description|
|----------------|-----------|-----------------|
|`SCC_I_SHARESUBPROJOK`|7|플러그인은 소스 제어에서 파일을 두 단계로 추가할 수 있도록 지원합니다. 자세한 내용은 [SccSetOption](../extensibility/sccsetoption-function.md)을 참조하십시오.|
|`SCC_I_FILEDIFFERS`|6|로컬 파일은 소스 제어 데이터베이스의 파일과 다릅니다(예: [SccDiff가](../extensibility/sccdiff-function.md) 이 값을 반환할 수 있음).|
|`SCC_I_RELOADFILE`|5|소스 제어 작업 중에 로컬 파일이 변경되었습니다. 가능하면 파일을 다시 로드해야 합니다.|
|`SCC_I_FILENOTAFFECTED`|4|파일은 영향을 받지 않습니다.|
|`SCC_I_PROJECTCREATED`|3|프로젝트는 소스 제어 작업 중에 만들어졌습니다(예: 플래그가 지정된 경우 `SCC_OP_CREATEIFNEW` [SccOpenProject를](../extensibility/sccopenproject-function.md) 호출하는 동안).|
|`SCC_I_OPERATIONCANCELED`|2|작업이 취소되었습니다.|
|`SCC_I_ADV_SUPPORT`|1|플러그인은 지정된 명령에 대한 고급 옵션을 지원합니다. 자세한 내용은 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)를 참조하십시오.|
|`SCC_OK`|0|성공했습니다.|
|`SCC_E_INITIALIZEFAILED`|-1|오류: 초기화가 실패했습니다.|
|`SCC_E_UNKNOWNPROJECT`|-2|오류: 프로젝트를 알 수 없습니다.|
|`SCC_E_COULDNOTCREATEPROJECT`|-3|오류: 프로젝트를 만들 수 없습니다.|
|`SCC_E_NOTCHECKEDOUT`|-4|오류: 파일이 체크 아웃되지 않았습니다.|
|`SCC_E_ALREADYCHECKEDOUT`|-5|오류: 파일이 이미 체크 아웃되었습니다.|
|`SCC_E_FILEISLOCKED`|-6|오류: 파일이 잠겨 있습니다.|
|`SCC_E_FILEOUTEXCLUSIVE`|-7|오류: 파일이 단독으로 체크 아웃되었습니다.|
|`SCC_E_ACCESSFAILURE`|-8|네트워크 또는 경합 문제로 인해 소스 제어 시스템에 액세스하는 데 문제가 있었습니다. 다시 시도하는 것이 좋습니다.|
|`SCC_E_CHECKINCONFLICT`|-9|오류: 체크 인 중에 충돌이 발생했습니다.|
|`SCC_E_FILEALREADYEXISTS`|-10|오류: 파일이 이미 있습니다.|
|`SCC_E_FILENOTCONTROLLED`|-11|오류: 파일이 소스 제어를 받지 않습니다.|
|`SCC_E_FILEISCHECKEDOUT`|-12|오류: 파일이 체크 아웃되었습니다.|
|`SCC_E_NOSPECIFIEDVERSION`|-13|오류: 지정된 버전이 없습니다.|
|`SCC_E_OPNOTSUPPORTED`|-14|오류: 작업이 지원되지 않습니다.|
|`SCC_E_NONSPECIFICERROR`|-15|비특정 오류입니다.|
|`SCC_E_OPNOTPERFORMED`|-16|오류가 발생하였고 작업이 수행되지 않았습니다.|
|`SCC_E_TYPENOTSUPPORTED`|-17|오류: 파일 형식(예: 바이너리)은 소스 코드 제어 시스템에서 지원되지 않습니다.|
|`SCC_E_VERIFYMERGE`|-18|파일이 자동으로 병합되었지만 사용자 확인 대기 중이기 때문에 확인되지 않았습니다.|
|`SCC_E_FIXMERGE`|-19|파일이 자동으로 병합되었지만 수동으로 해결해야 하는 병합 충돌로 인해 체크 인되지 않았습니다.|
|`SCC_E_SHELLFAILURE`|-20|셸 오류로 인한 오류입니다.|
|`SCC_E_INVALIDUSER`|-21|오류: 사용자가 잘못되었습니다.|
|`SCC_E_PROJECTALREADYOPEN`|-22|오류: 프로젝트가 이미 열려 있습니다.|
|`SCC_E_PROJSYNTAXERR`|-23|프로젝트 구문 오류입니다.|
|`SCC_E_INVALIDFILEPATH`|-24|오류: 파일 경로가 잘못되었습니다.|
|`SCC_E_PROJNOTOPEN`|-25|오류: 프로젝트가 열려 있지 않습니다.|
|`SCC_E_NOTAUTHORIZED`|-26|오류: 사용자가 이 작업을 수행할 권한이 없습니다.|
|`SCC_E_FILESYNTAXERR`|-27|파일 구문 오류입니다.|
|`SCC_E_FILENOTEXIST`|-28|로컬 파일이 없습니다.|
|`SCC_E_CONNECTIONFAILURE`|-29|오류: 연결 오류가 발생했습니다.|
|`SCC_E_UNKNOWNERROR`|-30|알 수 없는 오류입니다.|
|`SCC_E_BACKGROUNDGETINPROGRESS`|-31|백그라운드 get 작업이 현재 진행 중입니다.|

## <a name="macros-provided-for-quick-checking"></a>빠른 확인을 위해 제공되는 매크로

```cpp
IS_SCC_ERROR(rtn) (((rtn) < 0) ? TRUE : FALSE)
IS_SCC_SUCCESS(rtn) (((rtn) == SCC_OK) ? TRUE : FALSE)
IS_SCC_WARNING(rtn) (((rtn) > 0) ? TRUE : FALSE)
```

## <a name="remarks"></a>설명
 모든 소스 제어 플러그인 API [함수(SccAdd,](../extensibility/sccadd-function.md) [SccCheckin](../extensibility/scccheckin-function.md)및 [SccDiff](../extensibility/sccdiff-function.md)제외)는 인수로 전달되는 로컬 파일이 작업 폴더에 없을 때 성공할 것으로 예상됩니다. 예를 들어 IDE는 작업 폴더에 없지만 소스 제어 시스템에 있는 파일에 대해 [SccCheckout](../extensibility/scccheckout-function.md) 또는 [SccUncheckout에](../extensibility/sccuncheckout-function.md) 대한 호출을 발행할 수 있습니다. 이 호출이 성공할 것입니다. 작업 폴더 또는 소스 제어 시스템에 파일이 없는 경우에만 실패할 것으로 예상되는 함수입니다.

 및 와 `SccAdd` `SccCheckin`같은 특정 함수는 `SCC_E_FILENOTEXIST` 작업 폴더에 있는 파일이 없을 때 특별히 반환해야 합니다. 함수가 소스 제어 시스템에서 유효한 파일 이름으로 작동하는 경우 다른 함수는 작업 파일이 존재하지 않을 때 성공할 것으로 예상됩니다.

 소스 제어 플러그인은 일부 작업 중에 플러그 인이 파일 읽기 전용으로 표시한 경우에도 작업 폴더의 파일에 대한 권한에 대한 가정을 하지 않아야 합니다. 작업 폴더의 파일을 플러그 인 컨트롤 외부에서 이동, 삭제 및 변경할 수 있습니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그인](../extensibility/source-control-plug-ins.md)
