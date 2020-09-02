---
title: '방법: 컴파일러 경고 표시 안 함 | Microsoft 문서'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 31827b17-f933-413d-b28a-b19f903b64ca
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aeb404c479edec5dec89f28e80584d435f5c370a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670650"
---
# <a name="how-to-suppress-compiler-warnings"></a>방법: 컴파일러 경고 표시 안 함

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

포함하지 않을 컴파일러 경고 종류를 하나 이상 지정하여 빌드 로그의 혼잡을 방지할 수 있습니다. 예를 들어 이 방법을 사용하면 빌드 로그의 자세한 정도를 보통, 자세히 또는 진단으로 설정할 경우 자동으로 생성되는 정보의 전체가 아니라 일부를 검토할 수 있습니다. 자세한 정도에 대 한 자세한 내용은 [방법: 빌드 로그 파일 보기, 저장 및 구성](../ide/how-to-view-save-and-configure-build-log-files.md)을 참조 하세요.

### <a name="to-suppress-specific-warnings-for-visual-c-or-f"></a>Visual c # 또는 F에 대 한 특정 경고를 표시 하지 않으려면\#

1. **솔루션 탐색기**에서 경고를 표시하지 않으려는 프로젝트를 선택합니다.

2. 메뉴 모음에서 **보기**, **속성 페이지**를 선택합니다.

3. **빌드** 페이지를 선택합니다.

4. **경고 표시 안 함** 상자에 표시하지 않으려는 경고의 오류 코드를 세미콜론으로 구분하여 지정한 다음 솔루션을 다시 빌드합니다.

### <a name="to-suppress-specific-warnings-for-visual-c"></a>Visual C++에 대한 특정 경고를 표시하지 않으려면

1. **솔루션 탐색기**에서 경고를 표시하지 않으려는 프로젝트 또는 소스 파일을 선택합니다.

2. 메뉴 모음에서 **보기**, **속성 페이지**를 선택합니다.

3. **구성 속성** 범주를 선택하고 **C/C++** 범주를 선택한 다음 **고급** 페이지를 선택합니다.

4. 다음 단계 중 하나를 수행합니다.

    - **특정 경고 사용 안 함** 상자에 표시하지 않으려는 경고의 오류 코드를 세미콜론으로 구분하여 지정합니다.

    - **특정 경고 사용 안 함** 상자에서 **편집**을 선택하여 추가 옵션을 표시합니다.

5. **확인** 단추를 선택한 다음 솔루션을 다시 빌드합니다.

## <a name="suppressing-warnings-for-visual-basic"></a>Visual Basic에 대한 경고 표시 안 함

프로젝트의 .vbproj 파일을 편집하여 Visual Basic에 대한 특정 컴파일러 경고를 숨길 수 있습니다. [프로젝트 디자이너, 컴파일 페이지](../ide/reference/compile-page-project-designer-visual-basic.md)를 사용하여 범주별로 경고를 표시하지 않을 수도 있습니다. 자세한 내용은 [Visual Basic에서 경고 구성](../ide/configuring-warnings-in-visual-basic.md)을 참조하세요.

#### <a name="to-suppress-specific-warnings-for-visual-basic"></a>Visual Basic에 대한 특정 경고를 표시하지 않으려면

1. **솔루션 탐색기**에서 경고를 표시하지 않으려는 프로젝트를 선택합니다.

2. 메뉴 모음에서 **프로젝트**, **프로젝트 언로드**를 선택합니다.

3. **솔루션 탐색기**에서 프로젝트의 바로 가기 메뉴를 열고 **편집**_ProjectName_**.vbproj**를 선택합니다.

    프로젝트 파일이 코드 편집기에서 열립니다.

4. 빌드에 사용 중인 빌드 구성에서 `<NoWarn></NoWarn>` 요소를 찾습니다.

    다음 예제에서는 x86 플랫폼의 디버그 빌드 구성에 대한 `<NoWarn></NoWarn>` 요소를 굵은 텍스트로 표시합니다.

   ```xml
   <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x86' ">
       <PlatformTarget>x86</PlatformTarget>
       <DebugSymbols>true</DebugSymbols>
       <DebugType>full</DebugType>
       <Optimize>false</Optimize>
       <OutputPath>bin\Debug\</OutputPath>
       <DefineDebug>true</DefineDebug>
       <DefineTrace>true</DefineTrace>
       <ErrorReport>prompt</ErrorReport>
       <NoWarn></NoWarn>
       <WarningLevel>1</WarningLevel>
     </PropertyGroup>
   ```

5. 하나 이상의 경고 번호를 `<NoWarn>` 요소의 값으로 추가합니다. 여러 경고 번호를 지정하는 경우 다음 예제와 같이 쉼표로 구분합니다.

   ```xml
   <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x86' ">
       <PlatformTarget>x86</PlatformTarget>
       <DebugSymbols>true</DebugSymbols>
       <DebugType>full</DebugType>
       <Optimize>false</Optimize>
       <OutputPath>bin\Debug\</OutputPath>
       <DefineDebug>true</DefineDebug>
       <DefineTrace>true</DefineTrace>
       <ErrorReport>prompt</ErrorReport>
       <NoWarn>40059,42024</NoWarn>
       <WarningLevel>1</WarningLevel>
     </PropertyGroup>
   ```

6. 변경 내용을 .vbproj 파일에 저장합니다.

7. 메뉴 모음에서 **프로젝트**, **프로젝트 다시 로드**를 선택합니다.

8. 메뉴 모음에서 **빌드**, **솔루션 다시 빌드**를 선택합니다.

    지정한 경고가 **출력** 창에 더 이상 표시되지 않습니다.

   자세한 내용은 [/nowarn](https://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83)을 참조 하세요.

## <a name="see-also"></a>관련 항목

- [연습: 애플리케이션 빌드](../ide/walkthrough-building-an-application.md)
- [방법: 빌드 로그 파일 보기, 저장 및 구성](../ide/how-to-view-save-and-configure-build-log-files.md)
- [컴파일 및 빌드](../ide/compiling-and-building-in-visual-studio.md)
