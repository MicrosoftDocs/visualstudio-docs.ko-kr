---
title: VSIX 프로젝트 템플릿 시작 하기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cc3f461c9e7dbdea1fd8481594292a0a247d2173
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204293"
---
# <a name="getting-started-with-the-vsix-project-template"></a>VSIX 프로젝트 템플릿 시작
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSIX 프로젝트 템플릿을 사용 하 여 확장을 만들거나 배포를 위한 기존 확장을 패키지할 수 있습니다. VSIX 프로젝트 템플릿에는 Visual Basic 및 Visual c # 버전이 모두 있으며 Visual Studio SDK의 일부로 설치 됩니다.  
  
 VSIX 프로젝트 템플릿은 제공 된 확장 및 자산에 대 한 정보를 포함 하는 source.extension.vsixmanifest 파일로 구성 됩니다.  
  
 VSIX 프로젝트 템플릿을 찾으려면 Visual Studio SDK를 설치 해야 합니다. 자세한 내용은 [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md)를 참조 하세요.  
  
## <a name="deploying-a-custom-project-template-using-the-vsix-project-template"></a>VSIX 프로젝트 템플릿을 사용 하 여 사용자 지정 프로젝트 템플릿 배포  
 다음 단계에서는 VSIX 프로젝트를 사용 하 여 다른 개발자와 공유할 수 있는 프로젝트 템플릿을 패키지 하거나 Visual Studio 갤러리에 업로드 하는 방법을 보여 줍니다.  
  
1. 프로젝트 템플릿을 만듭니다.  
  
    1. 템플릿을 만들 프로젝트를 엽니다. 이 프로젝트는 모든 프로젝트 형식일 수 있습니다.  
  
    2. **파일** 메뉴에서 **템플릿 내보내기**를 클릭합니다. 마법사의 단계를 완료 합니다.  
  
         .Zip 파일 은%USERPROFILE%\My Documents\Visual Studio *\<version>* \My 내보낸 템플릿에서 생성 됩니다 \\ .  
  
2. 빈 VSIX 프로젝트를 만듭니다.  
  
     **파일** 메뉴에서 **새로 만들기**를 클릭하고 **프로젝트**를 클릭합니다. **Visual Basic** 또는 **Visual c #** 중 하나를 선택 합니다. 선택한 노드 아래에서 **확장성**을 선택한 다음 **VSIX 프로젝트**를 선택 합니다.  
  
3. 프로젝트에 .zip 파일을 추가 합니다. **출력 디렉터리로 복사** 속성을로 설정 `Copy Always` 합니다.  
  
4. **솔루션 탐색기**에서 파일을 두 번 클릭 `source.extension.vsixmanifest` 하 여 **VSIX 매니페스트 디자이너**에서 파일을 연 후 다음과 같이 변경 합니다.  
  
    - **제품 이름** 필드를 **내 프로젝트 템플릿으로**설정 합니다.  
  
    - **PRODUCT ID** 필드를 **myprojecttemplate-1**로 설정 합니다.  
  
    - **Author** 필드를 **Fabrikam**으로 설정 합니다.  
  
    - **설명** 필드를 **내 프로젝트 템플릿으로**설정 합니다.  
  
    - **자산** 섹션에서 **VisualStudio** 형식을 추가 하 고 해당 경로를 .zip 파일의 이름으로 설정 합니다.  
  
5. Source.extension.vsixmanifest 파일을 저장 하 고 닫습니다.  
  
6. 프로젝트를 빌드합니다.  
  
7. 출력 디렉터리에서 .vsix 파일을 두 번 클릭 합니다.  
  
8. **VSIX 설치 관리자** 메시지 상자가 나타납니다. 지침에 따라 확장을 설치 합니다.  
  
9. Visual Studio를 닫고 다시 엽니다.  
  
10. **도구** 메뉴에서 **확장 및 업데이트** 를 선택 하 고 **템플릿** 범주를 선택 합니다. 사용 가능한 확장 중 하나는 **내 프로젝트 템플릿**이어야 합니다.  
  
11. 새 프로젝트 템플릿이 원본 프로젝트 템플릿과 동일한 위치의 **새** 프로젝트 대화 상자에 나타납니다. 예를 들어 Visual Basic 콘솔 응용 프로그램에서 **Vb console** 이라는 템플릿을 만든 경우 **vb 콘솔** 은 Visual Basic **콘솔 응용 프로그램** 템플릿과 동일한 창에 표시 됩니다.  
  
#### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>새 프로젝트 대화 상자에서 템플릿의 위치를 지정 하려면  
  
1. 템플릿 폴더는 *Visual Studio 설치 경로*\Common7\IDE\ProjectTemplates 및 *Visual studio 설치 경로*\Common7\IDE\ItemTemplates 디렉터리에 있습니다. 새 프로젝트 대화 상자의 최상위 섹션 이름이 템플릿 폴더의 이름과 정확 하 게 일치 하지 않습니다. 서로 다른 위치에서 템플릿 폴더의 이름을 사용 합니다.  
  
     .Vsix 파일 확장명을 .zip으로 변경한 다음 파일을 엽니다.  
  
2. 새 프로젝트 대화 상자의 섹션과 같은 이름으로 새 폴더를 만듭니다.  
  
3. 템플릿이 하위 섹션에 표시 되는 경우 동일한 이름의 하위 폴더를 만듭니다.  
  
4. 템플릿 .zip 파일을 새 폴더로 이동 합니다.  
  
5. .Zip 확장명을 .vsix로 변경 합니다.  
  
6. VSIX 매니페스트를 엽니다.  
  
7. VSIX 매니페스트에서 템플릿 파일을 포함 하는 디렉터리 트리의 루트를 가리키도록 템플릿의 **자산** 경로를 업데이트 합니다. 예를 들어 템플릿이 \CSharp\Windows에 있는 경우 참조는 \CSharp.을 가리켜야 합니다.
