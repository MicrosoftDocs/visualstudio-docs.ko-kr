---
title: 서비스 참조 구성 대화 상자
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- msvse_wcf.dlg.ConfigureServiceReference
helpviewer_keywords:
- WCF services, Configure Service Reference dialog box
- service references [Visual Studio], configuring behavior
- Configure Service Reference dialog box
ms.assetid: 25e4c36b-2db6-4e71-9010-b7068255d09d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: f5bae3acb6f687c8c787e2d4121999d1133b0f1f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75586928"
---
# <a name="configure-service-reference-dialog-box"></a>서비스 참조 구성 대화 상자

**서비스 참조 구성** 대화 상자를 사용 하 여 WCF (Windows Communication Foundation) 서비스의 동작을 구성할 수 있습니다.

**서비스 참조 구성** 대화 상자에 액세스하려면 **솔루션 탐색기**에서 서비스 참조를 마우스 오른쪽 단추로 클릭하고 **서비스 참조 구성**을 선택합니다. **서비스 참조 추가 대화 상자**에서 **고급** 단추를 클릭하여 대화 상자에 액세스할 수도 있습니다.

## <a name="task-list"></a>작업 목록

- WCF 서비스가 호스팅되는 주소를 변경하려면 **주소** 필드에 새 주소를 입력합니다.

- WCF 클라이언트에서 클래스의 액세스 수준을 변경하려면 **생성된 클래스에 대한 액세스 수준** 목록에서 액세스 수준 키워드를 선택합니다.

- WCF 서비스의 메서드를 비동기적으로 호출하려면 **비동기 작업 생성** 확인란을 선택합니다.

- WCF 클라이언트에서 메시지 계약 형식을 생성하려면 **항상 메시지 계약 생성** 확인란을 선택합니다.

- WCF 클라이언트에 대해 목록 또는 사전 컬렉션 형식을 지정하려면 **컬렉션 형식** 및 **사전 컬렉션 형식** 목록에서 형식을 선택합니다.

- 형식 공유를 사용하지 않도록 설정하려면 **참조된 어셈블리의 형식 재사용** 확인란의 선택을 취소합니다. 일부 참조된 어셈블리에 대해 형식 공유를 사용하도록 설정하려면 **참조된 어셈블리의 형식 재사용** 확인란을 선택하고, **참조된 어셈블리 중 지정된 어셈블리의 형식 재사용**을 선택하고, **참조된 어셈블리 목록**에서 원하는 참조를 선택합니다.

## <a name="uielement-list"></a>UI 요소 목록

**주소**

서비스 참조가 서비스를 검색 하는 웹 주소를 업데이트 합니다. 예를 들어 개발 중에 서비스는 개발 서버에서 호스트 된 후 나중에 프로덕션 서버로 이동 하 여 주소를 변경할 수 있습니다.

> [!NOTE]
> Address 요소는 **서비스 참조 추가 대화 상자**에서 **서비스 참조 구성** 대화 상자가 표시된 경우에는 사용할 수 없습니다.

**생성된 클래스에 대한 액세스 수준**

WCF 클라이언트 클래스에 대한 코드 액세스 수준을 결정합니다.

> [!NOTE]
> 웹 사이트 프로젝트의 경우 이 옵션은 항상 `Public`으로 설정되며 변경할 수 없습니다. 자세한 내용은 [서비스 참조 문제 해결](../data-tools/troubleshooting-service-references.md)을 참조하세요.

**동기 작업 생성**

WCF 서비스 메서드를 동기적으로 (기본값) 또는 비동기적으로 호출 하는지 여부를 결정 합니다.

**작업 기반 작업 생성**

비동기 코드를 작성할 때이 옵션을 사용 하면 .NET 4에서 도입 된 TPL (작업 병렬 라이브러리)을 활용할 수 있습니다. [TPL (작업 병렬 라이브러리)](/dotnet/standard/parallel-programming/task-parallel-library-tpl)을 참조 하세요.

**항상 메시지 계약 생성**

WCF 클라이언트에 대해 메시지 계약 형식이 생성 되는지 여부를 결정 합니다. 메시지 계약에 대한 자세한 내용은 [메시지 계약 사용](/dotnet/framework/wcf/feature-details/using-message-contracts)을 참조하세요.

**컬렉션 형식**

WCF 클라이언트에 대한 목록 컬렉션 형식을 지정합니다. 기본 형식은 <xref:System.Array>입니다.

**사전 컬렉션 형식**

WCF 클라이언트에 대한 사전 컬렉션 형식을 지정합니다. 기본 형식은 <xref:System.Collections.Generic.Dictionary%602>입니다.

**참조된 어셈블리의 형식 재사용**

WCF 클라이언트가 서비스를 추가 하거나 업데이트할 때 새 형식을 생성 하는 대신 참조 된 어셈블리에 이미 있는 항목을 다시 사용 하려고 하는지 여부를 결정 합니다. 기본적으로 이 옵션은 선택되어 있습니다.

**모든 참조된 어셈블리의 형식 재사용**

이를 선택 하면 가능한 경우 **참조 된 어셈블리 목록의** 모든 형식이 다시 사용 됩니다. 이 옵션은 기본적으로 선택됩니다.

**참조된 어셈블리 중 지정된 어셈블리의 형식 재사용**

이를 선택 하면 **참조 된 어셈블리 목록** 에서 선택한 유형만 다시 사용 됩니다.

**참조된 어셈블리 목록**

프로젝트 또는 웹 사이트에 대 한 참조 어셈블리의 목록을 포함 합니다. **지정 된 참조 된 어셈블리의 형식 재사용**을 선택 하는 경우 개별 어셈블리를 선택 하거나 선택 취소할 수 있습니다.

**웹 참조 추가**

**웹 참조 추가** 대화 상자를 표시합니다.

> [!NOTE]
> 이 옵션은 .NET Framework 버전 2.0을 대상으로 하는 프로젝트에만 사용 해야 합니다.
>
> [!NOTE]
> **웹 참조 추가** 단추는 **서비스 참조 추가 대화 상자**에서 **서비스 참조 구성** 대화 상자가 표시 되는 경우에만 사용할 수 있습니다.

## <a name="see-also"></a>추가 정보

- [방법: 웹 서비스에 참조 추가](how-to-add-update-or-remove-a-wcf-data-service-reference.md)
- [Windows Communication Foundation 서비스 및 WCF Data Services](../data-tools/configure-service-reference-dialog-box.md)
