---
title: Dia2dump 샘플 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- sample applications [DIA SDK]
- Dia2dump sample [DIA SDK]
ms.assetid: 492c0893-7043-452f-a020-890a47230d20
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a817720c1ad73b666e0c9a586bb583120a2533c1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197595"
---
# <a name="dia2dump-sample"></a>Dia2dump 샘플
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dia2dump 샘플은 Visual Studio와 함께 설치 되며 Dia2dump 원본 파일을 포함 합니다. 컴파일된 실행 파일은 명령줄에서 실행 되며 전체 프로그램 데이터베이스 (.pdb) 파일의 내용을 표시 합니다.  
  
### <a name="to-install-the-sample"></a>샘플을 설치 하려면  
  
1. 시스템이 Visual Studio 설치 시작 페이지에서 설명 하는 모든 설치 요구 사항을 충족 하는지 확인 합니다.  
  
2. Visual Studio를 설치 하 고 포함 된 샘플에 대 한 모든 설치 및 설치 지침을 따릅니다.  
  
#### <a name="to-build-the-sample"></a>이 샘플을 빌드하려면  
  
1. Visual Studio에서 Dia2dump 파일을 엽니다. 필요한 경우 Visual Studio에서 먼저 Dia2dump 프로젝트를 업그레이드 하는 데 도움을 줍니다.  
  
2. 프로젝트 속성 페이지의 **C/c + +** &#124; **일반** &#124; **추가 포함 디렉터리** 속성에서 디렉터리를 지정 `..\DIA SDK\include` 합니다. 이렇게 하면 컴파일러가 dia2 파일을 찾을 수 있습니다.  
  
3. **빌드** 메뉴에서 **솔루션 다시 빌드**를 클릭합니다.  
  
4. Visual Studio를 닫습니다.  
  
#### <a name="to-run-the-sample"></a>이 샘플을 실행하려면  
  
1. 명령 프롬프트를 열고 다음을 입력 합니다.  
  
    ```  
    dia2dump filename  
    ```  
  
## <a name="see-also"></a>관련 항목  
 [Dia2dump 원본 파일](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)   
 [방법: 실패한 Visual Studio 프로젝트 업그레이드 문제 해결](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md)
