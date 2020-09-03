---
title: '방법: 프로젝트 템플릿 만들기 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ExportTemplateWizard
helpviewer_keywords:
- Visual Studio templates, creating project templates
- project templates, metadata files
- Visual Studio templates, project templates
- project templates, custom template locations
- project templates, creating
ms.assetid: a1a6999d-a34c-48a8-b1cf-027eb5c76398
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f358d5b95349fe99b2a2e01df5158d2c0aa10a11
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668047"
---
# <a name="how-to-create-project-templates"></a>방법: 프로젝트 템플릿 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 절차에서는 템플릿을 .zip 파일로 패키징하는 **템플릿 내보내기** 마법사를 사용하여 템플릿을 만들 수 있습니다. 템플릿 내보내기 마법사 확장을 사용하거나 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]에 포함된 템플릿을 사용하여 개선된 배포를 위한 VSIX 파일 형식으로 템플릿을 만들 수 있고 템플릿을 수동으로 만들 수도 있습니다.

### <a name="to-create-a-custom-project-template-with-the-standard-export-template-wizard"></a>표준 템플릿 내보내기 마법사를 사용하여 사용자 지정 프로젝트 템플릿을 만들려면

1. 프로젝트를 만듭니다.

    > [!NOTE]
    > 템플릿의 소스로 사용할 프로젝트의 이름을 지정할 때 유효한 식별자 문자만 사용하세요. 잘못된 문자로 이름이 지정된 프로젝트에서 내보낸 템플릿은 템플릿을 기반으로 하는 이후 프로젝트에서 컴파일 오류를 일으킬 수 있습니다. 유효한 식별자 문자에 대한 자세한 내용은 [선언 요소 이름](https://msdn.microsoft.com/library/09d8843b-c0dc-4afe-9dab-87c439a69e66)을 참조하세요.

2. 템플릿으로 내보낼 준비가 될 때까지 프로젝트를 편집합니다.

3. 해당하는 경우 매개 변수를 대체해야 하는 위치를 나타내도록 코드 파일을 편집합니다. 매개 변수 대체에 대한 자세한 내용은 [방법: 템플릿 매개 변수 대체](../ide/how-to-substitute-parameters-in-a-template.md)를 참조하세요.

4. **파일** 메뉴에서 **템플릿 내보내기**를 클릭합니다. **템플릿 내보내기** 마법사가 열립니다.

5. **프로젝트 템플릿**을 클릭합니다.

6. 현재 솔루션에 프로젝트가 두 개 이상 있으면 템플릿으로 내보낼 프로젝트를 선택합니다.

7. **다음**을 클릭합니다.

8. 템플릿에 대한 아이콘 및 미리 보기 이미지를 선택합니다. 이러한 항목은 **새 프로젝트** 대화 상자에 나타납니다.

9. 템플릿 이름 및 설명을 입력합니다.

10. **마침**을 클릭합니다. 프로젝트는 .zip 파일로 내보내고 지정된 출력 위치에 배치되며 선택할 경우 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]로 가져옵니다.

     [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]를 설치한 경우 **VSIX 프로젝트** 템플릿을 사용하여 완료된 템플릿을 .vsix 파일로 래핑하여 배포할 수 있습니다. 자세한 내용은 [VSIX 프로젝트 템플릿 시작](../extensibility/getting-started-with-the-vsix-project-template.md)을 참조 하세요.

## <a name="see-also"></a>관련 항목
 [프로젝트 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md) [방법: 항목 템플릿 만들기](../ide/how-to-create-item-templates.md)
