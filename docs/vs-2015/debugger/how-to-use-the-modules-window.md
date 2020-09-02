---
title: '방법: 모듈 창 사용 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.modules
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
- debugger, Modules window
- Modules window
- executable files, displaying while debugging
- debugging [Visual Studio], displaying modules
- DLLs, displaying while debugging
- modules, displaying
ms.assetid: d840fdca-b035-4452-b652-72580c831896
caps.latest.revision: 41
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b592515692e23dce49c125c7895bd158904b653f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696121"
---
# <a name="how-to-use-the-modules-window"></a>방법: 모듈 창 사용
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

참고]
> SQL 또는 스크립트 디버깅에는 이 기능을 사용할 수 없습니다.  
  
 **모듈** 창에는 프로그램에서 사용 하는 DLL 및 EXE가 나열 되며 각 dll에 대 한 관련 정보가 표시 됩니다.  
  
### <a name="to-display-the-modules-window-in-break-mode-or-in-run-mode"></a>중단 모드 또는 실행 모드에서 모듈 창을 표시하려면  
  
- **디버그** 메뉴에서 **창**을 선택한 다음 **모듈**을 클릭 합니다.  
  
     기본적으로 **모듈** 창에서는 모듈이 로드 순서대로 정렬됩니다. 그러나 열을 기준으로 정렬할 수도 있습니다.  
  
### <a name="to-sort-by-any-column"></a>열별로 정렬하려면  
  
- 정렬 기준이 될 열 맨 위에 있는 단추를 클릭합니다.  
  
     바로 가기 메뉴를 사용 하 여 **모듈** 창에서 기호를 로드 하거나 기호 경로를 지정할 수 있습니다.  
  
## <a name="loading-symbols"></a>기호 로드  
 **모듈** 창에서 디버깅 기호가 로드 된 모듈을 확인할 수 있습니다. 이 정보는 **기호 상태** 열에 표시 됩니다. 상태가 **loadingCannot에서 PDB 파일을 찾거나 열기**또는 **포함/제외로 로드 사용 안 함으로 설정**된 경우 디버거를 사용 하 여 Microsoft 공용 기호 서버에서 기호를 다운로드 하거나 컴퓨터의 기호 디렉터리에서 기호를 로드할 수 있습니다. 자세한 내용은 [기호 (.pdb) 및 소스 파일 지정](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) 을 참조 하세요.  
  
#### <a name="to-load-symbols-manually"></a>기호를 수동으로 로드하려면  
  
1. **모듈** 창에서 기호가 로드 되지 않은 모듈을 마우스 오른쪽 단추로 클릭 합니다.  
  
2. 다음 **에서 기호 로드** 를 가리킨 다음 **Microsoft 기호 서버** 또는 **기호 경로**를 클릭 합니다.  
  
#### <a name="to-change-symbol-load-settings"></a>기호 로드 설정을 변경하려면  
  
1. **모듈** 창에서 모듈을 마우스 오른쪽 단추로 클릭합니다.  
  
2. **기호 설정**을 클릭 합니다.  
  
     이제 [기호 위치 및 로드 동작 지정](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior)에 설명 된 대로 기호 로드 설정을 변경할 수 있습니다. 디버깅 세션을 다시 시작할 때까지 변경 내용이 적용되지 않습니다.  
  
#### <a name="to-change-symbol-load-behavior-for-a-specific-module"></a>특정 모듈에 대한 기호 로드 동작을 변경하려면  
  
1. **모듈** 창에서 모듈을 마우스 오른쪽 단추로 클릭합니다.  
  
2. **자동 기호 로드 설정** 을 가리킨 다음 **항상 수동 로드** 또는 **기본값**을 클릭 합니다. 디버깅 세션을 다시 시작할 때까지 변경 내용이 적용되지 않습니다.  
  
## <a name="see-also"></a>관련 항목  
 [실행 중단](https://msdn.microsoft.com/30fc4643-f337-4651-b1ff-f2de2c098d40)   
 [디버거에서 데이터 보기](../debugger/viewing-data-in-the-debugger.md)   
 [기호 파일(.pdb) 및 원본 파일 지정](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
