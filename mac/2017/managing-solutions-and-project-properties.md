---
title: 프로젝트 및 솔루션 속성 관리
description: 이 문서에서는 Mac용 Visual Studio에서 프로젝트와 솔루션의 속성을 관리하는 방법을 설명합니다.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 75247EB8-323A-4AFD-A451-6703A03D5D1F
ms.openlocfilehash: 514792804515541b7e4f64359a08e9c6093c5018
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "74985261"
---
# <a name="managing-project-and-solution-properties"></a>프로젝트 및 솔루션 속성 관리

## <a name="project-options"></a>프로젝트 옵션

프로젝트 옵션은 프로젝트마다 다르며 프로젝트 작성, 빌드 및 실행 방식에 영향을 줍니다. 이는 사용자별 옵션을 설정하는 Mac용 Visual Studio 기본 설정 및 전체 솔루션에 대한 옵션을 설정하는 솔루션 옵션과 대조됩니다. 프로젝트 옵션은 프로젝트(.csproj) 파일에 저장되므로 다른 개발자가 프로젝트를 올바르게 빌드하고 실행할 수 있습니다. 특정 프로젝트 옵션을 사용하면 여러 명의 개발자가 파일 형식을 손상하지 않고 같은 문서에서 작업할 수 있습니다.

Mac용 Visual Studio에서 프로젝트 옵션을 열려면 프로젝트 이름을 두 번 클릭하거나 마우스 오른쪽 단추를 클릭하여 상황에 맞는 메뉴를 연 다음, **옵션**을 선택합니다.

![상황에 맞는 메뉴의 옵션](media/projects-and-solutions-image2.png)

편집 가능한 옵션에는 소스 코드 및 버전 제어를 빌드, 실행 및 설정하는 옵션이 포함됩니다.

프로젝트 옵션은 다음과 같은 다섯 가지 범주로 분류됩니다.

* **일반** - 프로젝트의 위치와 함께 이름, 설명 및 기본 네임스페이스 등의 프로젝트 정보를 여기에서 설정합니다.
* **빌드** - 개발자가 이식 가능한 클래스 라이브러리에 대해 PCL 프로필을 설정하거나 변경할 수 있습니다. 또한 사용자 지정 명령, 구성, 컴파일러 옵션을 설정할 수 있습니다. 출력 경로 및 어셈블리 이름도 여기에서 설정할 수 있습니다.
* **실행** - 프로젝트 단위로 사용자 지정 실행 구성을 만들 수 있습니다.
* **소스 코드** - 다양한 파일 형식 및 명명 규칙의 서식을 제어할 수 있습니다. 또한 여기에서 명명 정책 및 기본 헤더 스타일을 설정할 수 있습니다.
* **버전 제어** - 프로젝트에 버전 제어를 사용할 때 커밋 메시지의 스타일을 편집할 수 있습니다.

각 프로젝트는 플랫폼에 따라 특정 프로젝트 옵션을 포함할 수 있습니다. 예를 들어 다음 이미지에 설명된 프로젝트와 같은 Xamarin.Android 프로젝트에는 링커 옵션과 같이 Android 빌드와 관련된 옵션 및 권한과 같이 애플리케이션과 관련된 옵션이 포함됩니다.

![Android 프로젝트 옵션](media/projects-and-solutions-image5.png)

Xamarin.iOS에는 사용할 필수 프로비저닝 프로필과 같이 번들 서명과 관련된 옵션이 있습니다.

![iOS 프로젝트 옵션](media/projects-and-solutions-image6.png)

## <a name="solution-options"></a>솔루션 옵션

솔루션 옵션은 프로젝트 옵션과 유사하지만 전체 솔루션의 범위를 포함합니다. 솔루션 옵션은 작성자 정보, 빌드 설정, 코드 서식 지정 스타일 및 버전 제어를 설정하는 방법을 제공하고, 솔루션에서 시작 프로젝트를 할당할 수 있게 합니다.  솔루션 옵션 대화 상자는 **프로젝트 > 솔루션 옵션** 메뉴 항목에서 액세스하거나, Solution Pad의 솔루션에 있는 **옵션** 상황에 맞는 메뉴 항목에서 액세스하거나, Solution Pad에서 [솔루션]을 두 번 클릭하여 액세스할 수 있습니다.

![솔루션 옵션](media/projects-and-solutions-image7.png)

## <a name="see-also"></a>참고 항목

* [프로젝트 및 솔루션 속성 관리(Windows의 Visual Studio)](/visualstudio/ide/managing-project-and-solution-properties)