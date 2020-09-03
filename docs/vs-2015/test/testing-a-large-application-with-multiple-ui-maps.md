---
title: 여러 UI 맵이 포함된 대형 애플리케이션 테스트 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, multiple UI maps
- coded UI tests, for large applications
ms.assetid: 6e1ae9ec-e9b1-458a-bd96-0eb15e46f1d5
caps.latest.revision: 24
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2f6936811ea753d66d212facdda627930fb1ab10
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672132"
---
# <a name="testing-a-large-application-with-multiple-ui-maps"></a>여러 UI 맵이 포함된 대형 애플리케이션 테스트
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 항목에서는 여러 UI 맵을 사용하여 대규모 애플리케이션을 테스트하는 경우 코딩된 UI 테스트를 사용하는 방법에 대해 설명합니다.

 **요구 사항**

- Visual Studio Enterprise

  새 코딩 된 UI 테스트를 만들 때 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 테스트 프레임 워크는 기본적으로 [UIMap](/previous-versions/dd580454(v=vs.140)) 클래스에서 테스트에 대 한 코드를 생성 합니다. 코딩된 UI 테스트를 기록하는 방법에 대한 자세한 내용은 [코딩된 UI 테스트 만들기](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate) 및 [코딩된 UI 테스트 분석](../test/anatomy-of-a-coded-ui-test.md)을 참조하세요.

  UI 맵에 대해 생성된 코드에는 테스트가 상호 작용하는 각 개체에 대한 클래스가 들어 있습니다. 특히 각각 생성된 메서드의 경우 메서드 매개 변수의 도우미 클래스가 특별히 해당 메서드를 위해 생성됩니다. 애플리케이션에 개체, 페이지, 폼 및 컨트롤이 매우 많으면 UI 맵이 매우 커질 수 있습니다. 또한 테스트 작업을 하는 사람이 여러 명인 경우 하나의 큰 UI 맵 파일로 애플리케이션을 통제하기 힘들어집니다.

  UI 맵 파일을 여러 개 사용하면 다음과 같은 이점을 얻을 수 있습니다.

- 각 맵은 애플리케이션의 논리적 하위 집합과 연결될 수 있습니다. 그러면 변경 내용을 보다 쉽게 관리할 수 있습니다.

- 각 테스터는 애플리케이션의 다른 섹션에 대한 작업을 수행 중인 다른 테스터를 방해하지 않고 애플리케이션의 한 섹션에 대한 작업을 수행하고 코드를 검사할 수 있습니다.

- UI의 다른 부분에 대한 테스트에 미치는 영향을 최소화하면서 애플리케이션 UI에 대한 추가 기능을 증분식으로 확장할 수 있습니다.

## <a name="do-you-need-multiple-ui-maps"></a>여러 UI 맵이 필요하나요?
 각각 다음과 같은 유형의 상황에서 UI 맵을 여러 개 만드세요.

- 여러 복합 UI 컨트롤의 복잡한 집합이 함께 논리 연산을 수행(예: 웹 사이트의 등록 페이지 또는 쇼핑 카트의 구매 페이지)

- 독립 컨트롤 집합을 애플리케이션의 다양한 지점에서 액세스(예: 여러 작업 페이지가 있는 마법사). 마법사의 각 페이지가 특히 더 복잡한 경우 각 페이지에 대한 개별 UI 맵을 만들 수 있습니다.

## <a name="adding-multiple-ui-maps"></a>여러 UI 맵 추가

#### <a name="to-add-a-ui-map-to-your-coded-ui-test-project"></a>코딩된 UI 테스트 프로젝트에 UI 맵을 추가하려면

1. **솔루션 탐색기**에서 코딩된 UI 테스트 프로젝트에 모든 UI 맵을 저장할 폴더를 만들려면 코딩된 UI 테스트 프로젝트 파일을 마우스 오른쪽 단추로 클릭하고 **추가**를 가리킨 다음 **새 폴더**를 선택합니다. 예를 들어 이 폴더의 이름을 `UIMaps`라고 지정해 봅니다.

    새 폴더는 코딩된 UI 테스트 프로젝트 아래에 표시됩니다.

2. `UIMaps` 폴더를 마우스 오른쪽 단추로 클릭하고 **추가**를 가리킨 다음 **새 항목**을 선택합니다.

    **새 항목 추가** 대화 상자가 표시됩니다.

   > [!NOTE]
   > 코딩된 UI 테스트 프로젝트 내에 있어야 새로 코딩된 UI 테스트 맵을 추가할 수 있습니다.

