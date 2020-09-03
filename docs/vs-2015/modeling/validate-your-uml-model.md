---
title: UML 모델 유효성 검사 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML, constraints
- UML, validation
ms.assetid: deed5092-c11d-4431-a801-1e866a103075
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8dfaf19e358d96b7737b06880d6fa4581b5c54f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659366"
---
# <a name="validate-your-uml-model"></a>UML 모델 유효성 검사
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio에서 그릴 수 있는 일부 UML 모델은 프로젝트에서 잘못된 것으로 간주할 수 있습니다. 예를 들어 사용 사례의 행위자를 나타내는 수명선이 있는 시퀀스 다이어그램에 항상 사용 사례가 연결되도록 할 수 있습니다. 팀이 이와 같은 요구 사항을 준수 하는 데 도움이 되는 *제약 조건을* 설치 하거나 정의할 수 있습니다. 제약 조건은 사용자가 모델을 저장하거나 열 때 적용할 수 있는 메뉴 명령으로 호출할 수 있습니다.

 제약 조건은 팀에서 UML 모델을 해석 및 사용하는 방법에 따라 달라지므로 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에는 제공되지 않습니다. 그러나 고유한 제약 조건을 정의하고 다른 사용자가 정의한 제약 조건을 설치할 수 있습니다. 제약 조건을 정의 하 고 배포를 위해 패키지를 배포 하는 방법을 알아보려면 [UML 모델에 대 한 유효성 검사 제약 조건 정의](../modeling/define-validation-constraints-for-uml-models.md)를 참조 하세요.

## <a name="invoking-validation"></a>유효성 검사 호출
 유효성 검사 확장을 설치한 경우 확장이 제공하는 제약 조건이 적용될 수 있는 경우는 다음과 같습니다. 일부 제약 조건은 이러한 몇몇 사례에서만 적용되도록 설정됩니다.

- **유효성 검사 명령입니다.** 언제 든 지 유효성 검사를 호출 하려면 **아키텍처** 메뉴에서 **UML 모델 유효성 검사** 를 클릭 합니다.

  > [!NOTE]
  > 유효성 검사 제약 조건이 설치된 경우에만 명령이 나타납니다.

- **모델 저장 시** 모델을 저장할 때 유효성 검사 제약 조건이 적용될 수 있습니다. 이들 제약 조건을 사용하면 프로젝트 해석에 따라 잘못된 모델을 저장하지 않게 할 수 있습니다.

   오류가 있으면 모델을 저장할지 묻는 메시지가 표시됩니다. 오류를 수정하거나 모델을 그대로 저장하도록 선택할 수 있습니다.

- **모델을 열 때.** 모델을 저장할 때 있던 오류 메시지를 복원하기 위해, 모델을 열 때 유효성 검사 메서드가 적용될 수 있습니다. 모델의 다른 파트에서 작업 중인 사용자가 적용한 변경 내용 간 불일치로 인해 오류가 도입될 수도 있습니다. 자세한 내용은 [모델 공유 및 다이어그램 내보내기](../modeling/share-models-and-exporting-diagrams.md)를 참조 하세요.

  유효성 검사 오류는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 오류 창에 보고됩니다.

  다이어그램에서 잘못된 요소를 선택하려면 오류를 두 번 클릭합니다. 이 방법은 잘못된 요소가 열린 다이어그램에 표시된 경우에만 사용할 수 있습니다.

## <a name="installing-validation-constraints"></a>유효성 검사 제약 조건 설치
 제약 조건은 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 확장(VSIX) 파일 내에 패키지됩니다. 일반적으로 제약 조건 집합은 메뉴 명령, 프로필, 도구 상자 항목 등의 기타 정의를 포함하는 확장의 파트입니다.

#### <a name="to-install-a-visual-studio-extension"></a>Visual Studio 확장을 설치하려면

1. Windows 탐색기 (또는 파일 탐색기)에서 **.vsix** 파일을 두 번 클릭 합니다.

2. 이미 실행 중인 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]의 인스턴스를 다시 시작합니다.

## <a name="disabling-and-uninstalling-validation-constraints"></a>유효성 검사 제약 조건 사용 안 함 및 제거
 제약 조건이 적용되지 않은 모델을 사용하려는 경우 제약 조건이 포함된 확장을 일시적으로 사용하지 않도록 설정할 수 있습니다. 이 방법으로 여러 가지 확장을 사용하거나 사용하지 않도록 설정하여 서로 다른 시간에 다양한 모델을 사용할 수 있습니다.

#### <a name="to-disable-or-uninstall-a-visual-studio-extension"></a>Visual Studio 확장을 사용하지 않도록 설정하거나 제거하려면

1. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **도구** 메뉴에서 **확장 및 업데이트**를 클릭합니다.

2. 확장과 함께 **사용 안 함** 을 클릭 하 여 확장을 일시적으로 사용 하지 않도록 설정 합니다. 나중에 **확장 및 업데이트** 창으로 돌아가 다시 사용 하도록 설정할 수 있습니다.

     \- 또는 -

     **제거** 를 클릭 하 여 확장을 제거 합니다.

3. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]를 다시 시작합니다.

## <a name="see-also"></a>참고 항목
 [UML 모델에 대 한 유효성 검사 제약 조건 정의](../modeling/define-validation-constraints-for-uml-models.md) [개발 프로세스에서 앱 사용 모델](../modeling/use-models-in-your-development-process.md) 에 [대 한 모델 만들기](../modeling/create-models-for-your-app.md)
