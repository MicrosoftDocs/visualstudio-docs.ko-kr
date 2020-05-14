---
title: 편집기 항목 템플릿으로 확장 만들기 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7ac19d99bf75c79ad011bfd0d5a56ecf3880b100
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739510"
---
# <a name="create-an-extension-with-an-editor-item-template"></a>편집기 항목 템플릿으로 확장 만들기
Visual Studio SDK에 포함된 항목 템플릿을 사용하여 분류자, 장식 및 여백을 편집기에 추가하는 기본 편집기 확장을 만들 수 있습니다. 편집기 항목 템플릿은 Visual C# 또는 Visual Basic VSIX 프로젝트에 사용할 수 있습니다.

## <a name="prerequisites"></a>사전 요구 사항
 Visual Studio 2015부터는 다운로드 센터에서 Visual Studio SDK를 설치하지 않습니다. 시각적 스튜디오 설정에서 선택적 기능으로 포함됩니다. 나중에 VS SDK를 설치할 수도 있습니다. 자세한 내용은 [Visual Studio SDK 설치를](../extensibility/installing-the-visual-studio-sdk.md)참조하십시오.

## <a name="create-a-classifier-extension"></a>분류자 확장 만들기
 편집기 분류자 항목 템플릿은 모든 텍스트 파일에 적절한 텍스트(이 경우 모든 항목)의 색상을 지정하는 편집기 분류를 만듭니다.

1. 새 **프로젝트** 대화 상자에서 **Visual C#** 또는 **Visual Basic을** 확장한 다음 **확장성을 클릭합니다.** **템플릿** 창에서 **VSIX 프로젝트를**선택합니다. **이름** 상자에서 `TestClassifier`을 입력합니다. **확인**을 클릭합니다.

2. 솔루션 **탐색기에서**프로젝트 노드를 마우스 오른쪽 단추로 클릭하고**새 항목** **추가를** > 선택합니다. 시각적 C# **확장성** 노드로 이동하여 **편집기 분류기를**선택합니다. 기본 파일*이름(EditorClassifier1.cs)을*둡니다.

3. 다음과 같이 네 개의 코드 파일이 있습니다.

    - *EditorClassifier1.cs* 클래스가 포함되어 있습니다. `EditorClassifier1`

    - *EditorClassifier1ClassificationDefinition.cs* 클래스가 포함되어 있습니다. `EditorClassifier1ClassificationDefinition`

    - *EditorClassifier1Format.cs* 클래스가 포함되어 있습니다. `EditorClassifier1Format`

    - *EditorClassifier1Provider.cs* 클래스가 포함되어 있습니다. `EditorClassifier1Provider`

4. 프로젝트를 빌드하고 디버깅을 시작합니다. Visual Studio의 실험 인스턴스가 나타납니다.

     텍스트 파일을 열면 모든 텍스트가 보라색 배경에 밑줄이 그어집니다.

## <a name="create-a-text-relative-adornment-extension"></a>텍스트 상대 장식 확장 만들기
 편집기 텍스트 장식 템플릿은 빨간색 윤곽선과 파란색 배경이 있는 상자를 사용하여 텍스트 문자 'a'의 모든 인스턴스를 장식하는 텍스트 상대 장식을 만듭니다. 상자는 이동하거나 다시 포일화할 때에도 항상 'a' 문자를 오버레이하기 때문에 텍스트 상대적입니다.

1. 새 **프로젝트** 대화 상자에서 **Visual C#** 또는 **Visual Basic을** 확장한 다음 **확장성을 클릭합니다.** **템플릿** 창에서 **VSIX 프로젝트를**선택합니다. **이름** 상자에서 `TestAdornment`을 입력합니다. **확인**을 클릭합니다.

2. 솔루션 **탐색기에서**프로젝트 노드를 마우스 오른쪽 단추로 클릭하고**새 항목** **추가를** > 선택합니다. 시각적 C# **확장성** 노드로 이동하여 **편집기 텍스트 장식을**선택합니다. 기본 파일*이름(TextAdornment1.cs/vb)을*둡니다.

