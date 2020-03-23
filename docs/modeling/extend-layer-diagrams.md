---
title: 종속성 다이어그램 확장
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, creating extensions
- layer models
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 305c562c7600dc6955ce0307db92f4e257fc1c21
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301490"
---
# <a name="extend-dependency-diagrams"></a>종속성 다이어그램 확장

코드를 작성하여 종속성 다이어그램을 만들고 업데이트하고 Visual Studio의 종속성 다이어그램에 대해 프로그램 코드의 구조를 검증할 수 있습니다. 다이어그램의 바로 가기(상황에 맞는) 메뉴에 표시되는 명령을 추가하고, 끌어서 놓기 제스처를 사용자 지정하고, 텍스트 템플릿에서 레이어 모델에 액세스할 수 있습니다. 이러한 확장을 VSIX(Visual Studio Integration Extension)로 패키징하고 다른 Visual Studio 사용자에게 배포할 수 있습니다.

## <a name="requirements"></a>요구 사항

레이어 확장을 개발하려는 컴퓨터에 다음이 설치되어 있어야 합니다.

- Visual Studio

- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)

- 비주얼 스튜디오를 위한 모델링 SDK

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

레이어 확장을 실행하려는 컴퓨터에 적합한 버전의 Visual Studio가 설치되어 있어야 합니다. 어떤 버전의 Visual Studio 지원 종속성 다이어그램을 확인하려면 [아키텍처 및 모델링 도구에 대한 에디션 지원을](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)참조하십시오.

## <a name="see-also"></a>참고 항목

- [종속성 다이어그램: 참조](../modeling/layer-diagrams-reference.md)
- [종속성 다이어그램: 지침](../modeling/layer-diagrams-guidelines.md)
- [코드에서 종속성 다이어그램 만들기](../modeling/create-layer-diagrams-from-your-code.md)
- [종속성 다이어그램을 사용하여 코드 유효성 검사](../modeling/validate-code-with-layer-diagrams.md)
