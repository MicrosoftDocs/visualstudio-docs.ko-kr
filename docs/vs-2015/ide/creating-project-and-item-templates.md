---
title: 프로젝트 템플릿 및 항목 템플릿 만들기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- templates [Visual Studio], projects
- item templates, about item templates
- templates [Visual Studio], item
- Visual Studio templates, item
- Visual Studio templates, about templates
- project templates [Visual Studio], about project templates
- Visual Studio templates, project
- templates [Visual Studio], about templates
ms.assetid: a6ce501a-699b-4e3e-ade8-c81895645c20
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 995696dafce64cdcb1fbb11d0788bbe13453c440
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72619295"
---
# <a name="creating-project-and-item-templates"></a>프로젝트 템플릿 및 항목 템플릿 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 프로젝트 및 항목 템플릿은 사용자가 자신의 용도로 사용할 수 있는 몇 가지 기본 코드와 구조를 제공 하는 재사용 가능한 스텁을 제공 합니다.

## <a name="visual-studio-templates"></a>Visual Studio 템플릿
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]를 설치할 때 미리 정의된 많은 프로젝트 템플릿과 항목 템플릿이 설치됩니다. 프로젝트 템플릿의 예로는 **새 프로젝트** 대화 상자에서 사용할 수 있는 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 및 [!INCLUDE[csprcs](../includes/csprcs-md.md)] Windows Forms 애플리케이션 및 클래스 라이브러리 템플릿이 있습니다. 설치된 항목 템플릿은 **새 항목 추가** 대화 상자에서 사용할 수 있으며 코드 파일, XML 파일, HTML 페이지 및 스타일 시트와 같은 항목을 포함합니다.

 이러한 템플릿은 사용자에게 프로젝트를 만들거나 현재 프로젝트를 확장하기 위한 시작 지점을 제공합니다. 프로젝트 템플릿은 특정 프로젝트 형식에 필요한 파일을 제공하고 표준 어셈블리 참조를 포함하며 기본 프로젝트 속성과 컴파일러 옵션을 설정합니다. 정확한 파일 확장명이 있는 하나의 빈 파일에서부터 스텁 코드가 있는 소스 코드 파일, 디자이너 정보 파일, 포함된 리소스 등이 포함된 다중 파일 항목에 이르기까지 항목 템플릿의 범위는 다양합니다.

 **새 프로젝트** 및 **새 항목 추가** 대화 상자에 설치 된 템플릿 외에도 고유한 템플릿을 작성 하거나 커뮤니티에서 만든 템플릿을 다운로드 하 여 사용할 수 있습니다. 자세한 내용은 [방법: 프로젝트 템플릿 만들기](../ide/how-to-create-project-templates.md) 및 [방법: 항목 템플릿 만들기](../ide/how-to-create-item-templates.md)를 참조 하세요.

## <a name="contents-of-a-template"></a>템플릿의 내용
 모든 프로젝트 템플릿과 항목 템플릿은 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]와 함께 설치되었는지 직접 만들었는지에 상관없이 동일한 원칙으로 작동하며 비슷한 내용으로 구성됩니다. 모든 템플릿에는 다음과 같은 항목이 포함됩니다.

- 템플릿이 사용될 때 만들어지는 파일입니다. 여기에는 소스 코드 파일, 포함 리소스, 프로젝트 파일 등이 있습니다.

- .vstemplate 파일을 엽니다. 이 파일에는 **새 프로젝트** 및 **새 항목 추가** 대화 상자에 템플릿을 표시하고 템플릿에서 프로젝트 또는 항목을 만드는 데 필요한 정보를 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에 제공하는 메타데이터가 들어 있습니다. .Vstemplate 파일에 대 한 자세한 내용은 [템플릿 매개 변수](../ide/template-parameters.md)를 참조 하세요.

  이러한 파일이 .zip 파일로 압축되어 올바른 폴더에 배치되면 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에서는 프로젝트 템플릿은 **새 프로젝트** 대화 상자의 **내 템플릿** 섹션에, 항목 템플릿은 **새 항목 추가** 대화 상자에 나타납니다. 템플릿 폴더에 대 한 자세한 내용은 [방법: 템플릿 찾기 및 구성](../ide/how-to-locate-and-organize-project-and-item-templates.md)을 참조 하세요.

## <a name="starter-kits"></a>시작 키트
 시작 키트는 커뮤니티의 다른 멤버와 공유 가능한 향상된 템플릿입니다. 시작 키트에는 유용한 실제 애플리케이션을 빌드하는 동안 새로운 도구와 프로그래밍 기술을 익히는 데 도움이 되는 컴파일할 코드 샘플, 설명서 및 기타 리소스가 포함되어 있습니다. 시작 키트에 대한 기본 내용과 절차는 템플릿에서와 동일합니다. 자세한 내용은 [방법: 시작 키트 만들기](../ide/how-to-create-starter-kits.md)를 참조하세요.

## <a name="see-also"></a>관련 항목
 [방법: 프로젝트 템플릿 만들기](../ide/how-to-create-project-templates.md) [방법: 항목 템플릿 만들기](../ide/how-to-create-item-templates.md) 템플릿 [매개 변수](../ide/template-parameters.md) [템플릿 사용자 지정](../ide/customizing-project-and-item-templates.md) [방법: 시작 키트 만들기](../ide/how-to-create-starter-kits.md)