3. 다음과 같이 두 개의 코드 파일이 있습니다.

    - *TextAdornment1.cs* 클래스가 포함되어 있습니다. `TextAdornment1`

    - *TextAdornment1TextViewCreationListener.cs* 클래스가 포함되어 있습니다. `TextAdornment1TextViewCreationListener`

4. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험 인스턴스가 나타납니다. 텍스트 파일을 열면 텍스트의 모든 'a' 문자가 파란색 배경에 빨간색으로 표시됩니다.

## <a name="create-a-viewport-relative-adornment-extension"></a>뷰포트 상대 장식 확장 만들기
 편집기 뷰포트 장식 템플릿은 뷰포트의 오른쪽 상단 모서리에 빨간색 윤곽선이 있는 보라색 상자를 추가하는 뷰포트 상대 장식을 만듭니다.

> [!NOTE]
> **뷰포트는** 현재 표시되는 텍스트 뷰의 영역입니다.

### <a name="to-create-a-viewport-adornment-extension-by-using-the-editor-viewport-adornment-template"></a>편집기 뷰포트 장식 템플릿을 사용하여 뷰포트 장식 확장을 만들려면

1. 새 **프로젝트** 대화 상자에서 **Visual C#** 또는 **Visual Basic을** 확장한 다음 **확장성을 클릭합니다.** **템플릿** 창에서 **VSIX 프로젝트를**선택합니다. **이름** 상자에서 `ViewportAdornment`을 입력합니다. **확인**을 클릭합니다.

2. 솔루션 **탐색기에서**프로젝트 노드를 마우스 오른쪽 단추로 클릭하고**새 항목** **추가를** > 선택합니다. 시각적 C# **확장성** 노드로 이동하여 **편집기 뷰포트 장식을**선택합니다. 기본 파일*이름(ViewportAdornment1.cs/vb)을*둡니다.

3. 다음과 같이 두 개의 코드 파일이 있습니다.

    - *ViewportAdornment1.cs* 클래스가 포함되어 있습니다. `ViewportAdornment1`

    - *ViewportAdornment1TextViewCreationListener.cs* 클래스가 포함되어 있습니다. `ViewportAdornment1TextViewCreationListener`

4. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험 인스턴스가 나타납니다. 새 텍스트 파일을 만들면 뷰포트의 오른쪽 상단 모서리에 빨간색 윤곽선이 있는 보라색 상자가 표시됩니다.

## <a name="create-a-margin-extension"></a>여백 확장 만들기
 편집기 여백 템플릿은 단어와 함께 나타나는 녹색 여백을 만듭니다 **안녕하세요 세계!* 가로 스크롤 막대 아래에 있습니다.

### <a name="to-create-a-margin-extension-by-using-the-editor-margin-template"></a>편집기 여백 템플릿을 사용하여 여백 확장을 만들려면

1. 새 **프로젝트** 대화 상자에서 **Visual C#** 또는 **Visual Basic을** 확장한 다음 **확장성을 클릭합니다.** **템플릿** 창에서 **VSIX 프로젝트를**선택합니다. **이름** 상자에서 `MarginExtension`을 입력합니다. **확인**을 클릭합니다.

2. 솔루션 **탐색기에서**프로젝트 노드를 마우스 오른쪽 단추로 클릭하고**새 항목** **추가를** > 선택합니다. 시각적 C# **확장성** 노드로 이동하여 **편집기 여백을**선택합니다. 기본 파일 이름(EditorMargin1.cs/vb)을 둡니다.

3. 다음과 같이 두 개의 코드 파일이 있습니다.

    - *EditorMargin1.cs* 클래스가 포함되어 있습니다. `EditorMargin1`

    - *EditorMargin1Factory.cs* 클래스가 포함되어 있습니다. `EditorMargin1Factory`

4. 이 프로젝트를 빌드하고 디버깅을 시작합니다. 실험 인스턴스가 나타납니다. 텍스트 파일을 열면 **Hello EditorMargin1이라는** 단어가 있는 녹색 여백이 가로 스크롤 막대 아래에 표시됩니다.

## <a name="see-also"></a>참조
- [언어 서비스 및 편집기 확장 지점](../extensibility/language-service-and-editor-extension-points.md)
