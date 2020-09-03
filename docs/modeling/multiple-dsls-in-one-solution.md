---
title: 하나의 솔루션에 여러 DSL 포함
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f2eef29db24da3be0a9376ea76a9a1a551af9e1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542599"
---
# <a name="multiple-dsls-in-one-solution"></a>하나의 솔루션에 여러 DSL 포함

여러 DSL이 함께 설치되도록 단일 솔루션의 일부분으로 패키지할 수 있습니다.

다양한 기술을 통해 여러 DSL을 통합할 수 있습니다. 자세한 내용은 [Visual Studio를 사용 하 여 모델 통합 Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md) 및 [방법: 끌어서 놓기 처리기 추가](../modeling/how-to-add-a-drag-and-drop-handler.md) 및 [복사 동작 사용자 지정](../modeling/customizing-copy-behavior.md)을 참조 하세요.

## <a name="build-more-than-one-dsl-in-the-same-solution"></a>동일한 솔루션에 두 개 이상의 DSL 빌드

1. 새 **VSIX 프로젝트** 프로젝트를 만듭니다.

2. VSIX 솔루션 디렉터리에 둘 이상의 DSL 프로젝트를 만듭니다.

   - 각 DSL에 대해 새 Visual Studio 인스턴스를 엽니다. 새 DSL을 만들고 VSIX 솔루션과 같은 솔루션 폴더를 지정합니다.

   - 각 DSL을 서로 다른 파일 확장명으로 만들어야 합니다.

   - **Dsl** 및 **dslpackage** 프로젝트의 이름을 모두 다른 것으로 변경 합니다. 예: `Dsl1`, `DslPackage1`, `Dsl2`, `DslPackage2`.

   - 각 **Dslpackage \* \ source.extension.tt**에서이 줄을 올바른 Dsl 프로젝트 이름으로 업데이트 합니다.

      `string dslProjectName = "Dsl2";`

   - VSIX 솔루션에서 Dsl * 및 DslPackage 프로젝트를 추가 \* 합니다. 각 쌍을 자체 솔루션 폴더에 배치할 수 있습니다.

2. DSL의 VSIX 매니페스트를 결합합니다.

   1. _YourVsixProject_**\source.extension.manifest**를 엽니다.

   2. 각 DSL에 대해 **콘텐츠 추가** 를 선택 하 고 추가 합니다.

       - `Dsl*`**MEF 구성 요소인** project

       - `DslPackage*`**MEF 구성 요소인** project

       - `DslPackage*`**VS 패키지인** 프로젝트

3. 솔루션을 빌드합니다.

   그러면 생성되는 VSIX가 두 DSL을 모두 설치합니다. F5 키를 사용 하 여 테스트 하거나 _YourVsixProject_**를 배포할 수 \\ \* 있습니다.**

## <a name="see-also"></a>추가 정보

- [Visual Studio Modelbus를 사용하여 모델 통합](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [방법: 끌어서 놓기 처리기 추가](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [복사 동작 사용자 지정](../modeling/customizing-copy-behavior.md)