---
title: 프로젝트 확장 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- projects [Visual Studio]
ms.assetid: 096d273d-4fe9-4f24-9b00-470bfbdf4bdf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 14108a304cc5f85c9a870bc66804df7daa98f3ca
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711745"
---
# <a name="extend-projects"></a>프로젝트 확장
프로젝트 및 솔루션은 Visual Studio에서 코드 및 리소스 파일을 컴파일 및 배포 단위로 구성하는 방법입니다. 프로젝트에 대한 자세한 내용은 [프로젝트(Visual Studio SDK)에서](../extensibility/extending-projects.md)확인할 수 있습니다.

 프로젝트에 대한 Visual Studio SDK 및 프로젝트에 대한 관리되는 패키지 프레임워크를 사용하여 사용자 고유의 프로젝트 유형을 만들 수 있으며, [프로젝트에 대한 관리되는 패키지 프레임워크에서](https://github.com/tunnelvisionlabs/MPFProj10)다운로드할 수 있습니다. 사용자 지정 프로젝트가 구현되는 방법을 이해하려면 [새 프로젝트 생성: 후드 아래, 1부](../extensibility/internals/new-project-generation-under-the-hood-part-one.md) 및 [새 프로젝트 생성: 후드 아래, 2부.](../extensibility/internals/new-project-generation-under-the-hood-part-two.md)

 이 섹션의 항목에서는 사용자 지정 프로젝트를 만드는 방법과 다양한 유형의 Visual Studio 솔루션을 관리하는 방법에 대해 설명합니다.

## <a name="in-this-section"></a>섹션 내용
- [기본 프로젝트 시스템 만들기, 1부](../extensibility/creating-a-basic-project-system-part-1.md) 사용자 지정 프로젝트 시스템을 만드는 방법에 대해 설명합니다.

- [기본 프로젝트 시스템 만들기, 2부](../extensibility/creating-a-basic-project-system-part-2.md) 사용자 지정 프로젝트 시스템을 만드는 방법에 대해 설명합니다.

- [프로젝트 파일에 데이터 저장](../extensibility/saving-data-in-project-files.md) 프로젝트에 추가하는 방법을<em>설명합니다.</em> proj*) 파일을 제공합니다.

- [런타임에 프로젝트의 하위 유형 확인](../extensibility/verifying-subtypes-of-a-project-at-run-time.md) 런타임에 프로젝트의 하위 유형을 확인하는 방법을 설명합니다.

- [속성 페이지 추가 및 제거](../extensibility/adding-and-removing-property-pages.md) 사용자 지정 프로젝트의 속성 페이지를 사용자 지정하는 방법을 설명합니다.

- [프로젝트 항목에 특성 추가](../extensibility/adding-an-attribute-to-a-project-item.md) 사용자 지정 프로젝트 항목에 특성을 추가하는 방법을 설명합니다.

- [프로젝트 항목의 속성 유지](../extensibility/persisting-the-property-of-a-project-item.md) 사용자 지정 프로젝트 항목의 속성을 유지하는 방법을 설명합니다.

- [범용 Windows 프로젝트 관리](../extensibility/managing-universal-windows-projects.md) 범용 프로젝트를 관리하는 방법을 설명합니다.
