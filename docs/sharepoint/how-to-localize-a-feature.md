---
title: '방법: 기능 지역화 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- features [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b0d15654ba48b6c95cf2b2f7fa4f9cd665f0959a
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016146"
---
# <a name="how-to-localize-a-feature"></a>방법: 기능 지역화
  기본적으로 기능 제목 및 설명은 하드 코드 된 문자열 값을 사용 합니다. 기능 제목 및 설명을 지역화 하려면 문자열을 지역화 된 리소스를 참조 하는 식으로 바꿉니다.

## <a name="localize-a-feature"></a>기능 지역화

#### <a name="to-localize-a-feature"></a>기능을 지역화 하려면

1. **솔루션 탐색기**에서 **Feature1** 노드의 바로 가기 메뉴를 열고 **기능 리소스 추가**를 선택 합니다.

2. **리소스 추가** 대화 상자에서 기본 언어 기능 리소스 파일의 문화권으로 목록에서 **고정 언어** 를 선택 합니다.

3. 지역화된 언어마다 이전 단계를 반복하여 지역화된 기능 리소스 파일에 대해 선택한 언어를 선택합니다.

     기본 언어와 지원할 지역화된 언어마다 하나씩 별도의 기능 리소스 파일이 만들어집니다.

4. 리소스 편집기에서 각 리소스 파일을 연 다음 문자열 ID와 그 값을 모두 입력합니다.

     예를 들어 기본 기능 리소스 파일에서 **내 기능 제목**값을 포함 하는 **제목의** 문자열 id를 입력 하 고 **내 기능 설명**의 값을 사용 하 여 **설명** 의 두 번째 문자열 id를 입력 합니다. 지역화된 각 리소스 파일에 대해 기본 기능 리소스에서 사용된 동일한 문자열 ID를 사용하지만 값의 지역화된 문자열을 입력합니다.

5. 모든 리소스 값을 입력 한 후 기능 (예 *Feature1*)에 대 한 바로 가기 메뉴를 열고 **디자이너 보기** 를 선택 하 여 기능 디자이너에서 기능을 엽니다.

6. 기능에서 **제목** 및 **설명** 필드를 지역화 하려면 다음 형식을 사용 하 여 해당 상자에 값을 입력 합니다.

     `$Resources:` *문자열 ID*

     예를 들어 **기능 제목** 상자에 $Resources**제목을** 입력 하 고 **기능 설명** 상자에 $Resources:**description** 을 입력 합니다.

     문자열 ID는 리소스 파일에서 사용되는 것과 일치해야 합니다.

7. **F5** 키를 선택 하 여 응용 프로그램을 빌드하고 실행 합니다.

8. SharePoint에서 **사이트 작업** 메뉴를 열고 **사이트 설정**을 선택한 후 **사이트 작업** 섹션에서 **사이트 기능 관리** 링크를 선택 합니다.

9. SharePoint에서 표시 언어를 기본값에서 변경 합니다.

     지역화 된 기능 제목 및 설명이 응용 프로그램에 표시 됩니다. 지역화 된 리소스를 표시 하려면 SharePoint 서버에 리소스 파일의 문화권과 일치 하는 언어 팩이 설치 되어 있어야 합니다.

## <a name="see-also"></a>참고 항목
- [SharePoint 솔루션 지역화](../sharepoint/localizing-sharepoint-solutions.md)
- [방법: 리소스 파일 추가](../sharepoint/how-to-add-a-resource-file.md)
- [방법: ASPX 태그 지역화](../sharepoint/how-to-localize-aspx-markup.md)
- [방법: 코드 지역화](../sharepoint/how-to-localize-code.md)
