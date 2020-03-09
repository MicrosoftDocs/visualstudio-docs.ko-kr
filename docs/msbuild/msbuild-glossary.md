---
title: MSBuild 용어
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: f767d8e4-24d8-4803-80eb-e857202dbe2c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8f20fdb4cd809e422bc33535f3143b45db99842f
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633345"
---
# <a name="msbuild-glossary"></a>MSBuild 용어

이러한 용어는 Microsoft Build Engine(MSBuild) 및 해당 구성 요소를 설명하는 데 사용됩니다.

## <a name="glossary"></a>용어

AssemblyFoldersEx\
타사 공급업체가 지원하는 프레임워크의 각 버전 경로를 저장하는 레지스트리 위치입니다. 디자인 타임 확인 시에 이 경로에서 참조 어셈블리를 찾을 수 있습니다.

batching\
일괄 처리란 항목을 항목 메타데이터에 따라 *배치*라는 서로 다른 범주로 구분한 후에 각 배치를 사용하여 대상이나 작업을 한 번 실행하는 방식을 의미합니다. 일괄 처리는 for-loop 구문에 해당하는 MSBuild 기능입니다. 자세한 내용은 [일괄 처리](../msbuild/msbuild-batching.md)를 참조하세요.

build-scope\
빌드 범위는 프로젝트 및 다중 프로젝트 빌드에서 생성된 자식 프로젝트에 표시될 수 있는 전역 속성 등의 MSBuild 개체를 설명합니다.

child project\
*프로젝트, 자식*을 참조하세요.

condition\
대부분의 MSBuild 요소는 조건부로(요소에 `Condition` 특성이 표시되도록) 정의할 수 있습니다. 조건이 `true`로 확인되지 않으면 조건부 요소의 내용이 무시됩니다. 자세한 내용은 [조건](../msbuild/msbuild-conditions.md)을 참조하세요.

definition, item\
*항목 정의*를 참조하세요.

emit item\
빌드의 실행 단계 중에는 `ItemName` 특성을 포함하는 자식 `Output` 요소가 있는 작업을 통해 항목을 만들거나 수정할 수 있습니다. 이 작업을 새 항목 "내보내기"라고 합니다.

emit property\
빌드의 실행 단계 중에는 `PropertyName` 특성을 포함하는 자식 `Output` 요소가 있는 작업을 통해 속성을 만들거나 수정할 수 있습니다. 이 작업을 새 속성 "내보내기"라고 합니다.

evaluation phase\
평가는 프로젝트 빌드의 첫 번째 단계입니다. 모든 속성 및 항목은 프로젝트에 표시되는 순서대로 평가됩니다. 가져온 프로젝트는 프로젝트에서 나오는 순서대로 평가됩니다. 대상과 작업은 실행 단계까지 실행되지 않으며, 이러한 대상과 작업이 선언하거나 내보내는 속성 또는 항목은 평가 중에 무시됩니다.

execution phase\
실행은 프로젝트 빌드의 두 번째 단계입니다. 선택한 대상이 빌드되고 작업이 실행됩니다. 속성과 항목을 만들거나 평가 값과 비교하여 수정할 수 있습니다.

function, property\
*속성 함수*를 참조하세요.

function, item\
항목 함수를 참조하세요.

item\
항목은 빌드 시스템에 대한 입력이며 해당 요소 이름에 따라 항목 종류로 그룹화됩니다. 항목은 일반적으로 파일을 나타냅니다. 항목은 속하는 항목 종류를 기준으로 이름이 지정되므로 *항목*과 *항목 값*이라는 용어는 동일한 의미로 사용할 수 있습니다. 자세한 내용은 [항목](../msbuild/msbuild-items.md)을 참조하세요.

item definition\
항목 정의 그룹에는 모든 항목 종류에 기본 메타데이터를 추가하는 항목 정의가 포함됩니다. 잘 알려진 메타데이터와 마찬가지로 기본 메타데이터도 지정된 항목 종류의 모든 항목과 연결됩니다. 항목 정의에서 기본 메타데이터를 명시적으로 재정의할 수 있습니다. 자세한 내용은 [항목 정의](../msbuild/item-definitions.md)를 참조하세요.

item function\
항목 함수는 프로젝트의 항목에 대한 정보를 가져옵니다. 이러한 함수를 사용하면 Distinct() 항목을 간편하게 가져올 수 있으며 항목을 반복하는 방식보다 속도도 더 빠릅니다. 항목 경로 및 문자열을 조작하는 함수도 있습니다. 자세한 내용은 [항목 함수](../msbuild/item-functions.md)를 참조하세요.

