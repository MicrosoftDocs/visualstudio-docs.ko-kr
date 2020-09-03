---
title: '방법: 서비스의 데이터에 연결'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- data [Visual Studio], connecting to web services
- data sources, creating from web services
- data [Visual Studio], reading from web services
- reading data, from web services
- web services, reading data
- web services, as data sources
- web services, connecting
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 0b49840a2190abfd223edf5643b8d70da1a59d6b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85282230"
---
# <a name="how-to-connect-to-data-in-a-service"></a>방법: 서비스의 데이터에 연결

[데이터 소스 구성 마법사](../data-tools/media/data-source-configuration-wizard.png) 를 실행 하 고 **데이터 소스 형식 선택** 페이지에서 **서비스** 를 선택 하 여 서비스에서 반환 된 데이터에 응용 프로그램을 연결 합니다.

마법사가 완료 되 면 서비스 참조가 프로젝트에 추가 되 고 [데이터 소스 창](add-new-data-sources.md#data-sources-window)에서 바로 사용할 수 있습니다.

> [!NOTE]
> **데이터 원본** 창에 표시되는 항목은 서비스에서 반환하는 정보에 따라 달라집니다. **데이터 원본 구성 마법사**에서 바인딩 가능한 개체를 만들기에 충분한 정보를 제공하지 않는 서비스도 있습니다. 예를 들어 서비스에서 형식화 되지 않은 데이터 집합을 반환 하는 경우 마법사를 완료할 때 **데이터 소스** 창에 항목이 표시 되지 않습니다. 이는 형식화 되지 않은 데이터 집합이 스키마를 제공 하지 않으므로 마법사에 데이터 소스를 만들 수 있는 충분 한 정보가 없기 때문입니다.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-connect-your-application-to-a-service"></a>응용 프로그램을 서비스에 연결 하려면

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

응용 프로그램에 기능을 추가 하려면 **데이터 소스** 창에서 항목을 선택 하 고 폼으로 끌어서 바인딩된 컨트롤을 만듭니다. 자세한 내용은 [Visual Studio에서 데이터에 컨트롤 바인딩](../data-tools/bind-controls-to-data-in-visual-studio.md)을 참조 하세요.

## <a name="see-also"></a>추가 정보

- [WCF 데이터 서비스에 WPF 컨트롤 바인딩](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)
- [Visual Studio에서 Windows Communication Foundation Services 및 WCF data Services](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
