---
title: 다이어그램에 배경 이미지 설정
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7701bf0ba1467b481f6da64d3c2e229be77a7fe7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542586"
---
# <a name="setting-a-background-image-on-a-diagram"></a>다이어그램에 배경 이미지 설정
Visual Studio 시각화 및 모델링 SDK에서 사용자 지정 코드를 사용 하 여 생성 된 디자이너의 배경 이미지를 설정할 수 있습니다.

## <a name="setting-the-background-image"></a>배경 이미지 설정

#### <a name="to-set-a-background-image-for-a-generated-designer"></a>생성된 디자이너의 배경 이미지를 설정하려면

1. 다이어그램 배경으로 사용할 이미지 파일을 현재 프로젝트의 Dsl\Resources 디렉터리에 복사합니다.

2. **솔루션 탐색기**에서 Dsl\Resources 폴더를 마우스 오른쪽 단추로 클릭 하 고 **추가**를 가리킨 다음 **기존 항목**을 클릭 합니다.

3. **기존 항목 추가** 대화 상자에서 Dsl\Resources 폴더로 이동 합니다.

4. **파일 형식** 목록에서 **이미지 파일**을 클릭 합니다.

5. 디렉터리에 복사한 이미지 파일을 클릭 한 다음 **추가**를 클릭 합니다.

6. Dsl을 마우스 오른쪽 단추로 클릭 하 고 **속성** 을 클릭 하 여 dsl 프로젝트의 속성을 엽니다.

7. **리소스** 탭에서 **이 프로젝트에 기본 리소스 파일이 없습니다 .를 클릭 합니다. 만들려면 여기를 클릭 하십시오.**

8. **솔루션 탐색기** 의 그림을 리소스 창으로 끌어 리소스 파일에 이미지 파일을 추가 합니다.

9. 파일 메뉴를 열고 프로젝트 속성을 저장할 옵션을 클릭합니다.

10. Dsl\Properties\Resources.resx 파일이 있으며 그 아래에 Resources.Designer.cs 파일이 있는지 확인합니다.

11. Resources.Designer.cs이 없는 경우 **솔루션 탐색기**에서 파일 리소스 .resx를 클릭 합니다.

12. **속성** 창에서 `Custom Tool` 속성을 `ResXFileCodeGenerator`로 설정합니다.

13. **솔루션 탐색기**에서 Dsl 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **추가**를 가리킨 다음 **새 폴더**를 클릭 합니다.

14. 폴더 이름을 **Custom으로 지정**합니다.

15. 사용자 지정 폴더를 마우스 오른쪽 단추로 클릭 하 고 **추가**를 가리킨 다음 **새 항목**을 클릭 합니다.

16. **새 항목 추가** 대화 상자의 **템플릿** 목록에서 **코드 파일**을 클릭 합니다.

17. **이름** 상자에 `BackgroundImage.cs` 를 입력 하 고 **추가**를 클릭 합니다.

18. 네임스페이스, 다이어그램 클래스 이름 및 이미지 파일 리소스 이름을 조정하여 다음 코드를 BackgroundImage.cs 파일에 복사합니다.

     "MyDiagramClass"는 Dsl\GeneratedCode\Diagrams.cs에 정의된 다이어그램 partial 클래스의 이름으로 바꿉니다. Dsl\GeneratedCode\Diagrams.cs 파일에서 정확한 네임스페이스를 검색할 수도 있습니다.

    ```csharp
    using System;
    using Microsoft.VisualStudio.Modeling.Diagrams;

    // Fix the namespace:
    namespace Fabrikam.MyLanguage
    {
      // Fix the Diagram Class name - get it from GeneratedCode\Diagram.cs

      public partial class Language29Diagram
      {
        protected override void InitializeInstanceResources()
        {
          // Fix the Resources namespace and the Image resource name:
          ImageField backgroundField = new ImageField("background",
              Fabrikam.MyLanguage.Properties.Resources.MyPicture);

          backgroundField.DefaultFocusable = false;
          backgroundField.DefaultSelectable = false;
          backgroundField.DefaultVisibility = true;
          backgroundField.DefaultUnscaled = false;

          shapeFields.Add(backgroundField);

          backgroundField.AnchoringBehavior
            .SetTopAnchor(AnchoringBehavior.Edge.Top, 0.01);
          backgroundField.AnchoringBehavior
            .SetLeftAnchor(AnchoringBehavior.Edge.Left, 0.01);
          backgroundField.AnchoringBehavior
            .SetRightAnchor(AnchoringBehavior.Edge.Right, 0.01);
          backgroundField.AnchoringBehavior
            .SetBottomAnchor(AnchoringBehavior.Edge.Bottom, 0.01);

          base.InitializeInstanceResources();
        }
      }
    }
    ```

     프로그램 코드를 사용 하 여 모델을 사용자 지정 하는 방법에 대 한 자세한 내용은 [프로그램 코드에서 모델 탐색 및 업데이트](../modeling/navigating-and-updating-a-model-in-program-code.md)를 참조 하세요.

## <a name="see-also"></a>추가 정보

- [모양 및 연결선 정의](../modeling/defining-shapes-and-connectors.md)
- [텍스트 및 이미지 필드 사용자 지정](../modeling/customizing-text-and-image-fields.md)
- [프로그램 코드에서 모델 탐색 및 업데이트](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [도메인별 언어를 사용자 지정하는 코드 작성](../modeling/writing-code-to-customise-a-domain-specific-language.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
