---
title: 프로젝트 확장 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80711745"
---
# <a name="extend-projects"></a>프로젝트 확장
프로젝트 및 솔루션은 Visual Studio에서 코드 및 리소스 파일을 컴파일 및 배포 단위로 구성 하는 방법입니다. 프로젝트에서 프로젝트에 대 한 자세한 정보 [(Visual STUDIO SDK)](../extensibility/extending-projects.md)를 찾을 수 있습니다.

 프로젝트에 대 한 관리 되는 [패키지 프레임 워크](https://github.com/tunnelvisionlabs/MPFProj10)에서 다운로드할 수 있는 프로젝트에 대 한 VISUAL Studio SDK 및 관리 되는 패키지 프레임 워크를 사용 하 여 고유한 프로젝트 형식을 만들 수 있습니다. 사용자 지정 프로젝트를 구현 하는 방법을 이해 하려면 [새 프로젝트 생성: 내부, 파트 1](../extensibility/internals/new-project-generation-under-the-hood-part-one.md) 및 [새 프로젝트 생성: 내부에서 2 부를](../extensibility/internals/new-project-generation-under-the-hood-part-two.md)참조 하세요.

 이 단원의 항목에서는 사용자 지정 프로젝트를 만드는 방법 및 다양 한 형식의 Visual Studio 솔루션을 관리 하는 방법을 설명 합니다.

## <a name="in-this-section"></a>섹션 내용
- [기본 프로젝트 시스템 만들기, 1 부](../extensibility/creating-a-basic-project-system-part-1.md) 사용자 지정 프로젝트 시스템을 만드는 방법을 설명 합니다.

- [기본 프로젝트 시스템 만들기, 2 부](../extensibility/creating-a-basic-project-system-part-2.md) 사용자 지정 프로젝트 시스템을 만드는 방법을 설명 합니다.

- [프로젝트 파일에 데이터 저장](../extensibility/saving-data-in-project-files.md) 프로젝트에 추가 하는 방법에 대해 설명<em>합니다.</em> proj *) 파일.

- [런타임에 프로젝트의 하위 형식 확인](../extensibility/verifying-subtypes-of-a-project-at-run-time.md) 런타임에 프로젝트의 하위 형식을 확인 하는 방법에 대해 설명 합니다.

- [속성 페이지 추가 및 제거](../extensibility/adding-and-removing-property-pages.md) 사용자 지정 프로젝트에 대 한 속성 페이지를 사용자 지정 하는 방법을 설명 합니다.

- [프로젝트 항목에 특성 추가](../extensibility/adding-an-attribute-to-a-project-item.md) 사용자 지정 프로젝트 항목에 특성을 추가 하는 방법에 대해 설명 합니다.

- [프로젝트 항목의 속성 유지](../extensibility/persisting-the-property-of-a-project-item.md) 사용자 지정 프로젝트 항목의 속성을 유지 하는 방법을 설명 합니다.

- [유니버설 Windows 프로젝트 관리](../extensibility/managing-universal-windows-projects.md) 유니버설 프로젝트를 관리 하는 방법을 설명 합니다.
