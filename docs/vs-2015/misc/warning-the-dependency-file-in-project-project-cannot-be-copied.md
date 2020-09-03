---
title: '경고: 프로젝트&#39; 프로젝트 &#39;&#39; 종속성 &#39;파일을 실행 디렉터리에 복사할 수 없습니다. 참조 &#39;파일을 덮어쓸 수 있기 때문입니다. &#39; | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.tasklisterror.copy_version_warning
ms.assetid: 116819f3-a4d4-48b5-9e71-7c54660d38ef
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a619168bd07fde5d27e5c3d87dc46f505cf5268d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672813"
---
# <a name="warning-the-dependency-39file39-in-project-39project39-cannot-be-copied-to-the-run-directory-because-it-would-overwrite-the-reference-39file39"></a>경고: 프로젝트&#39; 프로젝트 &#39;&#39; 종속성 &#39;파일을 실행 디렉터리에 복사할 수 없습니다. 참조 &#39;파일을 덮어쓸 수 있기 때문입니다. &#39;
참조 간에 충돌이 존재합니다. 즉, 실행할 애플리케이션의 bin 디렉터리에 파일 이름이 같은 둘 이상의 고유 어셈블리 파일을 복사하려고 했습니다. 종속성 중 하나가 기본 참조이므로 실행 디렉터리에서 충돌을 해결할 수 없습니다.

 이 작업 목록 항목을 두 번 클릭하여 충돌이 발생한 기본 참조 노드로 이동하세요.

 이 경고는 종속성 충돌이 발생했는데 충돌하는 종속성 중 하나를 참조로 추가하여 충돌을 해결했을 때 발생합니다. 또는 버전 1 참조를 사용하는데 첫째 참조의 버전 2를 참조하는 둘째 참조를 추가했을 때도 발생합니다.

 즉, 이 오류는 솔루션의 프로젝트가 서로를 참조하는데 **참조 추가** 대화 상자의 [프로젝트](https://msdn.microsoft.com/2feb0fe2-0805-4cc9-8cba-b0315849dfb7) 탭을 사용하여 참조를 프로젝트 대 프로젝트 참조로 만들지 않고 **참조 추가** 대화 상자의 **찾아보기** 단추를 사용하여 파일 참조로 만들었기 때문에 발생합니다. 프로젝트 간 참조의 이점은 빌드 시스템에서 프로젝트 간에 종속성을 만들므로 참조하는 프로젝트를 마지막으로 빌드한 후 프로젝트가 변경되면 종속 프로젝트가 빌드된다는 점입니다. 파일 참조는 빌드 종속성을 만들지 않으므로 참조하는 프로젝트만 빌드하고 종속 프로젝트를 빌드하지 않습니다. 그러면 참조가 사용되지 않는 참조가 되므로 이전에 빌드한 프로젝트 버전을 참조할 수 있습니다. 이 경우 bin 디렉터리에 몇 가지 버전의 단일 DLL이 있어야 하는데 여러 버전을 둘 수 없으므로 오류 메시지가 나타납니다.

 이 메시지는 bin 디렉터리에 충돌이 있고 애플리케이션이 제대로 작동하지 않을 때마다 나타납니다. 이 문제를 해결한 후에도 프로젝트 시스템에서 종속성 버전이 모든 구성 요소와 제대로 작동하는지 알 수 없기 때문에 경고가 나타납니다.

 **이 오류를 해결하려면**

- 어셈블리 파일을 전역 어셈블리 캐시에 두어 하나(또는 0개)의 어셈블리 파일만 bin 디렉터리에 복사합니다. 전역 어셈블리 캐시는 파일 이름 충돌을 해결합니다. 공용 언어 런타임이 전역 어셈블리 캐시에서 어셈블리를 찾는 방법을 알기 때문에 어셈블리 파일의 로컬 복사본이 만들어지지 않습니다. 자세한 내용은 [Working with Assemblies and the Global Assembly Cache](https://msdn.microsoft.com/library/8a18e5c2-d41d-49ef-abcb-7c27e2469433) 및 [Error: the dependency 'file' in project 'project' cannot be copied to the run directory because it would conflict with dependency 'file'](/visualstudio/misc/error-dependency-file?view=vs-2015)를 참조하세요.

## <a name="see-also"></a>관련 항목
 프로젝트 [전역 어셈블리 캐시](https://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202) [에서 참조 관리](../ide/managing-references-in-a-project.md) [방법: 프로젝트 종속성 만들기 및 제거](../ide/how-to-create-and-remove-project-dependencies.md)