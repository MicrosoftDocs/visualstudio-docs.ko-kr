---
title: MSBuild 작업을 사용 하 여 SharePoint 솔루션 패키지 만들기
description: 개발 컴퓨터에서 명령줄 MSBuild 작업을 사용 하 여 SharePoint 솔루션 패키지 (.wsp)를 빌드, 정리 및 유효성 검사 하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f2979073414434d2b8f5be9d070b6b505c09ee14
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903730"
---
# <a name="how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks"></a>방법: MSBuild 작업을 사용 하 여 SharePoint 솔루션 패키지 만들기
  개발 컴퓨터에서 명령줄 MSBuild 작업을 사용 하 여 SharePoint 패키지 (*.wsp*)를 빌드, 정리 및 유효성 검사할 수 있습니다. 이러한 명령을 사용 하 여 빌드 컴퓨터에서 Team Foundation Server를 사용 하 여 빌드 프로세스를 자동화할 수도 있습니다.

## <a name="build-a-sharepoint-package"></a>SharePoint 패키지 빌드

#### <a name="to-build-a-sharepoint-package"></a>SharePoint 패키지를 빌드하려면

1. Windows **시작** 메뉴에서 **모든 프로그램**  >  **보조 프로그램**  >  **명령 프롬프트** 를 선택 합니다.

2. SharePoint 프로젝트가 있는 디렉터리로 변경 합니다.

3. 다음 명령을 입력 하 여 프로젝트에 대 한 패키지를 만듭니다. *Projectfilename* 을 프로젝트 이름으로 바꿉니다.

    ```cmd
    msbuild /t:Package ProjectFileName
    ```

     예를 들어 다음 명령 중 하나를 실행 하 여 ListDefinition1 이라는 SharePoint 프로젝트를 패키지할 수 있습니다.

    ```cmd
    msbuild /t:Package ListDefinition1.vbproj
    msbuild /t:Package ListDefinition1.csproj
    ```

## <a name="clean-a-sharepoint-package"></a>SharePoint 패키지 정리

#### <a name="to-clean-a-sharepoint-package"></a>SharePoint 패키지를 정리 하려면

1. 명령 프롬프트 창을 엽니다.

2. SharePoint 프로젝트가 있는 디렉터리로 변경 합니다.

3. 다음 명령을 입력 하 여 프로젝트에 대 한 패키지를 정리 합니다. *Projectfilename* 을 프로젝트 이름으로 바꿉니다.

    ```cmd
    msbuild /t:CleanPackage ProjectFileName
    ```

     예를 들어 다음 명령 중 하나를 실행 하 여 ListDefinition1 이라는 SharePoint 프로젝트를 정리할 수 있습니다.

    ```cmd
    msbuild /t:CleanPackage ListDefinition1.vbproj
    msbuild /t:CleanPackage ListDefinition1.csproj
    ```

## <a name="validate-a-sharepoint-package"></a>SharePoint 패키지 유효성 검사

#### <a name="to-validate-a-sharepoint-package"></a>SharePoint 패키지의 유효성을 검사 하려면

1. 명령 프롬프트 창을 엽니다.

2. SharePoint 프로젝트가 있는 디렉터리로 변경 합니다.

3. 다음 명령을 입력 하 여 프로젝트에 대 한 패키지의 유효성을 검사 합니다. *Projectfilename* 을 프로젝트 이름으로 바꿉니다.

    ```cmd
    msbuild /t:ValidatePackage ProjectFileName
    ```

     예를 들어 다음 명령 중 하나를 실행 하 여 ListDefinition1 이라는 SharePoint 프로젝트의 유효성을 검사할 수 있습니다.

    ```cmd
    msbuild /t:ValidatePackage ListDefinition1.vbproj
    msbuild /t:ValidatePackage ListDefinition1.csproj
    ```

## <a name="set-properties-in-a-sharepoint-package"></a>SharePoint 패키지의 속성 설정

#### <a name="to-set-a-property-in-a-sharepoint-package"></a>SharePoint 패키지의 속성을 설정 하려면

1. 명령 프롬프트 창을 엽니다.

2. SharePoint 프로젝트가 있는 디렉터리로 변경 합니다.

3. 다음 명령을 입력 하 여 프로젝트에 대 한 패키지의 속성을 설정 합니다. *PropertyName* 을 설정 하려는 속성으로 바꿉니다.

    ```cmd
    msbuild /property:PropertyName=Value
    ```

     예를 들어 다음 명령을 실행 하 여 경고 수준을 설정할 수 있습니다.

    ```cmd
    msbuild /property:WarningLevel = 2
    ```

## <a name="see-also"></a>참고 항목
- [SharePoint 기능 만들기](../sharepoint/creating-sharepoint-features.md)
- [방법: SharePoint 기능 사용자 지정](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [방법: SharePoint 기능에 항목 추가 및 제거](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
