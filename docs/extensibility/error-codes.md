---
title: 오류 코드 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80711836"
---
# <a name="error-codes"></a>오류 코드
소스 제어 플러그 인 API 함수에서 오류를 반환 하는 경우 다음 오류 코드 중 하나 여야 합니다. 모든 오류는 음수, 경고 또는 정보 오류 코드가 긍정적 이며 success는 0입니다.

|오류 코드|값|설명|
|----------------|-----------|-----------------|
|`SCC_I_SHARESUBPROJOK`|7|플러그 인은 두 단계에서 소스 제어의 파일 추가를 지원 합니다. 자세한 내용은 [Sccsetoption](../extensibility/sccsetoption-function.md)를 참조 하세요.|
|`SCC_I_FILEDIFFERS`|6|로컬 파일이 소스 제어 데이터베이스의 파일과 다릅니다 (예: [Sccdiff](../extensibility/sccdiff-function.md) 에서이 값을 반환할 수 있음).|
|`SCC_I_RELOADFILE`|5|소스 제어 작업을 수행 하는 동안 로컬 파일이 변경 되었습니다. 가능 하면 IDE에서 파일을 다시 로드 해야 합니다.|
|`SCC_I_FILENOTAFFECTED`|4|파일이 영향을 받지 않습니다.|
|`SCC_I_PROJECTCREATED`|3|프로젝트가 소스 제어 작업 중에 생성 된 경우 (예: 플래그가 지정 된 경우 [Sccopenproject](../extensibility/sccopenproject-function.md) 를 호출 하는 동안 `SCC_OP_CREATEIFNEW` )|
|`SCC_I_OPERATIONCANCELED`|2|작업이 취소되었습니다.|
|`SCC_I_ADV_SUPPORT`|1|플러그 인은 지정 된 명령에 대 한 고급 옵션을 지원 합니다. 자세한 내용은 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)를 참조 하세요.|
|`SCC_OK`|0|성공했습니다.|
|`SCC_E_INITIALIZEFAILED`|-1|오류: 초기화 하지 못했습니다.|
|`SCC_E_UNKNOWNPROJECT`|-2|오류: 프로젝트를 알 수 없습니다.|
|`SCC_E_COULDNOTCREATEPROJECT`|-3|오류: 프로젝트를 만들 수 없습니다.|
|`SCC_E_NOTCHECKEDOUT`|-4|오류: 파일이 체크 아웃 되지 않았습니다.|
|`SCC_E_ALREADYCHECKEDOUT`|-5|오류: 파일이 이미 체크 아웃 되었습니다.|
|`SCC_E_FILEISLOCKED`|-6|오류: 파일이 잠겨 있습니다.|
|`SCC_E_FILEOUTEXCLUSIVE`|-7|오류: 파일을 단독으로 체크 아웃 했습니다.|
|`SCC_E_ACCESSFAILURE`|-8|네트워크 또는 경합 문제로 인해 원본 제어 시스템에 액세스 하는 동안 문제가 발생 했습니다. 다시 시도 하는 것이 좋습니다.|
|`SCC_E_CHECKINCONFLICT`|-9|오류: 체크 인하는 동안 충돌이 발생 했습니다.|
|`SCC_E_FILEALREADYEXISTS`|-10|오류: 파일이 이미 있습니다.|
|`SCC_E_FILENOTCONTROLLED`|-11|오류: 파일이 소스 제어에 있지 않습니다.|
|`SCC_E_FILEISCHECKEDOUT`|-12|오류: 파일이 체크 아웃 되었습니다.|
|`SCC_E_NOSPECIFIEDVERSION`|-13|오류: 지정 된 버전이 없습니다.|
|`SCC_E_OPNOTSUPPORTED`|-14|오류: 작업이 지원 되지 않습니다.|
|`SCC_E_NONSPECIFICERROR`|checks.-15-minutes|일반 오류입니다.|
|`SCC_E_OPNOTPERFORMED`|-16|오류가 발생 했습니다. 작업이 수행 되지 않았습니다.|
|`SCC_E_TYPENOTSUPPORTED`|-17|오류: 파일의 형식 (예: 이진)이 소스 코드 제어 시스템에서 지원 되지 않습니다.|
|`SCC_E_VERIFYMERGE`|-18|파일이 자동으로 병합 되었지만 사용자 확인이 보류 중 이므로 확인 되지 않았습니다.|
|`SCC_E_FIXMERGE`|-19|파일이 자동으로 병합 되었지만 수동으로 해결 해야 하는 병합 충돌로 인해 체크 인 되지 않았습니다.|
|`SCC_E_SHELLFAILURE`|-20|셸 오류로 인해 오류가 발생 했습니다.|
|`SCC_E_INVALIDUSER`|-21|오류: 사용자가 잘못 되었습니다.|
|`SCC_E_PROJECTALREADYOPEN`|-22|오류: 프로젝트가 이미 열려 있습니다.|
|`SCC_E_PROJSYNTAXERR`|-23|프로젝트 구문 오류입니다.|
|`SCC_E_INVALIDFILEPATH`|-24|오류: 파일 경로가 잘못 되었습니다.|
|`SCC_E_PROJNOTOPEN`|-25|오류: 프로젝트가 열려 있지 않습니다.|
|`SCC_E_NOTAUTHORIZED`|-26|오류: 사용자에 게이 작업을 수행할 수 있는 권한이 없습니다.|
|`SCC_E_FILESYNTAXERR`|-27|파일 구문 오류입니다.|
|`SCC_E_FILENOTEXIST`|-28-preview|오류가 발생 했습니다. 로컬 파일이 없습니다.|
|`SCC_E_CONNECTIONFAILURE`|-29|오류: 연결에 실패 했습니다.|
|`SCC_E_UNKNOWNERROR`|-30|알 수 없는 오류입니다.|
|`SCC_E_BACKGROUNDGETINPROGRESS`|-31|백그라운드 가져오기 작업이 현재 진행 중입니다.|

