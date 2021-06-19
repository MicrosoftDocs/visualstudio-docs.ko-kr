---
title: DSL 라이브러리를 사용하여 DSL 간에 클래스 공유
description: 시각화 및 모델링 SDK Visual Studio 다른 DSL로 가져올 수 있는 불완전한 DSL 정의를 만들 수 있습니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c3729e4f386ec5a21c8f30ee3f0df6e7ffa8d891
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385502"
---
# <a name="sharing-classes-between-dsls-by-using-a-dsl-library"></a>DSL 라이브러리를 사용하여 DSL 간에 클래스 공유
시각화 및 모델링 SDK Visual Studio 다른 DSL로 가져올 수 있는 불완전한 DSL 정의를 만들 수 있습니다. 이렇게 하면 유사한 모델의 공통 부분을 고려해 볼 수 있습니다.

## <a name="creating-and-using-dsl-libraries"></a>DSL 라이브러리 만들기 및 사용

#### <a name="to-create-a-dsl-library"></a>DSL 라이브러리를 만들려면

1. 새 DSL 프로젝트를 만들고 DSL 라이브러리 솔루션 템플릿을 선택합니다.

     빈 모델을 통해 단일 DSL 프로젝트가 만들어집니다.

2. 도메인 클래스, 관계, 셰이프 등을 추가할 수 있습니다.

     라이브러리의 요소는 단일 포함 트리를 형성할 필요가 없습니다.

     가져오기에서 사용할 수 있는 관계를 정의하려면 두 도메인 클래스를 만들고 두 도메인 클래스 간의 관계를 만듭니다.

     도메인 클래스의 **상속 한정자를** 로 설정하는 것이 `Abstract` 좋습니다.

3. DSL 탐색기에서 정의한 요소(예: 연결 작성기)를 추가할 수 있습니다.

4. 유효성 검사 제약 조건과 같은 추가 코드가 필요한 사용자 지정을 추가할 수 있습니다.

5. **모든 템플릿 변환을 클릭합니다.**

6. 프로젝트를 빌드합니다.

7. 다른 사람이 사용할 수 있도록 DSL을 배포하는 경우 컴파일된 어셈블리(DLL)와 파일을 모두 제공해야 `DslDefinition.dsl` 합니다. 아래의 폴더에서 컴파일된 어셈블리를 찾을 수 있습니다. `Dsl\bin\*`

#### <a name="to-import-a-dsl-library"></a>DSL 라이브러리를 가져오려면

1. 다른 DSL 정의의 **DSL 탐색기 에서 DSL의** 루트 클래스를 마우스 오른쪽 단추로 클릭한 다음 **새 DslLibrary 가져오기 추가를** 클릭합니다.

2. 속성 창 라이브러리의 **파일 경로를** 설정합니다. 상대 경로 또는 절대 경로를 사용할 수 있습니다.

    가져온 라이브러리는 DSL 탐색기에서 읽기 전용 모드로 표시됩니다.

3. 가져온 클래스를 기본 클래스로 사용할 수 있습니다. 가져오는 DSL에서 도메인 클래스를 만들고 속성 창 **기본 클래스를** 가져온 클래스로 설정합니다.

4. 모든 템플릿 변환을 클릭합니다.

5. DSL 라이브러리 프로젝트에서 빌드한 어셈블리(DLL)에 대한 참조를 DSL 프로젝트에 추가합니다.

6. 솔루션을 빌드합니다.

   DSL 라이브러리는 다른 라이브러리를 가져올 수 있습니다. 라이브러리를 가져올 때 해당 가져오기도 DSL 탐색기에 자동으로 표시됩니다.

## <a name="see-also"></a>참조

- [도메인별 언어 정의 방법](../modeling/how-to-define-a-domain-specific-language.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
