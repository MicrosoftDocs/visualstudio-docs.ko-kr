---
title: 서비스 참조 문제 해결
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- msvse_wcf.Err.ReferenceGroup_NamespaceConflictsOther
- msvse_wcf.Err.AddSvcRefDlg_NothingSelectedOnGo
- msvse_wcf.Err.ErrorOnOK
- msvse_wcf.cfg.ConfigurationErrorsException
helpviewer_keywords:
- service references [Visual Studio], troubleshooting
- WCF services, troubleshooting
ms.assetid: 3b531120-1325-4734-90c6-6e6113bd12ac
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: d52562382f10615c7da1dfab22d4c18323b725b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75586122"
---
# <a name="troubleshoot-service-references"></a>서비스 참조 문제 해결

이 항목에서는 Visual Studio에서 WCF (Windows Communication Foundation) 또는 WCF Data Services 참조를 사용 하 여 작업할 때 발생할 수 있는 일반적인 문제에 대해 설명 합니다.

## <a name="error-returning-data-from-a-service"></a>서비스에서 데이터를 반환 하는 동안 오류 발생

서비스에서 또는를 반환 하는 경우 `DataSet` `DataTable` "들어오는 메시지의 최대 크기 할당량을 초과 했습니다." 예외가 표시 될 수 있습니다. 기본적으로 `MaxReceivedMessageSize` 일부 바인딩의 속성은 서비스 거부 공격에 대 한 노출을 제한 하기 위해 상대적으로 작은 값으로 설정 됩니다. 예외를 방지 하기 위해이 값을 늘릴 수 있습니다. 자세한 내용은 <xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A>를 참조하세요.

이 오류를 해결하려면

1. **솔루션 탐색기**에서 *app.config* 파일을 두 번 클릭 하 여 엽니다.

2. 속성을 찾아 `MaxReceivedMessageSize` 더 큰 값으로 변경 합니다.

## <a name="cannot-find-a-service-in-my-solution"></a>내 솔루션에서 서비스를 찾을 수 없습니다.

**서비스 참조 추가** 대화 상자에서 **검색** 단추를 클릭 하면 솔루션에 있는 하나 이상의 WCF 서비스 라이브러리 프로젝트가 서비스 목록에 나타나지 않습니다. 이는 서비스 라이브러리가 솔루션에 추가 되었지만 아직 컴파일되지 않은 경우에 발생할 수 있습니다.

이 오류를 해결하려면

- **솔루션 탐색기**에서 WCF 서비스 라이브러리 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **빌드**를 클릭 합니다.

## <a name="error-accessing-a-service-over-a-remote-desktop"></a>원격 데스크톱을 통해 서비스에 액세스 하는 동안 오류 발생

사용자가 원격 데스크톱 연결을 통해 웹 호스팅 WCF 서비스에 액세스 하 고 사용자에 게 관리 권한이 없는 경우 NTLM 인증을 사용 합니다. 사용자에 게 관리 권한이 없는 경우 사용자에 게 다음 오류 메시지가 표시 될 수 있습니다. "HTTP 요청은 클라이언트 인증 스키마 ' 익명 '으로 인증 되지 않습니다. 서버에서 받은 인증 헤더가 ' NTLM ' 이었습니다.

이 오류를 해결하려면

1. 웹 사이트 프로젝트에서 **속성** 페이지를 엽니다.

2. **시작 옵션** 탭에서 **NTLM 인증** 확인란의 선택을 취소 합니다.

    > [!NOTE]
    > WCF 서비스를 단독으로 포함 하는 웹 사이트의 경우에만 NTLM 인증을 해제 해야 합니다. WCF 서비스에 대 한 보안은 *web.config* 파일의 구성을 통해 관리 됩니다. 이렇게 하면 NTLM 인증이 필요 하지 않습니다.

## <a name="access-level-for-generated-classes-setting-has-no-effect"></a>생성 된 클래스 설정에 대 한 액세스 수준이 아무런 영향을 주지 않습니다.

