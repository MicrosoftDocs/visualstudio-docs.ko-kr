---
title: 외부 도구 관리 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.externaltools
helpviewer_keywords:
- Create GUID tool
- RC (Resource Compiler)
- ReBase tool
- Windows NT Message Compiler
- Windows NT C++ Symbol Undecorator
- tstcon32.exe
- Type Library Generator
- Windows NT Image Binder
- tools [Visual Studio], external
- RowsetViewer tool
- utilities, external tools
- Local Test Manager
- OLE DB Rowset Viewer
- Midlc (IDL Compiler)
- ATL Trace Tool
- Odbcte32w.exe
- IDL Compiler
- HCW (Help Workshop)
- Message Compiler [Visual Studio]
- UUID Generator
- MIDL, external tools
- ErrLook tool
- MAKEHM tool
- Error lookup tool
- OLEVIEW (Object Viewer)
- Uuidgen.exe
- WebDbg tool
- OLE/COM Object Viewer
- LTM (Local Test Manager)
- ATLTraceTool.exe
- Bind tool
- Vsvars32.bat
- external tools [Visual Studio]
- ODBC Test
- Windows NT Image Rebaser
- undname.exe
- Vcspawn.exe
- ActiveX Control Test Container
- mc (Message Compiler)
- GUIDGEN tool
- Odbcte32.exe
- DisableMsg tool
- MkTypLib tool
- Help Workshop
- Resource Compiler
ms.assetid: f382fd40-a98f-4934-8c9a-5aeae881acde
caps.latest.revision: 41
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7a9ebda81f013f42aeac23c9c0a8cc5a0a41f5f0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651345"
---
# <a name="managing-external-tools"></a>외부 도구 관리
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 내에서 외부 도구를 호출할 수 있습니다. 몇 가지 기본 도구는 **도구** 메뉴에서 사용할 수 있지만 다른 실행 파일을 직접 추가할 수 있습니다.

## <a name="tools-available-on-the-visual-studio-tools-menu"></a>Visual Studio Tools 메뉴에서 사용할 수 있는 도구
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]의 **도구** 메뉴에서 다음 도구를 호출할 수 있습니다. **빠른 실행** 창에서 이름으로 호출할 수도 있습니다. 예를 들어 GuidGen.exe를 호출하려면 **GUID 만들기**를 입력합니다.

1. GUID 만들기: GUID를 생성합니다.

2. 오류 조회: 입력한 값에서 오류 메시지를 가져옵니다. 자세한 내용은 [ERRLOOK 참조](https://msdn.microsoft.com/library/6040ffc1-2355-4a45-8998-84cbcba4ca91)를 참조하세요.

3. ATL/MFC 추적 도구: ATL 및 MFC 소스에서 디버그 추적 메시지를 보여 줍니다.

4. PreEmptive Protection - Dotfuscator: .NET 프로그램을 리버스 엔지니어링에 대해 보호합니다.

5. SPY++: 프로세스, 스레드, 창 및 창 메시지를 그래픽으로 표시합니다.

6. WCF 서비스 구성 편집기: WCF 서비스에 대한 구성 설정을 만들고 수정할 수 있습니다.

> [!WARNING]
> 설치한 Visual Studio 버전과 적용한 설정 프로필에 따라 다른 외부 도구 목록이 나타날 수 있습니다. 자세한 내용은 [Visual Studio에서 개발 설정 사용자 지정](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)을 참조 하세요.

## <a name="adding-new-tools"></a>새 도구 추가
 **도구** 메뉴에 외부 도구를 추가할 수 있습니다. **외부 도구** 대화 상자를 열고 **추가**를 클릭 한 다음 정보를 입력 합니다. 예를 들어 다음 항목은 현재 Visual Studio에서 열려 있는 파일의 디렉터리를 Windows 탐색기에서 엽니다.

1. 제목: 파일 위치 열기

2. 명령: explorer.exe

3. 인수: /root, "$(ItemDir)"

## <a name="arguments-for-external-tools"></a>외부 도구의 인수
 다음 인수는 외부 도구를 시작할 때 할당되는 Visual Studio 변수입니다. 메모장 또는 Spy++ 같이 외부 도구에 대한 링크가 외부 도구 대화 상자를 사용하여 **도구** 메뉴에 나열될 수 있습니다.

> [!NOTE]
> IDE 상태 표시줄에는 활성 코드 편집기에서 삽입 지점 위치를 나타내기 위해 현재 줄과 현재 열 변수가 표시됩니다. 현재 텍스트 변수는 해당 위치에서 선택한 코드 또는 텍스트를 반환합니다.

|Name|인수|설명|
|----------|--------------|-----------------|
|항목 경로|$(ItemPath)|현재 파일의 전체 파일 이름(드라이브 + 경로 + 파일 이름)입니다.|
|항목 디렉터리|$(ItemDir)|현재 파일의 디렉터리(드라이브 + 경로)입니다.|
|항목 파일 이름|$(ItemFilename)|현재 파일의 파일 이름(파일 이름)입니다.|
|항목 확장명|$(ItemExt)|현재 파일의 파일 이름 확장명입니다.|
|현재 줄|$(CurLine)|코드 창 커서의 현재 줄 위치입니다.|
|현재 열|$(CurCol)|코드 창 커서의 현재 열 위치입니다.|
|현재 텍스트|$(CurText)|선택한 텍스트입니다.|
|대상 경로|$(TargetPath)|빌드할 항목의 전체 파일 이름(드라이브 + 경로 + 파일 이름)입니다.|
|대상 디렉터리|$(TargetDir)|빌드할 항목의 디렉터리입니다.|
|대상 이름|$(TargetName)|빌드할 항목의 파일 이름입니다.|
|대상 확장명|$(TargetExt)|빌드할 항목의 파일 이름 확장명입니다.|
|이진 디렉터리|$(BinDir)|빌드 중인 이진의 최종 위치(드라이브 + 경로)입니다. 예:** \\ . ..\My documents\visual Studio \<Version> \\<ProjectName \> \bin\debug**|
|프로젝트 디렉터리|$(ProjDir)|현재 프로젝트의 디렉터리(드라이브 + 경로)입니다.|
|프로젝트 파일 이름|$(ProjFileName)|현재 프로젝트의 파일 이름(드라이브 + 경로 + 파일 이름)입니다.|
|솔루션 디렉터리|$(SolutionDir)|현재 솔루션의 디렉터리(드라이브 + 경로)입니다.|
|솔루션 파일 이름|$(SolutionFileName)|현재 솔루션의 파일 이름(드라이브 + 경로 + 파일 이름)입니다.|

## <a name="see-also"></a>관련 항목
 [C/c + + 빌드 도구](https://msdn.microsoft.com/library/48d9daf4-6bbf-473a-8ce2-bf2923b69f80)
