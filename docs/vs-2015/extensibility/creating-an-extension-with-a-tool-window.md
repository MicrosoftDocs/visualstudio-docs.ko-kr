---
title: 도구 창을 사용 하 여 확장 만들기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 94c8335b8d723ef20c04cfffe6b3788d71ecaa4f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62431851"
---
# <a name="creating-an-extension-with-a-tool-window"></a>도구 창으로 확장 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 절차에서는 VSIX 프로젝트 템플릿 및 **사용자 지정 도구 창** 항목 템플릿을 사용 하 여 도구 창을 사용 하 여 확장을 만드는 방법에 대해 알아봅니다.  
  
## <a name="prerequisites"></a>사전 준비 사항  
 Visual Studio 2015 부터는 다운로드 센터에서 Visual Studio SDK를 설치 하지 않습니다. Visual Studio 설치 프로그램에서 선택적 기능으로 포함 됩니다. VS SDK는 나중에 설치할 수도 있습니다. 자세한 내용은 [Visual STUDIO SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)를 참조 하세요.  
  
### <a name="creating-a-tool-window"></a>도구 창 만들기  
  
1. **Firstwindow**라는 VSIX 프로젝트를 만듭니다. **새 프로젝트** 대화 상자의 **Visual c #/확장성**에서 VSIX 프로젝트 템플릿을 찾을 수 있습니다.  
  
2. 프로젝트가 열리면 **firstwindow**라는 도구 창 항목 템플릿을 추가 합니다. **솔루션 탐색기**에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 **추가/새 항목**을 선택 합니다. **새 항목 추가** 대화 상자에서 **Visual c #/확장성** 으로 이동 하 고 **사용자 지정 도구 창**을 선택 합니다. 창 맨 아래에 있는 **이름** 필드에서 도구 창 파일 이름을 **FirstWindow.cs**로 변경 합니다.  
  
3. 프로젝트를 빌드하고 디버깅을 시작합니다.  
  
     Visual Studio의 실험적 인스턴스가 나타납니다. 실험적 인스턴스에 대 한 자세한 내용은 [실험적 인스턴스](../extensibility/the-experimental-instance.md)를 참조 하세요.  
  
4. 실험적 인스턴스에서 **보기/기타 창**으로 이동 합니다.  
  
     **Firstwindow**의 메뉴 항목이 표시 됩니다. 이 단추를 클릭하십시오.  
  
     **창 제목 firstwindow** **Click Me!** 라는 단추가 있는 도구 창이 표시 됩니다.
