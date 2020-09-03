---
title: '방법: SharePoint 배포 명령 설정 | Microsoft Docs'
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
ms.openlocfilehash: c2329efef64e7d8605f8483ff7dce3107cd702fa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015502"
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>방법: SharePoint 배포 명령 설정
  배포 전 및 배포 후 명령을 설정 하 여 배포 프로세스를 사용자 지정할 수 있습니다. 이러한 명령은 Visual Studio에서 SharePoint 솔루션을 디버그할 때 다른 배포 작업 전후에 실행 됩니다.

### <a name="to-add-a-pre-deployment-command"></a>배포 전 명령을 추가 하려면

1. 메뉴 모음에서 **프로젝트**  >  ** \<*ProjectName*> 속성**을 선택 합니다.

2. **SharePoint** 탭을 선택 합니다.

3. **배포 전 명령줄** 텍스트 상자에 MS-DOS 또는 MSBuild 명령을 입력 하 여이 단계를 사용자 지정 합니다.

     예를 들어 배포를 완료 하기 전에 디렉터리 내용을 나열 하려면 **dir**을 입력 합니다.

### <a name="to-add-a-post-deployment-command"></a>배포 후 명령을 추가 하려면

1. 메뉴 모음에서 **프로젝트**  >  ** \<*ProjectName*> 속성**을 선택 합니다.

2. **SharePoint** 탭을 선택 합니다.

3. **배포 후 명령줄** 텍스트 상자에 MS-DOS 또는 MSBuild 명령을 입력 하 여이 단계를 사용자 지정 합니다.

     예를 들어 배포가 완료 된 후 디렉터리 내용을 나열 하려면 **dir**을 입력 합니다. MSBuild 변수를 사용 하 여 빌드 디렉터리에서 어셈블리를 복사 하려면 **copy $ (TargetPath) c:\DeploymentDirectory**를 입력 합니다.

## <a name="see-also"></a>추가 정보
- [SharePoint 솔루션 패키징 및 배포](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
