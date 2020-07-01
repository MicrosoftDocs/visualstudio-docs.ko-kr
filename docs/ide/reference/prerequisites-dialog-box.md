---
title: 필수 조건 대화 상자
ms.date: 06/29/2018
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- Microsoft.VisualStudio.Publish.BaseProvider.Dialog.Bootstrapper
helpviewer_keywords:
- Prerequisites dialog box
author: Mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf555a9a4b7c73e4e204bcc42e6b57d3ab96cd01
ms.sourcegitcommit: 9e15138a34532b222e80f6b42b1a9de7b2fe0175
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85419174"
---
# <a name="prerequisites-dialog-box"></a>필수 조건 대화 상자

**필수 구성 요소** 대화 상자에서는 설치할 필수 구성 요소, 설치 방법 및 패키지 설치 순서를 지정합니다.

![Visual Studio의 필수 구성 요소 대화 상자](media/prerequisites-dialog-box.png)

대화 상자에 액세스하려면 **솔루션 탐색기**에서 프로젝트 노드를 선택하고 **프로젝트** > **속성**을 선택합니다. **프로젝트 디자이너**가 나타나면 **게시** 탭을 선택한 다음, **필수 구성 요소**를 선택합니다. 설치 프로젝트인 경우 **프로젝트** 메뉴에서 **속성**을 클릭합니다. **속성 페이지** 대화 상자가 표시되면 **필수 구성 요소**를 클릭합니다.

## <a name="uielement-list"></a>UI 요소 목록

