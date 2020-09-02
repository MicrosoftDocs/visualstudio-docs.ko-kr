---
title: 디버깅 세션에 사용할 실행 파일 대화 상자 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.exefordebug
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- executable files, specifying when debugging
- DLLs, debugging
- debugger, Executable for Debugging Session dialog box
- Executable for Debugging Session dialog box
ms.assetid: c0ddbe32-b99f-4425-acf1-f48842804f56
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c2ee71c5e23b0c5784cd2fe9b57b46fe28d41d30
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157464"
---
# <a name="executable-for-debugging-session-dialog-box"></a>디버깅 세션에 사용할 실행 파일 대화 상자
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 대화 상자는 실행 파일이 지정되지 않은 DLL을 디버깅하려고 할 때 나타납니다. Visual Studio는 DLL을 직접 시작할 수 없으며, 대신 지정된 실행 파일을 시작합니다. DLL이 실행 파일에서 호출되면 DLL을 디버깅할 수 있습니다.  
  
 **실행 파일 이름**  
 디버깅할 DLL을 호출하는 실행 파일의 경로 이름을 입력합니다.  
  
 **프로젝트에 액세스할 수 있는 URL(ATL 서버 전용)**  
 ATL 서버 DLL을 디버깅하는 경우 프로젝트를 찾을 수 있는 URL을 입력합니다.  
  
 입력한 설정은 프로젝트 속성 페이지에 저장되므로 이후 디버깅 세션에서 다시 입력할 필요가 없습니다. 설정을 변경해야 하는 경우에는 속성 페이지를 열고 값을 변경할 수 있습니다. 디버깅 세션의 실행 파일 지정에 대한 자세한 내용은 [DLL 디버깅](../debugger/how-to-debug-native-dlls.md)을 참조하세요.  
  
## <a name="see-also"></a>관련 항목  
 [Visual Studio의 디버깅](../debugger/debugging-in-visual-studio.md)
