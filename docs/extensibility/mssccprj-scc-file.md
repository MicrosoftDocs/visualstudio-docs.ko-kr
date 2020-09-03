---
title: MSSCCPRJ.SCC. SCC 파일 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, MSSCCPRJ.SCC file
- MSSCCPRJ.SCC file
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 89511b7c8b69c5793eceef7d58153dde253a4f47
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80702465"
---
# <a name="mssccprjscc-file"></a>MSSCCPRJ.SCC. SCC 파일
IDE를 사용 하 여 소스 제어에서 Visual Studio 솔루션 또는 프로젝트를 배치한 경우 IDE는 두 가지 주요 정보를 받습니다. 이 정보는 소스 제어 플러그 인에서 문자열 형식으로 제공 됩니다. 이러한 문자열인 "지 Xpath" 및 "ProjName"은 IDE에 불투명 하지만 플러그 인에서 버전 제어의 솔루션 또는 프로젝트를 찾는 데 사용 됩니다. 일반적으로 IDE는 먼저 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)를 호출 하 여 이러한 문자열을 가져온 후 솔루션 또는 프로젝트 파일에 저장 [합니다.](../extensibility/sccopenproject-function.md) 솔루션 및 프로젝트 파일에 포함 되는 경우 사용자가 버전 제어에 있는 솔루션 및 프로젝트 파일을 분기, 포크 또는 복사 하는 경우 "포함 Xpath" 및 "ProjName" 문자열이 자동으로 업데이트 되지 않습니다. 솔루션 및 프로젝트 파일이 버전 제어에서 올바른 위치를 가리키는지 확인 하려면 사용자가 문자열을 수동으로 업데이트 해야 합니다. 문자열은 불투명 하므로 항상 업데이트 해야 하는 방법이 명확 하지 않을 수 있습니다.

 소스 제어 플러그 인은 Mssccprj.scc 파일 이라는 특수 파일에 " *MSSCCPRJ.SCC* " 문자열을 저장 하 여이 문제를 방지할 수 있습니다. 플러그 인에서 소유 하 고 유지 관리 하는 로컬 클라이언트 쪽 파일입니다. 이 파일은 소스 제어에 포함 되지 않지만 소스 제어 파일을 포함 하는 모든 디렉터리에 대해 플러그 인에서 생성 됩니다. Visual Studio 솔루션 및 프로젝트 파일을 확인 하기 위해 소스 제어 플러그 인에서 파일 확장명을 표준 또는 사용자가 제공한 목록과 비교할 수 있습니다. IDE에서 플러그 인이 Mssccprj.scc 파일을 지원 한다는 것을 감지 하면 " *MSSCCPRJ.SCC* " 문자열을 솔루션 및 프로젝트 파일에 포함 하는 것을 중지 하 고 대신 *mssccprj.scc* 파일에서 해당 문자열을 읽습니다.

 *Mssccprj.scc* 파일을 지 원하는 소스 제어 플러그 인은 다음 지침을 따라야 합니다.

- 디렉터리 마다 하나의 *mssccprj.scc* 파일만 있을 수 있습니다.

- Mssccprj.scc 파일에는 지정 된 디렉터리 내에서 소스 제어에 있는 여러 파일에 대 한 " *MSSCCPRJ.SCC* " 및 "ProjName"이 포함 될 수 있습니다.

- "내부 Xpath" 문자열에는 따옴표가 없어야 합니다. 따옴표를 구분 기호로 사용할 수 있습니다. 예를 들어 큰따옴표 쌍을 사용 하 여 빈 문자열을 나타낼 수 있습니다. IDE는 Mssccprj.scc 파일에서 읽을 때 " *MSSCCPRJ.SCC* " 문자열에서 모든 따옴표를 제거 합니다.

- Mssccprj.scc의 "ProjName" 문자열 *입니다. SCC 파일* 은 함수에서 반환 된 문자열과 정확히 일치 해야 합니다 `SccGetProjPath` . 함수에서 반환 된 문자열이 따옴표를 포함 하는 경우 *mssccprj.scc* 파일의 문자열에 따옴표를 포함 해야 하 고 그 반대의 경우도 마찬가지입니다.

- 파일이 소스 제어에서 배치 될 때마다 *mssccprj.scc* 파일이 만들어지거나 업데이트 됩니다.

- *Mssccprj.scc* 파일이 삭제 되는 경우 공급자는 다음에 해당 디렉터리에 대 한 소스 제어 작업을 수행할 때 해당 파일을 다시 생성 해야 합니다.

- *Mssccprj.scc* 파일은 정의 된 형식을 엄격 하 게 따라야 합니다.

## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>MSSCCPRJ.SCC의 그림입니다. SCC 파일 형식
 다음은 Mssccprj.scc 파일 형식의 샘플입니다 *.* 줄 번호는 안내선 으로만 제공 되며 파일 본문에 포함 되어서는 안 됩니다.

- [줄 1] `SCC = This is a Source Code Control file`

- [줄 2]

- [줄 3] `[TestApp.sln]`

- [줄 4] `SCC_Aux_Path = "\\server\vss\"`

- [줄 5] `SCC_Project_Name = "$/TestApp"`

- [줄 6 줄]

- [줄 7] `[TestApp.csproj]`

- [줄 8] `SCC_Aux_Path = "\\server\vss\"`

- [줄 9] `SCC_Project_Name = "$/TestApp"`

 첫 번째 줄에서는 파일의 용도를 설명 하 고이 형식의 모든 파일에 대 한 서명으로 사용 합니다. 이 줄은 모든 *mssccprj.scc* 파일에서 다음과 같이 정확히 표시 되어야 합니다.

 `SCC = This is a Source Code Control file`

 다음 섹션에서는 파일 이름에 대괄호로 표시 된 각 파일에 대 한 설정을 자세히 설명 합니다. 이 섹션은 추적 되는 각 파일에 대해 반복 됩니다. 이 줄은 파일 이름, 즉의 샘플입니다 `[TestApp.csproj]` . IDE에는 다음 두 줄이 필요 합니다. 그러나 정의 된 값의 스타일을 정의 하지는 않습니다. 변수는 `SCC_Aux_Path` 및 `SCC_Project_Name` 입니다.

 `SCC_Aux_Path = "\\server\vss\"`

 `SCC_Project_Name = "$/TestApp"`

 이 섹션에 대 한 끝 구분 기호가 없습니다. 파일 이름 및 파일에 표시 되는 모든 리터럴은 scc 헤더 파일에 정의 됩니다. 자세한 내용은 [소스 제어 플러그 인을 찾기 위한 키로 사용 되는 문자열](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)을 참조 하세요.

## <a name="see-also"></a>추가 정보
- [소스 제어 플러그 인](../extensibility/source-control-plug-ins.md)
- [소스 제어 플러그 인을 찾기 위한 키로 사용 되는 문자열](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)
