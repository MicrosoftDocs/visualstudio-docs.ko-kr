---
title: 편집기 항목 템플릿을 사용 하 여 확장 만들기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 46ccdd87d44ee90c925992f4d7b997c9bbe09684
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843287"
---
# <a name="creating-an-extension-with-an-editor-item-template"></a>편집기 항목 템플릿을 사용하여 확장 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio SDK에 포함 된 항목 템플릿을 사용 하 여 편집기에 분류자, 장식 및 여백을 추가 하는 기본 편집기 확장을 만들 수 있습니다. 편집기 항목 템플릿은 Visual c # 또는 Visual Basic VSIX 프로젝트에 사용할 수 있습니다.  
  
## <a name="prerequisites"></a>전제 조건  
 Visual Studio 2015 부터는 다운로드 센터에서 Visual Studio SDK를 설치 하지 않습니다. Visual Studio 설치 프로그램에서 선택적 기능으로 포함 됩니다. VS SDK는 나중에 설치할 수도 있습니다. 자세한 내용은 [Visual STUDIO SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)를 참조 하세요.  
  
## <a name="creating-a-classifier-extension"></a>분류자 확장 만들기  
 편집기 분류자 항목 템플릿은 텍스트 파일에서 적절 한 텍스트 (이 경우 모든 항목)를 색으로 구분 하는 편집기 분류자를 만듭니다.  
  
1. **새 프로젝트** 대화 상자에서 **Visual c #** 또는 **Visual Basic** 을 확장 한 다음 **확장성**을 클릭 합니다. **템플릿** 창에서 **VSIX 프로젝트**를 선택 합니다. **이름** 상자에 `TestClassifier`을 입력합니다. **확인**을 클릭합니다.  
  
2. **솔루션 탐색기**에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 **추가/새 항목**을 선택 합니다. Visual c # **확장성** 노드로 이동 하 여 **편집기 분류자**를 선택 합니다. 기본 파일 이름 (EditorClassifier1.cs)을 그대로 둡니다.  
  
3. 다음과 같은 세 가지 코드 파일이 있습니다.  
  
    - EditorClassifier1.cs에는 클래스가 포함 되어 있습니다 `EditorClassifier1` .  
  
    - EditorClassifier1ClassificationDefinition.cs에는 클래스가 포함 되어 있습니다 `OEditorClassifier1ClassificationDefinition` .  
  
    - EditorClassifier1Format.cs에는 클래스가 포함 되어 있습니다 `EditorClassifier1Format`  .  
  
    - EditorClassifier1Provider.cs에는 클래스가 포함 되어 있습니다 `EditorClassifier1Provider` .  
  
4. 프로젝트를 빌드하고 디버깅을 시작합니다. Visual Studio의 실험적 인스턴스가 나타납니다.  
  
     텍스트 파일을 열면 모든 텍스트에 자주색 배경의 밑줄이 표시 됩니다.  
  
## <a name="creating-a-text-relative-adornment-extension"></a>텍스트 상대 장식 확장 만들기  
 편집기 텍스트 장식 템플릿은 빨간색 윤곽선과 파란색 배경이 있는 상자를 사용 하 여 텍스트 문자 ' a '의 모든 인스턴스를 데코레이팅하는 텍스트 관련 장식을 만듭니다. 상자는 이동 하거나 다시 포맷 하는 경우에도 항상 ' a ' 문자를 중첩 하므로 텍스트를 기준으로 합니다.  
  
1. **새 프로젝트** 대화 상자에서 **Visual c #** 또는 **Visual Basic** 을 확장 한 다음 **확장성**을 클릭 합니다. **템플릿** 창에서 **VSIX 프로젝트**를 선택 합니다. **이름** 상자에 `TestAdornment`을 입력합니다. **확인**을 클릭합니다.  
  
2. **솔루션 탐색기**에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 **추가/새 항목**을 선택 합니다. Visual c # **확장성** 노드로 이동 하 여 **편집기 텍스트 장식**을 선택 합니다. 기본 파일 이름 (TextAdornment1.cs/vb)을 그대로 둡니다.  
  
