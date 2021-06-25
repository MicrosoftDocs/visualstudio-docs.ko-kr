---
title: MSSCCPRJ. SCC 파일 | Microsoft Docs
description: MSSCCPRJ에 대해 알아봅니다. SCC 파일은 Visual Studio SDK에서 작동하는 소스 제어 플러그 인에서 사용하는 로컬 클라이언트 쪽 파일입니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- source control plug-ins, MSSCCPRJ.SCC file
- MSSCCPRJ.SCC file
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e006e4462522f4c464f40e0656dcef4d32c85fb7
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899253"
---
# <a name="mssccprjscc-file"></a>MSSCCPRJ. SCC 파일
IDE를 사용하여 Visual Studio 솔루션 또는 프로젝트를 소스 제어 아래에 배치하면 IDE는 두 가지 주요 정보를 받습니다. 정보는 문자열 형식의 소스 제어 플러그 인에서 제공됩니다. 이러한 문자열 "AuxPath" 및 "ProjName"은 IDE에 불투명하지만 플러그 인에서 버전 제어에서 솔루션 또는 프로젝트를 찾는 데 사용됩니다. IDE는 일반적으로 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)를 호출하여 이러한 문자열을 처음 가져오고 나중에 [SccOpenProject](../extensibility/sccopenproject-function.md)를 호출하기 위해 솔루션 또는 프로젝트 파일에 저장합니다. 솔루션 및 프로젝트 파일에 포함된 경우 사용자가 버전 제어에 있는 솔루션 및 프로젝트 파일을 분기, 분기 또는 복사할 때 "AuxPath" 및 "ProjName" 문자열이 자동으로 업데이트되지 않습니다. 솔루션 및 프로젝트 파일이 버전 제어에서 올바른 위치를 가리키도록 하려면 사용자가 문자열을 수동으로 업데이트해야 합니다. 문자열은 불투명하므로 업데이트하는 방법이 항상 명확하지는 않을 수 있습니다.

 소스 제어 플러그 인은 *MSSCCPRJ.SCC* 파일이라는 특수 파일에 "AuxPath" 및 "ProjName" 문자열을 저장하여 이 문제를 방지할 수 있습니다. 플러그 인에서 소유하고 유지 관리하는 로컬 클라이언트 쪽 파일입니다. 이 파일은 소스 제어에 배치되지 않지만 소스 제어 파일이 포함된 모든 디렉터리에 대해 플러그 인에 의해 생성됩니다. 솔루션 및 프로젝트 파일을 Visual Studio 파일을 확인하기 위해 소스 제어 플러그 인은 파일 확장명과 표준 또는 사용자 제공 목록을 비교할 수 있습니다. IDE에서 플러그 인이 *MSSCCPRJ.SCC* 파일을 지원하는 것을 감지하면 "AuxPath" 및 "ProjName" 문자열을 솔루션 및 프로젝트 파일에 포함하는 것이 중단되고 *MSSCCPRJ.SCC* 파일에서 해당 문자열을 대신 읽습니다.

 *MSSCCPRJ.SCC* 파일을 지원하는 소스 제어 플러그 인은 다음 지침을 따라야 합니다.

- 디렉터리당 *하나의 MSSCCPRJ.SCC* 파일만 있을 수 있습니다.

- *MSSCCPRJ.SCC* 파일에는 지정된 디렉터리 내에서 소스 제어를 받는 여러 파일에 대한 "AuxPath" 및 "ProjName"이 포함될 수 있습니다.

- "AuxPath" 문자열에는 따옴표가 없어야 합니다. 따옴표는 구분 기호로 사용할 수 있습니다(예: 빈 문자열을 나타내는 데 큰 따옴표 쌍을 사용할 수 있음). IDE는 *MSSCCPRJ.SCC* 파일에서 읽을 때 "AuxPath" 문자열에서 모든 따옴표를 제거합니다.

- MSSCCPRJ의 "ProjName" *문자열입니다. SCC 파일은* 함수에서 반환된 문자열과 정확히 일치해야 `SccGetProjPath` 합니다. 함수에서 반환된 문자열에 따옴표가 있는 경우 *MSSCCPRJ.SCC* 파일의 문자열에는 따옴표가 있어야 하며 그 반대의 경우도 마찬가지입니다.

- 파일이 소스 제어에 배치되면 *MSSCCPRJ.SCC* 파일이 생성되거나 업데이트됩니다.

- *MSSCCPRJ.SCC* 파일이 삭제되면 공급자는 다음에 해당 디렉터리에 관한 소스 제어 작업을 수행할 때 다시 생성해야 합니다.

- *MSSCCPRJ.SCC* 파일은 정의된 형식을 엄격하게 따라야 합니다.

## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>MSSCCPRJ의 일러스트레이션입니다. SCC 파일 형식
 다음은 *MSSCCPRJ.SCC* 파일 형식의 샘플입니다(줄 번호는 가이드로만 제공되며 파일 본문에 포함되지 않아야 합니다).

- [줄 1] `SCC = This is a Source Code Control file`

- [줄 2]

- [줄 3] `[TestApp.sln]`

- [줄 4] `SCC_Aux_Path = "\\server\vss\"`

- [줄 5] `SCC_Project_Name = "$/TestApp"`

- [줄 6]

- [줄 7] `[TestApp.csproj]`

- [줄 8] `SCC_Aux_Path = "\\server\vss\"`

- [줄 9] `SCC_Project_Name = "$/TestApp"`

 첫 번째 줄은 파일의 용도를 명시하고 이 형식의 모든 파일에 대한 서명으로 사용됩니다. 이 줄은 모든 *MSSCCPRJ.SCC* 파일에서 다음과 같이 표시됩니다.

 `SCC = This is a Source Code Control file`

 다음 섹션에서는 대괄호로 묶은 파일 이름으로 표시된 각 파일에 대한 설정을 자세히 설명합니다. 이 섹션은 추적 중인 각 파일에 대해 반복됩니다. 이 줄은 파일 이름, 즉 의 `[TestApp.csproj]` 샘플입니다. IDE에는 다음 두 줄이 있습니다. 그러나 정의된 값의 스타일을 정의하지는 않습니다. 변수는 `SCC_Aux_Path` 및 `SCC_Project_Name` 입니다.

 `SCC_Aux_Path = "\\server\vss\"`

 `SCC_Project_Name = "$/TestApp"`

 이 섹션에는 끝 구분 기호가 없습니다. 파일 이름과 파일에 나타나는 모든 리터럴은 scc.h 헤더 파일에 정의됩니다. 자세한 내용은 [소스 제어 플러그 인을 찾기 위한 키로 사용되는 문자열을 참조하세요.](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)

## <a name="see-also"></a>참조
- [소스 제어 플러그 인](../extensibility/source-control-plug-ins.md)
- [소스 제어 플러그 인을 찾기 위한 키로 사용되는 문자열](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)
