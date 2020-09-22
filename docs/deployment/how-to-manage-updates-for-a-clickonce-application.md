---
title: ClickOnce 응용 프로그램에 대 한 업데이트 관리 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.Update
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, managing applications
- ClickOnce deployment, updates
- updating data, ClickOnce
- application updates
ms.assetid: a3f23f05-e7f1-4620-b23c-2d68f9643684
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6f4ebe4d04aa585d9129587fe3c250c46516c824
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851608"
---
# <a name="how-to-manage-updates-for-a-clickonce-application"></a>방법: ClickOnce 애플리케이션에 대한 업데이트 관리
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램은 자동으로 또는 프로그래밍 방식으로 업데이트를 확인할 수 있습니다. 개발자는 업데이트 확인을 수행 하는 시기와 방법, 업데이트가 필수 인지 여부 및 응용 프로그램이 업데이트를 확인 해야 하는 위치를 지정 하는 데 많은 유연성을 발휘할 수 있습니다.

 응용 프로그램이 시작 되기 전이나 응용 프로그램이 시작 된 후 설정 된 간격으로 업데이트를 자동으로 확인 하도록 응용 프로그램을 구성할 수 있습니다. 또한 필요한 최소 버전을 지정할 수 있습니다. 즉, 사용자의 버전이 필요한 버전 보다 낮은 경우 업데이트가 설치 됩니다.

 응용 프로그램에서 사용자 요청 등의 이벤트에 따라 프로그래밍 방식으로 업데이트를 확인 하도록 구성할 수 있습니다. 이 항목의 "프로그래밍 방식으로 업데이트를 확인 하려면" 절차에서는 클래스를 사용 하 여 이벤트를 <xref:System.Deployment.Application.ApplicationDeployment> 기반으로 업데이트를 확인 하는 코드를 작성 하는 방법을 보여 줍니다.

 한 위치에서 응용 프로그램을 배포 하 고 다른 위치에서 업데이트할 수도 있습니다. "다른 업데이트 위치를 지정 하려면" 절차를 참조 하십시오.

 자세한 내용은 [ClickOnce 업데이트 전략 선택](../deployment/choosing-a-clickonce-update-strategy.md)을 참조하세요.

 업데이트 동작은 **프로젝트 디자이너** 의 **게시** 페이지에서 사용할 수 있는 **응용 프로그램 업데이트** 대화 상자에서 관리 됩니다.

### <a name="to-check-for-updates-before-the-application-starts"></a>응용 프로그램을 시작 하기 전에 업데이트를 확인 하려면

1. **솔루션 탐색기**에서 프로젝트를 선택한 상태에서 **프로젝트** 메뉴에서 **속성**을 클릭합니다.

2. **게시** 탭을 클릭합니다.

3. **업데이트** 단추를 클릭 하 여 **응용 프로그램 업데이트** 대화 상자를 엽니다.

4. **응용 프로그램 업데이트** 대화 상자에서 **응용 프로그램이 업데이트를 확인 해야 함** 확인란을 선택 했는지 확인 합니다.

5. **응용 프로그램에서 업데이트를 확인 해야 하는 경우 선택** 섹션에서 **응용 프로그램 시작 전**을 선택 합니다. 이렇게 하면 네트워크에 연결 된 사용자가 항상 최신 업데이트를 사용 하 여 응용 프로그램을 실행 합니다.

### <a name="to-check-for-updates-in-the-background-after-the-application-starts"></a>애플리케이션을 시작한 후 백그라운드에서 업데이트를 확인하려면

1. **솔루션 탐색기**에서 프로젝트를 선택한 상태에서 **프로젝트** 메뉴에서 **속성**을 클릭합니다.

2. **게시** 탭을 클릭합니다.

3. **업데이트** 단추를 클릭 하 여 **응용 프로그램 업데이트** 대화 상자를 엽니다.

4. **응용 프로그램 업데이트** 대화 상자에서 **응용 프로그램이 업데이트를 확인 해야 함** 이 선택 되어 있는지 확인 합니다.

5. **응용 프로그램에서 업데이트를 확인 해야 하는 경우 선택 섹션**에서 **응용 프로그램이 시작 된 후**를 선택 합니다. 응용 프로그램은 이러한 방식으로 더 신속 하 게 시작 된 후 백그라운드에서 업데이트를 확인 하 고 업데이트를 사용할 수 있는 경우에만 사용자에 게 알립니다. 설치가 완료 되 면 응용 프로그램을 다시 시작할 때까지 업데이트가 적용 되지 않습니다.

