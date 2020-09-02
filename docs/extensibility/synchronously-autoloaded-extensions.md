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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80699379"
---
# <a name="synchronously-autoloaded-extensions"></a>동기적으로 자동 로드된 확장

동기적으로 자동 로드 된 확장은 Visual Studio의 성능에 부정적인 영향을 주므로 대신 비동기 autoload를 사용 하도록 변환 해야 합니다. 기본적으로 Visual Studio 2019은 모든 확장에서 동기적으로 자동 로드 된 패키지를 차단 하 고 사용자에 게 알립니다.

![확장 호환성 경고](media/extension-compatibility-warning-16-1.png.png)

다음과 같습니다.

- **동기 Autoload 허용** 을 클릭 하 여 autoload에 대 한 확장을 허용 합니다. Visual Studio 옵션에서이 설정을 변경 하려면 환경을 클릭 한 다음 확장을 클릭 하 고 "동기 autoload 확장 허용" 확인란을 선택 합니다. 

- 성능 **관리** 를 클릭 하 여 확장 및 도구 창의 성능 문제를 보여 주는 [성능 관리자 대화 상자](#performance-manager-dialog) 를 엽니다.

- **현재 확장에 대해이 메시지 표시 안 함** 을 클릭 하 여 알림을 해제 하 고 기존에 설치 된 확장의 이후 알림이 표시 되지 않도록 합니다. 동기적으로 자동 로드 되는 새 확장을 추가 하는 경우이 알림이 다시 표시 됩니다. 다른 Visual Studio 기능에 대 한 알림을 계속 받게 됩니다.

## <a name="performance-manager-dialog"></a>성능 관리자 대화 상자

![성능 관리자 대화 상자](media/performance-manager.png)

사용자 세션에서 모든 패키지를 동기적으로 로드 한 모든 확장은 **사용 되지 않는 api** 탭에 나타납니다.

* **이 문제에 대 한 자세한 정보** 를 클릭 하 여 사용 되지 않는 api에 대 한 자세한 정보를 수집 합니다.
* 마이그레이션 진행 상태는 해당 확장 공급 업체에 문의 하세요.

## <a name="specify-synchronous-autoload-settings-using-group-policy"></a>그룹 정책을 사용 하 여 동기 autoload 설정 지정

관리자는 그룹 정책을 사용 하도록 설정 하 여 동기 autoload을 허용할 수 있습니다. 이렇게 하려면 다음 키에 레지스트리 기반 정책을 설정합니다.

**HKEY_LOCAL_MACHINE \SOFTWARE\Policies\Microsoft\VisualStudio\SynchronousAutoload**

항목 = **허용 됨**

값 = (DWORD)
* **0** 은 동기 autoload 허용 되지 않습니다.
* **1** 은 동기 autoload 허용 됩니다.

## <a name="extension-authors"></a>확장 작성자
확장 작성자는 [AsyncPackage로 마이그레이션](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/AsyncPackageMigration)에서 패키지를 비동기 autoload로 마이그레이션하기 위한 지침을 찾을 수 있습니다.

## <a name="see-also"></a>추가 정보
Visual Studio 2019의 동기 autoload 설정에 대 한 자세한 내용은 [동기 Autoload 동작](https://devblogs.microsoft.com/visualstudio/updates-to-synchronous-autoload-of-extensions-in-visual-studio-2019/) 페이지를 참조 하세요.