## <a name="macros-provided-for-quick-checking"></a>빠른 검사를 위해 제공 되는 매크로

```cpp
IS_SCC_ERROR(rtn) (((rtn) < 0) ? TRUE : FALSE)
IS_SCC_SUCCESS(rtn) (((rtn) == SCC_OK) ? TRUE : FALSE)
IS_SCC_WARNING(rtn) (((rtn) > 0) ? TRUE : FALSE)
```

## <a name="remarks"></a>설명
 인수로 전달 되는 로컬 파일이 작업 폴더에 없는 경우 모든 소스 제어 플러그 인 API 함수 ( [Sccadd](../extensibility/sccadd-function.md), [sccadd](../extensibility/scccheckin-function.md)및 [sccadd](../extensibility/sccdiff-function.md)제외)는 성공할 것으로 예상 됩니다. 예를 들어 IDE는 작업 폴더에는 없지만 원본 제어 시스템에는 있는 파일에 대해 [Scccheckout](../extensibility/scccheckout-function.md) 또는 [SccUncheckout](../extensibility/sccuncheckout-function.md) 에 대 한 호출을 실행할 수 있습니다. 이 호출은 성공 합니다. 작업 폴더에 파일이 없거나 원본 제어 시스템에 오류가 발생 한 경우에만 함수가 실패할 것입니다.

 및와 같은 특정 함수 `SccAdd` 는 `SccCheckin` `SCC_E_FILENOTEXIST` 작업 폴더의 파일이 없을 때 특히를 반환 해야 합니다. 함수가 소스 제어 시스템의 유효한 파일 이름에 대해 작동 하는 경우에는 작업 파일이 없을 때 다른 함수가 성공 합니다.

 플러그 인에서 일부 작업 중에 파일을 읽기 전용으로 표시 한 경우에도 소스 제어 플러그 인은 작업 폴더에 있는 파일에 대 한 권한을 가정 하지 않아야 합니다. 작업 폴더의 파일을 이동, 삭제 및 플러그 인 컨트롤 외부에서 변경할 수 있습니다.

## <a name="see-also"></a>추가 정보
- [소스 제어 플러그 인](../extensibility/source-control-plug-ins.md)
