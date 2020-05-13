---
title: 도구 창으로 확장 만들기 | 마이크로 소프트 문서
ms.date: 3/16/2019
ms.topic: conceptual
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 17f72cf130c5ff0f2d6d03ca8c460aa98ea39111
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739550"
---
# <a name="create-an-extension-with-a-tool-window"></a>도구 창을 사용하여 확장 만들기

이 절차에서는 VSIX 프로젝트 템플릿 및 사용자 **지정 도구 창** 항목 템플릿을 사용하여 도구 창을 사용하여 확장을 만드는 방법을 알아봅니다.

## <a name="prerequisites"></a>사전 요구 사항

 Visual Studio 2015부터는 다운로드 센터에서 Visual Studio SDK를 설치하지 않습니다. 시각적 스튜디오 설정에서 선택적 기능으로 포함됩니다. 나중에 VS SDK를 설치할 수도 있습니다. 자세한 내용은 [Visual Studio SDK 설치를](../extensibility/installing-the-visual-studio-sdk.md)참조하십시오.

### <a name="create-a-tool-window"></a>도구 창 만들기

1. **FirstWindow라는**VSIX 프로젝트를 만듭니다. 새 프로젝트 대화 상자에서 "vsix"를 검색하여 VSIX **프로젝트** 템플릿을 찾을 수 있습니다.

2. 프로젝트가 열리면 **MyWindow**라는 도구 창 항목 템플릿을 추가합니다. 솔루션 **탐색기에서**프로젝트 노드를 마우스 오른쪽 단추로 클릭하고**새 항목** **추가를** > 선택합니다. 새 **항목 추가** 대화 상자에서 **시각적 C#** > **확장성으로** 이동하여 **사용자 지정 도구 창을**선택합니다. 창 아래쪽의 **이름** 필드에서 도구 창 파일 이름을 *MyWindow.cs.*

3. 프로젝트를 빌드하고 디버깅을 시작합니다.

   Visual Studio의 실험 인스턴스가 나타납니다. 실험 인스턴스에 대한 자세한 내용은 [실험 인스턴스 를](../extensibility/the-experimental-instance.md)참조하십시오.

4. 실험적 인스턴스에서는**다른 Windows** **보기로** > 이동합니다.

   **MyWindow**의 메뉴 항목이 표시됩니다. 이 단추를 클릭하십시오.

   **MyWindow라는** 제목의 도구 창과 나를 클릭하라는 버튼이 **표시됩니다.**
