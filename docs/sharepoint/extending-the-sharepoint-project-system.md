---
title: SharePoint 프로젝트 시스템 확장 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending projects
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7dce10c2bc44eb4fde6a6e38417d136ea5e9ba41
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62557026"
---
# <a name="extend-the-sharepoint-project-system"></a>SharePoint 프로젝트 시스템 확장
  Visual Studio에서 프로젝트 템플릿 및 항목 템플릿 집합을 사용 하 여 SharePoint 솔루션을 만들 수 있습니다. 이러한 템플릿은 다양 한 개발 시나리오의 요구 사항을 충족 하지만 필요한 기능을 제공 하지 않는 경우를 발견할 수 있습니다. 이러한 경우 SharePoint 프로젝트 시스템을 확장할 수 있습니다.

## <a name="overview-of-the-sharepoint-project-system"></a>SharePoint 프로젝트 시스템 개요
 SharePoint 프로젝트 시스템은 *sharepoint 프로젝트 항목*의 기본 구성 요소를 기반으로 합니다. SharePoint 프로젝트 항목은 목록 정의, 웹 파트, 콘텐츠 형식 등의 단일 SharePoint 사용자 지정을 나타냅니다.

 SharePoint 프로젝트는 하나 이상의 SharePoint 프로젝트 항목을 포함 하는 Visual Studio 프로젝트입니다. SharePoint 프로젝트에는 배포를 위해 프로젝트 항목을 기능 및 패키지로 그룹화 하는 방법을 정의 하는 추가 구성 요소도 포함 되어 있습니다.

 Sharepoint 프로젝트 항목 및 SharePoint 프로젝트의 내용에 대 한 자세한 내용은 [sharepoint 프로젝트 항목에 대 한 항목 템플릿 및 프로젝트 템플릿 만들기](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)를 참조 하세요.

## <a name="how-to-extend-the-sharepoint-project-system"></a>SharePoint 프로젝트 시스템을 확장 하는 방법
 다음과 같은 방법으로 SharePoint 프로젝트 시스템을 확장할 수 있습니다.

- 사용자 고유의 SharePoint 프로젝트 항목 형식을 정의 하 고 Visual Studio에서 새 항목 템플릿 또는 프로젝트 템플릿에 연결 합니다. 예를 들어 사용자 지정 작업 또는 필드를 만들기 위한 SharePoint 프로젝트 항목 형식을 정의할 수 있습니다. 자세한 내용은 [사용자 지정 SharePoint 프로젝트 항목 형식 정의](../sharepoint/defining-custom-sharepoint-project-item-types.md)를 참조 하세요.

- Visual Studio에 이미 설치 되어 있는 SharePoint 프로젝트 항목 형식을 확장 합니다. 예를 들어 **솔루션 탐색기** 의 프로젝트 항목에 바로 가기 메뉴 항목을 추가 하 고 개발자가 메뉴 항목을 선택할 때 프로젝트 항목을 사용자 지정할 수 있습니다. 자세한 내용은 [SharePoint 프로젝트 항목 확장](../sharepoint/extending-sharepoint-project-items.md)을 참조 하세요.

- SharePoint 프로젝트를 확장 합니다. 예를 들어 SharePoint 프로젝트에서 항목을 추가 하거나 제거할 때 이벤트 처리기를 추가 하 여 특정 작업을 수행할 수 있습니다. 자세한 내용은 [SharePoint 프로젝트 확장](../sharepoint/extending-sharepoint-projects.md)을 참조 하세요.

- SharePoint 프로젝트 항목 및 SharePoint 프로젝트의 패키징 및 배포 동작을 확장 합니다. 예를 들어 프로젝트를 배포 하거나 취소할 때 실행할 사용자 고유의 배포 단계를 만들거나 Visual Studio에서 특정 배포 단계를 실행할 때 추가로 사용자 지정 작업을 수행할 수 있습니다. 자세한 내용은 [SharePoint 패키징 및 배포 확장](../sharepoint/extending-sharepoint-packaging-and-deployment.md)을 참조 하세요.

## <a name="common-development-tasks"></a>일반적인 개발 작업
 SharePoint 프로젝트 시스템의 확장에서 다음과 같은 일반적인 작업을 수행할 수 있습니다.

- 프로젝트 항목과 여러 다른 형식의 프로젝트 파일에 사용자 지정 문자열 데이터를 저장 합니다. 자세한 내용은 [SharePoint 프로젝트 시스템의 확장에 데이터 저장](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)을 참조 하세요.

- SharePoint 프로젝트 시스템의 개체를 Visual Studio 자동화 개체 모델 또는 통합 개체 모델의 해당 개체로 변환 하거나 그 반대로 변환 합니다. 자세한 내용은 [SharePoint 프로젝트 시스템 형식과 기타 Visual Studio 프로젝트 형식 간의 관계](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)를 참조 하세요.

## <a name="see-also"></a>추가 정보
- [사용자 지정 SharePoint 프로젝트 항목 형식 정의](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [SharePoint 프로젝트 항목 확장](../sharepoint/extending-sharepoint-project-items.md)
- [SharePoint 프로젝트 확장](../sharepoint/extending-sharepoint-projects.md)
- [SharePoint 패키징 및 배포 확장](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [SharePoint 프로젝트 시스템의 확장에 데이터 저장](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)
- [SharePoint 프로젝트 시스템 형식과 기타 Visual Studio 프로젝트 형식 간의 변환](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
- [Visual Studio에서 SharePoint 도구 확장](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [SharePoint 도구 확장의 프로그래밍 개념 및 기능](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
