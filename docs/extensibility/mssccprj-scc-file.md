---
title: MSSCCPRJ. SCC 파일 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702465"
---
# <a name="mssccprjscc-file"></a>MSSCCPRJ. SCC 파일
IDE를 사용하여 소스 제어 하에 Visual Studio 솔루션 또는 프로젝트를 배치하면 IDE는 두 가지 주요 정보를 받습니다. 정보는 문자열 의 형태로 소스 제어 플러그인에서 온다. 이러한 문자열인 "AuxPath" 및 "ProjName"은 IDE에 불투명하지만 플러그인에서 버전 제어에서 솔루션 또는 프로젝트를 찾는 데 사용됩니다. IDE는 일반적으로 [SccGetProjPath를](../extensibility/sccgetprojpath-function.md)호출하여 이러한 문자열을 처음으로 가져옵니다. [SccOpenProject](../extensibility/sccopenproject-function.md) 솔루션 및 프로젝트 파일에 포함되면 사용자가 버전 제어에 있는 솔루션 및 프로젝트 파일을 분기, 분기 또는 복사할 때 "AuxPath" 및 "ProjName" 문자열이 자동으로 업데이트되지 않습니다. 솔루션 및 프로젝트 파일이 버전 제어에서 올바른 위치를 가리키도록 하려면 사용자가 문자열을 수동으로 업데이트해야 합니다. 문자열은 불투명하기 때문에 문자열을 업데이트하는 방법을 항상 명확하지 않을 수 있습니다.

 소스 제어 플러그인은 *MSSCCPRJ.SCC* 파일이라는 특수 파일에 "AuxPath" 및 "ProjName" 문자열을 저장하여 이 문제를 방지할 수 있습니다. 플러그인에서 소유하고 유지 관리하는 로컬 클라이언트 쪽 파일입니다. 이 파일은 소스 제어 하에 배치되지 않지만 소스 제어 파일을 포함하는 모든 디렉터리에 대한 플러그인에 의해 생성됩니다. 어떤 파일이 Visual Studio 솔루션 및 프로젝트 파일인지 확인하려면 소스 제어 플러그인에서 파일 확장자를 표준 또는 사용자가 제공한 목록과 비교할 수 있습니다. IDE가 플러그인이 *MSSCCPRJ.SCC* 파일을 지원하는 것을 감지하면 솔루션 및 프로젝트 파일에 "AuxPath" 및 "ProjName" 문자열을 포함하지 않고 *MSSCCPRJ.SCC* 파일에서 해당 문자열을 읽습니다.

 *MSSCCPRJ.SCC* 파일을 지원하는 소스 제어 플러그인은 다음 지침을 준수해야 합니다.

- 디렉터리당 *MSSCCPRJ.SCC* 파일은 하나만 있을 수 있습니다.

- *MSSCCPRJ.SCC* 파일에는 지정된 디렉터리 내에서 소스 제어를 받고 있는 여러 파일에 대한 "AuxPath" 및 "ProjName"이 포함될 수 있습니다.

- "AuxPath" 문자열에는 내부에 따옴표가 없어야 합니다. 구분 기호로 주위에 따옴표를 가질 수 있습니다 (예 : 한 쌍의 큰 따옴표는 빈 문자열을 나타내는 데 사용할 수 있습니다). IDE는 *MSSCCPRJ.SCC* 파일에서 읽을 때 "AuxPath" 문자열에서 모든 따옴표를 제거합니다.

- MSSCCPRJ의 "ProjName" *문자열입니다. SCC 파일은* 함수에서 반환된 `SccGetProjPath` 문자열과 정확히 일치해야 합니다. 함수에서 반환되는 문자열에 따옴표가 있는 경우 *MSSCCPRJ.SCC* 파일의 문자열에는 따옴표가 있어야 하며 그 반대의 경우도 마찬가지입니다.

- *MSSCCPRJ.SCC* 파일은 소스 제어하에 배치될 때마다 생성되거나 업데이트됩니다.

- *MSSCCPRJ.SCC* 파일이 삭제되면 공급자는 해당 디렉터리와 관련된 소스 제어 작업을 수행할 때 다시 생성해야 합니다.

- *MSSCCPRJ.SCC* 파일은 정의된 형식을 엄격히 따라야 합니다.

## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>MSSCCPRJ의 그림. SCC 파일 형식
 다음은 *MSSCCPRJ.SCC* 파일 형식의 샘플입니다(줄 번호는 가이드로만 제공되며 파일 본문에 포함되지 않아야 합니다).

- [1호선]`SCC = This is a Source Code Control file`

- [2호선]

- [3호선]`[TestApp.sln]`

- [4호선]`SCC_Aux_Path = "\\server\vss\"`

- [5호선]`SCC_Project_Name = "$/TestApp"`

- [6호선]

- [7호선]`[TestApp.csproj]`

- [8호선]`SCC_Aux_Path = "\\server\vss\"`

- [9호선]`SCC_Project_Name = "$/TestApp"`

 첫 번째 줄은 파일의 목적을 명시하고 이 유형의 모든 파일에 대한 서명 역할을 합니다. 이 줄은 모든 *MSSCCPRJ.SCC* 파일에서 다음과 같이 표시되어야 합니다.

 `SCC = This is a Source Code Control file`

 다음 섹션에서는 각 파일에 대한 설정을 자세히 설명하며, 파일 이름은 대괄호로 표시됩니다. 이 섹션은 추적중인 각 파일에 대해 반복됩니다. 이 줄은 파일 이름의 샘플, 즉 `[TestApp.csproj]`. IDE는 다음 두 줄을 기대합니다. 그러나 정의된 값의 스타일을 정의하지는 않습니다. 변수는 및 `SCC_Aux_Path` `SCC_Project_Name`.

 `SCC_Aux_Path = "\\server\vss\"`

 `SCC_Project_Name = "$/TestApp"`

 이 섹션에는 끝 구분 기호가 없습니다. 파일 이름과 파일에 나타나는 모든 리터럴은 scc.h 헤더 파일에 정의됩니다. 자세한 내용은 [소스 제어 플러그인을 찾기 위한 키로 사용되는 문자열을](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)참조하십시오.

## <a name="see-also"></a>참조
- [소스 제어 플러그인](../extensibility/source-control-plug-ins.md)
- [소스 제어 플러그인을 찾기 위한 키로 사용되는 문자열](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)
