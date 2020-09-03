---
title: 비즈니스 데이터 연결 모델 디자인 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], designing a model
- Business Data Connectivity service [SharePoint development in Visual Studio], designing a model
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 16a410b59cef6f282d2d27ad90a90013636d6489
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72984460"
---
# <a name="design-a-business-data-connectivity-model"></a>비즈니스 데이터 연결 모델 디자인
  모델 파일에 엔터티 및 메서드를 추가 하 여 BDC (비즈니스 데이터 연결) 서비스용 모델을 개발할 수 있습니다. 엔터티는 데이터 필드의 컬렉션을 설명 합니다. 예를 들어 엔터티는 데이터베이스의 테이블을 나타낼 수 있습니다. 메서드는 엔터티가 나타내는 데이터를 추가, 삭제 또는 업데이트 하는 등의 작업을 수행 합니다. 자세한 내용은 [SharePoint에 비즈니스 데이터 통합](../sharepoint/integrating-business-data-into-sharepoint.md)을 참조 하세요.

## <a name="add-entities"></a>엔터티 추가
 Visual Studio **도구 상자** 에서 BDC 디자이너로 **엔터티** 를 끌거나 복사 하 여 엔터티를 추가할 수 있습니다. 자세한 내용은 [방법: 모델에 엔터티 추가](../sharepoint/how-to-add-an-entity-to-a-model.md)를 참조 하세요.

 클래스에서 엔터티 필드를 정의 합니다. 예를 들어 라는 필드를 `Address` 클래스에 추가할 수 있습니다 `Customer` . 프로젝트에 새 클래스를 추가 하거나 개체 관계형 디자이너 (O/R 디자이너)와 같은 다른 도구를 사용 하 여 만든 기존 클래스를 사용할 수 있습니다. 엔터티 이름 및 엔터티를 나타내는 클래스의 이름은 일치할 필요가 없습니다. 모델에서 메서드를 정의 하는 경우 클래스를 엔터티와 관련 시킵니다.

## <a name="add-methods"></a>메서드 추가
 BDC 서비스는 사용자가 모델을 기반으로 하는 목록 또는 웹 파트에서 정보를 보거나 추가, 업데이트 또는 삭제할 때 모델의 메서드를 호출 합니다. 사용자가 수행할 수 있는 각 작업에 대해 모델에 메서드를 추가 해야 합니다. **BDC 메서드 세부 정보** 창에서 5 가지 기본 메서드 형식 중 하나를 선택 하 여 메서드를 만듭니다. 다음 표에서는 BDC 모델의 5 가지 기본 방법에 대해 설명 합니다.

|메서드|설명|
|------------|-----------------|
|Finder|엔터티 인스턴스의 컬렉션을 반환 합니다. 사용자가 목록 또는 웹 파트를 열 때 호출 됩니다. 자세한 내용은 [방법: Finder 메서드 추가](../sharepoint/how-to-add-a-finder-method.md)를 참조 하세요.|
|SpecificFinder|특정 엔터티 인스턴스를 반환 합니다. 사용자가 목록의 특정 항목에 대 한 세부 정보를 볼 때 호출 됩니다. 자세한 내용은 [방법: 특정 Finder 메서드 추가](../sharepoint/how-to-add-a-specific-finder-method.md)를 참조 하세요.|
|만든 이|엔터티의 데이터 원본에 새 데이터를 추가 합니다. 사용자가 모델을 기반으로 하는 목록의 리본에서 **새 항목** 단추를 선택 하면 호출 됩니다. 자세한 내용은 [방법: Creator 메서드 추가](../sharepoint/how-to-add-a-creator-method.md)를 참조 하세요.|
|Updater|목록의 데이터를 수정 합니다. 사용자가 목록에서 정보를 업데이트할 때 호출 됩니다. 자세한 내용은 [방법: 업데이트 프로그램 메서드 추가](../sharepoint/how-to-add-an-updater-method.md)를 참조 하세요.|
|Deleter|데이터를 제거 합니다. 사용자가 목록에서 항목을 삭제할 때 호출 됩니다. 자세한 내용은 [방법: Deleter 메서드 추가](../sharepoint/how-to-add-a-deleter-method.md)를 참조 하세요.|

## <a name="define-method-parameters"></a>메서드 매개 변수 정의
 메서드를 만들 때 Visual Studio는 메서드 형식에 적절 한 입력 및 출력 매개 변수를 추가 합니다. 이러한 매개 변수는 자리 표시자 일 뿐입니다. 대부분의 경우 올바른 형식의 데이터를 전달 하거나 반환 하도록 매개 변수를 수정 해야 합니다. 예를 들어 기본적으로 Finder 메서드는 문자열을 반환 합니다. 대부분의 경우 Finder 메서드의 반환 매개 변수를 수정 하 여 엔터티 컬렉션을 반환 하려고 합니다. 매개 변수의 형식 설명자를 수정 하 여이를 수행할 수 있습니다. 형식 설명자는 매개 변수의 데이터 형식을 설명 하는 특성의 컬렉션입니다. 자세한 내용은 [방법: 매개 변수의 형식 설명자 정의](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)를 참조 하세요.

 Visual Studio를 사용 하면 모델의 매개 변수 간에 형식 설명자를 복사할 수 있습니다. 예를 들어 `CustomerTD` 메서드의 반환 매개 변수에 대해 라는 형식 설명자를 정의할 수 있습니다 `GetCustomer` . `CustomerTD` **BDC 탐색기**에서 형식 설명자를 복사한 다음 해당 형식 설명자를 메서드의 입력 매개 변수에 붙여 넣을 수 있습니다 `CreateCustomer` . 이렇게 하면 동일한 형식 설명자를 두 번 이상 정의할 필요가 없습니다.

## <a name="method-instances"></a>메서드 인스턴스
 메서드를 만들 때 Visual Studio는 기본 메서드 인스턴스를 추가 합니다. 메서드 인스턴스는 메서드에 대 한 참조와 매개 변수의 기본값을 더한 값입니다. 단일 메서드에 여러 메서드 인스턴스를 사용할 수 있습니다. 각 인스턴스는 메서드 시그니처와 기본값 집합의 조합입니다. 자세한 내용은 [방법: 매개 변수의 형식 설명자 정의](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)를 참조 하세요.

 프로젝트를 실행 하면 메서드 인스턴스가 SharePoint 목록의 위쪽에 있는 드롭다운 목록에 표시 됩니다. 사용자는 메서드 인스턴스를 선택하여 데이터를 볼 수 있습니다.

 메서드 인스턴스에 기본값을 추가 하려면 모델의 XML을 직접 수정 해야 합니다. 자세한 내용은 [DefaultValue](/previous-versions/office/developer/sharepoint-2010/ee559319(v=office.14))를 참조 하세요.

## <a name="add-filter-descriptors"></a>필터 설명자 추가
 모델의 소비자는 특정 조건에 일치 하는 엔터티의 인스턴스를 검색할 수 있습니다. 이 기능을 사용 하려면 메서드에 필터 설명자를 추가할 수 있습니다. 모델 소비자는 필터 설명자를 사용 하 여 메서드를 실행 하기 전에 메서드에 값을 전달 하 여 메서드 결과 집합을 필터링 할 수 있습니다. 자세한 내용은 [방법: 작업에 필터 매개 변수를 추가 하 여 외부 시스템에서 인스턴스 제한](/previous-versions/office/developer/sharepoint-2010/ee554889(v=office.14))을 참조 하세요.

 SharePoint는 사용자가 필터 값을 제공할 수 있도록 하는 몇 가지 기능을 제공 합니다. 예를 들어 비즈니스 데이터 웹 파트는 필터 텍스트 상자를 제공 합니다. 사용자는 텍스트 상자에 값을 입력하여 목록에서 데이터를 제한할 수 있습니다. 메서드에 필터 설명자를 추가 하는 방법에 대 한 자세한 내용은 [방법: Finder 메서드에 필터 설명자 추가](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)를 참조 하세요.

