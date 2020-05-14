---
title: Visual Studio Tools for Unity 개요 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-unity-tools
ms.topic: overview
ms.assetid: b4231bb9-45c4-4c77-ac3c-d05033b26393
caps.latest.revision: 6
ms.author: crdun
manager: crdun
ms.openlocfilehash: ba5447301c3a5581d35825ed91c17b3c9f50015f
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "74298754"
---
# <a name="overview-of-visual-studio-tools-for-unity"></a>Visual Studio Tools for Unity 개요
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 섹션에서는 Visual Studio Tools for Unity가 제공하는 기능과 Unity를 사용하여 생산성을 높일 수 있는 방법에 대해 알아봅니다.  
  
 *VSTU*(Visual Studio Tools for Unity)를 사용하면 Visual Studio를 통해 게임 및 편집기 스크립트를 C#으로 작성한 다음 강력한 디버거를 사용하여 오류를 찾고 수정할 수 있습니다. VSTU의 최신 릴리스에는 Unity의 ShaderLab 셰이더 언어를 위한 구문 색 지정, 향상된 디버거 시각화 및 MonoBehavior 마법사에 대한 코드 생성 기능이 포함되어 있습니다. VSTU는 Unity 프로젝트 파일, 콘솔 메시지 및 Visual Studio에서 게임을 시작하는 기능도 제공하므로 코드를 작성하는 동안 Unity 편집기 전환에 소요되는 시간을 단축할 수 있습니다.  
  
 이러한 기능에 대해 자세히 알아보려면 계속 읽어보세요.  
  
## <a name="integration-with-unity"></a>Unity와의 통합  
 Unity 편집기와 Visual Studio 사이를 항상 전환해야 한다면 Visual Studio Tools for Unity는 생산성을 개선하는 데 도움이 되지 않을 것입니다. 이러한 이유로 Visual Studio Tools for Unity에서는 Visual Studio를 종료하지 않고 작업을 유지할 수 있습니다.  
  
- **Unity 프로젝트 탐색기**는 Unity 편집기에 표시된 동일한 계층 구조를 사용하여 Visual Studio 내 전체 Unity 프로젝트를 표시합니다.  
  
- Unity 콘솔 통합은 Visual Studio의 오류 창 바로 안쪽에 Unity 콘솔의 출력을 표시합니다.  
  
- Visual Studio에서 게임 디버깅을 시작하려면 Unity로 다시 전환할 필요 없이 F5 키를 누르면 됩니다.  
  
## <a name="superior-debugging"></a>뛰어난 디버깅 기능  
 독립형으로 실행되거나 Unity 편집기에서 실행되는 것에 관계없이 Visual Studio의 강력한 디버거를 Unity 게임에 연결하여 C# 스크립트 및 DLL을 디버그합니다. Visual Studio에서 기대하는 모든 디버깅 기능을 사용할 수 있습니다.  
  
- 조건부 중단점을 포함하는 중단점입니다.  
  
- 조사식 창에서 복잡한 식을 평가합니다.  
  
- 변수 및 인수 값을 조사하고 수정합니다.  
  
- 복잡한 개체 및 데이터 구조로 드릴다운합니다.  
  
  네트워크에 연결된 다른 컴퓨터에서 실행되는 동안 Unity 게임을 디버그할 수도 있습니다.  
  
## <a name="productivity"></a>생산성  
 C#에서의 코드 작성 및 리팩터링을 위한 Visual Studio의 설정된 생산성 기능 외에도 Visual Studio Tools for Unity는 Unity 개발자를 위한 추가 생산성 기능을 제공합니다.  
  
- Unity의 ShaderLab 언어에 대한 구문 색 지정을 통해 셰이더에서 실수를 발견하여 버그가 되는 것을 막을 수 있습니다. Visual Studio에서 ShaderLab 파일을 열기만 하면 됩니다.  
  
- MonoBehavior 마법사를 통해 Unity 동작의 목록을 찾아보고 익숙하지 않을 수 있는 동작에 대한 상용구 코드를 만들 수 있습니다. CTRL+SHIFT+M을 누릅니다.  
  
- 가장 많이 사용하는 Unity 동작에 익숙해지면 빠른 MonoBehavior 마법사를 언제든지 이용할 수 있습니다. CTRL+ALT+Q를 누릅니다.  
  
- Visual Studio에서 Unity 설명서에 액세스합니다. 알아보려는 API 호출을 강조 표시하고 CTRL+ALT+M, CTRL+H를 누릅니다.  
  
- 키보드 바로 가기를 사용하여 이러한 모든 기능 및 기타 항목에 액세스합니다.  
  
## <a name="visual-studio-tools-for-unity-api"></a>Visual Studio Tools for Unity API  
 제공된 API를 사용하여 Visual Studio Tools for Unity의 동작을 사용자 지정하고 확장합니다.  
  
- Visual Studio Tools for Unity에서 Unity 콘솔을 Visual Studio로 스트림할 수 있도록 로그 콜백을 등록합니다. 정보를 기록하는 편집기 스크립트가 있는 경우 동일한 콜백에 연결하여 Visual Studio에 메시지를 전송할 수 있습니다. 자세한 내용은 로그 콜백 예제를 참조하세요.  
  
- Unity 스타일 콜백 ProjectFileGeneration을 사용하여 Visual Studio Tools for Unity에서 프로젝트 파일을 생성하는 방법을 변경할 수 있습니다. 자세한 내용은 프로젝트 파일 생성 예제를 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [Unity 홈 페이지](https://unity.com/)
