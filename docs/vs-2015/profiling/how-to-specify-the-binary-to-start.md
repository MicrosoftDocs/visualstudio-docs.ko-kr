---
title: '방법: 시작할 이진 파일 지정 | Microsoft 문서'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.itemlaunch
helpviewer_keywords:
- profiling tools, launching
- performance tools, launching
- performance sessions, launching
ms.assetid: ba77fcf4-8d78-49f1-b8f3-7dd0acf84306
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 919e84393cf4aef929a504aadbefe905afe24bfb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203436"
---
# <a name="how-to-specify-the-binary-to-start"></a>방법: 시작할 이진 파일 지정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DLL 같은 이진 파일을 프로파일링하려면 **\<Target> 속성 페이지** 대화 상자에 정보를 입력해야 합니다. 이 정보는 DLL 프로젝트가 호출 애플리케이션을 찾을 수 있는 위치를 나타냅니다.  
  
 **요구 사항**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
### <a name="to-specify-the-executable-to-start"></a>시작할 실행 파일을 지정하려면  
  
1. **성능 탐색기**에서 대상 이진 파일을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.  
  
2. **속성 페이지** 대화 상자에서 **시작** 속성을 클릭합니다.  
  
3. **프로젝트 속성 재정의** 확인란을 선택합니다.  
  
4. **시작할 실행 파일** 텍스트 상자에 파일 위치를 지정합니다.  
  
5. **인수** 텍스트 상자에 애플리케이션 시작에 필요한 인수를 지정합니다.  
  
6. **작업 디렉터리** 텍스트 상자에 디렉터리 위치를 지정합니다.  
  
7. **확인**을 클릭합니다.  
  
## <a name="see-also"></a>참고 항목  
 [성능 세션 구성](../profiling/configuring-performance-sessions.md)
