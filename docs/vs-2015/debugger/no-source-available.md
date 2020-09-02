---
title: 사용 가능한 소스 없음 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.nosource
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- No Source Code Available for the Current Location dialog box
ms.assetid: ed0732bc-4b8c-490f-adb1-af06869a2a6b
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 69ea9c3a41f83b9c06dc18d6da1f859017f12ca5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697804"
---
# <a name="no-source-available"></a>소스 없음
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

프로젝트에 보려고 하는 코드의 소스 코드가 포함되어 있지 않습니다. 일반적인 원인은 **호출 스택 창** 또는 **스레드 창**에서 소스 코드가 없는 모듈을 두 번 클릭했기 때문입니다. 디버깅을 계속할 수 있지만 소스 창에서 중단점을 설정하고 현재 위치에서 다른 작업을 수행할 수는 없습니다. 중단점을 설정해야 하는 경우에는 **디스어셈블리 창**을 대신 사용합니다.  
  
 솔루션 속성 페이지에서 디버거가 소스 파일을 찾는 디렉터리를 변경하거나 디버거가 선택된 소스 파일을 무시하도록 지정할 수 있습니다. [소스 파일 디버그, 공용 속성, 솔루션 속성 페이지 대화 상자](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)를 참조하세요.  
  
 **소스 코드 찾기**  
 소스 코드를 찾을 수 있는 대화 상자를 열려면 이 링크를 클릭합니다.  
  
 **디스어셈블리 표시**  
 **디스어셈블리 창**을 시작합니다.  
  
 **누락된 소스 파일에 대해 항상 디스어셈블리 표시**  
 사용 가능한 소스가 없을 때 자동으로 **디스어셈블리 창**을 표시하려면 이 옵션을 선택합니다. 이 설정은 **옵션** 대화 상자, **디버깅** 범주, **일반** 페이지에서 **소스를 사용할 수 없을 경우 디스어셈블리 표시**를 선택하거나 선택 취소하여 변경할 수도 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [솔루션 속성 페이지 대화 상자, 공용 속성, 소스 파일 디버그](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)   
 [기호 (.pdb) 및 소스 파일 지정](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [SOS.dll(SOS 디버깅 확장)](https://msdn.microsoft.com/library/9ac1b522-77ab-4cdc-852a-20fcdc9ae498)
