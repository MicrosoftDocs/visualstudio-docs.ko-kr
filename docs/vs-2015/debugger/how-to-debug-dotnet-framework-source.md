---
title: '방법: 디버그 .NET Framework 소스 | Microsoft Docs'
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
- debugging, .NET Framework source
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 49b13b8406dc96e8e7ebe5e79e26c5da02e8a53a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205438"
---
# <a name="how-to-debug-net-framework-source"></a>방법: .NET Framework 소스 디버깅
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

최신 버전의에서는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 디버깅을 위한 새로운 기능을 제공 합니다 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]소스를 디버깅 하려면 코드에 대 한 디버깅 기호에 액세스할 수 있어야 합니다. 또한 소스를 한 단계씩 실행 하도록 설정 해야 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 합니다.  
  
 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] **옵션** 대화 상자에서 단계별 실행 및 기호 다운로드를 사용 하도록 설정할 수 있습니다. 기호 다운로드를 설정할 때 기호를 즉시 다운로드할 수도 있고 나중에 다운로드하도록 옵션만 설정해 놓을 수도 있습니다. 기호를 즉시 다운로드하지 않으면 기호는 다음 번에 애플리케이션 디버깅을 시작할 때 다운로드됩니다. **모듈** 창 또는 **호출 스택** 창에서 수동으로 다운로드할 수도 있습니다.  
  
### <a name="to-enable-net-framework-source-debugging"></a>.NET Framework 소스 디버깅을 사용하려면  
  
1. **도구** 메뉴에서 **옵션**을 클릭합니다.  
  
2. **옵션** 대화 상자에서 **디버깅** 범주를 클릭 합니다.  
  
3. **일반** 상자에서 **사용 .NET Framework** 원본 단계별 실행을 설정 합니다.  
  
    1. 내 코드만을 사용하는 경우에는 내 코드만을 이제 사용하지 않는다는 경고 대화 상자가 표시됩니다. **확인**을 클릭합니다.  
  
    2. 기호 캐시 위치가 설정되어 있지 않으면 기본 기호 캐시 위치가 이제 설정된다는 또 다른 경고 대화 상자가 표시됩니다. **확인**을 클릭합니다.  
  
4. **디버깅** 범주 아래에서 **기호**를 클릭 합니다.  
  
5. 기호 캐시 위치를 변경하려면:  
  
    1. 왼쪽 상자에서 **디버깅** 노드를 엽니다.  
  
    2. **디버깅** 노드 아래에서 **기호**를 클릭 합니다.  
  
    3. 기호 **서버에서이 디렉터리로 기호 캐시** 의 위치를 편집 하거나 **찾아보기** 를 클릭 하 여 위치를 선택 합니다.  
  
6. 기호를 즉시 다운로드 하려면 **위의 위치를 사용 하 여 기호 로드**를 클릭 합니다.  
  
     이 단추는 디자인 모드에서 사용할 수 없습니다.  
  
     지금 기호를 다운로드하도록 선택하지 않으면 다음 번 프로그램 디버깅을 시작할 때 기호가 자동으로 다운로드됩니다.  
  
7. **확인**을 클릭하여 **옵션** 대화 상자를 닫습니다.  
  
### <a name="to-load-framework-symbols-using-the-modules-window"></a>모듈 창을 사용하여 Framework 기호를 로드하려면  
  
1. **모듈** 창에서 기호가 로드 되지 않은 모듈을 마우스 오른쪽 단추로 클릭 합니다. 기호 **상태** 열을 보면 기호가 로드 되었는지 여부를 알 수 있습니다.  
  
2. 기호 **로드** 를 가리킨 다음 microsoft 공용 기호 서버에서 기호를 다운로드 하 여 microsoft 공용 기호 서버에서 기호를 다운로드 하거나 기호 **경로** **를 클릭 하** 여 이전에 기호를 저장 한 디렉터리에서 로드 합니다.  
  
### <a name="to-load-framework-symbols-using-the-call-stack-window"></a>호출 스택 창을 사용하여 Framework 기호를 로드하려면  
  
1. **호출 스택** 창에서 기호가 로드 되지 않은 프레임을 마우스 오른쪽 단추로 클릭 합니다. 프레임이 흐리게 표시됩니다.  
  
2. 다음 **에서 기호 로드** 를 가리킨 다음 **Microsoft 기호 서버** 또는 **기호 경로**를 클릭 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [관리 코드 디버깅](../debugger/debugging-managed-code.md)   
 [기호 파일(.pdb) 및 원본 파일 지정](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
