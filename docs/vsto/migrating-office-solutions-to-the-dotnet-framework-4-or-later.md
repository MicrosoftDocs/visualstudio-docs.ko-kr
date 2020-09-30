---
title: .NET Framework 4 이상으로 Office 솔루션 마이그레이션
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Project.TargetFrameworkWarning
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 86b975b7e84c69ff072df06e0a2c7701ab1909e7
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584492"
---
# <a name="migrate-office-solutions-to-the-net-framework-4-or-later"></a>.NET Framework 4 이상으로 Office 솔루션 마이그레이션
  Office 프로젝트의 대상 프레임 워크가 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 이전 버전의 .NET Framework에서 이상으로 변경 된 경우 개발 및 최종 사용자 컴퓨터에서 솔루션을 계속 실행 하려면 몇 가지 추가 단계가 필요할 수 있습니다. 자세한 내용은 [.NET Framework 4로 마이그레이션하는 Office 프로젝트를 실행 하는 데 필요한 변경 사항 또는 4.5 .NET Framework](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)를 참조 하세요.

 또한 프로젝트가 더 이상 컴파일되지 않을 수 있습니다. Office 프로젝트의 일부 기능은 각 버전의 .NET Framework에 대해 다른 프로그래밍 모델을 사용합니다. Office 프로젝트의 대상 프레임워크가 이전 버전의 .NET Framework에서 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 이상으로 변경된 경우 프로젝트의 코드를 다음과 같이 변경해야 합니다.

- [.NET Framework 4 또는 .NET Framework 4.5으로 마이그레이션하는 Excel 및 Word 프로젝트를 업데이트 합니다.](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

- [.NET Framework 4 또는 .NET Framework 4.5으로 마이그레이션하는 Office 프로젝트에서 리본 메뉴 사용자 지정 업데이트](update-ribbon-customizations-in-office-projects-to-migrate-to-dotnet-framework-4-or-4-5.md)

- [.NET Framework 4 또는 .NET Framework 4.5으로 마이그레이션하는 Outlook 프로젝트에서 양식 영역 업데이트](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

  이전 버전의 Visual Studio에서 해당 프로젝트를 업그레이드하는 경우 Office 프로젝트의 대상 프레임워크가 변경됩니다. 자세한 내용은 [Office 솔루션 업그레이드 및 마이그레이션](../vsto/upgrading-and-migrating-office-solutions.md)을 참조 하세요.

  이상을 대상으로 하는 경우 Office 프로젝트의 일부 기능이 다른 프로그래밍 모델을 갖는 이유에 대 한 자세한 내용은 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [.NET Framework 4를 대상으로 하는 office 프로젝트 디자인의 변경 내용 또는 4.5 .NET Framework](../vsto/changes-to-the-design-of-office-projects-that-target-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md) 및 [Visual Studio Tools for Office 런타임 개요](../vsto/visual-studio-tools-for-office-runtime-overview.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목
- [Office 솔루션 디자인 및 만들기](../vsto/designing-and-creating-office-solutions.md)
- [방법: 특정 버전의 .NET Framework 대상](../ide/visual-studio-multi-targeting-overview.md)
- [Office 솔루션의 오류 문제 해결](../vsto/troubleshooting-errors-in-office-solutions.md)
- [Office 솔루션의 오류에 대 한 추가 지원](../vsto/additional-support-for-errors-in-office-solutions.md)
