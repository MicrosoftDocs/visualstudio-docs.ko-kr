---
title: DSL 라이브러리를 사용 하 여 dsl 간에 클래스 공유 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 509bd96b-3e66-47f4-8642-771421d0d0d5
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 093cc277fa1cbe1915099fd9663fc1ccb797ca3a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671176"
---
# <a name="sharing-classes-between-dsls-by-using-a-dsl-library"></a>DSL 라이브러리를 사용하여 DSL 간에 클래스 공유
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]시각화 및 모델링 SDK에서 다른 dsl으로 가져올 수 있는 불완전 한 Dsl 정의를 만들 수 있습니다. 이렇게 하면 유사한 모델의 공통 요소를 지정할 수 있습니다.

## <a name="creating-and-using-dsl-libraries"></a>DSL 라이브러리 만들기 및 사용

#### <a name="to-create-a-dsl-library"></a>DSL 라이브러리를 만들려면

1. 새 DSL 프로젝트를 만들고 DSL 라이브러리 솔루션 템플릿을 선택 합니다.

     빈 모델을 사용 하 여 단일 DSL 프로젝트가 생성 됩니다.

2. 도메인 클래스, 관계, 셰이프 등을 추가할 수 있습니다.

     라이브러리의 요소는 단일 포함 트리를 구성할 필요가 없습니다.

     가져오기에서 사용할 수 있는 관계를 정의 하려면 두 개의 도메인 클래스를 만들고 두 개의 도메인 간에 관계를 만듭니다.

     도메인 클래스의 **상속 한정자** 를로 설정 하는 것이 좋습니다 `Abstract` .

3. DSL 탐색기에서 정의 하는 요소 (예: 연결 작성기)를 추가할 수 있습니다.

4. 유효성 검사 제약 조건과 같이 추가 코드가 필요한 사용자 지정 항목을 추가할 수 있습니다.

5. **모든 템플릿 변환**을 클릭 합니다.

6. 프로젝트를 빌드합니다.

7. 다른 사용자가 사용할 수 있도록 DSL을 배포 하는 경우 컴파일된 어셈블리 (DLL)와 파일을 모두 제공 해야 합니다 `DslDefinition.dsl` . 아래 폴더에서 컴파일된 어셈블리를 찾을 수 있습니다. `Dsl\bin\*`

#### <a name="to-import-a-dsl-library"></a>DSL 라이브러리를 가져오려면

1. 다른 DSL 정의의 dsl **탐색기**에서 dsl의 루트 클래스를 마우스 오른쪽 단추로 클릭 한 다음 **새 Dsllibrary 가져오기 추가**를 클릭 합니다.

2. 속성 창에서 라이브러리의 **파일 경로** 를 설정 합니다. 상대 경로 또는 절대 경로 중 하나를 사용할 수 있습니다.

    가져온 라이브러리는 DSL 탐색기에서 읽기 전용 모드로 표시 됩니다.

3. 가져온 클래스를 기본 클래스로 사용할 수 있습니다. 가져오기 DSL에서 도메인 클래스를 만들고, 속성 창에서 **기본 클래스** 를 가져온 클래스로 설정 합니다.

4. 모든 템플릿 변환을 클릭합니다.

5. Dsl 프로젝트에 DSL 라이브러리 프로젝트에 의해 빌드된 어셈블리 (DLL)에 대 한 참조를 추가 합니다.

6. 솔루션을 빌드합니다.

   DSL 라이브러리는 다른 라이브러리를 가져올 수 있습니다. 라이브러리를 가져올 때 해당 가져오기가 DSL 탐색기에도 자동으로 표시 됩니다.

## <a name="see-also"></a>관련 항목
 [도메인별 언어 정의 방법](../modeling/how-to-define-a-domain-specific-language.md)