item metadata\
*메타데이터, 항목*을 참조하세요.

item type\
항목 종류는 작업의 매개 변수로 사용할 수 있는 명명된 항목 목록입니다. 작업은 항목 값을 사용하여 빌드 프로세스의 단계를 수행합니다. 자세한 내용은 [항목](../msbuild/msbuild-items.md)을 참조하세요.

metadata, item\
항목 메타데이터는 항목과 연결된 이름/값 쌍의 컬렉션입니다. 메타데이터는 항목에 대한 설명 정보를 제공하며 잘 알려진 메타데이터를 제외하면 선택 사항입니다. 자세한 내용은 [항목](../msbuild/msbuild-items.md)을 참조하세요.

metadata, well-known\
잘 알려진 메타데이터는 미리 정의된 값을 사용하여 초기화되는 읽기 전용 항목 메타데이터입니다. 잘 알려진 메타데이터는 파일을 참조하는 항목에 대한 설명 정보를 제공합니다. 예를 들어 `FullPath`라는 잘 알려진 메타데이터의 값은 참조되는 파일의 전체 경로입니다. 자세한 내용은 [항목](../msbuild/msbuild-items.md)을 참조하세요.

multitargeting\
애플리케이션이나 어셈블리 프로젝트가 MSBuild 및 Visual Studio와 다른 여러 CLR 및 프레임워크를 대상으로 지정할 수 있는 기능입니다.

profile\
전체 프레임워크의 하위 집합입니다. 컴퓨터에 다운로드해야 하는 항목의 양을 최소화하는 데 사용됩니다.

project file\
프로젝트 파일에는 빌드를 제어하는 MSBuild 스크립트가 포함되어 있습니다. 프로젝트 파일의 파일 확장명은 *.csproj* 또는 *.vbproj*와 같이 대개 *proj*로 끝납니다. 프로젝트 파일은 속성 파일과 대상 파일을 가져올 수 있습니다.

property\
속성은 빌드 프로세스를 제어하는 데 사용되는 키/값 쌍입니다. 자세한 내용은 [MSBuild 속성](../msbuild/msbuild-properties.md)을 참조하세요.

property, environment\
환경 속성은 이름이 같은 시스템 환경 변수의 값으로 자동 초기화되는 속성입니다. 자세한 내용은 [MSBuild 속성](../msbuild/msbuild-properties.md)을 참조하세요.

property file\
속성 파일은 빌드를 안내하는 대부분의 속성 그룹 및 항목 그룹을 포함하는 프로젝트 파일입니다. 규칙에 따라 속성 파일의 확장명은 *.props*입니다. 일반적으로 관련 프로젝트 파일의 시작 부분에서 속성 파일을 가져옵니다.

property, function\
속성 함수는 MSBuild 스크립트를 평가하는 데 사용할 수 있는 시스템 속성 또는 메서드입니다. 속성 메서드를 사용하면 시스템 시간을 읽고 문자열을 비교하며 정규식을 일치시키고 다른 작업을 수행할 수 있습니다. 자세한 내용은 [속성 함수](../msbuild/property-functions.md)를 참조하세요.

property function, nested\
속성 함수를 결합하여 보다 복잡한 함수를 만들 수 있습니다. 예를 들면 다음과 같습니다.

 `$([MSBuild]::BitwiseAnd(32,   $([System.IO.File]::GetAttributes(tempFile))))`

자세한 내용은 [속성 함수](../msbuild/property-functions.md)를 참조하세요.

property, global\
전역 속성은 빌드 프로세스를 제어하는 데 사용되는 키/값 쌍입니다. 전역 속성은 명령 프롬프트에서 설정하거나 [MSBuild 작업](../msbuild/msbuild-task.md)의 `Properties` 특성을 사용하여 설정하며, 빌드의 평가 단계 중에는 수정할 수 없습니다. 자세한 내용은 [MSBuild 속성](../msbuild/msbuild-properties.md)을 참조하세요.

property, local\
로컬 속성은 빌드 프로세스를 제어하는 데 사용되는 키/값 쌍입니다. 이 용어는 전역 속성이 아닌 속성을 구분하기 위한 용도로만 사용됩니다.

property, registry\
레지스트리 속성은 시스템 레지스트리 하위 키의 값을 읽는 특수 구문을 사용하여 설정되는 값을 포함합니다. 자세한 내용은 [MSBuild 속성](../msbuild/msbuild-properties.md)을 참조하세요.

