---
title: 단위 테스트에서 Microsoft.VisualStudio.TestTools.UnitTesting 구성원 사용 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 0fa335fd-e442-448f-913f-25a19df90a93
caps.latest.revision: 8
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e8b3ea10b96a63bd18098030dc884ac3f3383353
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657192"
---
# <a name="using-microsoftvisualstudiotesttoolsunittesting-members-in-unit-tests"></a>단위 테스트에서 Microsoft.VisualStudio.TestTools.UnitTesting 멤버 사용
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
단위 테스트 프레임워크는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]의 단위 테스트를 지원합니다. 단위 테스트를 코딩하는 경우 <xref:Microsoft.VisualStudio.TestTools.UnitTesting> 네임스페이스의 클래스 및 멤버를 사용합니다. 단위 테스트를 처음부터 작성했거나 테스트 중인 코드에서 생성된 단위 테스트를 다시 정의하는 경우 이러한 클래스와 멤버를 사용할 수 있습니다.

## <a name="groups-of-elements"></a>요소 그룹
 단위 테스트 프레임워크의 개요를 보다 명확하게 제공하기 위해 이 섹션에서는 UnitTesting 네임스페이스의 요소가 관련 기능의 그룹으로 구성되어 있습니다.

> [!NOTE]
> 해당 이름이 Attribute 문자열로 끝나는 특성 요소는 Attribute 문자열을 포함하거나 포함하지 않고 사용할 수 있습니다. 예를 들어 다음 두 코드 예제는 동일하게 작동합니다.
>
> `[TestClass()]`
>
> `[TestClassAttribute()]`

### <a name="elements-used-for-data-driven-testing"></a>데이터 기반 테스트를 위해 사용되는 요소
 다음 요소를 사용하여 데이터 기반 단위 테스트를 설정합니다. 자세한 내용은 [방법: 데이터 기반 단위 테스트 만들기](../test/how-to-create-a-data-driven-unit-test.md) 및 [연습: 구성 파일을 사용하여 데이터 소스 정의](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md)를 참조하세요.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataAccessMethod>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElement>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElementCollection>

## <a name="attributes-used-to-establish-a-calling-order"></a>호출 순서를 설정하는 데 사용되는 특성
 다음 특성 중 하나를 사용하여 데코레이팅도니 코드 요소는 지정하는 즉시 호출됩니다. 자세한 내용은 [단위 테스트 분석](https://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144)을 참조하세요.

### <a name="for-assemblies"></a>어셈블리
 AssemblyInitialize 및 AssemblyCleanup은 어셈블리를 로드한 직후와 어셈블리를 언로드하기 직전에 호출됩니다.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyCleanupAttribute>

### <a name="for-classes"></a>클래스
 ClassInitialize 및 ClassCleanup은 클래스를 로드한 직후와 클래스를 언로드하기 직전에 호출됩니다.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassCleanupAttribute>

### <a name="for-test-methods"></a>테스트 메서드

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute>

## <a name="attributes-used-to-identify-test-classes-and-methods"></a>테스트 클래스 및 메서드를 식별하는 데 사용되는 특성
 모든 테스트 클래스에는 TestClass 특성이 있어야 하며 모든 테스트 메서드에는 TestMethod 특성이 있어야 합니다. 자세한 내용은 [단위 테스트 분석](https://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144)을 참조하세요.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute>

## <a name="assert-classes-and-related-exceptions"></a>Assert 클래스 및 관련 예외
 단위 테스트에서는 다양한 종류의 Assert 문, 예외 및 특성을 사용하여 특정 애플리케이션 동작을 확인할 수 있습니다. 자세한 내용은 [Assert 클래스 사용](../test/using-the-assert-classes.md)을 참조하세요.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute>

## <a name="the-testcontext-class"></a>TestContext 클래스
 다음 특성 및 해당 특성에 할당된 값은 특정 테스트 메서드에 대해 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 속성 창에 표시됩니다. 이러한 특성은 단위 테스트의 코드를 통해 액세스할 수 없습니다. 대신 개발자가 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]의 IDE를 통해, 또는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 테스트 엔진이 단위 테스트를 사용하거나 실행하는 방식에 영향을 줍니다. 예를 들어 이러한 특성 중 일부는 테스트 관리자 창과 테스트 결과 창에 열로 표시됩니다. 즉, 이러한 특성을 사용하여 테스트 및 테스트 결과를 그룹화하고 정렬할 수 있습니다. 이러한 특성 중 하나로 단위 테스트에 임의의 메타데이터를 추가하는 데 사용하는 TestPropertyAttribute가 있습니다. 예를 들어 이 특성을 사용하면 단위 테스트를 `[TestProperty("TestPass", "Accessibility")]`로 표시하여 이 테스트에 포함되는 테스트 합격의 이름을 저장할 수 있습니다. 또는 테스트의 종류를 나타내는 표시기(`[TestProperty("TestKind", "Localization")]`)를 저장하는 데 이 특성을 사용할 수도 있습니다. 이 특성을 사용하여 만드는 속성과 할당하는 속성 값은 둘 다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 속성 창에서 **테스트 특정**이라는 제목 아래에 표시됩니다.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DeploymentItemAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DescriptionAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.IgnoreAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.WorkItemAttribute>

## <a name="test-configuration-classes"></a>테스트 구성 클래스

- [ObjectTypes](/previous-versions/visualstudio/visual-studio-2013/dd987428(v=vs.120))

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection>

## <a name="attributes-used-for-generating-reports"></a>보고서 생성에 사용되는 특성
 이 섹션의 특성은 데코레이팅하는 테스트 메서드와 [!INCLUDE[esprtfs](../includes/esprtfs-md.md)] 팀 프로젝트의 프로젝트 계층 구조 내 엔터티 간의 관계를 설정합니다.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssIterationAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssProjectStructureAttribute>

## <a name="classes-used-with-private-accessors"></a>전용 접근자와 함께 사용되는 클래스
 [publicize를 사용하여 전용 접근자 만들기](https://msdn.microsoft.com/2056c6a7-6672-42a7-8f53-fead33c56deb)에서 설명하는 것처럼 전용 메서드에 대한 단위 테스트를 생성할 수 있습니다. 이러한 단위 테스트 생성에서는 PrivateObject 클래스의 개체를 인스턴스화하는 전용 접근자 클래스가 만들어집니다. PrivateObject 클래스는 전용 접근자 프로세스의 일부분으로 리플렉션을 사용하는 래퍼 클래스입니다. PrivateType 클래스도 이와 유사하지만 전용 인스턴스 메서드를 호출하는 대신 전용 정적 메서드를 호출하는 데 사용됩니다.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateType>

## <a name="see-also"></a>참고 항목

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting>