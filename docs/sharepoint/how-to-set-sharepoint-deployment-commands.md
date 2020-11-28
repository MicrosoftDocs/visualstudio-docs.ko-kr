---
title: '방법: SharePoint 배포 명령 설정 | Microsoft Docs'
description: SharePoint 배포 전 및 배포 후 명령을 설정 하 여 배포 프로세스를 사용자 지정 하는 방법을 이해 합니다.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fc1da67206e5e5c9fde1b5c595424239d1685ac7
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304389"
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>방법: SharePoint 배포 명령 설정
  배포 전 및 배포 후 명령을 설정 하 여 배포 프로세스를 사용자 지정할 수 있습니다. 이러한 명령은 Visual Studio에서 SharePoint 솔루션을 디버그할 때 다른 배포 작업 전후에 실행 됩니다.

### <a name="to-add-a-pre-deployment-command"></a>배포 전 명령을 추가 하려면

1. 메뉴 모음에서 **프로젝트**  >  **\<*ProjectName*> 속성** 을 선택 합니다.

2. **SharePoint** 탭을 선택 합니다.

3. **배포 전 명령줄** 텍스트 상자에 MS-DOS 또는 MSBuild 명령을 입력 하 여이 단계를 사용자 지정 합니다.

     예를 들어 배포를 완료 하기 전에 디렉터리 내용을 나열 하려면 **dir** 을 입력 합니다.

### <a name="to-add-a-post-deployment-command"></a>배포 후 명령을 추가 하려면

1. 메뉴 모음에서 **프로젝트**  >  **\<*ProjectName*> 속성** 을 선택 합니다.

2. **SharePoint** 탭을 선택 합니다.

3. **배포 후 명령줄** 텍스트 상자에 MS-DOS 또는 MSBuild 명령을 입력 하 여이 단계를 사용자 지정 합니다.

     예를 들어 배포가 완료 된 후 디렉터리 내용을 나열 하려면 **dir** 을 입력 합니다. MSBuild 변수를 사용 하 여 빌드 디렉터리에서 어셈블리를 복사 하려면 **copy $ (TargetPath) c:\DeploymentDirectory** 를 입력 합니다.

## <a name="see-also"></a>참고 항목
- [SharePoint 솔루션 패키지 및 배포](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
