---
title: Office 솔루션에 대 한 구성 정보 설정
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], configuration files
- configuration files [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e47ad00e3f9e90913784196894d514a755699864
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91581041"
---
# <a name="how-to-set-up-configuration-information-for-an-office-solution"></a>방법: Office 솔루션에 대 한 구성 정보 설정
  구성 파일을 사용 하 여 Office 솔루션과 관련 된 설정을 구성할 수 있습니다. 어셈블리 바인딩 정책, 원격 개체, 디버그 및 추적 설정과 같은 설정을 지정할 수 있습니다.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-a-configuration-file-to-your-office-project"></a>Office 프로젝트에 구성 파일을 추가 하려면

1. **프로젝트** 메뉴에서 **새 항목 추가**를 클릭합니다.

2. **범주** 창에서 **일반**을 클릭 합니다.

3. **템플릿** 창에서 **응용 프로그램 구성 파일**을 선택 합니다.

4. **이름** 상자에 어셈블리와 동일한 이름 및 확장명 *.config*를 입력 합니다. 예를 들어 *ExcelWorkbook1.dll* 이라는 Excel 프로젝트 어셈블리에 대 한 구성 파일의 이름은 *ExcelWorkbook1.dll.config*로 지정 됩니다.

5. **추가**를 클릭합니다.

6. 응용 프로그램 구성 파일 스키마에 따라 구성 파일을 만듭니다. 자세한 내용은 [.NET Framework 구성 파일 스키마](/dotnet/framework/configure-apps/file-schema/index)를 참조 하세요.

   Office 프로젝트에서 구성 파일을 사용 하는 경우 특별 한 고려 사항은 없습니다.

## <a name="see-also"></a>참고 항목
- [.NET Framework에 대 한 구성 파일 스키마](/dotnet/framework/configure-apps/file-schema/index)
- [Office 솔루션 디자인 및 만들기](../vsto/designing-and-creating-office-solutions.md)
- [Office 솔루션 배포](../vsto/deploying-an-office-solution.md)