3. 다음과 같은 두 가지 코드 파일이 있습니다.  
  
    - TextAdornment1.cs에는 클래스가 포함 되어 있습니다 `TextAdornment1` .  
  
    - extAdornment1TextViewCreationListener.cs에는 클래스가 포함 되어 있습니다 `TextAdornment1TextViewCreationListener` .  
  
4. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험적 인스턴스가 나타납니다. 텍스트 파일을 여는 경우 텍스트의 모든 ' a ' 문자는 파란색 배경에 빨강으로 표시 됩니다.  
  
## <a name="creating-a-viewport-relative-adornment-extension"></a>뷰포트 관련 장식 확장 만들기  
 편집기 뷰포트 장식 템플릿은 뷰포트 오른쪽 위 모퉁이에 빨간색 윤곽선이 있는 자주색 상자를 추가 하는 뷰포트 관련 장식을 만듭니다.  
  
> [!NOTE]
> *뷰포트* 는 현재 표시 되는 텍스트 뷰의 영역입니다.  
  
#### <a name="to-create-a-viewport-adornment-extension-by-using-the-editor-viewport-adornment-template"></a>편집기 뷰포트 장식 템플릿을 사용 하 여 뷰포트 장식 확장을 만들려면  
  
1. **새 프로젝트** 대화 상자에서 **Visual c #** 또는 **Visual Basic** 을 확장 한 다음 **확장성**을 클릭 합니다. **템플릿** 창에서 **VSIX 프로젝트**를 선택 합니다. **이름** 상자에 `ViewportAdornment`을 입력합니다. **확인**을 클릭합니다.  
  
2. **솔루션 탐색기**에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 **추가/새 항목**을 선택 합니다. Visual c # **확장성** 노드로 이동 하 여 **편집기 뷰포트 장식**을 선택 합니다. 기본 파일 이름 (ViewportAdornment1.cs/vb)을 그대로 둡니다.  
  
3. 다음과 같은 두 가지 코드 파일이 있습니다.  
  
    - ViewportAdornment1.cs에는 클래스가 포함 되어 있습니다 `ViewportAdornment1` .  
  
    - ViewportAdornment1TextViewCreationListener.cs에는 클래스가 포함 되어 있습니다. `ViewportAdornment1TextViewCreationListener`  
  
4. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험적 인스턴스가 나타납니다. 새 텍스트 파일을 만드는 경우 뷰포트의 오른쪽 위에 빨간색 윤곽선이 있는 자주색 상자가 표시 됩니다.  
  
## <a name="creating-a-margin-extension"></a>여백 확장 만들기  
 편집기 여백 템플릿은 "Hello 세계!"와 함께 표시 되는 녹색 여백을 만듭니다. 가로 스크롤 막대 아래에 있습니다.  
  
#### <a name="to-create-a-margin-extension-by-using-the-editor-margin-template"></a>편집기 여백 템플릿을 사용 하 여 여백 확장을 만들려면  
  
1. **새 프로젝트** 대화 상자에서 **Visual c #** 또는 **Visual Basic** 을 확장 한 다음 **확장성**을 클릭 합니다. **템플릿** 창에서 **VSIX 프로젝트**를 선택 합니다. **이름** 상자에 `MarginExtension`을 입력합니다. **확인**을 클릭합니다.  
  
2. **솔루션 탐색기**에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 **추가/새 항목**을 선택 합니다. Visual c # **확장성** 노드로 이동 하 여 **편집기 뷰포트 장식**을 선택 합니다. 기본 파일 이름 (EditorMargin1.cs/vb)을 그대로 둡니다.  
  
3. 다음과 같은 두 가지 코드 파일이 있습니다.  
  
    - EditorMargin1.cs에는 클래스가 포함 되어 있습니다 `EditorMargin1` .  
  
    - EditorMargin1Factory.cs에는 클래스가 포함 되어 있습니다 `EditorMargin1Factory` .  
  
4. 이 프로젝트를 빌드하고 디버깅을 시작 합니다. 실험적 인스턴스가 나타납니다. 텍스트 파일을 열면 "Hello EditorMargin1" 라는 단어가 있는 녹색 여백이 가로 스크롤 막대 아래에 표시 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [언어 서비스 및 편집기 확장 지점](../extensibility/language-service-and-editor-extension-points.md)
