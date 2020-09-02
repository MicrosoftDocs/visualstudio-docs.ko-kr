---
title: '방법: 서비스의 데이터에 연결 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], connecting to Web services
- data sources, creating from Web services
- data [Visual Studio], reading from Web services
- reading data, from Web services
- Web services, reading data
- Web services, as data sources
- Web services, connecting
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d9bfa6c776e3a2137f751d4253feb0239811d95a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72654697"
---
# <a name="how-to-connect-to-data-in-a-service"></a>방법: 서비스의 데이터에 연결
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[데이터 소스 구성 마법사](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) 를 실행 하 고 **데이터 소스 형식 선택** 페이지에서 **서비스** 를 선택 하 여 서비스에서 반환 된 데이터에 응용 프로그램을 연결 합니다.

 마법사가 완료 되 면 서비스 참조가 프로젝트에 추가 되 고 [데이터 소스 창](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)에서 바로 사용할 수 있습니다.

> [!NOTE]
> **데이터 원본** 창에 표시되는 항목은 서비스에서 반환하는 정보에 따라 달라집니다. **데이터 원본 구성 마법사**에서 바인딩 가능한 개체를 만들기에 충분한 정보를 제공하지 않는 서비스도 있습니다. 예를 들어 서비스에서 형식화 되지 않은 데이터 집합을 반환 하는 경우 마법사를 완료 하면 **데이터 소스 창** 에 항목이 표시 되지 않습니다. 이는 형식화 되지 않은 데이터 집합이 스키마를 제공 하지 않으므로 마법사에 데이터 소스를 만들 수 있는 충분 한 정보가 없기 때문입니다.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-connect-your-application-to-a-service"></a>응용 프로그램을 서비스에 연결 하려면

1. **데이터** 메뉴에서 **새 데이터 소스 추가**를 클릭합니다.

2. **데이터 소스 형식 선택** 페이지에서 **서비스** 를 선택 하 고 **다음**을 클릭 합니다.

3. 사용할 서비스의 주소를 입력 하거나 **검색** 을 클릭 하 여 현재 솔루션에서 서비스를 찾은 다음 **이동**을 클릭 합니다.

4. 필요에 따라 기본값 대신 새 **네임 스페이스** 를 입력할 수 있습니다.

    > [!NOTE]
    > **고급** 을 클릭 하 여 [서비스 참조 구성 대화 상자](../data-tools/configure-service-reference-dialog-box.md)를 엽니다.

5. **확인** 을 클릭 하 여 프로젝트에 서비스 참조를 추가 합니다.

6. **마침**을 클릭합니다.

     데이터 원본이 **데이터 원본** 창에 추가됩니다.

## <a name="next-steps"></a>다음 단계

#### <a name="to-add-functionality-to-your-application"></a>애플리케이션에 기능을 추가하려면

- **데이터 소스** 창에서 항목을 선택 하 고 폼으로 끌어서 바인딩된 컨트롤을 만듭니다. 자세한 내용은 [Visual Studio에서 데이터에 컨트롤 바인딩](../data-tools/bind-controls-to-data-in-visual-studio.md)을 참조 하세요.

## <a name="see-also"></a>관련 항목
 [Visual Studio에서 WCF 데이터 서비스 Windows Communication Foundation 서비스 및 WCF Data Services](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) [에 WPF 컨트롤 바인딩](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)