3. 목록에서 **코딩된 UI 테스트 맵**을 선택합니다.

    **이름** 상자에 새 UI 맵의 이름을 입력합니다. 해당 맵이 나타낼 구성 요소 또는 페이지의 이름을 사용합니다(예: `HomePageMap`).

4. **추가**를 선택합니다.

    [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 창이 최소화되고 **코딩된 UI 테스트 빌더** 대화 상자가 표시됩니다.

5. 첫 번째 메서드에 대한 작업을 기록하고 **코드 생성**을 선택합니다.

6. 첫 번째 구성 요소 또는 페이지에 대한 모든 작업 및 어설션을 기록한 다음, 메서드로 그룹화한 후 **코딩된 UI 테스트 빌더** 대화 상자를 닫습니다.

7. 계속해서 UI 맵을 만듭니다. 작업 및 어설션을 기록한 다음 각 구성 요소의 메서드로 그룹화한 후 코드를 생성합니다.

   대부분 모든 마법사, 폼 및 페이지의 경우 애플리케이션의 최상위 창은 일정하게 남아 있습니다. 각 UI 맵에 최상위 창에 대한 클래스가 있더라도 모든 맵은 아마도 애플리케이션의 모든 구성 요소가 실행되는 동일한 최상위 창을 참조할 것입니다. 코딩된 UI 테스트는 최상위 창에서 시작하여 위에서 아래로 계층적으로 컨트롤을 검색합니다. 따라서 복잡한 애플리케이션에서는 실제 최상위 창이 모든 UI 맵에 중복되어 있을 수 있습니다. 실제 최상위 창이 중복된 경우 해당 창이 변경되면 여러 가지 수정 사항이 발생합니다. 이로 인해 UI 맵 간에 전환 시 성능 문제가 발생할 수 있습니다.

   이러한 영향을 최소화하려면 `CopyFrom()` 메서드를 사용하여 해당 UI 맵의 새 최상위 창이 주 최상위 창과 동일한지 확인할 수 있습니다.

## <a name="example"></a>예제
 다음 예는 다양한 UI 맵에서 생성된 클래스로 표현되는 각 구성 요소 및 해당 자식 컨트롤에 액세스할 수 있는 유틸리티 클래스의 일부입니다.

 이 예제에서는 `Contoso`라는 웹 애플리케이션에 홈 페이지, 제품 페이지 및 쇼핑 카트 페이지가 있습니다. 이러한 각 페이지는 브라우저 창인 공통 최상위 창을 공유합니다. 각 페이지에 대한 UI 맵이 있으며 유틸리티 클래스에는 다음과 유사한 코드가 있습니다.

```csharp
using ContosoProject.UIMaps;
using ContosoProject.UIMaps.HomePageClasses;
using ContosoProject.UIMaps.ProductPageClasses;
using ContosoProject.UIMaps.ShoppingCartClasses;

namespace ContosoProject
{
    public class TestRunUtility
    {
        // Private fields for the properties
        private HomePage homePage = null;
        private ProductPage productPage = null;
        private ShoppingCart shoppingCart = null;

        public TestRunUtility()
        {
            homePage = new HomePage();
        }

        // Properties that get each UI Map
        public HomePage HomePage
        {
            get { return homePage; }
            set { homePage = value; }
        }

        // Gets the ProductPage from the ProductPageMap.
        public ProductPage ProductPageObject
        {
            get
            {
                if (productPage == null)
                {
                    // Instantiate a new page from the UI Map classes
                    productPage = new ProductPage();

                    // Since the Product Page and Home Page both use
                    // the same browser page as the top level window,
                    // get the top level window properties from the
                    // Home Page.
                    productPage.UIContosoFinalizeWindow.CopyFrom(
                        HomePage.UIContosoWindowsIWindow);
                }
                return productPage;
            }
        }

    // Continue to create properties for each page, getting the
    // page object from the corresponding UI Map and copying the
    // top level window properties from the Home Page.
}
```

## <a name="see-also"></a>참고 항목

- [UIMap](/previous-versions/dd580454(v=vs.140))
- <xref:Microsoft.VisualStudio.TestTools.UITesting.BrowserWindow.CopyFrom%2A>
- [UI 자동화를 사용 하 여 코드 테스트](../test/use-ui-automation-to-test-your-code.md)
- [코딩 된 UI 테스트 만들기](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)
- [코딩된 UI 테스트 분석](../test/anatomy-of-a-coded-ui-test.md)
