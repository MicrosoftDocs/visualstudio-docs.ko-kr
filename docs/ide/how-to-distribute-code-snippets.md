---
title: 코드 조각을 확장명으로 배포
ms.date: 03/21/2019
ms.topic: how-to
helpviewer_keywords:
- code snippets, distributing
ms.assetid: 5f717abd-e167-47ae-818c-6b0bae100ceb
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: c283d5ca29b67e772df2a0bb2e25dee70cd63fd3
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85284375"
---
# <a name="how-to-distribute-code-snippets"></a>방법: 코드 조각 배포

친구에게 코드 조각을 제공하고 **코드 조각 관리자**를 사용하여 고유한 컴퓨터에 코드 조각을 설치하면 됩니다. 그러나 배포할 코드 조각이 여러 개이거나 더 광범위하게 배포하려는 경우 Visual Studio 확장에 코드 조각 파일을 포함할 수 있습니다. 그런 다음, Visual Studio 사용자는 확장을 설치하여 코드 조각을 가져올 수 있습니다.

## <a name="prerequisites"></a>사전 요구 사항

**Visual Studio 확장 개발** 워크로드를 설치하여 **VSIX 프로젝트** 프로젝트 템플릿에 액세스합니다.

![Visual Studio 확장 개발 워크로드](media/vs-2019/extension-development-workload.png)

## <a name="set-up-the-extension"></a>확장 설정

이 프로시저에서는 다음 연습에서 만들어진 동일한 Hello World 코드 조각을 사용합니다. [연습: 코드 조각 만들기](../ide/walkthrough-creating-a-code-snippet.md)를 참조하세요. 이 문서에서는 코드 조각 XML을 제공하므로, 돌아가서 코드 조각을 만들 필요가 없습니다.

1. **빈 VSIX 프로젝트** 템플릿에서 새 프로젝트를 만들고 프로젝트의 이름을 **TestSnippet**으로 지정합니다.

2. **TestSnippet** 프로젝트에서 새 XML 파일을 추가하고 *VBCodeSnippet.snippet*을 호출합니다. 콘텐츠를 다음 XML로 바꿉니다.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <CodeSnippets
        xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
      <CodeSnippet Format="1.0.0">
        <Header>
          <Title>Hello World VB</Title>
          <Shortcut>HelloWorld</Shortcut>
          <Description>Inserts code</Description>
          <Author>MSIT</Author>
          <SnippetTypes>
            <SnippetType>Expansion</SnippetType>
            <SnippetType>SurroundsWith</SnippetType>
          </SnippetTypes>
        </Header>
        <Snippet>
          <Code Language="VB">
            <![CDATA[Console.WriteLine("Hello, World!")]]>
          </Code>
        </Snippet>
      </CodeSnippet>
    </CodeSnippets>
    ```

### <a name="set-up-the-directory-structure"></a>디렉터리 구조 설정

1. **솔루션 탐색기**에서 프로젝트 노드를 선택하고 코드 조각이 **코드 조각 관리자**에서 가진 이름을 사용하는 폴더를 추가합니다. 이 경우 폴더는 **HelloWorldVB**여야 합니다.

2. *.snippet* 파일을 *HelloWorldVB* 폴더로 이동합니다.

3. **솔루션 탐색기**에서 *.snippet* 파일을 선택하고, **속성** 창에서 **빌드 작업**이 **콘텐츠**로 설정되고, **출력 디렉터리에 복사**가 **항상 복사**로 설정되고, **VSIX에 포함**이 **true**로 설정되었는지 확인합니다.

### <a name="add-the-pkgdef-file"></a>.pkgdef 파일 추가

::: moniker range="vs-2017"

1. *HelloWorldVB* 폴더에 텍스트 파일을 추가하고 이름을 *HelloWorldVB.pkgdef*로 지정합니다. 이 파일을 사용하여 특정 키를 레지스트리에 추가합니다. 이 경우에 새 하위 키를 **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Languages\CodeExpansions\Basic** 키에 추가합니다.

::: moniker-end

::: moniker range=">=vs-2019"

1. *HelloWorldVB* 폴더에 텍스트 파일을 추가하고 이름을 *HelloWorldVB.pkgdef*로 지정합니다. 이 파일을 사용하여 특정 키를 레지스트리에 추가합니다. 이 경우에 새 하위 키를 **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\16.0\Languages\CodeExpansions\Basic** 키에 추가합니다.

::: moniker-end

2. 파일에 다음 줄을 추가합니다.

    ```txt
    // Visual Basic
    [$RootKey$\Languages\CodeExpansions\Basic\Paths]
    "HelloWorldVB"="$PackageFolder$"
    ```

    이 키를 검토하면 다른 언어를 지정하는 방법을 알 수 있습니다.

3. **솔루션 탐색기**에서 *.pkgdef* 파일을 선택하고 **속성** 창에서 다음을 확인합니다.

   - **빌드 작업**을 **콘텐츠**로 설정
   - **출력 디렉터리에 복사**를 **항상 복사**로 설정
   - **VSIX에 포함**을 **true**로 설정

4. *.pkgdef* 파일을 VSIX 매니페스트의 자산으로 추가합니다. *source.extension.vsixmanifest* 파일에서 **자산** 탭으로 이동하고 **새로 만들기**를 클릭합니다.

5. **새 자산 추가** 대화 상자에서 **형식**을 **Microsoft.VisualStudio.VsPackage**로 설정하고, **원본**을 **파일 시스템의 파일**로 설정하고, **경로**를 **HelloWorldVB.pkgdef**(드롭다운에 표시되어야 함)로 설정합니다.

### <a name="test-the-snippet"></a>코드 조각 테스트

1. 이제 코드 조각이 Visual Studio의 실험적 인스턴스에서 작동하는지 확인할 수 있습니다. 실험적 인스턴스는 코드 작성에 사용하는 복사본과 구분되는 Visual Studio의 두 번째 복사본입니다. 이를 사용하여 개발 환경에 영향을 주지 않고 확장 작업을 수행할 수 있습니다.

2. 프로젝트를 빌드하고 디버깅을 시작합니다.

   두 번째 Visual Studio 인스턴스가 표시됩니다.

3. 실험적 인스턴스에서 **도구** > **코드 조각 관리자**로 이동하고 **언어**를 **기본**으로 설정합니다. *HelloWorldVB*가 폴더의 하나로 표시되고 폴더를 확장하여 *HelloWorldVB* 코드 조각을 확인할 수 있어야 합니다.

4. 조각을 테스트합니다. 실험적 인스턴스에서 Visual Basic 프로젝트를 열고 코드 파일의 하나를 엽니다. 코드의 임의 위치에 커서를 놓고 마우스 오른쪽 단추를 클릭하고 나서 상황에 맞는 메뉴에서 **조각 삽입**을 선택합니다.

5. *HelloWorldVB*가 폴더의 하나로 표시되어야 합니다. 폴더를 두 번 클릭합니다. **코드 조각 삽입: HelloWorldVB >** 팝업이 표시되어야 하고 여기에는 드롭다운 **HelloWorldVB**가 포함됩니다. **HelloWorldVB** 드롭다운을 클릭합니다.

   다음 줄이 코드 파일에 추가됩니다.

    ```vb
    Console.WriteLine("Hello, World!")
    ```

## <a name="see-also"></a>참조

- [코드 조각](../ide/code-snippets.md)
