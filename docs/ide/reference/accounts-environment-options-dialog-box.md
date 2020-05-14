---
title: 계정 옵션 참조
ms.date: 12/10/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.RoamingSettings
ms.assetid: 3cfe09d2-1120-46e8-b882-f7056acb778b
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9ff457523024db49502ae982a390d9a7be6ba9dd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595906"
---
# <a name="accounts-environment-options-dialog-box"></a>계정, 환경, 옵션 대화 상자

이 페이지를 사용하여 Visual Studio에 로그인할 때 사용하는 계정과 관련된 다양한 옵션을 설정합니다.

## <a name="personalization-account"></a>개인 설정 계정

### <a name="synchronize-settings-across-devices"></a>디바이스 간에 설정 동기화

이 옵션을 사용하여 여러 머신 간에 설정을 동기화할지 여부를 지정할 수 있습니다. 자세한 내용은 [동기화된 설정](../../ide/synchronized-settings-in-visual-studio.md)을 참조하세요.

### <a name="enable-device-code-flow"></a>디바이스 코드 흐름 사용

이 옵션을 선택할 때 **파일** > **계정 설정** 페이지에서 **계정 추가**를 선택하면 Visual Studio의 동작이 변경됩니다. **계정에 로그인** 페이지를 확인하는 대신 로그인할 웹 브라우저에 붙여넣을 URL과 코드를 제공하는 대화 상자가 나타납니다. 이 옵션은 예를 들어 이전 버전의 Internet Explorer를 사용하거나 방화벽이 액세스를 제한하는 경우와 같이 Visual Studio에 일반적인 방식으로 로그인할 수 없는 경우에 유용합니다. 자세한 내용은 [여러 사용자 계정으로 작업](../work-with-multiple-user-accounts.md#add-an-account-using-device-code-flow)을 참조하세요.

## <a name="registered-azure-clouds"></a>등록된 Azure 클라우드

이 섹션에서는 Visual Studio에 로그인하는 데 사용하는 하나 이상의 계정을 통해 액세스할 수는 Azure 클라우드 인스턴스를 보여줍니다. 예를 들어 회사의 데이터 센터에서 Azure의 전용 인스턴스에 액세스할 수 있습니다. 또는 Azure China 21 Vianet 또는 Azure U.S.와 같은 Azure의 독립 또는 정부 인스턴스에 액세스할 수 있습니다. 정부. 글로벌 Azure 클라우드 인스턴스는 기본적으로 목록에 표시되며 제거할 수 없습니다.

**추가** 단추를 선택하여 추가 Azure 클라우드를 등록합니다. **새 Azure 클라우드 추가** 대화 상자에 연결할 수 있거나 전용 Azure 엔드포인트에 URL을 입력할 수 있는 몇 가지 잘 알려진 Azure 클라우드 인스턴스가 나열됩니다.

![새 Azure 클라우드 인스턴스 추가](media/add-new-azure-cloud.png)

추가 Azure 클라우드를 등록한 후에는 Visual Studio에 로그인할 때 로그인하려는 Azure 클라우드를 선택할 수 있습니다.

## <a name="see-also"></a>참조

- [여러 컴퓨터 간에 설정 동기화](../synchronized-settings-in-visual-studio.md)
- [Visual Studio에 로그인](../signing-in-to-visual-studio.md)
- [여러 사용자 계정으로 작업](../work-with-multiple-user-accounts.md)
- [환경 설정](../environment-settings.md)
