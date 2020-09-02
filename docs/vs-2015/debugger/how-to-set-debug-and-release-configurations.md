---
title: '방법: 디버그 및 릴리스 구성 설정 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.builds
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- configurations, release
- build configurations, release
- projects [Visual Studio], release configurations
- debugging [Visual Studio], release configurations
- release builds, changing settings
- debug builds
- debug builds, switching to release build
- debug builds, changing configuration settings
- debugging [Visual Studio], debug configurations
- projects [Visual Studio], debug configurations
- build configurations, debug
- debug configurations
- release builds, switching to debug build
- Visual Basic projects, debug and release builds
ms.assetid: 57b6bbb7-f2af-48f7-8773-127d75034ed2
caps.latest.revision: 48
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4984355c12a92529a943fe6778740ac2d7f522f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703657"
---
# <a name="how-to-set-debug-and-release-configurations"></a>방법: 디버그 및 릴리스 구성 설정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 프로젝트에는 사용하는 프로그램에 대한 별도의 릴리스 및 디버그 구성이 있습니다. 이름이 의미하는 것처럼 디버그 버전은 디버깅용으로 빌드하고 릴리스 버전은 최종 릴리스 배포용으로 빌드합니다.  
  
 프로그램의 디버그 구성은 완전히 기호화된 디버그 정보를 사용하여 컴파일되며 최적화되지 않습니다. 최적화하면 소스 코드와 생성된 명령 간의 관계가 복잡해지므로 디버깅이 복잡해집니다.  
  
 프로그램의 릴리스 구성은 완전히 최적화되고, 기호화된 디버그 정보를 포함하지 않습니다. 사용하는 컴파일러 옵션에 따라 디버그 정보가 PDB 파일에서 생성될 수 있습니다. PDB 파일을 만들면 나중에 릴리스 버전을 디버깅해야 하는 경우 매우 유용하게 사용할 수 있습니다.  
  
 빌드 구성에 대 한 자세한 내용은 [빌드 구성 이해](../ide/understanding-build-configurations.md)를 참조 하세요.  
  
 **빌드 메뉴,** 도구 모음 또는 프로젝트의 속성 페이지에서 빌드 구성을 변경할 수 있습니다. 프로젝트 속성 페이지는 언어마다 다릅니다. 다음 절차는 메뉴 및 도구 모음에서 빌드 구성을 변경하는 방법을 보여 줍니다. 서로 다른 언어로 된 프로젝트의 빌드 구성을 변경하는 방법에 대한 자세한 내용은 아래의 관련 항목 섹션을 참조하세요.  
  
### <a name="to-change-the-build-configuration"></a>빌드 구성 변경  
  
1. 빌드 메뉴에서 **빌드/Configuration Manager**를 클릭 한 다음 **디버그** 또는 **릴리스**를 선택 합니다.  
  
2. 도구 모음의 **솔루션 구성** 목록 상자에서 **디버그** 또는 **릴리스** 를 선택 합니다.  
  
     ![도구 모음 빌드 구성](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")  
  
     이 도구 모음은 Express Edition에서 사용할 수 없습니다. **솔루션 빌드 F6** 및 **디버깅 시작 F5** 메뉴 항목을 사용 하 여 구성을 선택할 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [디버거 설정 및 준비](../debugger/debugger-settings-and-preparation.md)   
 [C + + 디버그 구성에 대 한 프로젝트 설정](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [C # 디버그 구성에 대 한 프로젝트 설정](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Visual Basic 디버그 구성에 대 한 프로젝트 설정](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [방법: 구성 만들기 및 편집](../ide/how-to-create-and-edit-configurations.md)   
 [디버그 및 릴리스 프로젝트 구성](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e)