**서비스 참조 구성** 대화 상자의 **생성 된 클래스에 대 한 액세스 수준** 옵션을 **내부** 또는 **Friend** 로 설정 하면 항상 작동 하지 않을 수 있습니다. 대화 상자에서 옵션을 설정 하는 것 처럼 보이는 경우에도의 액세스 수준을 사용 하 여 결과 지원 클래스가 생성 됩니다 `Public` .

이는를 사용 하 여 serialize 되는 것과 같은 특정 형식의 알려진 제한 사항입니다 <xref:System.Xml.Serialization.XmlSerializer> .

## <a name="error-debugging-service-code"></a>서비스 코드 디버깅 오류

클라이언트 코드에서 WCF 서비스에 대 한 코드를 한 단계씩 코드 실행 하면 누락 된 기호와 관련 된 오류가 발생할 수 있습니다. 솔루션에 포함 된 서비스를 솔루션에서 이동 하거나 제거 하는 경우 이러한 문제가 발생할 수 있습니다.

현재 솔루션의 일부인 WCF 서비스에 대 한 참조를 처음 추가 하면 서비스 프로젝트와 서비스 클라이언트 프로젝트 간에 명시적 빌드 종속성이 추가 됩니다. 이렇게 하면 클라이언트가 항상 최신 서비스 이진 파일에 액세스할 수 있습니다 .이는 클라이언트 코드를 서비스 코드로 단계별로 실행 하는 것과 같은 디버깅 시나리오에서 특히 중요 합니다.

서비스 프로젝트가 솔루션에서 제거 되는 경우이 명시적 빌드 종속성이 무효화 됩니다. Visual Studio는 필요에 따라 서비스 프로젝트를 다시 작성 하는 것을 더 이상 보장할 수 없습니다.

이 오류를 해결 하려면 서비스 프로젝트를 수동으로 다시 빌드해야 합니다.

1. **도구** 메뉴에서 **옵션**을 클릭합니다.

2. **옵션** 대화 상자에서 **프로젝트 및 솔루션**을 확장 한 다음 **일반**을 선택 합니다.

3. **고급 빌드 구성 표시** 확인란이 선택 되어 있는지 확인 한 다음 **확인**을 클릭 합니다.

4. WCF 서비스 프로젝트를 로드 합니다.

5. **Configuration Manager** 대화 상자에서 **활성 솔루션 구성을** **디버그**로 설정 합니다. 자세한 내용은 [방법: 구성 만들기 및 편집](../ide/how-to-create-and-edit-configurations.md)을 참조하세요.

6. **솔루션 탐색기**에서 WCF 서비스 프로젝트를 선택 합니다.

7. **빌드** 메뉴에서 **다시** 빌드를 클릭 하 여 WCF 서비스 프로젝트를 다시 빌드합니다.

## <a name="wcf-data-services-do-not-display-in-the-browser"></a>브라우저에 표시 되지 WCF Data Services

에서 데이터의 XML 표현을 보려고 하면 [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] Internet Explorer에서 데이터를 RSS 피드로 잘못 해석할 수 있습니다. RSS 피드를 표시 하는 옵션이 사용 하지 않도록 설정 되어 있는지 확인 합니다.

이 오류를 해결 하려면 RSS 피드를 사용 하지 않도록 설정 합니다.

1. Internet Explorer의 **도구** 메뉴에서 **인터넷 옵션**을 클릭합니다.

2. **콘텐츠** 탭의 **피드** 섹션에서 **설정**을 클릭 합니다.

3. **피드 설정** 대화 상자에서 **피드 읽기용 보기 설정** 확인란의 선택을 취소 한 다음 **확인**을 클릭 합니다.

4. **확인** 을 클릭 하 여 **인터넷 옵션** 대화 상자를 닫습니다.

## <a name="see-also"></a>추가 정보

- [Visual Studio에서 서비스 및 WCF Data Services Windows Communication Foundation](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
