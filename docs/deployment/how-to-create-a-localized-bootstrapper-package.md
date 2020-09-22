---
title: 지역화 된 부트스트래퍼 패키지 만들기 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- localized bootstrapper packages
- dependencies, creating localized bootstrapper packages
- prerequisites, creating localized bootstrapper packages
ms.assetid: 66a1bc7e-6540-4164-963d-557196a69d8a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2c673c6488b93802877ef088d9d9a1a4793cf50b
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852487"
---
# <a name="how-to-create-a-localized-bootstrapper-package"></a>방법: 지역화된 부트스트래퍼 패키지 만들기
부트스트래퍼 패키지를 만든 후에는 각 로캘에 대해 두 파일, 즉 *eula.rtf*와 같은 소프트웨어 사용 약관 파일과 패키지 매니페스트(*package.xml*)를 추가로 만들어 부트스트래퍼 패키지의 지역화된 버전을 만들 수 있습니다.

 Visual Studio 2010에는 기본적으로 .NET Framework 4, .NET Framework 4 Client Profile, F# Runtime 2.0 및 F# Runtime 4.0용 지역화된 부트스트래퍼 패키지만 포함되어 있습니다. 3개 단계를 완료하면 다른 부트스트래퍼용 지역화된 패키지를 만들 수 있습니다.

1. *Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages \\ \<BootstrapperPackageName> *에 로캘 이름 뒤에 이름이 지정 된 폴더를 만듭니다.

2. 부트스트래퍼 패키지용 소프트웨어 사용 약관이 포함된 파일을 만들어 새 폴더에 저장합니다.

3. *package.xml* 패키지 매니페스트를 만들고 문자열과 문화권을 업데이트한 다음, 새 폴더에 파일을 저장합니다. 대상 언어로 Visual Studio의 부트스트래퍼를 이미 만든 경우이 단계에서 Visual Studio *package.xml* 파일을 복사 하 여 수정할 수 있습니다.

> [!NOTE]
> 설치 프로젝트를 사용하여 애플리케이션을 배포하는 경우 **지역화** 속성을 변경하여 애플리케이션을 지역화할 수 있습니다.

 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-a-localized-bootstrapper-package"></a>지역화된 부트스트래퍼 패키지를 만들려면

1. 로캘 이름과 같은 이름을 지정하여 폴더를 만듭니다.

     32 비트 컴퓨터에서 *Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages \\ \<BootstrapperPackageName> \\ * 폴더에 폴더를 만듭니다.

     64 비트 컴퓨터의 경우에는 *filefiles (86 \\ \<BootstrapperPackageName> \\ ) \Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages* 폴더에 폴더를 만듭니다.

     아래 테이블에는 로캘과 일치하도록 이름을 지정하는 데 사용할 수 있는 폴더 이름이 나와 있습니다.

    |로캘|폴더 이름|
    |------------|-----------------|
    |중국어(간체)|zh-Hans|
    |중국어(번체)|zh-Hant|
    |체코어|cs|
    |독일어|de|
    |영어|en|
    |스페인어|es|
    |프랑스어|fr|
    |이탈리아어|it|
    |한국어|ko|
    |일본어|ja|
    |폴란드어|pl|
    |포르투갈어(브라질)|pt-BR|
    |러시아어|ru|
    |터키어|tr|

2. 부트스트래퍼 패키지용 소프트웨어 사용 약관이 포함된 파일을 만들어 새 폴더에 저장합니다.

3. *package.xml* 라는 패키지 매니페스트를 만들어 새 폴더에 넣습니다. 자세한 내용은 [방법: 패키지 매니페스트 만들기](../deployment/how-to-create-a-package-manifest.md)를 참조 하세요.

4. 문자열이 로캘에 맞는 언어로 설정되도록 패키지 매니페스트의 `<Strings>` 섹션을 업데이트합니다.

5. 폴더 이름과 일치하도록 `<String Name="Culture">` 값을 변경합니다.

6. *package.xml* 파일을 저장 합니다.

### <a name="to-create-a-bootstrapper-package-for-net-framework-35-service-pack-1-localized-in-french"></a>프랑스어로 지역화된 .NET Framework 3.5 서비스 팩 1용 부트스트래퍼 패키지를 만들려면

1. 이름이 *fr*인 폴더를 만듭니다. 폴더 이름은 로캘 이름과 일치해야 합니다.

     32 비트 컴퓨터에서 *Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1 \\ * 폴더에 폴더를 만듭니다.

     64비트 컴퓨터에서는 해당 폴더를 *\Program Files (86)\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\\* 폴더에서 만듭니다.

2. 소프트웨어 사용 조건의 지역화 된 버전을 *fr* 폴더에 넣습니다.

3. Filefiles *(x86) \Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\en\package.xml* 파일을 *fr* 폴더에 복사 하 고 XML 디자이너에서 파일을 엽니다.

4. 오류 문자열이 프랑스어로 표시되도록 패키지 매니페스트의 `<Strings>` 섹션을 업데이트합니다.

5. 값을 `<String Name="Culture">` *fr*로 변경 합니다.

6. *package.xml* 파일을 저장 합니다.

## <a name="see-also"></a>참고 항목
- [부트스트래퍼 패키지 만들기](../deployment/creating-bootstrapper-packages.md)
- [애플리케이션 배포 필수 구성 요소](../deployment/application-deployment-prerequisites.md)
- [방법: 패키지 매니페스트 만들기](../deployment/how-to-create-a-package-manifest.md)