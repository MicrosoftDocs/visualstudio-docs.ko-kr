---
title: 사용자 지정 문서 속성 개요
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], custom properties
- custom document properties
- document-level customizations [Office development in Visual Studio], custom properties
- Office documents [Office development in Visual Studio], custom properties
- _AssemblyLocation property
- _AssemblyName property
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7b3f4038a05478d8e2d747efa700c7ece02e4827
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62951175"
---
# <a name="custom-document-properties-overview"></a>사용자 지정 문서 속성 개요

문서 수준 프로젝트를 빌드하면 Visual Studio에서 프로젝트의 문서에 \_ assemblylocation 및 AssemblyName 이라는 두 가지 사용자 지정 속성을 추가 합니다 \_ . 사용자가 문서를 열면 Microsoft Office 응용 프로그램에서 이러한 사용자 지정 문서 속성을 확인 합니다. 문서에 있는 경우 응용 프로그램은 사용자 지정을 시작 하는를 로드 합니다 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . 자세한 내용은 [Visual Studio의 Office 솔루션 아키텍처](../vsto/architecture-of-office-solutions-in-visual-studio.md)를 참조 하세요.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="_assemblyname"></a>\_기능의

이 속성은의 Office 솔루션 로더 구성 요소에 있는 인터페이스의 CLSID를 포함 합니다 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . CLSID 값은 4E3C66D5-58D4-491E-A7D4-64AF99AF6E8B입니다. 이 값을 변경해 서는 안 됩니다.

## <a name="_assemblylocation"></a>\_AssemblyLocation

이 속성은 사용자 지정에 대 한 배포 매니페스트에 대 한 세부 정보를 제공 하는 문자열을 포함 합니다. 매니페스트에 대 한 자세한 내용은 [Office 솔루션의 응용 프로그램 및 배포 매니페스트](../vsto/application-and-deployment-manifests-in-office-solutions.md)를 참조 하세요.

 \_Assemblylocation 속성 값은 솔루션이 배포 되는 방법에 따라 다양 한 형식을 가질 수 있습니다.

- 웹 사이트, UNC 경로 또는 CD 또는 USB 드라이브에서 설치 하도록 솔루션을 게시 하는 경우 _AssemblyLocation 속성은 *DeploymentManifestPath* | *솔루션 id*형식입니다. 다음 문자열을 예로 들 수 있습니다.

     file://deployserver/MyShare/ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9

- Visual Studio에서 솔루션을 실행 하거나 디버깅 하는 경우 _AssemblyLocation 속성의 형식은 *DeploymentManifestName* | *솔루션 id*| vstolocal입니다. 다음 문자열을 예로 들 수 있습니다.

     Excelworkbook1.xlsx | 74744e4b-e4d6-41eb-84f7-ad20346fe2d9 | vstolocal

  솔루션 *id* 는에서 솔루션을 식별 하는 데 사용 하는 GUID입니다 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . 프로젝트를 빌드할 때 *솔루션 id* 가 자동으로 생성 됩니다. **Vstolocal** 용어는 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 어셈블리를 문서와 동일한 폴더에서 로드 해야 함을에 나타냅니다.

## <a name="see-also"></a>추가 정보

- [Visual Studio의 Office 솔루션 아키텍처](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [문서 수준 사용자 지정의 아키텍처](../vsto/architecture-of-document-level-customizations.md)
- [Office 솔루션의 응용 프로그램 및 배포 매니페스트](../vsto/application-and-deployment-manifests-in-office-solutions.md)
- [방법: ClickOnce를 사용 하 여 Office 솔루션 게시](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)
- [방법: 사용자 지정 문서 속성 만들기 및 수정](../vsto/how-to-create-and-modify-custom-document-properties.md)
