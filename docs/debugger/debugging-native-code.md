---
title: 네이티브 코드 디버깅 | Microsoft Docs
ms.date: 04/11/2017
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging native code
- debugging [C++], native code
- debugging [Visual Studio], native code
- native code, debugging
ms.assetid: d94eee90-7e0d-4cac-88c1-9831030daa5e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: f98b99a31d9215d661879aa7fa52d4b671024496
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738163"
---
# <a name="debugging-native-code"></a>네이티브 코드 디버깅
이 단원에서는 네이티브 애플리케이션의 몇 가지 일반적인 디버깅 문제와 기술에 대해 설명합니다. 이 단원에서 설명하는 기술은 높은 수준의 기술입니다. Visual Studio 디버거를 사용하는 방법에 대한 자세한 내용은 [먼저 디버거 살펴보기](../debugger/debugger-feature-tour.md)를 참조하세요.

## <a name="in-this-section"></a>단원 내용
 [방법: 최적화된 코드 디버깅](../debugger/how-to-debug-optimized-code.md) 최적화된 코드를 디버깅하기 위한 팁, 특히 프로그램의 최적화되지 않은 버전을 디버깅해야 하는 이유, 디버그 및 릴리스 구성에 대한 기본 최적화 설정, 최적화된 코드에만 표시되는 버그를 찾기 위한 팁(디버그 빌드 구성의 최적화 켜기)을 제공합니다.

 [Debugbreak 및 __debugbreak](../debugger/debugbreak-and-debugbreak.md) Win32 `DebugBreak` 함수에 대해 설명하고 Platform SDK의 해당 참조 항목에 대한 링크를 제공합니다. `__debugbreak` 내장 함수도 설명합니다.

 [C/C++ 어설션](../debugger/c-cpp-assertions.md) 어설션 문에 대해 설명하고, 사용하는 방법, 사용 이점(로직 오류 포착, 작업 결과 확인 및 오류 조건 테스트), `_DEBUG`와의 상호 작용 및 Visual Studio에서 지원되는 어설션의 유형을 설명합니다.

 [방법: 인라인 어셈블리 코드 디버그](../debugger/how-to-debug-inline-assembly-code.md) 디스어셈블리 창을 사용하여 어셈블리 지침 및 레지스터 창을 보는 방법에 대한 간략한 지침을 제공하여 레지스터 내용을 확인하고 해당 창과 관련된 항목에 대한 링크를 제공합니다.

 [MFC 디버깅 기술](../debugger/mfc-debugging-techniques.md) AfxDebugBreak, TRACE 매크로, MFC의 메모리 누수 탐지, MFC 어설션, MFC 디버그 빌드의 크기 감소를 비롯하여 MFC 프로그램의 디버깅 기술에 대한 링크를 제공합니다.

 [CRT 디버깅 기술](../debugger/crt-debugging-techniques.md) CRT 디버그 라이브러리 사용, 보고용 매크로, malloc와 _malloc_dbg의 차이, 디버그 후크 함수 작성, CRT 디버그 힙 등을 비롯한 C 런타임 라이브러리에 대한 디버깅 기술에 대한 링크를 제공합니다.


[네이티브 코드 디버그 FAQ](../debugger/debugging-native-code-faqs.md) C++ 프로그램 디버깅에 대한 자주 묻는 질문에 대한 대답을 제공합니다.


 [COM 및 ActiveX 디버깅](../debugger/com-and-activex-debugging.md) Com 및 ActiveX 디버깅에 사용할 수 있는 도구를 포함하여 COM 및 ActiveX 응용 프로그램 디버깅에 대한 정보를 제공합니다.

 [방법: 삽입된 코드 디버그](../debugger/how-to-debug-injected-code.md) 특성을 사용하는 코드 디버깅에 대한 지침을 제공합니다. 여기에는 소스 주석을 표시하는 방법, 삽입한 코드를 보는 방법, 현재 실행 위치에서 디스어셈블리 코드를 보는 방법 등의 내용이 들어 있습니다.

 [연습: 병렬 응용 프로그램 디버깅](../debugger/walkthrough-debugging-a-parallel-application.md) 병렬 **작업** 및 **병렬 스택** 도구 창을 사용 하 여 병렬 응용 프로그램을 디버깅 하는 방법을 설명 합니다.

## <a name="related-sections"></a>관련 단원
 [C++ 프로젝트 디버깅 준비](../debugger/debugging-preparation-visual-cpp-project-types.md) C++ 프로젝트 템플릿에서 만든 네이티브 프로젝트 형식을 디버깅하는 방법을 설명하는 항목에 대한 링크를 제공합니다.

 [DLL 프로젝트 디버깅](../debugger/debugging-dll-projects.md) 네이티브 및 관리되는 DLL을 디버깅하는 방법에 대한 정보를 제공합니다.

 [먼저 디버거 살펴보기](../debugger/debugger-feature-tour.md). 디버깅 설명서의 더 큰 섹션에 대한 링크를 제공합니다. 이러한 정보에는 디버거의 새로운 기능, 설정 및 준비, 중단점, 예외 처리, 편집하며 계속하기, 관리 코드 디버깅, 네이티브 코드 디버깅, SQL 디버깅, 사용자 인터페이스 참조 등이 있습니다.

## <a name="see-also"></a>참조

- [디버거 보안](../debugger/debugger-security.md)
- [Visual Studio의 디버깅](../debugger/index.yml)
