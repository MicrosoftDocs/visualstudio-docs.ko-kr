---
title: 도메인별 언어 시작 하기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 024392a2-2c04-404f-a27b-7273553c3b60
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6fe720b380133d15f9bc60485896d4b7acbf2c4b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543197"
---
# <a name="getting-started-with-domain-specific-languages"></a>도메인별 언어 시작
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 항목에서는 Visual Studio 용 모델링 SDK를 사용 하 여 만든 DSL (도메인별 언어)을 정의 하 고 사용 하는 기본 개념을 설명 합니다.

## <a name="what-can-you-do-with-a-domain-specific-language"></a>도메인 특정 언어로 무엇을 할 수 있나요?
 도메인별 언어는 특정 용도에 사용 하도록 디자인 된 표기법으로, 일반적으로 그래픽입니다. 이와 대조적으로 UML과 같은 언어는 범용입니다. DSL에서는 모델 요소 및 해당 관계의 유형과 화면에 표시 되는 방식을 정의할 수 있습니다.

 DSL을 디자인 한 경우 VSIX (Visual Studio Integration Extension) 패키지의 일부로 배포할 수 있습니다. 에서 DSL을 사용 하는 사용자는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 다음과 같습니다.

 ![패밀리 트리 다이어그램, 도구 상자 및 탐색기](../modeling/media/familyt-instance.png "FamilyT_Instance")

 표기법은 DSL의 일부일 뿐입니다. VSIX 패키지에는 표기법과 함께 사용자가 모델에서 재질을 편집 하 고 생성 하는 데 사용할 수 있는 도구가 포함 되어 있습니다.

 Dsl의 주요 응용 프로그램 중 하나는 프로그램 코드, 구성 파일 및 기타 아티팩트를 생성 하는 것입니다. 특히 제품의 여러 변형이 생성 되는 대규모 프로젝트와 제품 라인에서 Dsl의 많은 변수 측면을 생성 하면 안정성 증가와 요구 사항 변화에 대 한 매우 신속한 응답을 제공할 수 있습니다.

 이 개요의 나머지 부분은에서 도메인별 언어를 만들고 사용 하는 기본 작업을 소개 하는 연습입니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

## <a name="prerequisites"></a>필수 구성 요소
 DSL을 정의하려면 다음 구성 요소를 설치해야 합니다.

