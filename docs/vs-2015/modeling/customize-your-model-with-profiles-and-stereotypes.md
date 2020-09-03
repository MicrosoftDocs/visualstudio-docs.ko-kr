---
title: 프로필 및 스테레오 타입을 사용 하 여 모델 사용자 지정 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, profiles
- UML model, stereotypes
- UML model, customizing
ms.assetid: fd607157-0d3a-4583-a84e-427a4b2a5acb
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b634b11418ef2d4220dc4eb07c825b514ab5494c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74301203"
---
# <a name="customize-your-model-with-profiles-and-stereotypes"></a>프로필 및 스테레오타입을 사용하여 모델 사용자 지정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio에서 클래스 및 구성 요소와 같은 표준 UML 모델 요소를 조정하여 특정 용도에 맞게 사용자 지정할 수 있습니다. 요소의 속성 목록을 변경할 수 있는 모델 요소에 *스테레오 타입* 을 적용할 수 있습니다. 스테레오 타입은 *프로필*이라는 컬렉션 내에 정의 됩니다.

 이 기능을 지원하는 Visual Studio 버전을 확인하려면 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)을 참조하세요.

 스테레오타입을 사용하려면 패키지를 프로필에 연결합니다. 이렇게 하면 프로필에 정의된 스테레오타입을 패키지의 요소에 적용할 수 있습니다. 일부 프로필은 Visual Studio와 함께 설치됩니다. 또한 고유한 프로필을 정의할 수 있습니다.

 스테레오타입은 요소의 속성 목록에서 설정할 수 있습니다. 다이어그램에 있는 주요 모양의 경우 예제에서와 같이 적용된 스테레오타입이 모양에도 나타납니다.

 ![스테레오타입을 포함하는 UML 클래스](../modeling/media/uml-class-stereotype.png "UML_class_stereotype")

> [!NOTE]
> 프로필을 사용하여 모델을 만들고 모델을 다른 사용자와 공유할 경우 컴퓨터에 같은 프로필을 설치해야 스테레오타입을 볼 수 있습니다.

## <a name="related-topics"></a>관련 항목

|제목|설명|
|-----------|-----------------|
|[UML 모델 요소에 스테레오타입 추가](../modeling/add-stereotypes-to-uml-model-elements.md)|패키지에 모델 요소 배치, 프로필에 패키지 연결 및 요소에 스테레오타입 적용.|
|[UML 모델의 표준 스테레오타입](../modeling/standard-stereotypes-for-uml-models.md)|UML 표준 프로필 L2 및 L3은 Visual Studio와 함께 설치되고 모든 모델은 기본적으로 이러한 프로필에 연결됩니다. 이러한 프로필은 모델을 주석으로 처리하는 데 사용할 수 있는 스테레오타입을 제공합니다.<br /><br /> 예를 들어 «specification» 스테레오타입을 클래스에 적용하여 외부에 표시되는 동작만 정의하려는 의도를 나타낼 수 있습니다.|
|[프로필을 정의하여 UML 확장](../modeling/define-a-profile-to-extend-uml.md)|고유한 애플리케이션 영역에 맞게 조정된 고유한 스테레오타입 및 도구를 정의할 수 있습니다.<br /><br /> 예를 들어 뱅킹 소프트웨어를 개발하는 경우 클래스에 적용될 수 있는 «Account» 스테레오타입을 정의할 수 있습니다. 그다음에 클래스 다이어그램을 사용하여 다양한 계정 형식 및 해당 관계를 설명할 수 있습니다.|
|[UML 프로필 설치](../modeling/install-a-uml-profile.md)|누군가 UML 프로필을 제공하면 컴퓨터에 이 프로필을 설치할 수 있습니다.|
|[사용자 지정 모델링 도구 상자 항목 정의](../modeling/define-a-custom-modeling-toolbox-item.md)|사용자 지정 도구 상자 항목을 사용하면 새 요소에서 스테레오타입을 반복해서 설정할 필요가 없습니다.|
