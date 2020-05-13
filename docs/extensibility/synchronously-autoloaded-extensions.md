---
title: 동기적으로 자동 로드된 확장
ms.date: 12/11/2019
ms.topic: conceptual
ms.assetid: 822e3cf8-f723-4ff1-8467-e0fb42358a1f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab62d235fd6ed4e47e765fc23868acd5c56efcb2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699379"
---
# <a name="synchronously-autoloaded-extensions"></a>동기적으로 자동 로드된 확장

동기식 자동 로드 된 확장은 Visual Studio의 성능에 부정적인 영향을 미치며 대신 비동기 자동 로드를 사용하도록 변환해야합니다. 기본적으로 Visual Studio 2019는 모든 확장에서 동기화적으로 자동 로드된 패키지를 차단하고 사용자에게 알려주게 합니다.

![확장 호환성 경고](media/extension-compatibility-warning-16-1.png.png)

다음을 수행할 수 있습니다.

- 확장이 자동 로드되도록 하려면 **동기 자동 로드 허용을 클릭합니다.** Visual Studio 옵션에서 이 설정을 변경하려면 환경을 클릭한 다음 확장을 클릭한 다음 "확장의 동기 자동 로드 허용" 확인란을 선택합니다. 

- 성능 **관리를** 클릭하여 확장 및 도구 창에 성능 문제를 표시하는 [성능 관리자 대화 상자를](#performance-manager-dialog) 엽니다.

- 현재 **확장에 대해 이 메시지를 표시하지 않으면** 알림을 해제하고 기존 설치된 확장에서 향후 알림을 방지합니다. 동기적으로 자동 로드되는 새 확장을 추가하면 이 알림이 다시 표시됩니다. 다른 Visual Studio 기능에 대한 알림을 계속 받게 됩니다.

## <a name="performance-manager-dialog"></a>성능 관리자 대화 상자

![성능 관리자 대화 상자](media/performance-manager.png)

사용자 세션의 모든 패키지를 동기로 로드한 모든 확장은 **더 이상 사용되지 않는 API** 탭에 나타납니다.

* **이 문제에 대한 자세한 정보를** 클릭하여 더 이상 사용되지 이상API에 대한 자세한 정보를 수집합니다.
* 마이그레이션 진행 상황에 대해 확장 공급업체에 문의하십시오.

## <a name="specify-synchronous-autoload-settings-using-group-policy"></a>그룹 정책을 사용하여 동기 자동 로드 설정 지정

관리자는 그룹 정책을 사용하여 동기 자동 로드를 허용할 수 있습니다. 이렇게 하려면 다음 키에 레지스트리 기반 정책을 설정합니다.

**HKEY_LOCAL_MACHINE\SOFTWARE\정책\마이크로소프트\비주얼 스튜디오\동기 자동 로드**

항목 = **허용됨**

값 = (DWORD)
* **0은** 동기 자동 로드가 허용되지 않습니다.
* **1은** 동기 자동 로드 허용됨

## <a name="extension-authors"></a>확장 작성자
확장 작성자는 [AsyncPackage로](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/AsyncPackageMigration)마이그레이션할 때 패키지를 비동기 자동 로드로 마이그레이션하는 방법에 대한 지침을 찾을 수 있습니다.

## <a name="see-also"></a>참조
Visual Studio 2019의 동기 자동 로드 설정에 대한 자세한 내용은 [동기 자동 로드 동작](https://devblogs.microsoft.com/visualstudio/updates-to-synchronous-autoload-of-extensions-in-visual-studio-2019/) 페이지를 참조하십시오.
