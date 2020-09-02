---
title: 빌드 구성 이해
description: 이 문서에서는 Mac용 Visual Studio의 다양한 빌드 구성을 설명합니다.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.assetid: 78107CFA-9308-4293-A92A-9B552A259E15
ms.openlocfilehash: d1511434a34017a7f0f7da65fe1ea6956d45d497
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "71128406"
---
# <a name="understanding-build-configurations"></a>빌드 구성 이해

개발 프로세스 중에 빌드 종류에 따라 사용할 솔루션 및 프로젝트 속성의 다양한 구성을 저장할 수 있습니다. Mac용 Visual Studio에서 템플릿을 사용하여 만든 프로젝트에는 일반적으로 앱 디버깅과 앱 배포를 각각 지원하는 디버그 및 릴리스 구성이 포함되어 있습니다. 

사용자 지정 구성을 만들려는 경우 [빌드 구성 만들기 및 편집](/visualstudio/mac/create-and-edit-configurations)을 참조하세요.

>[!NOTE]
>이 토픽은 Mac용 Visual Studio에 적용됩니다. Windows용 Visual Studio의 경우 [빌드 구성 이해](/visualstudio/ide/understanding-build-configurations)를 참조하세요.

## <a name="solution-configurations"></a>솔루션 구성

솔루션 구성은 솔루션에 포함된 모든 프로젝트의 구성을 지정하는 데 사용됩니다. **빌드 > 구성** 항목 아래의 **구성 매핑** 탭을 사용하여, 열린 솔루션의 각 항목에 대해 대상 구성을 할당할 수 있습니다. 이 내용은 다음 그림에 나와 있습니다.

![구성 매핑 옵션](media/projects-and-solutions-image3.png)

구성에 대한 자세한 내용은 James Montemagno의 [구성 관리자](https://www.youtube.com/watch?v=tjSdkqYh5Vg) 동영상을 참조하세요.

## <a name="project-build-configurations"></a>프로젝트 빌드 구성

대체로 프로젝트는 여러 개의 구성을 사용합니다. 프로젝트의 대상 플랫폼과 구성을 함께 사용하여 빌드 시 사용할 속성을 지정합니다. 구성 간에 전환하면 빌드 시 다른 출력을 생성할 수 있습니다. 예를 들어, 디버그 구성은 디버깅 기호를 출력하므로 디버거가 충돌한 애플리케이션의 스택 추적에서 함수 이름, 매개 변수 또는 변수를 확인할 수 있습니다. 이 추가 정보는 개발 중에 유용하지만 파일 크기를 확장하므로 배포에 적합하지 않습니다.

각 플랫폼에 해당 빌드에 대한 특정 구성이 있습니다. **프로젝트 옵션** 대화 상자의 **빌드** 섹션으로 이동하여 프로젝트의 빌드 구성 페이지에 액세스할 수 있습니다. 프로젝트를 마우스 오른쪽 단추로 클릭하고 **옵션**을 선택하거나, 솔루션 탐색기에서 프로젝트를 두 번 클릭하여 이 대화 상자를 엽니다.

## <a name="run-configuration"></a>실행 구성

Mac용 Visual Studio를 사용하여 ‘실행 구성’을 설정할 수 있습니다.__ 실행 구성은 아래 그림과 같이 도구 모음에서 빌드 구성 선택기 옆에 있는 드롭다운 목록에 표시됩니다.

![실행 구성 드롭다운](media/projects-and-solutions-image8.png)

실행 구성은 다양한 용도로 프로젝트에서 정의된 여러 구성과 이름을 가진 실행 옵션 집합입니다. 실행 구성은 프로젝트 수준에서 정의되며, 필요한 개수만큼 추가할 수는 있지만 각 실행 가능 프로젝트에 대해 기본값이 자동으로 생성됩니다. 특정 프로젝트 형식은 추가 실행 구성을 자동으로 생성합니다. 예를 들어 watchOS 프로젝트는 _한눈에 보기 및 알림 구성_을 생성할 수 있습니다.

구성을 다른 개발자와 공유(이 경우 구성이 .csproj 파일에 저장됨)하거나 로컬에 유지(이 경우 .user 파일에 저장됨)할 수 있습니다.

### <a name="android-run-configurations"></a>Android 실행 구성

Android 프로젝트의 실행 구성을 사용하면 프로젝트를 실행하거나 디버그할 때 시작할 특정 작업, 서비스 또는 브로드캐스트 수신기를 지정할 수 있습니다. 의도 추가 데이터를 전달하고 의도 플래그를 설정하여 다양한 시작 조건에서 구성 요소를 테스트할 수 있습니다.

`MainLauncher` 이외의 작업을 물리적 디바이스에서 디버그하려면 작업 특성에 `Exported=true`가 추가되어야 하거나 의도 필터가 정의되어 있어야 합니다.

## <a name="examples-of-data-that-might-be-included-in-run-configurations"></a>실행 구성에 포함될 수 있는 데이터의 예

다음 목록에는 실행 구성에 포함될 수 있는 데이터의 몇 가지 예가 나와 있습니다.

* 기본 .NET 프로젝트
  * 대체 시작 앱
  * 시작 인수
  * 작업 디렉터리
  * 환경 변수
  * Mono 런타임 옵션(Mono에서 실행하는 경우에만 사용)
* Android 프로젝트
  * 진입점(작업, 서비스, 수신기)
  * 의도 인수 및 데이터
* iOS 프로젝트
  * 모드(기본, 백그라운드 가져오기)
* iOS 확장 프로젝트
  * 시작 앱: 기본 또는 사용자 지정
* WatchKit 프로젝트
  * 모드(한눈에 보기, 알림)
  * 알림 페이로드

## <a name="see-also"></a>추가 정보

- [빌드 구성 이해(Windows의 Visual Studio)](/visualstudio/ide/understanding-build-configurations)