### <a name="filter-descriptor-properties"></a>필터 설명자 속성
 필터 설명자의 **연결 된 형식 설명자**, **이름**및 **형식** 속성의 값을 설정 해야 합니다. 다른 모든 속성은 선택 사항입니다.

 **연결 된 형식 설명자** 속성은 필터 설명자를 입력 매개 변수에 연결 합니다. 사용자가 필터 값을 제공 하면 BDC 서비스에서 입력 매개 변수를 사용 하 여 해당 값을 메서드에 전달 합니다.

 **Type** 속성은 사용 하려는 필터링 패턴을 설명 합니다. SharePoint에서 선택한 필터링 패턴은 UI (사용자 인터페이스)에 표시 되는 텍스트에 영향을 줍니다. 예를 들어 비교 연산자 필터링 패턴의 경우 텍스트는 비즈니스 데이터 웹 파트 위의 컨트롤로 표시 **되는 것과 같습니다** . 각 필터링 패턴에 대 한 자세한 내용은 [BDC에서 지 원하는 필터 유형](/previous-versions/office/developer/sharepoint-2010/ee556392(v=office.14))을 참조 하세요.

 필터 설명자의 속성에 대 한 자세한 내용은 [FilterDescriptor](/previous-versions/office/developer/sharepoint-2010/ee557835(v=office.14))를 참조 하십시오.

### <a name="provide-default-values"></a>기본값 제공
 경우에 따라 사용자가 필터 값을 제공 하지 않을 수 있습니다. 메서드 인스턴스에 기본값을 추가 하거나 메서드 코드의 기본값을 설정 하 여 기본값을 제공할 수 있습니다. 메서드 인스턴스에 기본값을 추가 하는 방법에 대 한 자세한 내용은 [MethodInstance](/previous-versions/office/developer/sharepoint-2010/ee556838(v=office.14))를 참조 하십시오. 메서드의 코드에서 입력 매개 변수의 기본값을 설정 하는 방법에 대 한 예제는 [방법: Finder 메서드에 필터 설명자 추가](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)를 참조 하세요.

## <a name="validate-the-model"></a>모델의 유효성 검사
 개발 하는 동안 모델의 유효성을 검사할 수 있습니다. Visual Studio는 모델이 예상 대로 동작 하지 않을 수 있는 문제를 식별 합니다. 이러한 문제는 Visual Studio **오류 목록**에 나타납니다.

 BDC 디자이너에 대 한 바로 가기 메뉴를 열고 **유효성 검사**를 선택 하 여 모델의 유효성을 검사할 수 있습니다. 모델에 오류가 포함 되어 있으면 **오류 목록**에 표시 됩니다. 목록에서 오류를 두 번 클릭하여 오류가 포함된 코드로 빠르게 커서를 이동할 수 있습니다. 또는 **f8** 키를 **Shift** + **F8** 반복 해 서 선택 하 여 목록에 있는 오류를 앞으로 또는 뒤로 이동할 수 있습니다.

 모델 규칙을 위반 하는 경우 유효성 검사 오류가 발생할 수 있습니다. 예를 들어 형식 설명자의 **IsCollection** 속성이 **true**로 설정 되어 있지만 자식 형식 설명자가 없는 경우 유효성 검사 오류가 표시 됩니다. Visual Studio **오류 목록**에 표시 되는 일부 오류를 이해 하려면 BDC 모델의 규칙을 참조 해야 할 수 있습니다. BDC 모델의 규칙에 대 한 자세한 내용은 [BDCMetadata 스키마](/previous-versions/office/developer/sharepoint-2010/ee556387(v=office.14))를 참조 하세요.

## <a name="debug-the-solution-that-contains-the-model"></a>모델을 포함 하는 솔루션 디버그
 Visual Studio에서 코드를 디버깅 하는 것 처럼 코드를 디버그할 수 있습니다. 코드를 디버그 하려면 코드의 아무 곳에 나 중단점을 설정한 다음 디버거를 시작 합니다. Visual Studio에서 SharePoint 사이트를 엽니다. SharePoint에서 비즈니스 데이터를 사용 하는 목록 또는 웹 파트를 만듭니다. 그런 다음 코드를 단계별로 실행 할 수 있습니다. SharePoint 프로젝트를 디버깅 하는 방법에 대 한 자세한 내용은 [sharepoint 솔루션 문제 해결](../sharepoint/troubleshooting-sharepoint-solutions.md)을 참조 하세요.

 또한 프로젝트에 추가 하는 사용자 지정 어셈블리에서 코드를 디버그할 수 있습니다. 그러나 사용자 지정 어셈블리의 코드를 디버깅 하려면 어셈블리를 솔루션 패키지에 추가 해야 합니다. 자세한 내용은 [방법: 추가 어셈블리 추가 및 제거](../sharepoint/how-to-add-and-remove-additional-assemblies.md)를 참조 하세요.

 사용자 지정 어셈블리를 프로젝트에 추가 하는 방법에 대 한 자세한 내용은 [방법: BDC 기능에 사용자 지정 어셈블리 포함](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)을 참조 하세요.

