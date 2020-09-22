---
title: '개발 모범 사례: Office의 COM, VSTO, & VBA 추가 기능'
ms.date: 07/25/2017
ms.topic: conceptual
dev_langs:
- ''
helpviewer_keywords:
- ''
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: be48e7ce721c84656362a019e0cc5eec1ae2ee17
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808209"
---
# <a name="development-best-practices-for-com-vsto-and-vba-add-ins-in-office"></a>Office의 COM, VSTO 및 VBA 추가 기능에 대 한 개발 모범 사례
  Office 용 COM, VSTO 또는 VBA 추가 기능을 개발 하는 경우이 문서에 설명 된 개발 모범 사례를 따릅니다.   이렇게 하면 다음과 같은 이점을 얻을 수 있습니다.

- 다양 한 버전 및 Office 배포에서 추가 기능의 호환성
- 사용자 및 IT 관리자에 대 한 추가 기능 배포의 복잡성이 줄어듭니다.
- 의도 하지 않은 설치 또는 추가 기능에 대 한 런타임 실패가 발생 하지 않습니다.

>참고: [데스크톱 브리지](/windows/uwp/porting/desktop-to-uwp-root) 를 사용 하 여 Windows 스토어 용 COM, VSTO 또는 VBA 추가 기능을 준비 하는 것은 지원 되지 않습니다. COM, VSTO 및 VBA 추가 기능은 Windows 스토어 또는 Office 스토어에 배포할 수 없습니다.

## <a name="do-not-check-for-office-during-installation"></a>설치 하는 동안 Office 확인 안 함
 추가 기능 설치 프로세스 중에 Office가 설치 되었는지 여부를 추가 기능에서 감지 하지 않는 것이 좋습니다. Office가 설치 되지 않은 경우 추가 기능을 설치할 수 있습니다. 그러면 Office가 설치 된 후에 사용자가 해당 추가 기능에 액세스할 수 있습니다.

## <a name="use-embedded-interop-types-nopia"></a>포함 된 Interop 형식 사용 (NoPIA)
솔루션이 .NET 4.0 이상 버전을 사용 하는 경우 Office PIA (주 Interop 어셈블리) 재배포 가능 패키지에 의존 하지 않고 포함 된 interop 형식 (NoPIA)을 사용 합니다. 형식 포함을 사용 하면 솔루션의 설치 크기를 줄이고 이후 버전과의 호환성을 보장 합니다. Office 2010는 PIA 재배포 가능 패키지가 제공 된 최신 버전의 Office입니다. 자세한 내용은 [연습: Microsoft Office 어셈블리의 형식 정보 포함](/previous-versions/ee317478(v=vs.140)) 및 [동일 형식 및 포함 된 interop 형식](/windows/uwp/porting/desktop-to-uwp-root)을 참조 하세요.

솔루션에서 이전 버전의 .NET을 사용 하는 경우 .NET 4.0 이상을 사용 하도록 솔루션을 업데이트 하는 것이 좋습니다. .NET 4.0 이상을 사용 하면 최신 버전의 Windows에 대 한 런타임 필수 구성 요소가 줄어듭니다.

## <a name="avoid-depending-on-specific-office-versions"></a>특정 Office 버전에 따라 방지
솔루션에서 최신 버전의 Office 에서만 사용할 수 있는 기능을 사용 하는 경우 런타임에 기능 수준에서 해당 기능이 있는지 확인 합니다 (예: 예외 처리 사용 또는 버전 확인). [응용 프로그램 버전 속성과](<xref:Microsoft.Office.Interop.Excel._Application.Version%2A>)같이 개체 모델에서 지원 되는 api를 사용 하 여 특정 버전이 아닌 최소 버전의 유효성을 검사 합니다. 설치, 환경 및 버전 간에 변경 될 수 있으므로 Office 이진 메타 데이터, 설치 경로 또는 레지스트리 키를 사용 하지 않는 것이 좋습니다.

## <a name="enable-both-32-bit-and-64-bit-office-usage"></a>32 비트 및 64 비트 Office 사용을 모두 사용 합니다.
솔루션이 특정 비트에만 사용할 수 있는 라이브러리에 의존 하지 않는 한 기본 빌드 대상은 32 비트 (x86) 및 64 비트 (x64)를 모두 지원 해야 합니다. 64 비트 버전의 Office는 특히 빅 데이터 환경에서 도입 되었습니다. 32 비트와 64 비트를 모두 지원 하면 사용자가 보다 쉽게 32 비트 및 64 비트 버전의 Office를 전환할 수 있습니다.

