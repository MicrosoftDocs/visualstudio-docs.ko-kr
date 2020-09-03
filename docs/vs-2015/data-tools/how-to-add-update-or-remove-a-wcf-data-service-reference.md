---
title: '방법: WCF 데이터 서비스 참조 추가, 업데이트 또는 제거 Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- service references [Visual Studio]
- WCF Data Service reference
- WCF data service references
- ADO.NET service references
- ADO.NET Data Service reference
ms.assetid: 892ebf37-3af4-472e-8744-92837677d611
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 89a667e3254be8161d4defb54d524756a5eb02fc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670012"
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>방법: WCF 데이터 서비스 참조 추가, 업데이트 또는 제거
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*서비스 참조* 를 사용 하면 프로젝트에서 하나 이상의에 액세스할 수 있습니다 [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] . **서비스 참조 추가** 대화 상자를 사용 하 여 [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] 로컬 영역 네트워크 또는 인터넷에서 현재 솔루션의를 검색할 수 있습니다.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="adding-a-service-reference"></a>서비스 참조 추가

#### <a name="to-add-a-reference-to-an-external-service"></a>외부 서비스에 대 한 참조를 추가 하려면

1. **솔루션 탐색기**에서 서비스를 추가 하려는 프로젝트의 이름을 마우스 오른쪽 단추로 클릭 한 다음 **서비스 참조 추가**를 클릭 합니다.

     **서비스 참조 추가** 대화 상자가 나타납니다.

2. **주소** 상자에 서비스에 대 한 URL을 입력 하 고 **이동** 을 클릭 하 여 서비스를 검색 합니다. 서비스에서 사용자 이름 및 암호 보안을 구현 하는 경우 사용자 이름 및 암호를 입력 하 라는 메시지가 표시 될 수 있습니다.

    > [!NOTE]
    > 신뢰할 수 있는 원본의 서비스만 참조해야 합니다. 신뢰할 수 없는 원본에서 참조를 추가하면 보안이 손상될 수 있습니다.

     또한 올바른 서비스 메타 데이터를 찾은 이전 15 개 Url을 저장 하는 **주소** 목록에서 URL을 선택할 수 있습니다.

     검색을 수행 하는 동안 진행률 표시줄이 표시 됩니다. **중지**를 클릭 하 여 언제 든 지 검색을 중지할 수 있습니다.

3. **서비스** 목록에서 사용 하려는 서비스에 대 한 노드를 확장 하 고 엔터티 집합을 선택 합니다.

4. 참조에 사용하려는 네임스페이스를 **네임스페이스** 상자에 입력합니다.

5. **확인**을 클릭하여 프로젝트에 대한 참조를 추가합니다.

     서비스 클라이언트 (프록시)가 생성 되 고 서비스를 설명 하는 메타 데이터가 app.config 파일에 추가 됩니다.

#### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>현재 솔루션의 서비스에 대 한 참조를 추가 하려면

1. **솔루션 탐색기**에서 서비스를 추가 하려는 프로젝트의 이름을 마우스 오른쪽 단추로 클릭 한 다음 **서비스 참조 추가**를 클릭 합니다.

     **서비스 참조 추가** 대화 상자가 나타납니다.

2. **검색**을 클릭 합니다.

     [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)]현재 솔루션의 모든 서비스 (및 WCF 서비스)가 **서비스** 목록에 추가 됩니다.

3. **서비스** 목록에서 사용 하려는 서비스에 대 한 노드를 확장 하 고 엔터티 집합을 선택 합니다.

4. 참조에 사용하려는 네임스페이스를 **네임스페이스** 상자에 입력합니다.

5. **확인**을 클릭하여 프로젝트에 대한 참조를 추가합니다.

     서비스 클라이언트 (프록시)가 생성 되 고 서비스를 설명 하는 메타 데이터가 app.config 파일에 추가 됩니다.

## <a name="updating-a-service-reference"></a>서비스 참조 업데이트
 에 대 한 엔터티 데이터 모델 [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] 변경 되는 경우도 있습니다. 이 경우 서비스 참조를 업데이트 해야 합니다.

#### <a name="to-update-a-service-reference"></a>서비스 참조를 업데이트 하려면

- **솔루션 탐색기**에서 서비스 참조를 마우스 오른쪽 단추로 클릭 한 다음 **서비스 참조 업데이트**를 클릭 합니다.

     원본 위치에서 참조를 업데이트 하는 동안 진행률 대화 상자가 표시 되 고 메타 데이터의 변경 내용을 반영 하도록 서비스 클라이언트가 다시 생성 됩니다.

## <a name="removing-a-service-reference"></a>서비스 참조 제거
 서비스 참조가 더 이상 사용 되지 않는 경우 솔루션에서 제거할 수 있습니다.

#### <a name="to-remove-a-service-reference"></a>서비스 참조를 제거 하려면

- **솔루션 탐색기**에서 서비스 참조를 마우스 오른쪽 단추로 클릭 한 다음 **삭제**를 클릭 합니다.

     서비스 클라이언트는 솔루션에서 제거 되 고, 서비스를 설명 하는 메타 데이터는 app.config 파일에서 제거 됩니다.

    > [!NOTE]
    > 서비스 참조를 참조 하는 모든 코드는 수동으로 제거 해야 합니다.

## <a name="see-also"></a>관련 항목
 [Visual Studio에서 서비스 및 WCF Data Services Windows Communication Foundation](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