### <a name="configure-bdc-security"></a>BDC 보안 구성
 솔루션을 디버깅 하려면 먼저 SharePoint에서 보안 설정을 수정 해야 할 수 있습니다. 이러한 설정을 수정 하려면 SharePoint 2010 중앙 관리 웹 사이트에서 비즈니스 데이터 연결 서비스 응용 프로그램을 엽니다. **메타 데이터 저장소 권한 설정** 대화 상자에서 사용자 계정을 추가 하 고 다음 옵션 중 하나를 선택 합니다.

|Task|옵션|
|----------|------------|
|BDC 서비스에 모델을 배포 합니다.|편집|
|모델에서 외부 콘텐츠 형식 (엔터티)을 사용 하 여 목록 및 웹 파트을 만들려면|클라이언트에서 선택할 수 있습니다.|
|엔터티 데이터를 만들고, 읽고, 업데이트 하 고, 삭제 합니다.|Execute|

 이러한 설정에 대 한 자세한 내용은 [비즈니스 데이터 연결 서비스 관리](/previous-versions/office/sharepoint-server-2010/ee661742(v=office.14))를 참조 하세요.

 개별 모델 또는 외부 콘텐츠 유형에 대 한 보안 권한을 설정할 수도 있습니다. 모델의 보안 권한을 설정 하는 방법에 대 한 자세한 내용은 [BDC 모델 관리](/previous-versions/office/sharepoint-server-2010/ee524073(v=office.14))를 참조 하세요. 외부 콘텐츠 형식의 보안 권한을 설정 하는 방법에 대 한 자세한 내용은 [외부 콘텐츠 형식 관리](/previous-versions/office/sharepoint-server-2010/ee524076(v=office.14))를 참조 하세요.

> [!NOTE]
> 이러한 설정을 사용 하 여 로컬 SharePoint 서버에서 솔루션을 디버그할 수 있습니다. 프로덕션 SharePoint 서버에서 BDC 관련 보안 설정을 구성 하는 방법에 대 한 자세한 내용은 [비즈니스 데이터 연결 서비스 보안 개요](/previous-versions/office/sharepoint-server-2010/ee661743(v=office.14))를 참조 하세요.

### <a name="retract-models-that-become-corrupt"></a>손상 된 모델 취소
 디버거를 처음 시작하면 Visual Studio에서 전체 모델을 SharePoint에 배포합니다. 그런 다음, Visual Studio는 각 시간에 대해 배포 간 변경 내용을 적용 하 여 SharePoint의 모델을 업데이트 합니다.

 Visual Studio에서 SharePoint의 모델을 완전히 제거 하려는 경우가 있을 수 있습니다. 예를 들어 모델이 손상 될 수 있습니다.  모델을 SharePoint에 다시 배포 하려면 모델의 **증분 업데이트** 속성을 **False**로 설정한 다음 디버거를 시작 합니다. **증분 업데이트** 속성은 **BDC 탐색기**에서 모델을 나타내는 노드를 선택 하면 **속성** 창에 표시 됩니다. 기본적으로 모델의 이름은 **BdcModel1**입니다.

### <a name="change-identifier-names-of-entities-in-the-model"></a>모델 엔터티의 식별자 이름 변경
 모델을 배포한 후 식별자의 이름을 변경 하면 배포 오류가 발생할 수 있습니다. 모델의 **증분 업데이트** 속성을 **False**로 설정 하 여이 오류를 해결할 수 없습니다. 모델을 수동으로 취소 한 다음 솔루션을 다시 배포 해야 합니다. 자세한 내용은 [SharePoint 솔루션 문제 해결](../sharepoint/troubleshooting-sharepoint-solutions.md)을 참조 하세요. 모델을 처음 배포 하기 전에 **증분 업데이트** 속성을 **False** 로 설정 하 여이 오류를 방지할 수 있습니다.

