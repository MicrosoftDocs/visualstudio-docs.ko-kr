---
title: '문제 해결: 어떻게 기존 확장의 새 버전을 릴리스하나요?'
description: 게시 워크플로를 통해 기존 확장을 업데이트하는 방법에 대한 가이드입니다.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 12/14/2020
ms.technology: vs-ide-general
ms.assetid: 5DA76197-7859-421f-AC45-401F22F5D794
ms.topic: troubleshooting
ms.openlocfilehash: 862ae404571da44d9ca28db2c94d2ebeb39ce79f
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97488546"
---
# <a name="troubleshooting-how-do-i-release-a-new-version-of-my-existing-extension"></a>문제 해결: 어떻게 기존 확장의 새 버전을 릴리스하나요?

> [!IMPORTANT]
> 현재 Mac용 Visual Studio 2019에서 새 확장을 만드는 것은 공식적으로 지원되지 않습니다.

Mac용 Visual Studio 확장 리포지토리 서버는 2021년 1월 15일에 이동됩니다. 확장을 이미 다운로드한 사용자는 이러한 이동의 영향을 받지 않지만 이 날짜 이후 확장의 새 릴리스를 게시하는 방식이 달라집니다.

기존 확장의 작성자는 다른 워크플로를 수행하여 추가 업데이트를 릴리스해야 합니다. 이 프로세스는 다음으로 구성됩니다.
- 각 확장에 대한 공용 GitHub 리포지토리 설정
- [확장 게시 메일 그룹](mailto:vsmextpub@microsoft.com)을 통해 Mac용 Visual Studio 팀에 리포지토리 URL 공유
- GitHub의 릴리스 기능을 사용하여 확장 업데이트


## <a name="initial-setup"></a>초기 설정 

확장에 대한 업데이트를 계속 게시하려면 공용 GitHub 리포지토리를 만들어야 합니다. 여러 확장을 게시하는 경우 각 확장에 대해 별도의 리포지토리를 사용해야 합니다. 단, 항상 확장을 버전 지정하고 함께 게시하는 경우에는 단일 리포지토리를 사용할 수 있습니다.

> [!NOTE]
> 확장의 GitHub 리포지토리는 공용이어야 하지만 코드를 호스트할 필요는 없습니다. 이 프로세스를 수행하면 GitHub에 코드가 필요하지 않습니다.


## <a name="share-the-location-of-your-repository"></a>리포지토리의 위치 공유

리포지토리를 설정했으면 [확장 게시 메일 그룹](mailto:vsmextpub@microsoft.com)에 URL을 기재한 이메일을 발송합니다.


## <a name="release-a-new-version"></a>새 버전 릴리스

리포지토리의 기본 페이지에서 "새 릴리스 만들기" 링크를 사용하여 확장을 업데이트하는 프로세스를 시작합니다. 이 링크를 선택한 후에는 다음 단계를 수행합니다.

1. 릴리스의 **태그 버전** 에 다음 형식으로 정보를 추가합니다.

    > v\<releaseVersion>\-vsm\<targetVersion>

    위치:
     - **&lt;releaseVersion&gt;** 은 확장 버전 번호입니다.
     - **&lt;targetVersion&gt;** 은 확장이 대상으로 하는 Mac용 Visual Studio의 최소 버전입니다.

2. (선택 사항) **title** 및 **description** 필드는 원하는 정보로 채울 수 있습니다. 이 워크플로는 해당 필드의 정보를 사용하지 않습니다.

3. **pre-release** 확인란이 선택 취소되었는지 확인합니다. 이 확인란이 선택되어 있으면 이 게시 프로세스에서 릴리스가 선택되지 않습니다.

4. **binaries** 섹션에서 확장을 구현하는 **.mpack** 파일을 연결합니다. 한 릴리스에 여러 **.mpack** 파일을 연결할 수 있습니다.

Mac용 Visual Studio는 확장 리포지토리에 액세스하는 데 사용된 Mac용 Visual Studio 설치와 호환되는 최신 버전의 확장을 표시합니다.

Mac용 Visual Studio 팀에 GitHub 리포지토리를 등록한 경우 Mac용 Visual Studio에서 24시간 이내에 해당 확장 릴리스를 선택합니다.

## <a name="additional-information"></a>추가 정보

- 위에 설명한 요구 사항을 준수하지 않는 릴리스는 게시되지 않습니다. 
- 2021년 1월 15일 이후에는 확장 업데이트가 Mac용 Visual Studio 8.0 이상에만 표시됩니다.
- 기존 확장은 따로 작업을 수행하지 않아도 Mac용 Visual Studio 사용자에게 계속 제공됩니다. 2021년 1월 15일 이후에 새 버전을 게시하는 경우에만 이 가이드의 지침을 따라야 합니다.
