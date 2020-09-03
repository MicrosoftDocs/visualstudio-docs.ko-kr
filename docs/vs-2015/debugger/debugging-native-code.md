---
title: 네이티브 코드 디버깅 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging native code
- debugging [C++], native code
- debugging [Visual Studio], native code
- native code, debugging
ms.assetid: d94eee90-7e0d-4cac-88c1-9831030daa5e
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 61ee852f75737d85604fda106b15e61dc3634899
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196415"
---
# <a name="debugging-native-code"></a>네이티브 코드 디버깅
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 단원에서는 네이티브 애플리케이션의 몇 가지 일반적인 디버깅 문제와 기술에 대해 설명합니다. 이 단원에서 설명하는 기술은 높은 수준의 기술입니다. Visual Studio 디버거를 사용 하는 메커니즘은 [디버거 로드맵](../debugger/debugger-basics.md)을 참조 하세요.  
  
## <a name="in-this-section"></a>섹션 내용  
 [방법: 최적화된 코드 디버그](../debugger/how-to-debug-optimized-code.md)  
 최적화된 코드를 디버깅하는 방법, 특히, 최적화되지 않은 프로그램 버전을 디버깅해야 하는 이유, 디버그 및 릴리스 구성에 대한 기본 최적화 설정, 최적화된 코드에서만 발생하는 버그를 찾는 방법 등에 대해 설명합니다.  
  
 [DebugBreak 및 __debugbreak](../debugger/debugbreak-and-debugbreak.md)  
 Win32 `DebugBreak` 함수에 대해 설명하고 Platform SDK의 참조 항목에 대한 링크를 제공합니다. `__debugbreak` 내장 함수도 설명합니다.  
  
 [C/C++ 어설션](../debugger/c-cpp-assertions.md)  
 어설션 문, 어설션의 작동 방식, 어설션을 사용하여 수행할 수 있는 작업(논리 오류 검색, 작업 결과 확인, 오류 조건 테스트), `_DEBUG`와의 상호 작용, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에서 지원하는 어설션 형식 등에 대해 설명합니다.  
  
 [방법: 인라인 어셈블리 코드 디버그](../debugger/how-to-debug-inline-assembly-code.md)  
 디스어셈블리 창에서 어셈블리 명령을 보는 방법과 레지스터 창에서 등록 내용을 보는 방법에 대해 간략히 설명하고 이러한 창을 소개하는 항목으로의 링크를 제공합니다.  
  
 [MFC 디버깅 기술](../debugger/mfc-debugging-techniques.md)  
 afxDebugBreak, TRACE 매크로, MFC의 메모리 누수 탐지, MFC 어설션, MFC 디버그 빌드 크기 줄이기 등의 MFC 프로그램에 대한 디버깅 기술을 소개합니다.  
  
 [CRT 디버깅 기술](../debugger/crt-debugging-techniques.md)  
 CRT 디버그 라이브러리 사용, 보고서 매크로 , malloc와 _malloc_dbg의 차이, 디버그 후크 함수 작성, CRT 디버그 힙 등의 C 런타임 라이브러리의 디버깅 기술에 대해 설명합니다.  
  
 [네이티브 코드 디버그 FAQ](../debugger/debugging-native-code-faqs.md)  
 Visual C++ 프로그램의 디버깅에 대한 질문과 대답을 제공합니다.  
  
 [COM 및 ActiveX 디버깅](../debugger/com-and-activex-debugging.md)  
 COM 및 ActiveX 디버깅에 사용할 수 있는 도구와 COM 및 ActiveX 애플리케이션 디버깅에 대한 정보를 제공합니다.  
  
 [방법: 네이티브 DLL 디버깅](../debugger/how-to-debug-native-dlls.md)  
 네이티브 코드에서 DLL 디버깅 설정 방법에 대해 설명합니다.  
  
 [방법: 삽입한 코드 디버그](../debugger/how-to-debug-injected-code.md)  
 특성을 사용하는 코드의 디버깅 방법에 대해 설명합니다. 여기에는 소스 주석을 표시하는 방법, 삽입한 코드를 보는 방법, 현재 실행 위치에서 디스어셈블리 코드를 보는 방법 등의 내용이 들어 있습니다.  
  
 [연습: 병렬 애플리케이션 디버깅](../debugger/walkthrough-debugging-a-parallel-application.md)  
 **병렬 작업** 및 **병렬 스택** 도구 창을 사용하여 병렬 애플리케이션을 디버깅하는 방법을 설명합니다.  
  
## <a name="related-sections"></a>관련 단원  
 [Visual C++ 프로젝트 형식](../debugger/debugging-preparation-visual-cpp-project-types.md)  
 Visual C++ 프로젝트 템플릿으로 만든 기본 프로젝트 형식의 디버깅 방법에 대한 링크를 제공합니다.  
  
 [Visual Studio의 디버깅](../debugger/debugging-in-visual-studio.md)  
 자세한 디버깅 설명서 단원으로 연결되는 링크를 제공합니다. 이러한 정보에는 디버거의 새로운 기능, 설정 및 준비, 중단점, 예외 처리, 편집하며 계속하기, 관리 코드 디버깅, 네이티브 코드 디버깅, SQL 디버깅, 사용자 인터페이스 참조 등이 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [디버거 보안](../debugger/debugger-security.md)   
 [Visual Studio의 디버깅](../debugger/debugging-in-visual-studio.md)