6. **응용 프로그램에서 업데이트를 확인 하는 빈도를 지정** 하십시오. 섹션에서 **응용 프로그램이 실행 될 때마다 확인** (기본값)을 선택 하거나, **각 확인란** 을 선택 하 여 숫자 및 시간 간격을 입력 합니다.

### <a name="to-specify-a-minimum-required-version-for-the-application"></a>응용 프로그램에 필요한 최소 버전을 지정 하려면

1. **솔루션 탐색기**에서 프로젝트를 선택한 상태에서 **프로젝트** 메뉴에서 **속성**을 클릭합니다.

2. **게시** 탭을 클릭합니다.

3. **업데이트** 단추를 클릭 하 여 **응용 프로그램 업데이트** 대화 상자를 엽니다.

4. **응용 프로그램 업데이트** 대화 상자에서 **응용 프로그램이 업데이트를 확인 해야 함** 확인란을 선택 했는지 확인 합니다.

5. **이 응용 프로그램에 필요한 최소 버전 지정** 확인란을 선택한 다음 응용 프로그램의 **주**버전, **부**버전, **빌드**번호 및 **수정** 번호를 입력 합니다.

### <a name="to-specify-a-different-update-location"></a>다른 업데이트 위치를 지정 하려면

1. **솔루션 탐색기**에서 프로젝트를 선택한 상태에서 **프로젝트** 메뉴에서 **속성**을 클릭합니다.

2. **게시** 탭을 클릭합니다.

3. **업데이트** 단추를 클릭 하 여 **응용 프로그램 업데이트** 대화 상자를 엽니다.

4. **응용 프로그램 업데이트** 대화 상자에서 **응용 프로그램이 업데이트를 확인 해야 함** 확인란을 선택 했는지 확인 합니다.

5. **업데이트 위치** 필드에서 형식 또는 \Server\ApplicationName 형식을 사용 하 여 정규화 된 URL을 사용 하 여 업데이트 위치를 입력 *http://Hostname/ApplicationName* 하거나 **찾아보기** 단추를 클릭 * \\ *하 여 업데이트 위치를 찾습니다.

### <a name="to-check-for-updates-programmatically"></a>프로그래밍 방식으로 업데이트를 확인 하려면

1. **솔루션 탐색기**에서 프로젝트를 선택한 상태에서 **프로젝트** 메뉴에서 **속성**을 클릭합니다.

2. **게시** 탭을 클릭합니다.

3. **업데이트** 단추를 클릭 하 여 **응용 프로그램 업데이트** 대화 상자를 엽니다.

4. **응용 프로그램 업데이트** 대화 상자에서 **응용 프로그램이 업데이트를 확인 해야 함** 확인란의 선택을 취소 했는지 확인 합니다. (선택 사항)이 확인란을 선택 하 여 프로그래밍 방식으로 업데이트를 확인 하 고 ClickOnce 런타임에서 업데이트를 자동으로 확인 하도록 할 수도 있습니다.

5. **업데이트 위치** 필드에서 형식 또는 \Server\ApplicationName 형식을 사용 하 여 정규화 된 URL을 사용 하 여 업데이트 위치를 입력 *http://Hostname/ApplicationName* 하거나 **찾아보기** 단추를 클릭 * \\ *하 여 업데이트 위치를 찾습니다. 업데이트 위치는 응용 프로그램이 업데이트 된 버전을 검색 하는 위치입니다.

6. 사용자가 업데이트를 확인 하기 위해 선택 하는 Windows Form에서 단추, 메뉴 항목 또는 기타 사용자 인터페이스 항목을 만듭니다. 해당 항목의 이벤트 처리기에서 메서드를 호출 하 여 업데이트를 확인 하 고 설치 합니다. [방법: ClickOnce 배포 API를 사용 하 여 프로그래밍 방식으로 응용 프로그램 업데이트 확인](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md)에서 이러한 메서드에 대 한 Visual Basic 및 Visual c # 코드의 예제를 찾을 수 있습니다.

7. 응용 프로그램을 빌드합니다.

## <a name="see-also"></a>참고 항목
- <xref:System.Deployment.Application.ApplicationDeployment>
- [애플리케이션 업데이트 대화 상자](/previous-versions/visualstudio/visual-studio-2010/axw1fa38(v=vs.100))
- [ClickOnce 업데이트 전략 선택](../deployment/choosing-a-clickonce-update-strategy.md)
- [ClickOnce 애플리케이션 게시](../deployment/publishing-clickonce-applications.md)
- [방법: 게시 마법사를 사용 하 여 ClickOnce 응용 프로그램 게시](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [방법: ClickOnce 배포 API를 사용하여 프로그래밍 방식으로 애플리케이션 업데이트 확인](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md)
