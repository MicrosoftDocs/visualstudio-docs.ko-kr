---
title: '방법: BDC 기능에 사용자 지정 어셈블리 포함 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.BDC.Add_Assemblies_Dialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], add reference
- Business Data Connectivity service [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], add reference
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 772cdbaca67cc82fc6b7eb2c5ef5adb6508df34a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015252"
---
# <a name="how-to-include-a-custom-assembly-in-a-bdc-feature"></a>방법: BDC 기능에 사용자 지정 어셈블리 포함
  프로젝트는 같은 솔루션에 있는 다른 프로젝트의 어셈블리를 참조할 수 있습니다. 그러나 **lobsystem에 참조 된 어셈블리 할당** 대화 상자를 사용 하 여 프로젝트의 기능 파일에 이러한 어셈블리를 추가 해야 합니다.

### <a name="to-include-a-custom-assembly-in-a-business-data-connectivity-bdc-feature"></a>BDC (비즈니스 데이터 연결) 기능에 사용자 지정 어셈블리를 포함 하려면

1. **솔루션 탐색기**에서 BDC 모델이 포함 된 폴더를 선택 합니다.

2. **보기** 메뉴에서 **속성 창**을 클릭합니다.

3. **속성** 창에서 **어셈블리** 속성을 선택 하 고 줄임표 단추 (![ASP.NET Mobile Designer ellipse](../sharepoint/media/mwellipsis.gif "ASP.NET 모바일 디자이너 줄임표"))를 선택 합니다.

     **Lobsystem에 참조 된 어셈블리 할당** 대화 상자가 나타납니다.

4. **어셈블리 선택** 목록에서 사용자 지정 어셈블리를 선택 합니다.

    > [!NOTE]
    > 어셈블리가 포함 된 프로젝트에 대 한 참조를 추가한 경우 어셈블리는 **lobsystem에 참조 된 어셈블리 할당** 대화 상자에만 나타납니다. 자세한 내용은 [방법: 참조 추가 대화 상자를 사용 하 여 참조 추가 또는 제거](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)를 참조 하세요.

5. **참조 속성** 그룹에서 **LobSystem 범위** 속성에 대해 표시 되는 목록을 열고 사용자 지정 어셈블리를 사용 하는 메서드의 LOB 시스템을 선택한 다음 **확인** 단추를 선택 합니다.

    > [!NOTE]
    > 사용자 지정 어셈블리의 코드를 디버깅 하려면 솔루션 패키지에 어셈블리를 추가 해야 합니다. 자세한 내용은 [방법: 추가 어셈블리 추가 및 제거](../sharepoint/how-to-add-and-remove-additional-assemblies.md)를 참조 하세요.

## <a name="see-also"></a>추가 정보
- [방법: 리소스 파일을 사용 하 여 지역화 된 이름, 속성 및 사용 권한 지정](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [방법: SharePoint 프로젝트에 기존 BDC 모델 파일 추가](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [비즈니스 데이터 연결 모델 만들기](../sharepoint/creating-a-business-data-connectivity-model.md)
- [방법: BDC 모델 만들기](../sharepoint/how-to-create-a-bdc-model.md)
- [SharePoint에 비즈니스 데이터 통합](../sharepoint/integrating-business-data-into-sharepoint.md)
