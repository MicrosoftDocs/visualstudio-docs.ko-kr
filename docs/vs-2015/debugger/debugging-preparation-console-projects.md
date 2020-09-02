---
title: '디버깅 준비: 콘솔 프로젝트 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], console applications
- debugging console applications
- console applications, debugging
ms.assetid: 9641f1d9-2d5a-48b1-8731-6525e8f67892
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5ac87f6c5ef5fcf9fc7ca5532fe7436dedb8ba97
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691210"
---
# <a name="debugging-preparation-console-projects"></a>디버깅 준비: 콘솔 프로젝트
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

콘솔 프로젝트 디버깅을 준비하는 과정은 Windows 프로젝트 디버깅을 준비하는 과정과 비슷하지만 몇 가지 사항을 추가로 고려해야 합니다. 자세한 내용은 [Windows Forms 애플리케이션](../debugger/debugging-preparation-windows-forms-applications.md) 및 [디버깅 준비: Windows Forms 애플리케이션(.NET)](https://msdn.microsoft.com/a8bc54de-41a3-464d-9a12-db9bdcbc1ad5)을 참조하세요. 콘솔 애플리케이션은 모두 비슷하므로 이 항목에서는 다음과 같은 프로젝트 형식을 다룹니다.  
  
- C# 콘솔 애플리케이션  
  
- Visual Basic 콘솔 애플리케이션  
  
- C++ 콘솔 애플리케이션(.NET)  
  
- C++ 콘솔 애플리케이션(Win32)  
  
  콘솔 애플리케이션에 대한 명령줄 인수를 지정해야 할 수도 있습니다. 자세한 내용은 [C++ 디버그 구성에 대한 프로젝트 설정](../debugger/project-settings-for-a-cpp-debug-configuration.md), [Visual Basic 디버그 구성에 대한 프로젝트 설정](../debugger/project-settings-for-a-visual-basic-debug-configuration.md) 또는 [C# 디버그 구성에 대한 프로젝트 설정](../debugger/project-settings-for-csharp-debug-configurations.md)을 참조하세요.  
  
  모든 프로젝트 속성과 마찬가지로 이러한 인수도 디버그 세션 사이와 Visual Studio 세션 사이에 지속적으로 적용됩니다. 따라서 콘솔 응용 프로그램이 이전에 디버깅 한 응용 프로그램의 경우 ** \<Project> 속성 페이지** 대화 상자에 입력 된 이전 세션의 인수가 있을 수 있습니다.  
  
  콘솔 애플리케이션은 **콘솔** 창을 사용하여 입력을 받고 출력 메시지를 표시합니다. **콘솔** 창에 출력을 표시하려면 애플리케이션에서 디버그 개체 대신 **콘솔** 개체를 사용해야 합니다. 단, **Visual Studio 출력** 창에 결과를 표시하려는 경우에는 보통 때처럼 Debug 개체를 사용합니다. 사용자는 애플리케이션에서 출력하는 위치를 정확하게 알아야 합니다. 정확한 위치를 모르면 잘못된 위치에서 메시지를 찾을 수 있습니다. 자세한 내용은 [Console 클래스](https://msdn.microsoft.com/library/system.console.aspx), [Debug 클래스](https://msdn.microsoft.com/library/system.diagnostics.debug.aspx) 및 [출력 창](../ide/reference/output-window.md)을 참조하세요.  
  
## <a name="starting-the-application"></a>애플리케이션 시작  
 일부 콘솔 애플리케이션은 시작되면 완료될 때까지 실행된 다음 종료됩니다. 이 동작은 실행을 중단하고 디버깅할 충분한 시간을 제공하지 않을 수 있습니다. 애플리케이션을 디버깅할 수 있으려면 다음 절차 중 하나를 사용하여 애플리케이션을 시작합니다.  
  
- 애플리케이션이 실행을 시작하고 중단점에 도달할 때까지 실행됩니다.  
  
- 애플리케이션이 시작되고 소스 코드의 첫째 줄에서 즉시 중단됩니다.  
  
- 소스 코드 창에서 줄을 마우스 오른쪽 단추로 클릭 하 고 **커서까지 실행**을 선택 합니다.  
  
   애플리케이션이 시작되고 선택된 줄까지 실행되거나 해당 줄 전에 중단점이 적중되는 경우 중단점까지 실행됩니다.  
  
  콘솔 애플리케이션을 디버깅할 때는 Visual Studio 대신 명령 프롬프트에서 애플리케이션을 시작하는 경우가 있을 수 있습니다. 이 경우에는 명령 프롬프트에서 애플리케이션을 시작하고 Visual Studio 디버거를 애플리케이션에 연결할 수 있습니다. 자세한 내용은 [실행 중인 프로세스에 연결](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)을 참조하세요.  
  
  Visual Studio에서 콘솔 애플리케이션을 시작하면 **콘솔** 창이 Visual Studio 창 뒤에 나타날 수도 있습니다. Visual Studio에서 콘솔 애플리케이션을 시작했는데 콘솔 창이 보이지 않으면 Visual Studio 창을 이동해 보십시오.  
  
## <a name="see-also"></a>관련 항목  
 [네이티브 코드 디버깅](../debugger/debugging-native-code.md)   
 [관리 코드 디버깅](../debugger/debugging-managed-code.md)   
 [Visual C++ 프로젝트 형식](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [C #, F # 및 Visual Basic 프로젝트 형식](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [C + + 디버그 구성에 대 한 프로젝트 설정](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [디버거 보안](../debugger/debugger-security.md)
