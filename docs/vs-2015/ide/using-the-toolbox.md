---
title: 도구 상자 사용 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.chooseitems
- vs.toolboxpages.activexcontrols
- VS.CHOOSEITEMS.windowsuixamlcomponents
- VS.chooseitems.silverlightcomponents
- VC.EDITORS.RIBBON
- vs.customizetoolbox
- VS.chooseitems.System.Workflow_Components
- vs.chooseitems.frameworkcomponents
- VS.ToolboxPages..NET_Framework_Components
- VS.chooseitems.Microsoft.VisualStudio.Toolbox.VsToolboxPage
- vs.chooseitems.comcomponents
- vs.toolboxpages.NGWS_components
helpviewer_keywords:
- toolbox, adding items
- Visual Studio, toolbox
- toolbox, tabs
- toolbox
ms.assetid: 82e7cb43-4d0b-4e17-b7b0-43f96c22c3c2
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ba8a37ac9e049455ffe19314dee0e228c3c14c97
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74295600"
---
# <a name="using-the-toolbox"></a>도구 상자 사용
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

도구 상자를 사용하여 프로젝트에 컨트롤과 기타 항목을 추가할 수 있습니다. 여러 컨트롤을 사용 중인 디자이너 화면에 끌어 놓은 다음 해당 컨트롤의 크기를 조정하고 배치할 수 있습니다.

 도구 상자는 XAML 파일의 디자이너 보기와 같은 디자이너 보기와 함께 나타납니다. 현재 디자이너에서 사용할 수 있는 컨트롤만 도구 상자에 표시됩니다.

 프로젝트의 대상 .NET Framework 버전도 도구 상자에 표시되는 컨트롤 집합에 영향을 줍니다. 기본적으로 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 프로젝트는 .NET Framework 4.5.1을 대상으로 합니다. **솔루션 탐색기**에서 프로젝트 노드를 선택한 다음 **속성/애플리케이션/대상 프레임워크**로 이동하여 다른 .NET Framework 버전을 대상으로 하도록 프로젝트를 설정할 수 있습니다.

## <a name="managing-the-toolbox-and-its-controls"></a>도구 상자 및 해당 컨트롤 관리
 기본적으로 도구 상자는 Visual Studio IDE 왼쪽에 축소되어 있으며 커서를 위로 이동하면 표시됩니다. 도구 상자 도구 모음의 **핀** 아이콘을 클릭하여 도구 상자를 고정하면 커서를 이동해도 도구 상자가 열린 상태로 유지됩니다. 도구 상자 창의 도킹을 해제하고 화면의 원하는 위치로 끌어 올 수도 있습니다. 도구 상자 도구 모음을 마우스 오른쪽 단추로 클릭하고 옵션 중 하나를 선택하여 도구 상자를 도킹 및 도킹 해제하고 숨길 수 있습니다.

 상황에 맞는 메뉴에서 다음 명령을 사용하여 도구 상자 탭의 항목을 다시 정렬하거나 사용자 지정 탭과 항목을 추가할 수 있습니다.

- **항목 이름 바꾸기** -선택한 항목의 이름을 바꿉니다.

- **모두 표시** - 현재 디자이너에 적용된 컨트롤뿐 아니라 사용 가능한 모든 컨트롤을 표시합니다.

- **목록 보기** - 세로 목록에 컨트롤을 표시합니다. 선택을 취소하면 컨트롤이 가로로 표시됩니다.

- **항목 선택** - **도구 상자**에 표시되는 항목을 지정할 수 있도록 **도구 상자 항목 선택** 대화 상자를 엽니다. 확인란을 선택하거나 선택을 취소하여 항목을 표시하거나 숨길 수 있습니다.

- **항목 사전순 정렬** -이름을 기준으로 항목을 정렬 합니다.

- **도구 모음 다시 설정** -기본 도구 상자 설정 및 항목을 복원 합니다.

- **탭 추가** -새 도구 상자 탭을 추가 합니다.

- **위로 이동** - 선택한 항목을 위로 이동합니다.

- **아래로 이동** - 선택한 항목을 아래로 이동합니다.

## <a name="creating-and-distributing-custom-toolbox-controls"></a>사용자 지정 도구 상자 컨트롤 만들기 및 배포
 Visual Basic 또는 Visual C#에서 사용자 지정 도구 상자 컨트롤을 만들 수 있으며, [Windows Presentation Foundation](../extensibility/creating-a-wpf-toolbox-control.md) 또는 [Windows Forms](../misc/how-to-create-a-toolbox-control-that-uses-windows-forms.md)를 기반으로 하는 프로젝트 템플릿으로 시작할 수도 있습니다. 그런 후에 [도구 상자 컨트롤 설치 관리자](http://www.unicode.org/versions/Unicode5.2.0/ch04.pdf)를 사용하여 컨트롤을 팀원에게 배포하거나 웹에 게시할 수 있습니다.
