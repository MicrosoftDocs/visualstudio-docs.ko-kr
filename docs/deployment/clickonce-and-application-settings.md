---
title: ClickOnce 및 응용 프로그램 설정 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, application settings
ms.assetid: 891caba6-faef-4a3c-8f71-60e6fadb60eb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a72b5bc3f3645d9af1008f2c178ab285e8b45449
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "84184135"
---
# <a name="clickonce-and-application-settings"></a>ClickOnce 및 애플리케이션 설정
Windows Forms에 대 한 응용 프로그램 설정을 사용 하면 클라이언트에서 사용자 지정 응용 프로그램 및 사용자 기본 설정을 쉽게 만들고 저장 하 고 유지 관리할 수 있습니다. 다음 문서에서는 ClickOnce 응용 프로그램에서 응용 프로그램 설정 파일의 작동 방식 및 사용자가 다음 버전으로 업그레이드 하는 경우 ClickOnce에서 설정을 마이그레이션하는 방법에 대해 설명 합니다.

 아래 정보는 기본 응용 프로그램 설정 공급자 인 클래스에만 적용 됩니다 <xref:System.Configuration.LocalFileSettingsProvider> . 사용자 지정 공급자를 제공 하는 경우 해당 공급자는 데이터를 저장 하는 방법 및 버전 간에 해당 설정을 업그레이드 하는 방법을 결정 합니다. 응용 프로그램 설정 공급자에 대 한 자세한 내용은 [응용 프로그램 설정 아키텍처](/dotnet/framework/winforms/advanced/application-settings-architecture)를 참조 하세요.

## <a name="application-settings-files"></a>응용 프로그램 설정 파일
 응용 프로그램 설정은 * \<app>.exe.config* 및 *user.config*의 두 파일을 사용 합니다. 여기서 *app* 은 Windows Forms 응용 프로그램의 이름입니다. *user.config* 는 응용 프로그램이 사용자 범위 설정을 처음 저장할 때 클라이언트에서 만들어집니다. 이와 대조적으로 * \<app>.exe.config*설정에 대 한 기본값을 정의 하는 경우 배포 전에 존재 합니다. Visual Studio는 해당 **게시** 명령을 사용할 때이 파일을 자동으로 포함 합니다. *Mage.exe* 또는 *MageUI.exe*를 사용 하 여 ClickOnce 응용 프로그램을 만드는 경우 응용 프로그램 매니페스트를 채울 때이 파일이 응용 프로그램의 다른 파일에 포함 되어 있는지 확인 해야 합니다.

 ClickOnce를 사용 하 여 배포 되지 않은 Windows Forms 응용 프로그램에서는 응용 프로그램의 * \<app>.exe.config* 파일이 응용 프로그램 디렉터리에 저장 되 고 *user.config* 파일은 사용자의 **Documents and Settings** 폴더에 저장 됩니다. ClickOnce 응용 프로그램에서 * \<app>.exe.config* 은 clickonce 응용 프로그램 캐시 내부의 응용 프로그램 디렉터리에 있고 *user.config* 는 해당 응용 프로그램에 대 한 clickonce 데이터 디렉터리에 상주 합니다.

 응용 프로그램을 배포 하는 방법에 관계 없이 응용 프로그램 설정은 * \<app>.exe.config*에 대 한 안전한 읽기 액세스와 *user.config*에 대 한 안전한 읽기/쓰기 액세스를 보장 합니다.

 ClickOnce 응용 프로그램에서 응용 프로그램 설정에 사용 되는 구성 파일의 크기는 ClickOnce 캐시 크기에 의해 제한 됩니다. 자세한 내용은 [ClickOnce 캐시 개요](../deployment/clickonce-cache-overview.md)를 참조 하세요.

## <a name="version-upgrades"></a>버전 업그레이드
 ClickOnce 응용 프로그램의 각 버전이 다른 모든 버전과 격리 되는 것 처럼 ClickOnce 응용 프로그램에 대 한 응용 프로그램 설정도 다른 버전의 설정에서 격리 됩니다. 사용자가 응용 프로그램의 최신 버전으로 업그레이드 하는 경우 응용 프로그램 설정은 최신 (가장 높은 번호) 버전의 설정을 업데이트 된 버전으로 제공 된 설정과 비교 하 고 설정을 새 설정 파일 집합으로 병합 합니다.

 다음 표에서는 응용 프로그램 설정에서 복사할 설정을 결정 하는 방법을 설명 합니다.

|변경 형식|업그레이드 작업|
|--------------------|--------------------|
|* \<app>.exe.config* 에 추가 된 설정|새 설정이 현재 버전의 * \<app>.exe.config* 에 병합 됩니다.|
|* \<app>.exe.config* 에서 제거 되는 설정|이전 설정은 현재 버전의 * \<app>.exe.config* 에서 제거 되었습니다.|
|설정의 기본값이 변경 되었습니다. 로컬 설정은 *user.config* 의 원래 기본값으로 설정 되어 있습니다.|설정은 새 기본값을 값으로 사용 하 여 현재 버전의 *user.config* 으로 병합 됩니다.|
|설정의 기본값이 변경 되었습니다. *user.config* 에서 기본값이 아닌 설정으로 설정 됩니다.|이 설정은 기본값이 아닌 값이 유지 되는 현재 버전의 *user.config* 에 병합 됩니다.|

사용자 고유의 응용 프로그램 설정 래퍼 클래스를 만들고 업데이트 논리를 사용자 지정 하려는 경우 메서드를 재정의할 수 있습니다 <xref:System.Configuration.ApplicationSettingsBase.Upgrade%2A> .

## <a name="clickonce-and-roaming-settings"></a>ClickOnce 및 로밍 설정
 ClickOnce는 로밍 설정에서 작동 하지 않으므로 설정 파일이 네트워크의 컴퓨터에서 사용자를 팔 로우 할 수 있습니다. 로밍 설정이 필요한 경우 네트워크를 통해 설정을 저장 하는 응용 프로그램 설정 공급자를 구현 하거나 원격 컴퓨터에 설정을 저장 하기 위한 고유한 사용자 지정 설정 클래스를 개발 해야 합니다. 설정 공급자에 대 한 자세한 내용은 [응용 프로그램 설정 아키텍처](/dotnet/framework/winforms/advanced/application-settings-architecture)를 참조 하세요.

## <a name="see-also"></a>추가 정보
- [ClickOnce 보안 및 배포](../deployment/clickonce-security-and-deployment.md)
- [응용 프로그램 설정 개요](/dotnet/framework/winforms/advanced/application-settings-overview)
- [ClickOnce 캐시 개요](../deployment/clickonce-cache-overview.md)
- [ClickOnce 애플리케이션의 로컬 및 원격 데이터 액세스](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)