VBA 코드를 작성 하는 경우 64 비트 safe 선언 문을 사용 하 고 변수를 적절 하 게 변환 합니다. 또한 각 비트에 대 한 코드를 제공 하 여 32 비트 또는 64 비트 버전의 Office를 실행 하는 사용자 간에 문서를 공유할 수 있는지 확인 합니다. 자세한 내용은 [응용 프로그램용 64 비트 Visual Basic 개요](/office/vba/Language/Concepts/Getting-Started/64-bit-visual-basic-for-applications-overview)를 참조 하세요.

## <a name="support-restricted-environments"></a>제한 된 환경 지원
사용자의 솔루션에는 사용자 계정 권한 상승이 나 관리자 권한이 필요 하지 않습니다. 또한 솔루션은 설정 또는 변경에 의존 하지 않아야 합니다.

- 현재 작업 디렉터리.
- DLL 로드 디렉터리입니다.
- 경로 변수입니다.

## <a name="change-the-save-location-of-shared-data-and-settings"></a>공유 데이터 및 설정의 저장 위치를 변경 합니다.
솔루션이 추가 기능과 Office 외부의 프로세스로 구성 된 경우 사용자의 응용 프로그램 데이터 폴더 또는 레지스트리를 사용 하 여 추가 기능과 외부 프로세스 간에 데이터 또는 설정을 교환 하지 마십시오. 대신 사용자의 임시 폴더, 문서 폴더 또는 솔루션의 설치 디렉터리를 사용 하는 것이 좋습니다.

## <a name="increment-the-version-number-with-each-update"></a>각 업데이트를 사용 하 여 버전 번호를 늘립니다.
솔루션에서 이진 파일의 버전 번호를 설정 하 고 각 업데이트를 사용 하 여 늘립니다. 이렇게 하면 사용자가 버전 간 변경 내용을 쉽게 파악 하 고 호환성을 평가할 수 있습니다.

## <a name="provide-support-statements-for-the-latest-versions-of-office"></a>최신 버전의 Office에 대 한 지원 문 제공
고객은 Isv에 게 Office에서 실행 되는 COM, VSTO 및 VBA 추가 기능에 대 한 지원 문을 제공 하도록 요청 합니다. 명시적 지원 문을 나열 하면 고객이 엔터프라이즈 준비 도구에 대 한 Microsoft 365 앱을 사용 하 여 지원을 이해할 수 있습니다.

Office 클라이언트 응용 프로그램에 대 한 지원 문을 제공 하려면 (예: Word 또는 Excel) 먼저 현재 Office 릴리스에서 추가 기능이 실행 되는지 확인 한 다음 추가 기능이 이후 버전에서 중단 되는 경우 업데이트 제공을 커밋합니다. Microsoft에서 새 빌드 또는 Office 업데이트를 릴리스할 때 추가 기능을 테스트할 필요가 없습니다. Microsoft는 Office에서 COM, VSTO 및 VBA 확장성 플랫폼을 거의 변경 하지 않으며 이러한 변경 내용은 잘 설명 되어 있습니다.

>중요: Microsoft는 준비 보고서에 대해 지원 되는 추가 기능 목록과 ISV 연락처 정보를 유지 관리 합니다. 추가 기능 목록을 보려면 [/configmgr/desktop-analytics/ready-for-windows](/configmgr/desktop-analytics/ready-for-windows)를 참조 하세요.

## <a name="use-process-monitor-to-help-debug-installation-or-loading-issues"></a>프로세스 모니터를 사용 하 여 설치 또는 로드 문제를 디버깅할 수 있습니다.
설치 또는 로드 하는 동안 추가 기능에 호환성 문제가 있는 경우 파일 또는 레지스트리 액세스와 관련 된 문제가 있을 수 있습니다. [프로세스 모니터](/sysinternals/downloads/procmon) 또는 유사한 디버깅 도구를 사용 하 여 문제를 식별 하는 데 도움이 되도록 작업 환경에 대 한 동작을 기록 하 고 비교 합니다.