|요소|설명|
|-------------|-----------------|
|**필수 구성 요소를 설치하기 위한 설치 프로그램 만들기**|종속성 순서에 따라 애플리케이션보다 필수 구성 요소가 먼저 설치되도록 애플리케이션의 설치 프로그램(*Setup.exe*)에 필수 구성 요소를 포함합니다. 기본적으로 이 옵션이 선택됩니다. 이 옵션을 선택하지 않으면 *Setup.exe*가 작성되지 않습니다.|
|**설치할 필수 구성 요소 선택**|.NET Framework 및 C++ 런타임 라이브러리와 같은 구성 요소를 설치할지 여부를 지정합니다.<br /><br />예를 들어, **SQL Server 2012 Express** 옆의 확인란을 선택하여 설치 프로그램에서 이 구성 요소가 대상 컴퓨터에 설치되었는지 여부를 확인하고 설치되지 않았으면 설치하도록 지정합니다.<br /><br />각 필수 구성 요소 패키지에 대한 자세한 내용은 [필수 구성 요소 정보](#prerequisites-information)를 참조하세요.|
|**구성 요소 공급업체의 웹 사이트에서 필수 구성 요소 다운로드**|공급업체의 웹 사이트에서 필수 구성 요소를 설치하도록 지정합니다. 기본 옵션입니다.|
|**내 애플리케이션과 동일한 위치에서 필수 구성 요소 다운로드**|애플리케이션과 동일한 위치에서 필수 구성 요소가 설치되도록 지정합니다. 이 옵션은 모든 필수 구성 요소 패키지를 게시 위치에 복사합니다. 이 옵션이 작동하려면 필수 구성 요소 패키지가 개발 컴퓨터에 있어야 합니다.|
|**다음 위치에서 필수 구성 요소 다운로드**|입력한 위치에서 필수 구성 요소가 설치되도록 지정합니다. **찾아보기** 단추를 사용하여 위치를 선택할 수 있습니다.|

> [!NOTE]
> 필수 구성 요소를 배치할 위치에 대한 자세한 내용은 [부트스트래퍼 패키지 만들기](../../deployment/creating-bootstrapper-packages.md#create-custom-bootstrapper-packages)를 참조하세요.

## <a name="prerequisites-information"></a>필수 구성 요소 정보

**필수 구성 요소** 대화 상자에 나타나는 필수 구성 요소는 다음 목록에 나와 있는 구성 요소와 다를 수도 있습니다. 대화 상자를 처음 열면 **필수 조건 대화 상자**에 나열된 필수 조건 패키지가 자동으로 설정됩니다. 이후에 프로젝트의 대상 프레임워크를 변경하는 경우에는 새 대상 프레임워크에 맞도록 필수 구성 요소를 수동으로 선택해야 합니다.

|요소|설명|
|-------------|-----------------|
|**.NET Framework 3.5 SP1**|이 패키지는 다음 항목을 설치합니다.<br /><br /> -   .NET Framework 버전 2.0, 3.0 및 3.5.<br />-   32비트(x86) 및 64비트(x64) 운영 체제에서 모든 .NET Framework 버전에 대한 지원.<br />-   패키지와 함께 설치된 각 .NET Framework 버전에 대한 언어 팩.<br />-   .NET Framework 2.0 및 3.0용 서비스 팩.<br /><br /> .NET Framework 3.0은 Windows Vista에 포함되고 .NET Framework 3.5는 Visual Studio에 포함됩니다. .NET Framework 3.5는 32비트 운영 체제용으로 컴파일되고 대상 프레임워크가 **.NET Framework 3.5**로 설정된 모든 Visual Basic 및 C# 프로젝트와 64비트 운영 체제용으로 컴파일된 Visual Basic 및 C# 프로젝트에 필요합니다. IA64는 지원되지 않습니다. Visual Basic 및 C# 프로젝트는 기본적으로 모든 CPU 아키텍처에 대해 컴파일됩니다. 자세한 내용은 [Framework 대상 지정 개요](../../ide/visual-studio-multi-targeting-overview.md) 및 [64비트 앱의 필수 구성 요소 배포](../../deployment/deploying-prerequisites-for-64-bit-applications.md)를 참조하세요.|
|**Microsoft .NET Framework 4.x**|이 패키지는 x86 및 x64 플랫폼 모두에 .NET Framework 4.x를 설치합니다.|
|**SQL Server 2014용 Microsoft System CLR Types(x64 및 x86)**|이 패키지는 x64 또는 x86의 SQL Server 2014용 Microsoft System CLR Types를 설치합니다.|
|**SQL Server 2008 R2 Express**|이 패키지는 소규모 웹, 서버 또는 데스크톱 애플리케이션에 적합한 데이터베이스이며 Microsoft SQL Server 2008 R2의 체험판 버전인 Microsoft SQL Server 2008 R2 Express를 설치합니다. 이 응용 프로그램은 개발 및 프로덕션 용도로 무료로 사용할 수 있습니다.|
|**SQL Server 2012 Express**|이 패키지는 Microsoft SQL Server 2012 Express를 설치합니다.|
|**SQL Server 2012 Express LocalDB**|이 패키지는 Microsoft SQL Server 2012 Express LocalDB를 설치합니다.|
|**Visual C++ "14" 런타임 라이브러리(ARM)**|이 패키지는 Microsoft Windows 운영 체제에 프로그래밍 루틴을 제공하는 Itanium 아키텍처용 Visual C++ 런타임 라이브러리를 설치합니다. 이러한 루틴은 C 및 C++ 언어에서 제공하지 않는 여러 일반 프로그래밍 작업을 자동화합니다.<br /><br /> 자세한 내용은 [C 런타임 라이브러리 참조](/cpp/c-runtime-library/c-run-time-library-reference)를 참조하세요.|
|**Visual C++ “14” 런타임 라이브러리(x64)**|이 패키지는 Microsoft Windows 운영 체제에 프로그래밍 루틴을 제공하는 x64 운영 체제용 Visual C++ 런타임 라이브러리를 설치합니다. 이러한 루틴은 C 및 C++ 언어에서 제공하지 않는 여러 일반 프로그래밍 작업을 자동화합니다.<br /><br /> 자세한 내용은 [C 런타임 라이브러리 참조](/cpp/c-runtime-library/c-run-time-library-reference)를 참조하세요.|
|**Visual “14” 런타임 라이브러리(x86)**|이 패키지는 Microsoft Windows 운영 체제에 프로그래밍 루틴을 제공하는 x86 운영 체제용 Visual C++ 런타임 라이브러리를 설치합니다. 이러한 루틴은 C 및 C++ 언어에서 제공하지 않는 여러 일반 프로그래밍 작업을 자동화합니다.<br /><br /> 자세한 내용은 [C 런타임 라이브러리 참조](/cpp/c-runtime-library/c-run-time-library-reference)를 참조하세요.|

## <a name="see-also"></a>참조

- [프로젝트 디자이너, 게시 페이지](../../ide/reference/publish-page-project-designer.md)
- [애플리케이션 배포 필수 조건](../../deployment/application-deployment-prerequisites.md)
- [64비트 애플리케이션의 필수 조건 배포](../../deployment/deploying-prerequisites-for-64-bit-applications.md)
- [Framework 대상 지정 개요](../../ide/visual-studio-multi-targeting-overview.md)
