---
title: UML 모델 및 다이어그램 확장 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending
- UML model, extending
ms.assetid: b5bfa61e-ea59-4c3b-b5af-53475d7d13cd
caps.latest.revision: 39
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ee4e307040f22078ed66f897eaa868ccfd259577
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "82586724"
---
# <a name="extend-uml-models-and-diagrams"></a>UML 모델 및 다이어그램 확장
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 항목에서는 Visual Studio와 함께 제공된 UML 모델링 도구를 확장할 수 있는 다양한 방법을 간략하게 설명합니다. 각 모델 유형 및 도구를 지원하는 Visual Studio 버전을 확인하려면 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)을 참조하세요.

 다음 예제 시나리오에서 Fabrikam은 공항 수하물 처리 시스템을 설계 및 설치합니다. 공항 프로젝트 간에는 기본 장비 및 장비를 제어하는 소프트웨어에 많은 공통점이 있습니다. 그러나 컨베이어 벨트, 체크인 데스크, 스토리지 창고, 기타 가방 처리 장비와 같은 여러 가지 요소가 크게 달라질 수 있습니다.

 새 프로젝트를 시작할 때 Fabrikam 팀은 팀 내에서, 그리고 고객과 함께 이러한 요구 사항을 논의하는 데 도움이 되는 UML 모델을 만듭니다. 팀에서는 동작 다이어그램을 사용하여 가방 흐름을 표시하고 개체 노드를 사용하여 각 장비를 표시합니다. UML 모델은 시스템 코드를 직접 나타내지 않습니다.

 Fabrikam의 도구 팀에서는 개발 팀을 지원하기 위해 다양한 기능을 향상합니다. 다음 섹션에서는 사용자가 정의할 수 있는 다양한 확장 종류를 설명합니다. 이러한 여러 방법 중 몇 가지를 단일 Visual Studio 확장으로 결합할 수 있습니다.

 자세한 내용은 다음 비디오를 참조 하세요. MSDN ![링크 비디오](../data-tools/media/playvideo.gif "링크 playvideo 보려면")[MSDN 방법 I 시리즈: UML 도구 및 확장성](https://msdn.microsoft.com/vstudio/ff859492).

## <a name="requirements"></a><a name="Requirements"></a> 요구 사항

- [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md).

- [Visual Studio 2015용 SDK 모델링](https://www.microsoft.com/download/details.aspx?id=48148).

## <a name="profiles"></a>Profiles
 프로필을 통해 UML 요소에 대한 스테레오타입 및 추가 속성을 정의할 수 있습니다.

 Fabrikam의 도구 개발자는 동작 다이어그램의 개체 노드에서 스테레오타입을 정의합니다(예: «conveyor belt» 및 «checkin desk»). 팀 멤버가 동작 다이어그램을 사용하여 수하물 처리 체계를 만들 때 도구 개발자는 스테레오타입을 설정하여 각 노드가 나타내는 장비 형식을 지정할 수 있습니다. 도구 개발자가 일부 스테레오타입에 대한 추가 속성을 정의하므로 사용자는 컨베이어 벨트 용량 및 체크인 데스크 손잡이(handedness)과 같은 값을 기록할 수 있습니다.

 자세한 내용은 [프로필을 정의 하 여 UML 확장](../modeling/define-a-profile-to-extend-uml.md)을 참조 하세요.

## <a name="custom-toolbox-items"></a>사용자 지정 도구 상자 항목
 사용자 지정 도구 상자 항목은 다이어그램에서 정의한 프로토타입을 기반으로 요소 또는 요소 그룹을 만듭니다. 예를 들어 특정 색 또는 스테레오타입으로 사용 사례를 만들거나 디자인 패턴을 나타내는 클래스 및 연관 그룹을 만드는 도구를 만들 수 있습니다. 이러한 도구 상자 항목을 Visual Studio 확장에 추가하고 다른 사용자에게 배포할 수 있습니다.

 자세한 내용은 [사용자 지정 모델링 도구 상자 항목 정의](../modeling/define-a-custom-modeling-toolbox-item.md)를 참조 하세요.

## <a name="validation"></a>유효성 검사
 UML 모델이 지정된 제약 조건을 준수하는지 확인하는 규칙을 정의할 수 있습니다.

 Fabrikam의 도구 개발자는 팀 멤버가 수하물 처리 모델에서 단순한 실수를 피하도록 도와주는 규칙을 정의합니다. 예를 들어 체크인 데스크를 스토리지 창고에 직접 연결할 수 없습니다. 체크인 데스크와 저장 창고 사이에 적어도 컨베이어 벨트가 있어야 합니다.

 자세한 내용은 [UML 모델에 대 한 유효성 검사 제약 조건 정의](../modeling/define-validation-constraints-for-uml-models.md)를 참조 하세요.

## <a name="menu-commands"></a>메뉴 명령
 UML 다이어그램에서 요소를 마우스 오른쪽 단추로 클릭하여 사용자가 호출할 수 있는 명령을 정의할 수 있습니다. 명령으로 모델과 다이어그램을 업데이트하거나 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]에서 다른 작업을 수행할 수 있습니다.

 Fabrikam은 메뉴 명령을 정의하여 체크인 데스크를 만들고 선택된 컨베이어 벨트와 연결하거나 회사의 레이아웃 규칙에 따라 다이어그램을 다시 정렬하는 등의 자주 수행되는 작업을 자동화합니다.

 [모델링 다이어그램의 메뉴 명령 정의](../modeling/define-a-menu-command-on-a-modeling-diagram.md)를 참조 하세요.

## <a name="gestures"></a>제스처
 사용자가 다이어그램 요소를 두 번 클릭하거나 다이어그램 또는 다이어그램의 요소로 끌어서 사용자가 시작하는 명령을 정의할 수 있습니다. 다른 UML 다이어그램, Visual Studio의 다른 부분 또는 다른 애플리케이션이나 Windows 탐색기(또는 파일 탐색기)에서 끌어 놓은 항목을 처리할 수 있는 명령을 정의할 수 있습니다.

 Fabrikam 팀 멤버는 Windows 바탕 화면에서 끌어서 사양과 같은 파일을 모델 요소와 연결할 수 있습니다. 도구 개발자는 요소에 파일 경로 속성을 제공하는 스테레오타입과 파일을 요소에 놓을 때 스테레오타입과 파일 경로를 설정하는 제스처를 정의했습니다.

 자세한 내용은 [모델링 다이어그램에서 제스처 처리기 정의](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)를 참조 하세요.

## <a name="responding-to-changes"></a>변경에 응답
 사용자 작업 또는 다른 프로그램 코드에 의해 발생하는지와 관계없이 모델의 변경에 응답하는 코드를 작성할 수 있습니다.

 Fabrikam의 개발자는 스테레오타입에 따라 요소 색을 자동으로 설정하는 코드를 만듭니다. 이렇게 하면 사용자가 모델에서 요소가 수행하는 역할을 쉽게 구분할 수 있습니다.

 자세한 내용은 [방법: UML 모델의 변경 내용에 응답](../misc/how-to-respond-to-changes-in-a-uml-model.md)을 참조 하세요.

## <a name="model-bus"></a>모델 버스
 모델 버스를 사용하여 다른 다이어그램이나 다른 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 확장에서 다이어그램 또는 모델에 액세스할 수 있습니다. 무엇보다 이를 통해 정보를 둘 이상의 모델에 전파하라 수 있으므로 여러 사람이 동시에 결합 모델에서 작업할 수 있습니다.

 Fabrikam은 동작 다이어그램의 요소를 사용하여 수하물 처리 장비를 나타냅니다. 장비의 각 항목은 또 다른 다이어그램에 더 자세한 사양이 있을 수 있고 이 다이어그램은 또 다른 모델이 될 수 있습니다. 수하물 흐름 다이어그램에 대한 유효성 검사 제약 조건은 다른 다이어그램에서 장비의 관련 속성을 검색할 수 있습니다. 다른 다이어그램에 대한 참조는 스테레오타입에 정의된 추가 속성에 저장됩니다.

 자세한 내용은 [UML 모델을 다른 모델 및 도구와 통합](../modeling/integrate-uml-models-with-other-models-and-tools.md)을 참조 하세요.

## <a name="generation"></a>Generation
 모델에서 프로그램 코드, 스크립트, 구성, 문서, 새 모델 또는 기타 아티팩트를 생성할 수 있습니다.

 Fabrikam이 설계한 수하물 시스템에서 대부분 프로그램 코드는 여러 프로젝트에서 동일합니다. 주요 변수 측면은 공항 주위의 수하물 흐름 계획입니다. 설계 팀에서는 처음 몇 프로젝트에 대한 경험을 확보한 후 도구 개발자가 수하물 흐름 모델을 기반으로 대부분 변수 프로그램 코드 및 기타 파일(예: 사용자 문서)을 생성하는 템플릿을 만듭니다. 이를 통해 새로운 각 프로젝트에 대한 개발 시간과 오류 비율이 크게 감소합니다.

 자세한 내용은 [UML 모델에서 파일 생성](../modeling/generate-files-from-a-uml-model.md)을 참조 하세요.

## <a name="team-foundation-server-integration"></a>Team Foundation Server 통합
 작업 항목을 모델 요소에 연결하고 연결된 항목에 프로그래밍 방식으로 액세스합니다.

 Fabrikam의 도구 개발자는 각 공항 프로젝트에 대한 작업 일정을 생성하는 도구를 작성합니다. 일정의 작업 항목은 모델 요소에 연결됩니다.

 자세한 내용은 [작업 항목 링크 처리기 정의](../modeling/define-a-work-item-link-handler.md)를 참조 하세요.

## <a name="tools-that-update-models"></a>모델을 업데이트하는 도구
 UML 모델을 로드할 수 있는 독립 실행형 애플리케이션 및 Visual Studio 확장을 만들 수 있습니다.

 Fabrikam의 개발자는 모델을 읽고 각 모델 요소의 작업 진행에 대한 보고서를 생성하는 도구를 만듭니다.

 자세한 내용은 [프로그램 코드에서 UML 모델 읽기](../modeling/read-a-uml-model-in-program-code.md)를 참조 하세요.

## <a name="domain-specific-languages"></a>도메인 특정 언어
 특정 모델 형식을 자주 사용할 경우 도메인 특정 언어를 만드는 것이 유용할 수 있습니다. UML 모델보다 더 밀접하게 비즈니스 요구 사항에 맞추면 도메인 특정 언어를 만들 수 있지만 빌드와 유지 관리에 더 많은 작업이 필요합니다. 자세한 내용은 [Visual Studio 용 모델링 SDK-도메인별 언어](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)를 참조 하세요.

## <a name="external-resources"></a>외부 리소스

|**범주**|**연결**|
|------------------|---------------|
|**비디오**|![비디오에 대 한 링크](../data-tools/media/playvideo.gif "링크 playvideo 보려면") [MSDN How Do DO 시리즈: UML 도구 및 확장성](https://msdn.microsoft.com/vstudio/ff859492)<br /><br /> ![비디오 채널 9에 대 한 링크](../data-tools/media/playvideo.gif "링크 playvideo 보려면") [: Visual Studio를 사용 하는 UML](https://channel9.msdn.com/posts/clinted/)|
|**포럼**|-   [Visual Studio 시각화 및 모델링 도구](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />-   [Visual Studio 시각화 및 모델링 SDK(DSL 도구)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|
|**Blogs**|[Visual Studio ALM + Team Foundation Server 블로그](https://devblogs.microsoft.com/devops/welcome-to-the-visual-studio-alm-team-foundation-server-blog/)|
|**기술 문서 및 저널**|[MSDN 아키텍처 센터](https://msdn.microsoft.com/architecture/default.aspx)|

## <a name="see-also"></a>관련 항목
 [UML 모델링 확장성에 대 한 앱 API 참조](../modeling/api-reference-for-uml-modeling-extensibility.md) [에 대 한 모델 만들기](../modeling/create-models-for-your-app.md)
