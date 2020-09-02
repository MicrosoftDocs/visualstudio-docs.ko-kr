---
title: 관리 코드에 대 한 라이브 코드 분석 범위 구성
ms.date: 03/23/2018
ms.topic: conceptual
helpviewer_keywords:
- live code analysis
- background analysis
- analysis scope
- full solution analysis
author: Mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 6df882d50d0c1d052191246605af856743ffdf3d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88249187"
---
# <a name="how-to-configure-live-code-analysis-scope-for-managed-code"></a>방법: 관리 코드에 대 한 라이브 코드 분석 범위 구성

## <a name="what-is-live-code-analysis-for-managed-code"></a>관리 코드에 대 한 "라이브 코드 분석" 이란?
Visual Studio는 편집기에서 소스 파일을 편집 하는 동안 *백그라운드 분석*이 라고도 하는 여러 라이브 코드 분석을 실행 합니다. 그 중 일부는 적절 한 Visual Studio IDE 편집 환경을 위한 최소한의 분석에 필요 합니다. 그 중 일부는 IDE 기능의 응답성 향상을 위한 것입니다. 그 중 일부는 Roslyn 분석기의 진단 및 코드 수정과 같은 추가 IDE 기능을 사용 하도록 설정 하는 것입니다. 이러한 분석은 기능에 따라 다음과 같이 그룹화 할 수 있습니다.

- **진단의 백그라운드 계산**: 소스 파일에서 오류, 경고 및 제안 사항을 계산 하는 데 대 한 분석입니다. 이러한 진단은 오류 목록에 항목으로 표시 되 고 편집기에 물결선로 표시 됩니다. 두 가지 범주로 분류할 수 있습니다.
  - C # 및 Visual Basic 컴파일러 진단
  - 다음을 포함 하는 Roslyn analyzer 진단

    - 코드 스타일 제안 사항에 대 한 기본 제공 IDE 분석기
    - 현재 솔루션의 프로젝트용으로 [설치 된](./install-roslyn-analyzers.md) 타사 analyzer 패키지입니다.

- **기타 백그라운드 분석**: IDE 기능의 응답성 및 Visual Studio 상호 작용을 개선 하는 분석입니다. 이러한 분석의 몇 가지 예는 다음과 같습니다.
  - 열려 있는 파일의 백그라운드 구문 분석입니다.
  - 특정 IDE 기능의 응답성 향상을 위해 기호를 제공 하기 위해 열려 있는 파일을 사용 하 여 프로젝트를 백그라운드에서 컴파일합니다.
  - 구문 및 기호 캐시 작성.
  - 소스 파일에 대 한 디자이너 연결 검색 (예: 폼, 컨트롤 등)

## <a name="default-analysis-scope"></a>기본 분석 범위

기본적으로 진단의 백그라운드 계산에 대 한 라이브 코드 분석은 Visual Studio에서 _열리는_ 모든 파일에 대해 실행 됩니다. 위에서 언급 한 _다른 배경 분석_ 중 일부는 열려 있는 파일이 하나 이상 있는 모든 프로젝트에 대해 실행 됩니다. 일부 백그라운드 분석은 전체 솔루션에 대해 실행 됩니다.

## <a name="custom-analysis-scope"></a>사용자 지정 분석 범위

대부분의 고객 시나리오와 솔루션에 대 한 최적의 사용자 환경, 기능 및 성능을 위해 각 백그라운드 분석의 기본 범위가 조정 되었습니다. 그러나 고객이 배경 분석을 낮추거나 늘리기 위해이 범위를 사용자 지정 하려는 경우가 있습니다. 예를 들면 다음과 같습니다.

- 절전 모드: 사용자가 노트북 배터리를 실행 하는 경우 더 긴 배터리 수명 동안 전원 소비를 최소화 하는 것이 좋습니다. 이 시나리오에서는 백그라운드 분석을 최소화 하려고 합니다.
- 주문형 코드 분석: 사용자가 라이브 분석기 실행을 해제 하 고 요청 시 수동으로 코드 분석을 실행 하는 것을 선호 하는 경우 백그라운드 분석을 최소화 하려고 합니다. [방법: 요청 시 수동으로 코드 분석 실행을](./how-to-run-code-analysis-manually-for-managed-code.md)참조 하세요.
- 전체 솔루션 분석: 편집기에서 열려 있는지 여부에 관계 없이 사용자가 솔루션에 있는 모든 파일의 모든 진단을 항상 표시 하려는 경우입니다. 이 시나리오에서는 전체 솔루션에 대 한 백그라운드 분석 범위를 최대화 하려고 합니다.

Visual Studio 2019 버전 16.5부터 사용자는 c # 및 Visual Basic 프로젝트에 대 한 진단 계산을 포함 하 여 모든 라이브 코드 분석의 범위를 명시적으로 사용자 지정할 수 있습니다. 사용 가능한 분석 범위는 다음과 같습니다.

- **현재 문서**: 편집기에서 현재 또는 표시 되는 파일에 대해서만 실행 하도록 라이브 코드 분석 범위를 최소화 합니다.
- **문서 열기**: 위의 섹션에서 설명한 대로 기본 라이브 코드 분석 범위입니다.
- **전체 솔루션**: 전체 솔루션의 모든 파일 및 프로젝트에 대해 실행할 라이브 코드 분석 범위를 최대화 합니다.

아래 단계에 따라 도구 옵션 대화 상자에서 위의 사용자 지정 분석 범위 중 하나를 선택할 수 있습니다.

1. **옵션** 대화 상자를 열려면 Visual Studio의 메뉴 모음에서 **도구**  >  **옵션**을 선택 합니다.

2. **옵션** 대화 상자에서 **텍스트 편집기**  >  **c #** 또는 **기본**  >  **고급**을 선택 합니다.

3. 원하는 **배경 분석 범위** 를 선택 하 여 분석 범위를 사용자 지정 합니다. 완료 되 면 **확인을** 선택 합니다.

![분석 범위.](./media/background-analysis-scope.png)

> [!NOTE]
> Visual Studio 2019 버전 16.5 이전 버전에서는 **도구**옵션 텍스트 편집기 **Enable full solution analysis**  >  **Options**  >  **Text Editor**  >  **c #** 또는 **기본**  >  **고급** 탭에서 전체 솔루션 분석 사용 확인란을 사용 하 여 진단 계산의 분석 범위를 전체 솔루션으로 사용자 지정할 수 있습니다. 이전 Visual Studio 버전에서는 백그라운드 분석 범위를 최소화 하는 기능이 지원 되지 않습니다.

## <a name="automatically-minimize-live-code-analysis-scope"></a>자동으로 라이브 코드 분석 범위 최소화

Visual Studio에서 200 MB 이하의 시스템 메모리를 사용할 수 있음을 감지 하면 라이브 코드 분석 범위를 "현재 문서"로 자동으로 최소화 합니다. 이 문제가 발생 하는 경우 Visual Studio에서 일부 기능을 사용 하지 않도록 설정 했다는 알림이 표시 됩니다. 원하는 경우 단추를 사용 하 여 이전 분석 범위로 다시 전환할 수 있습니다.

![경고 텍스트 분석 범위 최소화](./media/fsa_alert.png)

## <a name="see-also"></a>추가 정보

- [자동 기능 일시 중단](./automatic-feature-suspension.md)
- [절전 모드 기능 요청](https://github.com/dotnet/roslyn/issues/38429)
