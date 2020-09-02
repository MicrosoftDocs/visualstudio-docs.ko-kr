---
title: 디버거에서 소스 코드 또는 디스어셈블리를 표시할 수 없습니다. | Microsoft Docs
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
- disassembly code, errors
ms.assetid: 112d3ea3-fdd2-4bce-92b4-167a76258934
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5ce4460aecb634523de02f2e3f6929b206b415e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186503"
---
# <a name="debugger-cannot-display-source-code-or-disassembly"></a>디버거가 현재 위치에 대한 소스 코드나 디스어셈블리를 표시할 수 없습니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 오류의 의미는 다음과 같습니다.  
  
 실행이 중지된 현재 위치에 대한 소스 코드나 디스어셈블리를 디버거에서 표시할 수 없습니다.  
  
 이 오류 메시지의 원인은 다음과 같습니다.  
  
- 디스어셈블리를 지원하지 않는 언어를 디버깅하는 동안 소스 코드가 없는 위치에서 중단점이 적중되었을 수 있습니다. **중단점** 창을 열고 해당하는 중단점을 찾아서 삭제합니다.  
  
- 스크립트를 디버깅하는 경우 프로그램에 스레드가 없을 때 중단점이 적중되었을 수 있습니다. **디버그** 메뉴에서 **단계** 또는 **계속**을 선택하여 디버깅을 다시 시작합니다.  
  
- 보안상의 이유로, 디버깅하고 있는 프로그램에서 디버거가 스택, 스레드, 레지스터 및 기타 컨텍스트 정보를 읽지 못할 수 있습니다. 이러한 오류는 가상 디렉터리에 대한 올바른 액세스 권한 없이 웹 애플리케이션을 디버깅하는 경우에 발생합니다. 가상 디렉터리의 보안 권한을 Anonymous로 설정하고 다시 시도하십시오.  
  
## <a name="see-also"></a>관련 항목  
 [디버거 기본 사항](../debugger/debugger-basics.md)   
 [Visual Studio에서 디버깅](../debugger/debugging-in-visual-studio.md)   
 [디버거에서 데이터 보기](../debugger/viewing-data-in-the-debugger.md)
