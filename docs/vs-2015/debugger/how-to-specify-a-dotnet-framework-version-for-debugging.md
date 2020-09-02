---
title: '방법: 디버깅을 위한 .NET Framework 버전 지정 | Microsoft Docs'
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
- .NET Framework, specifying version for debugging
- debugging [Visual Studio], specifying .NET Framework version
ms.assetid: 7a4893ba-4620-4774-893f-378d4ca28893
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4c785c419ead31ad90e2b20ae7f48af778598bb6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176564"
---
# <a name="how-to-specify-a-net-framework-version-for-debugging"></a>방법: 디버깅을 위한 .NET Framework 버전 지정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 디버거는 현재 버전을 비롯하여 이전 버전의 Microsoft [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 디버깅을 지원합니다. Visual Studio에서 애플리케이션을 시작하는 경우 디버거는 디버깅하려는 애플리케이션에 대한 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 버전을 항상 올바르게 식별할 수 있습니다. 응용 프로그램이 이미 실행 중이 고 **에 연결**을 사용 하는 경우 디버거는 이전 버전의를 항상 식별 하지 못할 수 있습니다 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . 이러한 문제가 발생하면 다음과 같은 오류 메시지가 표시됩니다.  
  
 디버거가 애플리케이션에서 사용하는 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 버전을 잘못 예상했는지 확인합니다.  
  
 드물기는 하지만 이러한 문제가 발생하면 레지스트리 키를 설정하여 디버거에 사용하려는 버전을 지정할 수 있습니다.  
  
### <a name="to-specify-a-net-framework-version-for-debugging"></a>디버깅을 위한 .NET Framework 버전을 지정하려면  
  
1. Windows\Microsoft.NET\Framework 디렉터리에서 컴퓨터에 설치되어 있는 .NET Framework의 버전을 확인합니다. 버전 번호는 다음과 비슷합니다.  
  
     `V1.1.4322`  
  
     올바른 버전 번호를 확인하여 기록해 둡니다.  
  
2. **레지스트리 편집기**(regedit)를 시작합니다.  
  
3. **레지스트리 편집기**에서 HKEY_LOCAL_MACHINE 폴더를 엽니다.  
  
4. 다음으로 이동합니다. HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine\\{449EC4CC-30D2-4032-9256-EE18EB41B62B}  
  
     이 키가 없으면 마우스 오른쪽 단추로 HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine을 클릭하고 **새 키**를 클릭합니다. 새 키의 이름을 `{449EC4CC-30D2-4032-9256-EE18EB41B62B}`로 지정합니다.  
  
5. {449EC4CC-30D2-4032-9256-EE18EB41B62B}로 이동한 후 **이름** 열에서 CLRVersionForDebugging 키를 찾습니다.  
  
    1. 해당하는 키가 없으면 {449EC4CC-30D2-4032-9256-EE18EB41B62B}를 마우스 오른쪽 단추로 클릭하고 **새 문자열 값**을 클릭합니다. 그다음에 새 문자열 값을 마우스 오른쪽 단추로 클릭하고 **이름 바꾸기**를 클릭하고 `CLRVersionForDebugging`을 입력합니다.  
  
6. **CLRVersionForDebugging**을 두 번 클릭합니다.  
  
7. **문자열 편집** 상자에서 **값** 상자에 .NET Framework 버전 번호를 입력합니다. 예를 들어: V1.1.4322  
  
8. **확인**을 클릭합니다.  
  
9. **레지스트리 편집기**를 닫습니다.  
  
     디버깅을 시작할 때 여전히 오류 메시지가 표시되면 레지스트리에 버전 번호를 올바르게 입력했는지 확인합니다. 현재 사용하고 있는 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 버전이 Visual Studio에서 지원되는지 여부도 확인합니다. 현재 디버거는 .NET Framework 버전 및 이전 버전과 호환되지만 이후 버전과는 호환되지 않을 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [디버거 설정 및 준비](../debugger/debugger-settings-and-preparation.md)