property, reserved\
예약된 속성은 빌드 프로세스를 제어하는 데 사용되는 키/값 쌍입니다. 예약된 속성은 미리 정의된 값으로 자동 초기화됩니다. 자세한 내용은 [MSBuild 속성](../msbuild/msbuild-properties.md)을 참조하세요.

project-scope\
프로젝트 범위는 포함하는 프로젝트 파일 및 이 파일이 가져오는 프로젝트에만 표시되는 로컬 속성 등의 MSBuild 개체를 설명합니다.

project, child\
자식 프로젝트는 프로젝트 빌드 중에 MSBuild 작업에서 만들어집니다. 이 새 프로젝트는 MSBuild 작업이 포함된 대상을 가져오거나 포함하는 프로젝트의 자식입니다. 자식 프로젝트는 `Properties` 특성을 통해 수정되는 경우가 아니면 부모 프로젝트의 전역 속성을 상속합니다.

redist list\
재배포 목록은 지정된 프레임워크에 해당하는 어셈블리 목록입니다.

reference assembly\
디자인 타임 동안 애플리케이션을 만드는 데 사용되는 어셈블리입니다. 참조 어셈블리에서는 실제 코드와 개인 인터페이스를 제거하고 메타데이터와 공용 인터페이스만 남겨 둘 수 있습니다.

property\
*속성, 레지스트리*를 참조하세요.

target\
대상은 작업을 특정 순서로 그룹화하고 프로젝트 파일의 섹션을 빌드 프로세스의 진입점으로 표시합니다. 자세한 내용은 [대상](../msbuild/msbuild-targets.md)을 참조하세요.

target, building\
대상, 실행을 참조하세요.

target, evaluating\
증분 컴파일이 수행되므로 대상에서 속성과 항목의 변경 가능성을 분석해야 합니다. 대상을 건너뛰더라도 이러한 변경은 수행되어야 합니다. 대상을 평가한다는 것은 이 분석을 수행하고 해당 변경을 수행하는 과정을 의미합니다. 자세한 내용은 [증분 빌드](../msbuild/incremental-builds.md)를 참조하세요.

target, executing\
대상을 실행한다는 것은 해당 대상을 평가하고 조건이 없거나 조건이 true로 평가되는 모든 작업을 실행하는 과정을 의미합니다. 증분 컴파일 중에는 대상을 건너뛰거나 실행할 수 있지만, 어떤 경우든 대상을 항상 평가해야 합니다. 자세한 내용은 대상, 평가를 참조하세요.

target, running\
조건이 false로 평가되는 대상은 실행되지 않으므로 빌드에 영향을 주지 않습니다. 실행되는 대상의 경우 작업이 실행되거나 해당 대상을 건너뜁니다. 두 경우 모두 대상은 평가됩니다. 자세한 내용은 대상, 평가를 참조하세요.

target, skipping\
증분 컴파일에서 모든 출력 파일이 최신 상태임이 확인되면 대상을 건너뜁니다. 즉, 대상이 평가는 되지만 대상 내의 작업이 실행되지는 않습니다. 자세한 내용은 대상, 평가를 참조하세요.

target framework moniker\
대상으로 지정하려는 프레임워크(예: .NET Framework, Silverlight 등), 버전 및 프로필(예: 클라이언트, 서버 등)을 설명하는 이름입니다.

targeting pack\
지정된 프레임워크 및 해당 프레임워크용 참조 어셈블리 집합을 사용하여 배포되는 어셈블리의 목록입니다.

targets file\
대상 파일은 빌드를 안내하는 대부분의 대상 및 작업을 포함하는 프로젝트 파일입니다. 규칙에 따라 대상 파일의 확장명은 *.targets*입니다. 일반적으로 관련 프로젝트 파일의 끝부분에서 대상 파일을 가져옵니다.

task\
작업은 MSBuild 프로젝트에서 빌드 작업을 수행하는 데 사용하는 실행 코드 단위입니다. 예를 들어, 작업은 입력 파일을 컴파일하거나 외부 도구를 실행할 수 있습니다. 자세한 내용은 [작업](../msbuild/msbuild-tasks.md)을 참조하세요.

transform\
변형은 항목 컬렉션 간의 일대일 변환입니다. 변형을 수행하면 프로젝트가 항목 컬렉션을 변환할 수 있을 뿐 아니라, 대상이 입력과 출력 간의 직접 매핑을 식별할 수 있습니다. 자세한 내용은 [변환](../msbuild/msbuild-transforms.md)을 참조하세요.

well-known metadata\
*메타데이터, 잘 알려짐*을 참조하세요.

## <a name="see-also"></a>참조

- [MSBuild](../msbuild/msbuild.md)
