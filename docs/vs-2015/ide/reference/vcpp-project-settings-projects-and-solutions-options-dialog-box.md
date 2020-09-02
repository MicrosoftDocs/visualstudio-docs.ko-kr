---
title: VC++ 프로젝트 설정, 프로젝트 및 솔루션, 옵션 대화 상자 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.VCBuild
helpviewer_keywords:
- builds [Visual Studio], logs
- build process [C++]
- files [Visual Studio], built by C/C++ compiler
- file extensions, built by C or C++ compiler
- cl.exe compiler, file extensions
- extensions, files built by C or C++ compiler
- BuildLog.htm
ms.assetid: 56420efd-6a95-464e-b890-e2b38c48d66a
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ef861d13387c013659e5e4c1714680b71896858c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657859"
---
# <a name="vc-project-settings-projects-and-solutions-options-dialog-box"></a>옵션 대화 상자, 프로젝트 및 솔루션, VC++ 프로젝트 설정
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

이 대화 상자를 사용하면 빌드 로깅 및 지원 파일 형식과 관련된 [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] 프로젝트 설정을 정의할 수 있습니다.

### <a name="to-access-this-dialog-box"></a>이 대화 상자에 액세스하려면

1. **도구** 메뉴에서 **옵션**을 클릭합니다.

2. **프로젝트 및 솔루션**을 선택한 다음 **VC++ 프로젝트 설정**을 선택합니다.

## <a name="build-customization-search-path"></a>빌드 사용자 지정 검색 경로
 프로젝트에 대한 빌드 규칙을 정의하는 데 도움이 되는 .rules 파일을 포함하는 디렉터리 목록을 지정합니다.

## <a name="build-logging"></a>빌드 로깅
 **예** 빌드 로그 파일의 생성을 설정 합니다. 이 옵션은 프로젝트의 중간 파일 디렉터리에서 찾을 수 있는 BuildLog.htm을 생성합니다. 모든 최신 빌드는 이전 BuildLog.htm 파일을 덮어씁니다.

 **아니요** 빌드 로그 파일의 생성을 해제 합니다.

## <a name="build-timing"></a>빌드 타이밍
 **예** 빌드 타이밍을 설정 합니다. 이 옵션을 선택하면 빌드가 완료되는 데 걸리는 시간이 출력 창에 게시됩니다. 자세한 내용은 [출력 창](../../ide/reference/output-window.md)을 참조하세요.

 **아니요** 빌드 타이밍을 끕니다.

## <a name="extensions-to-hide"></a>숨길 확장명
 **모든 파일 표시**를 사용 설정한 경우 **솔루션 탐색기**에 표시하지 않을 파일의 파일 이름 확장명을 지정합니다.

## <a name="extensions-to-include"></a>포함할 확장명
 프로젝트로 이동할 수 있는 파일의 파일 이름 확장명을 지정합니다.

## <a name="maximum-concurrent-c-compilations"></a>최대 동시 C++ 컴파일
 병렬 C++ 컴파일에 사용할 CPU 코어의 최대 수를 지정합니다.

## <a name="show-environment-in-log"></a>로그에 환경 표시
 **예** 빌드 로그 파일에 환경 변수를 나열 합니다. 이 옵션은 [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] 프로젝트를 빌드하는 동안 모든 환경 변수를 빌드 로그 파일에 에코하도록 지정합니다.

 **아니요** 빌드 로그 파일에서 환경 변수를 제외 합니다.

## <a name="solution-explorer-mode"></a>솔루션 탐색기 모드
 **프로젝트에 파일만 표시** 프로젝트의 파일만 표시 하도록 **솔루션 탐색기** 를 구성 합니다.

 **모든 파일 표시** 프로젝트에 파일을 표시 하 고 프로젝트 폴더의 디스크에 파일을 표시 하도록 **솔루션 탐색기** 를 구성 합니다.

## <a name="see-also"></a>관련 항목
 [C/c + + 프로그램 빌드](https://msdn.microsoft.com/library/fa6ed4ff-334a-4d99-b5e2-a1f83d2b3008) [c/c + + 빌드 참조](https://msdn.microsoft.com/library/100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d)
