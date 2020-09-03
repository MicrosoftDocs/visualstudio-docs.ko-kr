---
title: '오류: 프로젝트 &#39;프로젝트&#39;에서 종속성 &#39;파일&#39;은 (는) 종속성 &#39;파일&#39;과 (와) 충돌 하므로 실행 디렉터리에 복사할 수 없습니다. Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.tasklisterror.copy_version_conflict
ms.assetid: cd7de1eb-7d58-4e2c-9811-a7201f7817be
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5d4fd45741585aaf82c82257999b40d6257e82d9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656042"
---
# <a name="error-the-dependency-39file39-in-project-39project39-cannot-be-copied-to-the-run-directory-because-it-would-conflict-with-dependency-39file39"></a>오류: 프로젝트 &#39;프로젝트&#39;에서 종속성 &#39;파일&#39;은 (는) 종속성 &#39;파일과 충돌 하므로 실행 디렉터리에 복사할 수 없습니다&#39;
참조 간에 충돌이 존재합니다. 즉, 실행할 애플리케이션의 bin 디렉터리에 파일 이름이 같은 둘 이상의 고유 종속성을 복사하려고 했습니다. 종속성이 모두 기본 참조가 아니므로 실행 디렉터리에서 충돌을 해결할 수 없습니다.

 이 오류가 발생하면 빌드는 실패합니다.

 작업 목록 항목을 두 번 클릭하여 충돌이 발생한 프로젝트의 참조 노드로 이동하세요.

 **이 오류를 해결하려면**

- 어셈블리 중 하나를 프로젝트의 직접 참조로 만듭니다. 단, 이 방법을 사용하면 선택한 어셈블리가 다른 버전의 참조된 어셈블리를 사용하는 어셈블리와 작동하지 않을 수 있습니다.

     \- 또는 -

- 어셈블리의 두 복사본을 모두 강력한 이름으로 지정하고 전역 어셈블리 캐시에 둡니다. 이렇게 하면 어셈블리를 bin 디렉터리에 복사하지 않아도 됩니다.

## <a name="see-also"></a>관련 항목
 [프로젝트의 참조 관리](../ide/managing-references-in-a-project.md) [전역 어셈블리 캐시](https://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202) [강력한 이름의 어셈블리](https://msdn.microsoft.com/library/d4a80263-f3e0-4d81-9b61-f0cbeae3797b) [어셈블리 버전 관리](https://msdn.microsoft.com/library/775ad4fb-914f-453c-98ef-ce1089b6f903) [방법: 프로젝트 종속성 만들기 및 제거](../ide/how-to-create-and-remove-project-dependencies.md)