## <a name="locate-documentation-for-bdc-model-elements"></a>BDC 모델 요소에 대 한 설명서 찾기
 Visual Studio에서는 각 엔터티, 메서드 또는 사용자가 만드는 다른 항목에 대 한 XML 요소를 모델에 추가 합니다. 요소 특성은 **속성 창에 속성으로** 표시 됩니다. 모델을 디자인할 때 Visual Studio에서 생성 하는 요소 및 특성에 대 한 자세한 내용은 [BDCMetadata 스키마](/previous-versions/office/developer/sharepoint-2010/ee556387(v=office.14))를 참조 하세요.

## <a name="related-topics"></a>관련 항목

|제목|설명|
|-----------|-----------------|
|[BDC 모델 디자인 도구 개요](../sharepoint/bdc-model-design-tools-overview.md)|BDC를 위한 모델을 시각적으로 디자인 하는 데 사용할 수 있는 도구에 대해 설명 합니다.|
|[방법: 모델에 엔터티 추가](../sharepoint/how-to-add-an-entity-to-a-model.md)|외부 콘텐츠 형식 또는 엔터티를 모델에 추가 하는 방법을 보여 줍니다.|
|[방법: Finder 메서드 추가](../sharepoint/how-to-add-a-finder-method.md)|사용자가 목록 또는 웹 파트에서 엔터티 목록을 볼 수 있도록 하는 메서드를 추가 하는 방법을 보여 줍니다.|
|[방법: 특정 Finder 메서드 추가](../sharepoint/how-to-add-a-specific-finder-method.md)|사용자가 특정 엔터티의 세부 정보를 볼 수 있도록 하는 메서드를 추가 하는 방법을 보여 줍니다.|
|[방법: Creator 메서드 추가](../sharepoint/how-to-add-a-creator-method.md)|사용자가 목록 또는 웹 파트에서 직접 데이터 원본에 레코드를 추가할 수 있도록 하는 메서드를 추가 하는 방법을 보여 줍니다.|
|[방법: Deleter 메서드 추가](../sharepoint/how-to-add-a-deleter-method.md)|사용자가 목록 또는 웹 파트의 UI (사용자 인터페이스)에서 옵션을 사용 하 여 데이터 소스에서 데이터를 제거할 수 있도록 하는 메서드를 추가 하는 방법을 보여 줍니다.|
|[방법: 업데이트 프로그램 메서드 추가](../sharepoint/how-to-add-an-updater-method.md)|사용자가 목록 또는 웹 파트에서 직접 데이터 원본의 데이터 레코드를 변경할 수 있도록 하는 메서드를 추가 하는 방법을 보여 줍니다.|
|[방법: 메서드에 매개 변수 추가](../sharepoint/how-to-add-a-parameter-to-a-method.md)|Visual Studio에서 메서드 세부 정보 창을 사용 하 여 입력 및 반환 매개 변수를 메서드에 추가 하는 방법을 보여 줍니다.|
|[방법: 매개 변수의 형식 설명자 정의](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)|모델에서 매개 변수 데이터 형식을 정의 하는 방법을 보여 줍니다.|
|[방법: 메서드 인스턴스 정의](../sharepoint/how-to-define-a-method-instance.md)|BDC가 실행 하는 메서드의 인스턴스를 만드는 방법을 보여 줍니다.|
|[방법: Finder 메서드에 필터 설명자 추가](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)|사용자가 Finder 메서드에서 반환 하는 인스턴스 수를 제한할 수 있도록 하는 방법을 보여 줍니다.|
|[엔터티 간 연결 만들기](../sharepoint/creating-an-association-between-entities.md)|모델에서 엔터티 간의 관계를 정의 하는 방법을 설명 합니다. 비즈니스 데이터 웹 파트, 외부 목록 및 사용자 지정 응용 프로그램은 UI (사용자 인터페이스)에 이러한 데이터 관계를 표시할 수 있습니다.|
|[방법: 엔터티 간 연결 만들기](../sharepoint/how-to-create-an-association-between-entities.md)|모델에서 엔터티 간의 관계를 정의 하는 방법을 보여 줍니다.|
|[연습: 비즈니스 데이터를 사용 하 여 SharePoint에서 외부 목록 만들기](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)|SharePoint 외부 목록에 연락처를 표시 하는 모델을 만들고 테스트 하는 방법을 보여 주는 단계별 지침을 제공 합니다.|
|[SharePoint에 비즈니스 데이터 통합](../sharepoint/integrating-business-data-into-sharepoint.md)|BDC 서비스의 모델을 만들고 디자인 하는 방법에 대 한 개요를 제공 합니다.|
