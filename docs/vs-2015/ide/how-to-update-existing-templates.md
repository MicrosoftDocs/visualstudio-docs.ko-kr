---
title: '방법: 기존 템플릿 업데이트 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- item templates, updating existing templates
- Visual Studio templates, updating existing templates
- project templates, updating existing templates
ms.assetid: d585e45b-7fe2-45fa-9cf3-7f2bc060f3c4
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4b56cf11057957b0eb99fc065ed26af10d8adfbd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670580"
---
# <a name="how-to-update-existing-templates"></a>방법: 기존 템플릿 업데이트
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

템플릿을 만들고 파일을 .zip 파일로 압축한 후 템플릿을 수정하려고 할 수 있습니다. 템플릿의 파일을 수동으로 변경하거나 해당 템플릿을 기반으로 하는 프로젝트에서 새 템플릿을 내보내는 방법으로 이 작업을 수행할 수 있습니다.

## <a name="using-the-export-template-wizard-to-update-an-existing-template"></a>템플릿 내보내기 마법사를 사용하여 기존 템플릿 업데이트
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에서는 기존 템플릿을 업데이트하는 데 사용할 수 있는 **템플릿 내보내기** 마법사를 제공합니다.

#### <a name="to-use-export-template-to-update-an-existing-template"></a>템플릿 내보내기를 사용하여 기존 템플릿을 업데이트하려면

1. **파일** 메뉴에서 **새로 만들기** 를 클릭한 다음 **새 프로젝트**를 클릭합니다.

2. 업데이트할 템플릿을 선택하고 임시 프로젝트의 이름과 위치를 입력한 다음, **확인**을 클릭합니다.

3. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에서 프로젝트를 수정합니다.

4. **파일** 메뉴에서 **템플릿 내보내기**를 클릭하고 **템플릿 내보내기** 마법사에서 새 템플릿을 만듭니다.

5. 업데이트된 템플릿이 .zip 파일로 압축되었으면 이전 템플릿 .zip 파일을 삭제합니다.

## <a name="manually-updating-an-existing-template"></a>기존 템플릿 수동 업데이트
 압축된 .zip 파일에 있는 파일을 수정하여 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 외부에서 기존 템플릿을 업데이트할 수 있습니다.

#### <a name="to-manually-update-an-existing-template"></a>기존 템플릿을 수동으로 업데이트하려면

1. 템플릿을 포함하는 .zip 파일을 찾습니다. 기본적으로 이 파일은 \My Documents\Visual Studio *Version*\My Exported Templates\\에 있습니다.

2. .zip 파일의 압축을 풉니다.

3. 현재 템플릿 파일을 수정 또는 삭제하거나 템플릿에 새 파일을 추가합니다.

4. .vstemplate XML 파일을 열어서 수정한 다음 저장하여 업데이트된 동작 또는 새 파일을 처리합니다. .vstemplate 스키마에 대한 자세한 내용은 [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)를 참조하세요. 소스 파일에서 매개 변수화 할 수 있는 항목에 대 한 자세한 내용은 [템플릿 매개 변수](../ide/template-parameters.md) 를 참조 하세요.

5. 템플릿에 있는 파일을 선택하고 마우스 오른쪽 단추를 클릭하고 **보내기**를 클릭한 다음, **압축(ZIP) 폴더**를 클릭합니다. 선택한 파일이 .zip 파일로 압축됩니다.

6. 새 .zip 파일을 이전 .zip 파일과 같은 디렉터리에 넣습니다.

7. 추출된 템플릿 파일과 이전 템플릿 .zip 파일을 삭제합니다.

8. 시작 메뉴의 **Visual Studio 2010/Visual Studio Tools/개발자 명령 프롬프트**에서 개발자 명령 프롬프트의 인스턴스를 시작(관리자로 실행)합니다.

9. 명령 `devenv /installvstemplates`를 실행합니다.

## <a name="see-also"></a>관련 항목
 [템플릿 사용자 지정](../ide/customizing-project-and-item-templates.md) [프로젝트 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md) [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md) [템플릿 매개 변수](../ide/template-parameters.md) [방법: 시작 키트 만들기](../ide/how-to-create-starter-kits.md)