|제품|다운로드 링크|
|-|-|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185579](https://www.visualstudio.com/)|
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185580](/azure/devops/integrate/index?view=azure-devops&viewFallbackFrom=vsts)|
|Visual Studio 용 모델링 SDK|[MSDK 다운로드](https://www.microsoft.com/download/details.aspx?id=48148)|

## <a name="creating-a-dsl-solution"></a>DSL 솔루션 만들기
 도메인 특정 언어를 새로 만들려면 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 도메인별 언어 프로젝트 템플릿을 사용 하 여 새 솔루션을 만듭니다.

#### <a name="to-create-a-dsl-solution"></a>DSL 솔루션을 만들려면

1. **파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **프로젝트**를 클릭합니다.

2. **프로젝트 형식**에서 **기타 프로젝트 형식** 노드를 확장 하 고 **확장성**을 클릭 합니다.

3. **도메인 특정 언어 디자이너**를 클릭 합니다.

    ![DSL 만들기 대화 상자](../modeling/media/create-dsldialog.png "Create_DSLDialog")

4. **이름** 상자에 **FamilyTree**을 입력 합니다. **확인**을 클릭합니다.

    **도메인 특정 언어 마법사** 가 열리고 템플릿 DSL 솔루션 목록이 표시 됩니다.

    각 템플릿을 클릭 하 여 설명을 표시 합니다.

    템플릿은 유용한 시작 점으로 사용할 수 있습니다. 각각은 요구에 맞게 편집할 수 있는 완전 한 작업 DSL을 제공 합니다. 일반적으로 만들려는 항목에 가장 가까운 템플릿을 선택 합니다.

5. 이 연습에서는 **최소 언어** 템플릿을 선택 합니다.

6. 해당하는 마법사 페이지에서 DSL의 파일 이름 확장명을 입력합니다. 이 확장명은 DSL의 인스턴스가 포함된 파일에 사용됩니다.

   - 컴퓨터의 응용 프로그램과 연결 되지 않은 확장 또는 DSL을 설치할 컴퓨터를 선택 합니다. 예를 들어 **.docx** 와 **htm** 은 파일 이름 확장명이 허용 되지 않습니다.

   - 입력한 확장명이 DSL로 사용되고 있으면 경고가 표시됩니다. 이 경우 다른 파일 이름 확장명을 사용해야 합니다. Visual Studio SDK 실험적 인스턴스를 다시 설정하여 오래된 실험적 디자이너를 지울 수도 있습니다. **시작**, **모든 프로그램**, **Microsoft Visual Studio 2010 SDK**, **도구**를 차례로 클릭 한 다음 **Microsoft Visual Studio 2010 실험적 인스턴스를 다시 설정**합니다.

7. 다른 페이지를 검사 한 다음 **마침**을 클릭 합니다.

    두 개의 프로젝트가 포함 된 솔루션이 생성 됩니다. Dsl 및 DslPackage 라는 이름이 지정 됩니다. 이름이 DslDefinition. dsl 인 다이어그램 파일이 열립니다.

   > [!NOTE]
   > 두 프로젝트의 폴더에서 볼 수 있는 대부분의 코드는 DslDefinition. dsl에서 생성 됩니다. 이러한 이유로 DSL에 대 한 대부분의 수정이이 파일에 적용 됩니다.

   이제 사용자 인터페이스는 다음 그림과 같이 표시됩니다.

   ![dsl 디자이너](../modeling/media/dsl-designer.png "dsl_designer")

   이 솔루션은 DSL을 정의합니다. 자세한 내용은 [도메인 특정 언어 도구 사용자 인터페이스 개요](../modeling/overview-of-the-domain-specific-language-tools-user-interface.md)를 참조 하세요.

## <a name="the-important-parts-of-the-dsl-solution"></a>DSL 솔루션의 중요 한 부분
 새 솔루션의 다음 측면을 확인 하세요.

- **Dsl\dsldefinitiondsl** DSL 솔루션을 만들 때 표시 되는 파일입니다. 이 파일에서는 솔루션의 거의 모든 코드가 생성 되며, DSL 정의에 대 한 대부분의 변경 내용이 여기에 적용 됩니다. 자세한 내용은 [DSL 정의 다이어그램 작업](../modeling/working-with-the-dsl-definition-diagram.md)을 참조 하세요.

- **Dsl 프로젝트** 이 프로젝트에는 도메인별 언어를 정의 하는 코드가 포함 되어 있습니다.

- **Dslpackage 프로젝트** 이 프로젝트에는에서 DSL 인스턴스를 열고 편집할 수 있도록 하는 코드가 포함 되어 있습니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

## <a name="running-the-dsl"></a><a name="Debugging"></a> DSL 실행
 DSL 솔루션을 만든 후 바로 실행할 수 있습니다. 나중에 DSL 정의를 점진적으로 수정 하 여 각 변경 후에 솔루션을 다시 실행할 수 있습니다.

#### <a name="to-experiment-with-the-dsl"></a>DSL을 사용 하 여 시험해 보려면

1. 솔루션 탐색기 도구 모음에서 **모든 템플릿 변환** 을 클릭 합니다. 이를 통해 대부분의 소스 코드를 생성 합니다. dsl.

   > [!NOTE]
   > Node.js를 변경할 때마다 솔루션을 다시 빌드하기 전에 **모든 템플릿 변환** 을 클릭 해야 합니다. 이 단계는 자동화할 수 있습니다. 자세한 내용은 [모든 템플릿 변환을 자동화 하는 방법](https://msdn.microsoft.com/b63cfe20-fe5e-47cc-9506-59b29bca768a)을 참조 하세요.

2. F5 키를 누르거나 **디버그** 메뉴에서 **디버깅 시작**을 클릭 합니다.

    DSL은의 실험적 인스턴스에 빌드되고 설치 됩니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

    [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 의 실험적 인스턴스가 시작됩니다. 실험적 인스턴스는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 디버깅 목적으로 확장이 등록 된 별도의 레지스트리 하위 트리에서 해당 설정을 가져옵니다. 의 일반 인스턴스에는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 등록 된 확장에 대 한 액세스 권한이 없습니다.

3. 의 실험적 인스턴스에서 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **솔루션 탐색기**에서 **Test** 라는 모델 파일을 엽니다.

    \- 또는 -

    디버깅 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **추가**를 가리킨 다음 **항목**을 클릭 합니다. **항목 추가** 대화 상자에서 DSL의 파일 형식을 선택 합니다.

    모델 파일이 빈 다이어그램으로 열립니다.

    도구 상자가 열리고 다이어그램 형식에 적합 한 도구가 표시 됩니다.

4. 도구를 사용 하 여 다이어그램에 모양과 연결선을 만듭니다.

   1. 도형을 만들려면 도형 도구 예제에서 다이어그램으로 끌어 옵니다.

   2. 두 셰이프를 연결 하려면 예 커넥터 도구를 클릭 하 고 첫 번째 셰이프를 클릭 한 다음 두 번째 셰이프를 클릭 합니다.

5. 셰이프의 레이블을 클릭 하 여 변경 합니다.

   실험적 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 은 다음 예제와 유사 합니다.

   ![](../modeling/media/dsl-min.png "DSL_min")

### <a name="the-content-of-a-model"></a>모델의 내용
 DSL 인스턴스인 파일의 내용을 *모델*이라고 합니다. 모델에는 *모델 요소* 와 요소 간의 *링크가* 포함 되어 있습니다. DSL 정의는 모델에 존재 하는 모델 요소 및 링크의 유형을 지정 합니다. 예를 들어 최소 언어 템플릿에서 만든 DSL에는 하나의 모델 요소 형식 및 하나의 링크 형식이 있습니다.

 DSL 정의는 다이어그램에 모델을 표시 하는 방법을 지정할 수 있습니다. 도형 및 연결선의 다양 한 스타일에서 선택할 수 있습니다. 일부 셰이프가 다른 모양 안에 나타나도록 지정할 수 있습니다.

 모델을 편집 하는 동안 **탐색기** 보기에서 트리로 모델을 볼 수 있습니다. 다이어그램에 셰이프를 추가 하면 모델 요소도 탐색기에 표시 됩니다. 다이어그램이 없는 경우에도 탐색기를 사용할 수 있습니다.

 의 디버깅 인스턴스에서 탐색기가 표시 되지 않으면 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **보기** 메뉴에서 **다른 창**을 가리킨 다음 탐색기를 클릭 합니다 *\<Your Language>* **Explorer**.

### <a name="the-api-of-your-dsl"></a>DSL의 API
 DSL은 DSL 인스턴스인 모델을 읽고 업데이트 하는 데 사용할 수 있는 API를 생성 합니다. API의 한 가지 응용 프로그램은 모델에서 텍스트 파일을 생성 하는 것입니다. 자세한 내용은 [T4 텍스트 템플릿을 사용 하 여 디자인 타임 코드 생성](../modeling/design-time-code-generation-by-using-t4-text-templates.md)을 참조 하세요.

 디버깅 솔루션에서 확장명이 ".tt" 인 템플릿 파일을 엽니다. 이러한 샘플은 모델에서 텍스트를 생성 하는 방법을 보여 주며 DSL의 API를 테스트 하는 데 사용할 수 있습니다. 샘플 중 하나가에 작성 되어 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] [!INCLUDE[csprcs](../includes/csprcs-md.md)] 있습니다.

 각 템플릿 파일은 생성 되는 파일입니다. 솔루션 탐색기에서 템플릿 파일을 확장 하 고 생성 된 파일을 엽니다.

 템플릿 파일에는 모델의 모든 요소를 나열 하는 짧은 코드 세그먼트가 포함 되어 있습니다.

 생성 된 파일에는 결과가 포함 됩니다.

 모델 파일을 변경 하는 경우 파일을 다시 생성 한 후 생성 된 파일에 해당 하는 변경 내용이 표시 됩니다.

##### <a name="to-regenerate-text-files-after-you-change-the-model-file"></a>모델 파일을 변경한 후 텍스트 파일을 다시 생성 하려면

1. 실험적 인스턴스에서 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 모델 파일을 저장 합니다.

2. 각 .tt 파일의 파일 이름 매개 변수가 실험에 사용 하는 모델 파일을 참조 하는지 확인 합니다. .Tt 파일을 저장 합니다.

3. **솔루션 탐색기**도구 모음에서 **모든 템플릿 변환** 을 클릭 합니다.

    \- 또는 -

    다시 생성 하려는 템플릿을 마우스 오른쪽 단추로 클릭 한 다음 **사용자 지정 도구 실행**을 클릭 합니다.

   프로젝트에 원하는 수의 텍스트 템플릿 파일을 추가할 수 있습니다. 각 템플릿은 하나의 결과 파일을 생성 합니다.

> [!NOTE]
> DSL 정의를 변경 하면이를 업데이트 하지 않는 한 샘플 텍스트 템플릿 코드가 작동 하지 않습니다.

 자세한 내용은 도메인별 [언어에서 코드 생성](../modeling/generating-code-from-a-domain-specific-language.md) 및 [도메인별 언어를 지정 하는 코드 작성](../modeling/writing-code-to-customise-a-domain-specific-language.md)을 참조 하세요.

## <a name="customizing-the-dsl"></a>DSL 사용자 지정
 DSL 정의를 수정 하려면 실험적 인스턴스를 닫고 주 인스턴스에서 정의를 업데이트 합니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

> [!NOTE]
> DSL 정의를 수정한 후에는 이전 버전을 사용 하 여 만든 테스트 모델의 정보가 손실 될 수 있습니다.  예를 들어, 디버깅 솔루션에는 몇 가지 모양과 커넥터가 포함 된 Sample 이라는 파일이 포함 되어 있습니다. DSL 정의 개발을 시작한 후에는 표시 되지 않으며 파일을 저장할 때 손실 됩니다.

 DSL에 대 한 다양 한 확장을 만들 수 있습니다. 다음 예에서는 가능성에 대 한 인상을 제공 합니다.

 각 변경 후에는 DSL 정의를 저장 하 고 **솔루션 탐색기**의 **모든 템플릿 변환** 을 클릭 한 다음 **F5** 키를 눌러 변경 된 dsl을 시험해 봅니다.

### <a name="rename-the-types-and-tools"></a>형식 및 도구 이름 바꾸기
 기존 도메인 클래스 및 관계의 이름을 바꿉니다. 예를 들어 최소 언어 템플릿에서 만든 Dsl 정의에서 시작 하 여 DSL이 패밀리 트리를 나타내도록 다음 이름 바꾸기 작업을 수행할 수 있습니다.

##### <a name="to-rename-domain-classes-relationships-and-tools"></a>도메인 클래스, 관계 및 도구 이름을 바꾸려면

1. DslDefinition 다이어그램에서 **examplemodel.store.customer** 을 **FamilyTreeModel**로, **ExampleElement** to **Person**, **Targets** 를 **부모로**, **Sources** 를 **Children**으로 바꿉니다. 각 레이블을 클릭 하 여 변경할 수 있습니다.

     ![DSL 정의 다이어그램 &#45; 패밀리 트리 모델](../modeling/media/familyt-person.png "FamilyT_Person")

2. 요소 및 커넥터 도구의 이름을 바꿉니다.

    1. 솔루션 탐색기 아래에 있는 탭을 클릭 하 여 DSL 탐색기 창을 엽니다. 표시 되지 않는 경우 **보기** 메뉴에서 **다른 창** 을 가리킨 다음 **DSL 탐색기**를 클릭 합니다. Dsl 탐색기는 DSL 정의 다이어그램이 활성 창인 경우에만 표시 됩니다.

    2. 속성 창를 열고 DSL 탐색기와 속성을 동시에 볼 수 있도록 배치 합니다.

    3. DSL 탐색기에서 **편집기**, **도구 상자 탭**, *\<your DSL>* , **도구**를 차례로 확장 합니다.

    4. **ExampleElement**을 클릭 합니다. 요소를 만드는 데 사용 되는 도구 상자 항목입니다.

    5. 속성 창에서 **이름** 속성을 **Person**으로 변경 합니다.

         **Caption** 속성도 변경 됩니다.

    6. 동일한 방식으로 **ExampleConnector** 도구의 이름을 **parentlink**로 변경 합니다. **Caption** 속성이 Name 속성의 복사본이 되지 않도록 변경 합니다. 예를 들어 **부모 링크**를 입력 합니다.

3. DSL을 다시 빌드합니다.

    1. DSL 정의 파일을 저장 합니다.

    2. 의 도구 모음에서 **모든 템플릿 변환** 을 클릭 솔루션 탐색기

    3. F5 키를 누릅니다. 의 실험적 인스턴스가 나타날 때까지 기다립니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

4. 실험적 인스턴스의 디버깅 솔루션에서 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 테스트 모델 파일을 엽니다. 도구 상자에서 요소를 끌어 옵니다. DSL 탐색기의 도구 캡션과 형식 이름이 변경 되었습니다.

5. 모델 파일을 저장 합니다.

6. .Tt 파일을 열고 이전 형식 및 속성 이름의 발생 항목을 새 이름으로 바꿉니다.

7. .Tt 파일에 지정 된 파일 이름이 테스트 모델을 지정 하는지 확인 합니다.

8. .Tt 파일을 저장 합니다. 생성 된 파일을 열어 .tt 파일에서 코드를 실행 한 결과를 확인 합니다. 올바른지 확인 합니다.

### <a name="add-domain-properties-to-classes"></a>클래스에 도메인 속성 추가
 도메인 클래스에 속성을 추가 합니다. 예를 들어 사용자의 출생 연도와 죽음을 나타냅니다.

 다이어그램에 새 속성을 표시 하려면 모델 요소를 표시 하는 셰이프에 *데코레이터* 를 추가 해야 합니다. 또한 속성을 데코레이터에 매핑해야 합니다.

##### <a name="to-add-properties-and-display-them"></a>속성을 추가 하 고 표시 하려면

1. 속성을 추가 합니다.

   1. DSL 정의 다이어그램에서 **Person** 도메인 클래스를 마우스 오른쪽 단추로 클릭 하 고 **추가**를 가리킨 다음 **도메인 속성**을 클릭 합니다.

   2. **생년월일** 및 **죽음**과 같은 새 속성 이름 목록을 입력 합니다. 각 항목 뒤에 **enter** 키를 누릅니다.

2. 셰이프에 속성을 표시 하는 데코레이터를 추가 합니다.

   1. Person 도메인 클래스에서 다이어그램의 다른 쪽으로 확장 되는 회색 줄을 따릅니다. 이는 다이어그램 요소 맵입니다. 도메인 클래스를 shape 클래스에 연결 합니다.

   2. 이 shape 클래스를 마우스 오른쪽 단추로 클릭 하 고 **추가**를 가리킨 다음 **텍스트 데코레이터**를 클릭 합니다.

   3. **BirthDecorator** 및 **DeathDecorator**와 같은 이름을 사용 하 여 두 개의 데코레이터를 추가 합니다.

   4. 각각의 새 데코레이터를 선택 하 고 속성 창에서 **위치** 필드를 설정 합니다. 이렇게 하면 셰이프에 도메인 속성 값이 표시 되는 위치가 결정 됩니다. 예를 들어 **InnerBottomLeft** 및 **InnerBottomRight**를 설정 합니다.

        ![구획 모양 정의](../modeling/media/familyt-compartment.png "FamilyT_Compartment")

3. 데코레이터을 속성에 매핑합니다.

   1. DSL 정보 창을 엽니다. 일반적으로 출력 창 옆에 있는 탭에 있습니다. 표시 되지 않는 경우 **보기** 메뉴에서 **다른 창**을 가리킨 다음 **DSL 정보**를 클릭 합니다.

   2. DSL 정의 다이어그램에서 **Person** 도메인 클래스를 shape 클래스에 연결 하는 선을 클릭 합니다.

   3. **DSL 세부 정보**의 **데코레이터 맵** 탭에서 매핑되지 않은 데코레이터의 확인란을 클릭 합니다. **표시 속성**에서 매핑할 도메인 속성을 선택 합니다. 예를 들어 **BirthDecorator** 를 **생년월일**에 매핑합니다.

4. DSL을 저장 하 고 모든 템플릿 변환을 클릭 한 다음 F5 키를 누릅니다.

5. 샘플 모델 다이어그램에서 이제 선택한 위치를 클릭 하 고 값을 입력할 수 있는지 확인 합니다. 또한 **Person** 셰이프를 선택 하면 속성 창 새 속성 생년월일 및 죽음이 표시 됩니다.

6. .Tt 파일에서 각 사용자의 속성을 가져오는 코드를 추가할 수 있습니다.

   ![패밀리 트리 다이어그램, 도구 상자 및 탐색기](../modeling/media/familyt-instance.png "FamilyT_Instance")

### <a name="define-new-classes"></a>새 클래스 정의
 도메인 클래스와 관계를 모델에 추가할 수 있습니다. 예를 들어 도시를 나타내는 새 클래스를 만들고, 해당 사용자가 타운에 있는 것을 나타내는 새 관계를 만들 수 있습니다.

 모델 다이어그램에서 서로 다른 형식을 고유 하 게 만들려면 도메인 클래스를 다른 종류의 셰이프 또는 기 하 도형 및 색을 사용 하는 도형에 매핑할 수 있습니다.

##### <a name="to-add-and-display-a-new-domain-class"></a>새 도메인 클래스를 추가 하 고 표시 하려면

1. 도메인 클래스를 추가 하 고이를 모델 루트의 자식으로 만듭니다.

    1. DSL 정의 다이어그램에서 **포함 관계** 도구를 클릭 하 고 루트 클래스 **FamilyTreeModel**을 클릭 한 다음 다이어그램의 빈 부분을 클릭 합니다.

         포함 관계를 사용 하 여 FamilyTreeModel에 연결 된 새 도메인 클래스가 표시 됩니다.

         이름을 설정 합니다 (예: **타운**).

        > [!NOTE]
        > 모델의 루트를 제외한 모든 도메인 클래스는 하나 이상의 포함 관계의 대상 이거나 포함의 대상인 클래스에서 상속 되어야 합니다. 이러한 이유로 포함 관계 도구를 사용 하 여 도메인 클래스를 만드는 것이 편리 합니다.

    2. **이름**과 같이 새 클래스에 도메인 속성을 추가 합니다.

2. 사람 및 타운 간에 참조 관계를 추가 합니다.

    1. **참조 관계** 도구를 클릭 하 고 Person을 클릭 한 다음 마을를 클릭 합니다.

         ![DSL 정의 조각: 패밀리 트리 루트](../modeling/media/familyt-root.png "FamilyT_Root")

        > [!NOTE]
        > 참조 관계는 모델 트리의 한 부분에서 다른 부분으로의 상호 참조를 나타냅니다.

3. 모델 다이어그램에서 도시를 나타내는 셰이프를 추가 합니다.

    1. **Geometry 셰이프** 를 도구 상자에서 다이어그램으로 끌고 이름을 TownShape 합니다 (예: **TownShape**).

    2. 속성 창에서 채우기 색, 기 하 도형 등의 새 모양의 모양 필드를 설정 합니다.

    3. 데코레이터를 추가 하 여 타운의 이름을 표시 하 고 이름을 NameDecorator로 바꿉니다. Position 속성을 설정 합니다.

4. TownShape에 마을 도메인 클래스를 매핑합니다.

    1. **다이어그램 요소 맵** 도구를 클릭 하 고 마을 도메인 클래스를 클릭 한 다음 TownShape shape 클래스를 클릭 합니다.

    2. **DSL 정보** 창의 **데코레이터 맵** 탭에서 지도 커넥터가 선택 된 상태에서 NameDecorator를 확인 하 고 **표시 속성** 을 이름으로 설정 합니다.

5. 커넥터를 만들어 사람과 도시 간의 관계를 표시 합니다.

    1. 도구 상자에서 다이어그램으로 연결선을 끌어 옵니다. 이름을 바꾸고 모양 속성을 설정 합니다.

    2. **다이어그램 요소 맵** 도구를 사용 하 여 새 커넥터를 개인 및 타운 간의 관계에 연결 합니다.

         ![추가된 모양 맵을 사용하여 패밀리 트리 정의](../modeling/media/familyt-shapemap.png "FamilyT_ShapeMap")

6. 새 타운을 만들기 위한 요소 도구를 만듭니다.

    1. **DSL 탐색기**에서 **편집기** , **도구 상자 탭**을 차례로 확장 합니다.

    2. 마우스 오른쪽 단추 *\<your DSL>* 를 클릭 한 다음 **새 요소 도구 추가**를 클릭 합니다.

    3. 새 도구의 **Name** 속성을 설정 하 고 **Class** 속성을 타운으로 설정 합니다.

    4. **도구 상자 아이콘** 속성을 설정 합니다. **[...]** 를 클릭 하 고 **파일 이름** 필드에서 아이콘 파일을 선택 합니다.

7. 도시와 사람 간에 링크를 만들기 위한 연결선 도구를 만듭니다.

    1. 마우스 오른쪽 단추로 클릭 한 *\<your DSL>* 다음 **새 커넥터 도구 추가**를 클릭 합니다.

    2. 새 도구의 이름 속성을 설정 합니다.

    3. **Connectionbuilder** 속성에서 사용자-타운 관계의 이름을 포함 하는 작성기를 선택 합니다.

    4. **도구 상자 아이콘**을 설정 합니다.

8. DSL 정의를 저장 하 고 **모든 템플릿 변환**을 클릭 한 다음 **f5**키를 누릅니다.

9. 실험적 인스턴스에서 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 테스트 모델 파일을 엽니다. 새 도구를 사용 하 여 마을을 도시와 사람 간에 링크를 만들 수 있습니다. 올바른 요소 형식 간에만 링크를 만들 수 있습니다.

10. 각 사용자가 거주 하는 마을을 나열 하는 코드를 만듭니다. 텍스트 템플릿은 이러한 코드를 실행할 수 있는 위치 중 하나입니다. 예를 들어 다음 코드를 포함 하도록 디버깅 솔루션에서 기존 Sample.tt 파일을 수정할 수 있습니다.

    ```
    <#@ template inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" debug="true" #>
    <#@ output extension=".txt" #>
    <#@ FamilyTree processor="FamilyTreeDirectiveProcessor" requires="fileName='Sample.ftree'" #>

    <#
      foreach (Person person in this.FamilyTreeModel.People)
      {
    #>
        <#= person.Name #><#if (person.Town != null) {#> of <#= person.Town.Name #> <#}#>

    <#
          foreach (Person child in person.Children)
      {
    #>
                <#= child.Name #>
    <#
      }
      }
    #>

    ```

     * .Tt 파일을 저장 하면 사용자 및 해당 residences 목록이 포함 된 자회사 파일이 생성 됩니다. 자세한 내용은 [도메인별 언어에서 코드 생성](../modeling/generating-code-from-a-domain-specific-language.md)을 참조 하세요.

## <a name="validation-and-commands"></a>유효성 검사 및 명령
 유효성 검사 제약 조건을 추가 하 여이 DSL을 추가로 개발할 수 있습니다. 이러한 제약 조건은 모델이 올바른 상태 인지 확인 하기 위해 정의할 수 있는 메서드입니다. 예를 들어 자식의 출생 날짜가 부모 항목 보다 최신 인지 확인 하기 위한 제약 조건을 정의할 수 있습니다. DSL 사용자가 제약 조건을 위반 하는 모델을 저장 하려고 하면 유효성 검사 기능이 경고를 표시 합니다. 자세한 내용은 [도메인별 언어의 유효성 검사](../modeling/validation-in-a-domain-specific-language.md)를 참조 하세요.

 사용자가 호출할 수 있는 메뉴 명령을 정의할 수도 있습니다. 명령은 모델을 수정할 수 있습니다. 또한 및 외부 리소스를 사용 하 여의 다른 모델과 상호 작용할 수 있습니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . 자세한 내용은 [방법: 표준 메뉴 명령 수정](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)을 참조 하세요.

## <a name="deploying-the-dsl"></a>DSL 배포
 다른 사용자가 도메인별 언어를 사용할 수 있도록 하려면 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 확장 (VSIX) 파일을 배포 합니다. DSL 솔루션을 빌드할 때 만들어집니다.

 솔루션의 bin 폴더에서 .vsix 파일을 찾습니다. 설치 하려는 컴퓨터에 복사 합니다. 해당 컴퓨터에서 VSIX 파일을 두 번 클릭 합니다. DSL은 해당 컴퓨터의 모든 인스턴스에서 사용할 수 있습니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

 동일한 절차를 사용 하 여 자체 컴퓨터에 DSL을 설치할 수 있으므로의 실험적 인스턴스를 사용할 필요가 없습니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

 자세한 내용은 [도메인 특정 언어 솔루션 배포](../modeling/deploying-domain-specific-language-solutions.md)를 참조하세요.

## <a name="removing-old-experimental-dsls"></a><a name="Reset"></a> 이전 실험적 Dsl 제거
 더 이상 원치 않는 실험적 Dsl을 만든 경우 실험적 인스턴스를 다시 설정 하 여 컴퓨터에서 제거할 수 있습니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

 그러면 모든 실험적 Dsl 및 기타 실험적 확장을 컴퓨터에서 제거 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 합니다. 이러한 확장은 디버깅 모드에서 실행 된 확장입니다.

 이 절차는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] VSIX 파일을 실행 하 여 완전히 설치 된 dsl 또는 기타 확장을 제거 하지 않습니다.

#### <a name="to-reset-the-visual-studio-experimental-instance"></a>Visual Studio 실험적 인스턴스를 다시 설정 하려면

1. **시작**, **모든 프로그램**, **Microsoft Visual Studio 2010 SDK**, **도구**를 차례로 클릭 한 다음 **Microsoft Visual Studio 2010 실험적 인스턴스를 다시 설정**합니다.

2. 계속 사용 하려는 실험적 Dsl 또는 기타 실험적 확장을 다시 빌드합니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

## <a name="see-also"></a>관련 항목
 [모델, 클래스 및 관계 이해](../modeling/understanding-models-classes-and-relationships.md) [도메인별 언어](../modeling/how-to-define-a-domain-specific-language.md) [Visualizaton 및 모델링 SDK](https://www.microsoft.com/download/details.aspx?id=48148) 를 정의 하는 방법
