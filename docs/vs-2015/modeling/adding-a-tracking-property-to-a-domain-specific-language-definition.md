---
title: 도메인별 언어 정의에 추적 속성 추가 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- tracking properties [Domain-Specific Language Tools], walkthrough
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
ms.assetid: 4aa47777-de75-4897-a423-a3c4426b4125
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 382d5dc5ee416d901e1b73b7b2fb346e83abbef6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545576"
---
# <a name="adding-a-tracking-property-to-a-domain-specific-language-definition"></a>도메인별 언어 정의에 추적 속성 추가
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 연습에서는 도메인 모델에 추적 속성을 추가 하는 방법을 보여 줍니다.

 *추적 도메인* 속성은 사용자가 업데이트할 수 있지만 다른 도메인 속성이 나 요소의 값을 사용 하 여 계산 되는 기본값을 갖는 속성입니다.

 예를 들어 도메인 특정 언어 도구 (DSL 도구)에서 도메인 클래스의 표시 이름 속성은 도메인 클래스의 이름을 사용 하 여 계산 되는 기본값을 가지 지만 사용자가 디자인 타임에 값을 변경 하거나 계산 된 값으로 다시 설정할 수 있습니다.

 이 연습에서는 모델의 기본 네임 스페이스 속성을 기반으로 하는 기본 값을 가진 네임 스페이스 추적 속성이 있는 DSL (도메인별 언어)을 만듭니다. 추적 속성에 대 한 자세한 내용은 [추적 속성 정의](https://msdn.microsoft.com/0538b0e4-6221-4e7d-911a-b92cd622f0be)를 참조 하세요.

- DSL 도구는 추적 속성 설명자를 지원 합니다. 그러나 DSL 디자이너는 언어에 추적 속성을 추가 하는 데 사용할 수 없습니다. 따라서 사용자 지정 코드를 추가 하 여 추적 속성을 정의 하 고 구현 해야 합니다.

  추적 속성에는 추적 및 사용자가 업데이트 하는 두 가지 상태가 있습니다. 추적 속성의 기능은 다음과 같습니다.

- 추적 상태에 있는 경우 추적 속성의 값이 계산 되 고 모델 변경의 다른 속성이 해당 값으로 업데이트 됩니다.

- 사용자가 업데이트 한 상태에서 추적 속성 값은 사용자가 속성을 마지막으로 설정한 값을 유지 합니다.

- **속성 창에서** 추적 속성의 **Reset** 명령은 속성이 사용자 업데이트 상태에 있는 경우에만 사용할 수 있습니다. **Reset** 명령은 추적 속성 상태를 tracking으로 설정 합니다.

- **속성** 창에서 추적 속성이 추적 상태 이면 해당 값이 일반 글꼴로 표시 됩니다.

- **속성** 창에서 추적 속성이 사용자에 의해 업데이트 됨 상태에 있는 경우 해당 값은 굵은 글꼴로 표시 됩니다.

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 시작 하려면 먼저 다음 구성 요소를 설치 해야 합니다.

|제품|다운로드 링크|
|-|-|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[https://www.visualstudio.com/](https://www.visualstudio.com/)|
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[Visual Studio SDK](../extensibility/visual-studio-sdk.md)|
|Visual Studio Visualization and Modeling SDK|[모델링 SDK 다운로드](https://www.microsoft.com/download/details.aspx?id=48148)|

## <a name="creating-the-dsl-project"></a>DSL 프로젝트 만들기
 도메인 특정 언어에 대 한 프로젝트를 만듭니다.

#### <a name="to-create-the-project"></a>프로젝트를 만들려면

1. 도메인 특정 언어 디자이너 프로젝트를 만듭니다. 이름을 `TrackingPropertyDSL`로 지정합니다.

2. **도메인 특정 언어 디자이너 마법사**에서 다음 옵션을 설정 합니다.

    1. **MinimalLanguage** 템플릿을 선택 합니다.

    2. 도메인 특정 언어의 기본 이름인를 사용 `TrackingPropertyDSL` 합니다.

    3. 모델 파일의 확장명을로 설정 `trackingPropertyDsl` 합니다.

    4. 모델 파일의 기본 템플릿 아이콘을 사용 합니다.

    5. 제품의 이름을로 설정 `Product Name` 합니다.

    6. 회사의 이름을로 설정 `Company Name` 합니다.

    7. 솔루션의 프로젝트에 대 한 루트 네임 스페이스의 기본값을 사용 `CompanyName.ProductName.TrackingPropertyDSL` 합니다.

    8. 마법사에서 어셈블리에 대 한 강력한 이름 키 파일을 만들도록 허용 합니다.

    9. 솔루션의 세부 정보를 검토 한 다음 **마침** 을 클릭 하 여 DSL 정의 프로젝트를 만듭니다.

## <a name="customizing-the-default-dsl-definition"></a>기본 DSL 정의 사용자 지정
 이 섹션에서는 다음 항목을 포함 하도록 DSL 정의를 사용자 지정 합니다.

- 모델의 모든 요소에 대 한 네임 스페이스 추적 속성입니다.

- 모델의 모든 요소에 대 한 부울 IsNamespaceTracking 속성입니다. 이 속성은 추적 속성이 추적 상태 또는 사용자가 업데이트 한 사용자 상태 인지 여부를 나타냅니다.

- 모델에 대 한 기본 네임 스페이스 속성입니다. 이 속성은 네임 스페이스 추적 속성의 기본값을 계산 하는 데 사용 됩니다.

- 모델에 대 한 CustomElements 계산 된 속성입니다. 이 속성은 사용자 지정 네임 스페이스를 포함 하는 요소의 비율을 표시 합니다.

#### <a name="to-add-the-domain-properties"></a>도메인 속성을 추가 하려면

1. DSL 디자이너에서 **examplemodel.store.customer** 도메인 클래스를 마우스 오른쪽 단추로 클릭 하 고 **추가**를 가리킨 다음 **domainproperty**를 클릭 합니다.

    1. 새 속성의 이름을로 `DefaultNamespace` 합니다.

    2. 새 속성에 대 한 **속성** 창에서 **기본값** 을으로 설정 하 `DefaultNamespace` 고 **형식** 을 **문자열**로 설정 합니다.

2. **Examplemodel.store.customer** 도메인 클래스에 라는 도메인 속성을 추가 합니다 `CustomElements` .

     새 속성의 **속성** 창에서 **Kind** 를 **계산**됨으로 설정 합니다.

3. **ExampleElement** 도메인 클래스에 라는 도메인 속성을 추가 합니다 `Namespace` .

     새 속성의 **속성** 창에서을 (를) **찾아볼** 수 있음을 **False**로 설정 하 고 **Kind** 를 **customstorage**로 설정 합니다.

4. **ExampleElement** 도메인 클래스에 라는 도메인 속성을 추가 합니다 `IsNamespaceTracking` .

     새 속성의 **속성** 창에서을 (를) **찾아볼** 수 있음을 **False**로 설정 하 고 **기본값** 을으로 설정 하 `true` 고 **형식** 을 **부울**로 설정 합니다.

#### <a name="to-update-the-diagram-elements-and-dsl-details"></a>다이어그램 요소 및 DSL 세부 정보를 업데이트 하려면

1. DSL 디자이너에서 **ExampleShape** geometry 셰이프를 마우스 오른쪽 단추로 클릭 하 고 **추가**를 가리킨 다음 **텍스트 데코레이터**를 클릭 합니다.

    1. 새 텍스트 데코레이터의 이름을로 `NamespaceDecorator` 합니다.

    2. 텍스트 데코레이터의 **속성** 창에서 **위치** 를 **InnerBottomLeft**로 설정 합니다.

2. DSL 디자이너에서 **ExampleElement** 클래스를 **ExampleShape** 셰이프에 연결 하는 선을 선택 합니다.

    1. **DSL 정보** 창에서 **데코레이터 맵** 탭을 선택 합니다.

    2. **데코레이터** 목록에서 **NamespaceDecorator**을 선택 하 고 해당 확인란을 선택한 다음 **표시 속성** 목록에서 **네임 스페이스**를 선택 합니다.

3. **DSL 탐색기**에서 **도메인 클래스** 폴더를 확장 하 고 **ExampleElement** 노드를 마우스 오른쪽 단추로 클릭 한 다음 **새 도메인 형식 설명자 추가**를 클릭 합니다.

    1. **ExampleElement** 노드를 확장 하 고 **사용자 지정 형식 설명자 (도메인 유형 설명자)** 노드를 선택 합니다.

    2. 도메인 유형 설명자에 대 한 **속성** 창에서 **사용자 지정 코딩** 을 **True**로 설정 합니다.

4. **DSL 탐색기**에서 **Xml Serialization 동작** 노드를 선택 합니다.

    1. **속성** 창에서 **사용자 지정 사후 로드** 를 **True**로 설정 합니다.

## <a name="transforming-templates"></a>템플릿 변환
 이제 DSL에 대 한 도메인 클래스와 속성을 정의 했으므로 DSL 정의를 올바르게 변환 하 여 프로젝트에 대 한 코드를 다시 생성할 수 있는지 확인할 수 있습니다.

#### <a name="to-transform-the-text-templates"></a>텍스트 템플릿을 변환 하려면

1. **솔루션 탐색기** 도구 모음에서 **모든 템플릿 변환**을 클릭 합니다.

2. 시스템은 솔루션에 대 한 코드를 다시 생성 하 고, 정의 파일의 XML 형식에 대 한 자세한 내용은 참조 [Dsl 파일](../modeling/the-dsldefinition-dsl-file.md).

## <a name="creating-files-for-custom-code"></a>사용자 지정 코드에 대 한 파일 만들기
 모든 템플릿을 변환 하면 시스템은 Dsl 및 DslPackage 프로젝트에서 도메인별 언어를 정의 하는 소스 코드를 생성 합니다. 생성 된 텍스트를 방해 하지 않도록 하려면 생성 된 코드 파일과는 다른 파일에 사용자 지정 코드를 작성 합니다.

 값 및 추적 속성의 상태를 유지 관리 하는 코드를 제공 해야 합니다. 생성 된 코드와 사용자 지정 코드를 구분 하 고 파일 이름 지정 충돌을 방지 하려면 별도의 하위 폴더에 사용자 지정 코드 파일을 저장 합니다.

#### <a name="to-create-the-code-files"></a>코드 파일을 만들려면

1. **솔루션 탐색기**에서 **DSL** 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **추가**를 가리킨 다음 **새 폴더**를 클릭 합니다. 새 폴더의 이름을로 `CustomCode` 합니다.

2. 새 **Customcode** 폴더를 마우스 오른쪽 단추로 클릭 하 고 **추가**를 가리킨 다음 **새 항목**을 클릭 합니다.

3. **코드 파일** 템플릿을 선택 하 고 **이름을** 로 설정한 `NamespaceTrackingProperty.cs` 다음 **확인**을 클릭 합니다.

     NamespaceTrackingProperty.cs 파일을 만들고 편집용으로 엽니다.

4. 폴더에서 `ExampleModel.cs,``HelperClasses.cs` , 및 코드 파일을 만듭니다. `Serialization.cs` `TypeDescriptor.cs`

5. 또한 **Dslpackage** 프로젝트에서 폴더를 만들고 `CustomCode` 이 폴더에 `Package.cs` 코드 파일을 추가 합니다.

## <a name="adding-helper-classes-to-support-tracking-properties"></a>추적 속성을 지원 하기 위한 도우미 클래스 추가
 HelperClasses.cs 파일에 `TrackingHelper` 다음과 같이 및 클래스를 추가 합니다 `CriticalException` . 이러한 클래스는이 연습의 뒷부분에서 참조 합니다.

#### <a name="to-add-the-helper-classes"></a>도우미 클래스를 추가 하려면

1. HelperClasses.cs 파일에 다음 코드를 추가 합니다.

    ```csharp
    using System;
    using System.Collections;
    using System.Diagnostics;
    using Microsoft.VisualStudio.Modeling;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        internal static class TrackingHelper
        {
            /// <summary>Notify each model element in a collection that a tracked
            /// property has changed.</summary>
            /// <param name="store">The store for the model.</param>
            /// <param name="collection">The collection of model elements that
            /// contain the tracking property.</param>
            /// <param name="propertyId">The ID of the tracking property.</param>
            /// <param name="trackingPropertyId">The ID of the property that
            /// indicates whether the tracking property is tracking.</param>
            internal static void UpdateTrackingCollectionProperty(
                Store store,
                IEnumerable collection,
                Guid propertyId,
                Guid trackingPropertyId)
            {
                DomainPropertyInfo propInfo =
                    store.DomainDataDirectory.GetDomainProperty(propertyId);

                DomainPropertyInfo trackingPropInfo =
                    store.DomainDataDirectory.GetDomainProperty(trackingPropertyId);

                Debug.Assert(propInfo != null);
                Debug.Assert(trackingPropInfo != null);
                Debug.Assert(trackingPropInfo.PropertyType.Equals(typeof(bool)),
                    "Tracking property not specified as a boolean");

                foreach (ModelElement element in collection)
                {
                    // If the tracking property is currently tracking, then notify
                    // it that the tracked property has changed.
                    bool isTracking = (bool)trackingPropInfo.GetValue(element);
                    if (isTracking)
                    {
                        propInfo.NotifyValueChange(element);
                    }
                }
            }
        }

        /// <summary>Helper class to flag critical exceptions from ones that are
        /// safe to ignore.</summary>
        internal static class CriticalException
        {
            /// <summary>Gets whether an exception is critical and can not be
            /// ignored.</summary>
            /// <param name="ex">The exception to check.</param>
            /// <returns>True if the exception is critical.</returns>
            internal static bool IsCriticalException(Exception ex)
            {
                if (ex is NullReferenceException
                    || ex is StackOverflowException
                    || ex is OutOfMemoryException
                    || ex is System.Threading.ThreadAbortException)
                    return true;

                if (ex.InnerException != null)
                    return IsCriticalException(ex.InnerException);

                return false;
            }
        }
    }
    ```

## <a name="adding-custom-code-for-the-custom-type-descriptor"></a>사용자 지정 형식 설명자에 대 한 사용자 지정 코드 추가
 `GetCustomProperties`도메인 클래스에 대 한 형식 설명자에 대 한 메서드를 구현 합니다 `ExampleModel` .

> [!NOTE]
> DSL 도구에서 호출에 대 한 사용자 지정 형식 설명자에 대해 생성 하는 코드 `ExampleModel` `GetCustomProperties` 입니다. 그러나 dsl 도구는 메서드를 구현 하는 코드를 생성 하지 않습니다.

 이 메서드를 정의 하면 네임 스페이스 추적 속성에 대 한 추적 속성 설명자가 만들어집니다. 또한 추적 속성의 특성을 제공 하면 **속성 창에서 속성을** 올바르게 표시할 수 있습니다.

#### <a name="to-modify-the-type-descriptor-for-the-examplemodel-domain-class"></a>Examplemodel.store.customer 도메인 클래스에 대 한 형식 설명자를 수정 하려면

1. TypeDescriptor.cs 파일에 다음 코드를 추가 합니다.

    ```csharp
    using System;
    using System.ComponentModel;
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.Design;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        // To the custom type descriptor for the ExampleElement domain class, add
        // the GetCustomProperties method.
        public partial class ExampleElementTypeDescriptor
        {
            /// <summary>Returns the property descriptors for the described
            /// ExampleElement domain class.</summary>
            /// <remarks>This method adds the tracking property descriptor.
            /// </remarks>
            private PropertyDescriptorCollection GetCustomProperties(
                Attribute[] attributes)
            {
                // Get the default property descriptors from the base class
                PropertyDescriptorCollection propertyDescriptors =
                    base.GetProperties(attributes);

                // Get a reference to the model element that is being described.
                ExampleElement source = this.ModelElement as ExampleElement;

                //Add the descriptor for the tracking property.
                if (source != null)
                {
                    DomainPropertyInfo domainProperty =
                        source.Store.DomainDataDirectory.GetDomainProperty(
                            ExampleElement.NamespaceDomainPropertyId);

                    DomainPropertyInfo trackingProperty =
                        source.Store.DomainDataDirectory.GetDomainProperty(
                            ExampleElement.IsNamespaceTrackingDomainPropertyId);

                    // Define attributes for the tracking property so that the
                    // Properties window displays the property correctly.
                    Attribute[] attr = new Attribute[] {
                        new DisplayNameAttribute("Element Namespace"),
                        new DescriptionAttribute("The namespace of the element."),
                        new CategoryAttribute("Tracking Properties"),
                    };

                    propertyDescriptors.Add(new TrackingPropertyDescriptor(
                        source, domainProperty, trackingProperty, attr));
                }

                // Return the property descriptors for this element
                return propertyDescriptors;
            }
        }
    }
    ```

## <a name="adding-custom-code-for-the-package"></a>패키지에 대 한 사용자 지정 코드 추가
 생성 된 코드는 ExampleElement 도메인 클래스에 대 한 형식 설명 공급자를 정의 합니다. 그러나이 형식 설명 공급자를 사용 하도록 DSL에 지시 하는 코드를 추가 해야 합니다.

#### <a name="to-update-the-dsl-package-to-use-your-custom-type-descriptor"></a>사용자 지정 형식 설명자를 사용 하도록 DSL 패키지를 업데이트 하려면

1. Package.cs 파일에 다음 코드를 추가 합니다.

    ```csharp
    using System.ComponentModel;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        // Override the default Initialize method.
        internal sealed partial class TrackingPropertyDSLPackage
        {
            protected override void Initialize()
            {
                // Add the custom type descriptor for the ExampleElement type.
                TypeDescriptor.AddProvider(
                    new ExampleElementTypeDescriptionProvider(),
                    typeof(ExampleElement));

                base.Initialize();
            }
        }
    }
    ```

## <a name="adding-custom-code-for-the-model"></a>모델에 대 한 사용자 지정 코드 추가
 `GetCustomElementsValue`도메인 클래스에 대 한 메서드를 구현 합니다 `ExampleModel` .

> [!NOTE]
> DSL 도구에서 호출을 위해 생성 하는 코드는 `ExampleModel` `GetCustomElementsValue` dsl 도구에서 메서드를 구현 하는 코드를 생성 하지 않습니다.

 메서드를 정의 하면 `GetCustomElementsValue` 의 CustomElements 계산 된 속성에 대 한 논리를 제공 합니다 `ExampleModel` . 이 메서드는 `ExampleElement` 사용자가 업데이트 한 값을 포함 하는 네임 스페이스 추적 속성이 있는 도메인 클래스의 수를 계산 하 고이 개수를 모델에 있는 전체 요소의 비율로 반환 하는 문자열을 반환 합니다.

 또한에 메서드를 추가 하 `OnDefaultNamespaceChanged` `ExampleModel` 고 `OnValueChanged` 의 중첩 된 클래스의 메서드를 재정의 하 여을 `DefaultNamespacePropertyHandler` `ExampleModel` 호출 `OnDefaultNamespaceChanged` 합니다.

 DefaultNamespace 속성은 네임 스페이스 추적 속성을 계산 하는 데 사용 되므로는 `ExampleModel` `ExampleElement` defaultnamespace의 값이 변경 되었음을 모든 도메인 클래스에 알려야 합니다.

#### <a name="to-modify-the-property-handler-for-the-tracked-property"></a>추적 된 속성에 대 한 속성 처리기를 수정 하려면

1. ExampleModel.cs 파일에 다음 코드를 추가 합니다.

    ```csharp
    using System.Linq;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        public partial class ExampleModel
        {
            public string GetCustomElementsValue()
            {
                if (this.Elements.Count == 0) return "0/0";

                int number = this.Elements.Count(e => !e.IsNamespaceTracking);
                return string.Format("{0}/{1}", number, this.Elements.Count);
            }

            #region Value changed handler for the tracked property

            // When a tracked property changes, it needs to notify all of the properties
            // that track it.

            /// <summary>Called by the DefaultNamespace property value handler when the
            /// DefaultNamespace property changes.</summary>
            /// <param name="oldValue">The previous value of the property.</param>
            /// <param name="newValue">The new value of the property.</param>
            protected virtual void OnDefaultNamespaceChanged(
                string oldValue, string newValue)
            {
                // Use the helper class to notify all of the elements in the model
                // that the default namespace has changed.
                TrackingHelper.UpdateTrackingCollectionProperty(
                    this.Store,
                    this.Elements,
                    ExampleElement.NamespaceDomainPropertyId,
                    ExampleElement.IsNamespaceTrackingDomainPropertyId);
            }

            // Update the change handler for the DefaultNamespace property.
            internal sealed partial class DefaultNamespacePropertyHandler
            {
                /// <summary>Called when the DefaultNamespace property changes.</summary>
                /// <param name="element">The model element that has the property that
                /// changed.</param>
                /// <param name="oldValue">The previous value of the property.</param>
                /// <param name="newValue">The new value of the property.</param>
                protected override void OnValueChanged(
                    ExampleModel element, string oldValue, string newValue)
                {
                    base.OnValueChanged(element, oldValue, newValue);

                    if (!element.Store.InUndoRedoOrRollback)
                    {
                        element.OnDefaultNamespaceChanged(oldValue, newValue);
                    }
                }
            }

            #endregion
        }
    }
    ```

## <a name="adding-custom-code-for-the-tracking-property"></a>추적 속성에 대 한 사용자 지정 코드 추가
 `CalculateNamespace`도메인 클래스에 메서드를 추가 `ExampleElement` 합니다.

 이 메서드를 정의 하면의 CustomElements 계산 된 속성에 대 한 논리를 제공 합니다 `ExampleModel` . 이 메서드는 `ExampleElement` 사용자 상태별로 업데이트 된 네임 스페이스 추적 속성이 있는 도메인 클래스의 수를 계산 하 고이 개수를 모델에 있는 총 요소에 대 한 비율로 반환 합니다.

 또한, 및 메서드에 대 한 저장소를 추가 하 고, 도메인 클래스의 네임 스페이스 사용자 지정 저장소 속성을 가져오고 설정 합니다 `ExampleElement` .

> [!NOTE]
> DSL 도구에서 생성 하는 코드는 `ExampleModel` get 및 set 메서드를 호출 하지만 Dsl 도구는 메서드를 구현 하는 코드를 생성 하지 않습니다.

#### <a name="to-add-the-method-for-the-custom-type-descriptor"></a>사용자 지정 형식 설명자에 대 한 메서드를 추가 하려면

1. NamespaceTrackingProperty.cs 파일에 다음 코드를 추가 합니다.

    ```csharp
    using System;
    using Microsoft.VisualStudio.Modeling;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        // To the domain class that has the tracking property, add the caluclation
        // for when the property is tracking.
        public partial class ExampleElement
        {
            /// <summary>Calculates the actual value of the property when it is
            /// tracking.</summary>
            /// <returns>The value of the tracking property when it is
            /// tracking.</returns>
            /// <remarks>Making this method virtual allows child classes to modify
            /// the calculation. This method does not need to perform validation, as
            /// its caller handles validation prior to calling this method.
            /// <para>In this case, the tracking value depends on the default namespace
            /// property of the parent model.</para></remarks>
            protected virtual string CalculateNamespace()
            {
                return this.ExampleModel.DefaultNamespace;
            }

            #region Tracking property implementation

            // Implement the Namespace domain property of the ExampleElement domain class,
            // and update the IsNamespaceTracking domain property value handler.

            /// <summary>Storage for the Namespace property.</summary>
            private string namespaceStorage;

            /// <summary>Gets the value of the Namespace property.</summary>
            /// <returns>The value of the Namespace property.</returns>
            private string GetNamespaceValue()
            {
                // Only retrieve the tracked value if the store is not in the
                // middle of a serialization transaction.
                bool loading = this.Store.TransactionManager.InTransaction
                    && this.Store.TransactionManager.CurrentTransaction.IsSerializing;

                if (!loading && this.IsNamespaceTracking)
                {
                    try
                    {
                        return this.CalculateNamespace();
                    }
                    catch (NullReferenceException)
                    {
                        return default(string);
                    }
                    catch (Exception e)
                    {
                        if (CriticalException.IsCriticalException(e))
                        {
                            throw;
                        }
                        else
                        {
                            return default(string);
                        }
                    }
                }

                return namespaceStorage;
            }

            /// <summary>Sets the value of the Namespace property.</summary>
            /// <param name="value">The new value for the property.</param>
            private void SetNamespaceValue(string value)
            {
                namespaceStorage = value;

                // Only update the state of the tracking property if the store is
                // not in the middle of a serialization transaction.
                bool loading = this.Store.TransactionManager.InTransaction
                    && this.Store.TransactionManager.CurrentTransaction.IsSerializing;

                if (!this.Store.InUndoRedoOrRollback && !loading)
                {
                    this.IsNamespaceTracking = false;
                }
            }

            // Update the default behavior of the ExampleElement.IsNamespaceTracking
            // domain property value handler.
            internal sealed partial class IsNamespaceTrackingPropertyHandler
            {
                /// <summary>Called after the IsNamespaceTracking property changes.
                /// </summary>
                /// <param name="element">The model element that has the property
                /// that changed.</param>
                /// <param name="oldValue">The previous value of the property.
                /// </param>
                /// <param name="newValue">The new value of the property.</param>
                protected override void OnValueChanged(
                    ExampleElement element, Boolean oldValue, Boolean newValue)
                {
                    base.OnValueChanged(element, oldValue, newValue);
                    if (!element.Store.InUndoRedoOrRollback && newValue)
                    {
                        DomainPropertyInfo propInfo =
                            element.Store.DomainDataDirectory.GetDomainProperty(
                                ExampleElement.NamespaceDomainPropertyId);
                        propInfo.NotifyValueChange(element);
                    }
                }

                /// <summary>Performs the reset operation for the IsNamespaceTracking
                /// property for a model element.</summary>
                /// <param name="element">The model element that has the property
                /// to reset.</param>
                internal void ResetValue(ExampleElement element)
                {
                    object calculatedValue = null;

                    try
                    {
                        calculatedValue = element.CalculateNamespace();
                    }
                    catch (NullReferenceException)
                    {
                    }
                    catch (System.Exception e)
                    {
                        if (CriticalException.IsCriticalException(e))
                        {
                            throw;
                        }
                    }

                    if ((calculatedValue != null
                        && object.Equals(element.Namespace, calculatedValue)))
                    {
                        element.isNamespaceTrackingPropertyStorage = true;
                    }
                }

                /// <summary>Method to set IsNamespaceTracking to false so that this
                /// instance of this tracking property is not storage-based.
                /// </summary>
                /// <param name="element">The element on which to reset the property
                /// value.</param>
                internal void PreResetValue(ExampleElement element)
                {
                    // Force the IsNamespaceTracking property to false so that the value
                    // of the Namespace property is retrieved from storage.
                    element.isNamespaceTrackingPropertyStorage = false;
                }
            }

            #endregion
        }
    }
    ```

## <a name="adding-custom-code-to-support-serialization"></a>Serialization을 지 원하는 사용자 지정 코드 추가
 XML serialization에 대 한 사용자 지정 사후 로드 동작을 지 원하는 코드를 추가 합니다.

> [!NOTE]
> DSL 도구에서 생성 하는 코드는 `OnPostLoadModel` 및 메서드를 호출 `OnPostLoadModelAndDiagram` 하지만 dsl 도구는 이러한 메서드를 구현 하는 코드를 생성 하지 않습니다.

#### <a name="to-add-code-to-support-the-custom-post-load-behavior"></a>사용자 지정 사후 로드 동작을 지 원하는 코드를 추가 하려면

1. Serialization.cs 파일에 다음 코드를 추가 합니다.

    ```csharp
    using System;
    using System.Diagnostics;
    using Microsoft.VisualStudio.Modeling;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        #region Helper classes for maintaining state while the store is serializing.

        public abstract partial class TrackingPropertyDSLSerializationHelperBase
        {
            /// <summary>Reset the tracking state properties to their natural values
            /// based on comparing storage with calculation.</summary>
            /// <param name="store">The store that contains this model.</param>
            internal static void ResetTrackingProperties(Store store)
            {
                // Two passes required - one to set all elements to storage-based
                // then another to set some back to being tracking.
                foreach (ModelElement element in store.ElementDirectory.AllElements)
                {
                    ExampleElement myElementInstance = element as ExampleElement;
                    if (myElementInstance != null)
                    {
                        myElementInstance.PreResetIsTrackingProperties();
                        continue;
                    }
                }
                foreach (ModelElement element in store.ElementDirectory.AllElements)
                {
                    ExampleElement myElementInstance = element as ExampleElement;
                    if (myElementInstance != null)
                    {
                        myElementInstance.ResetIsTrackingProperties();
                        continue;
                    }
                }
            }
        }

        // Add the pre-reset and reset methods for the model element.
        public partial class ExampleElement
        {
            /// <summary>Calls the pre-reset method on the associated property value
            /// handler for each tracking property of this model element.</summary>
            internal virtual void PreResetIsTrackingProperties()
            {
                ExampleElement.IsNamespaceTrackingPropertyHandler.Instance.PreResetValue(this);
            }

            /// <summary>Calls the reset method on the associated property value
            /// handler for each tracking property of this model element.</summary>
            internal virtual void ResetIsTrackingProperties()
            {
                ExampleElement.IsNamespaceTrackingPropertyHandler.Instance.ResetValue(this);
            }
        }

        #endregion

        #region Custom serialization code

        // To the serialization helper for the TrackingPropertyDSL class, add post
        // load handlers to bind the tracking property to the serialization process.
        // These handlers manage the tracking states and property values when the
        // model is serialized and deserialized.
        public partial class TrackingPropertyDSLSerializationHelperBase
        {
            /// <summary>Customize model loading.</summary>
            /// <param name="serializationResult">The serialization result from the
            /// load operation.</param>
            /// <param name="partition">The partition in which the new
            /// instance was created.</param>
            /// <param name="fileName">The name of the file from which the
            /// instance was deserialized.</param>
            /// <param name="modelRoot">The root of the file that was loaded.
            /// </param>
            private void OnPostLoadModel(
                SerializationResult serializationResult,
                Partition partition,
                string fileName,
                ExampleModel modelRoot)
            {
            }

            /// <summary>Customize model and diagram loading.</summary>
            /// <param name="serializationResult">Stores serialization result from
            /// the load operation.</param>
            /// <param name="modelPartition">Partition in which the new
            /// instance will be created.</param>
            /// <param name="modelFileName">Name of the file from which the
            /// instance will be deserialized.</param>
            /// <param name="diagramPartition">Partition in which the new
            /// diagram instance will be created.</param>
            /// <param name="diagramFileName">Name of the file from which the
            /// diagram instance will be deserialized.</param>
            /// <param name="modelRoot">The root of the file that was loaded.</param>
            /// <param name="diagram">The diagram matching the modelRoot.</param>
            private void OnPostLoadModelAndDiagram(
                SerializationResult serializationResult,
                Partition modelPartition,
                string modelFileName,
                Partition diagramPartition,
                string diagramFileName,
                ExampleModel modelRoot,
                TrackingPropertyDSLDiagram diagram)
            {
                Debug.Assert(modelPartition != null);
                Debug.Assert(modelPartition.Store != null);

                // Tracking properties need to be set up according to whether the
                // serialization matches the calculated values.
                TrackingPropertyDSLSerializationHelperBase.ResetTrackingProperties(
                    modelPartition.Store);
            }
        }

        #endregion
    }
    ```

## <a name="testing-the-language"></a>언어 테스트
 다음 단계는 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 추적 속성이 제대로 작동 하는지 확인할 수 있도록 새 인스턴스에서 DSL 디자이너를 빌드하고 실행 하는 것입니다.

#### <a name="to-exercise-the-language"></a>언어를 실행 하려면

1. **빌드** 메뉴에서 **솔루션 다시 빌드**를 클릭합니다.

2. **디버그** 메뉴에서 **디버깅 시작**을 클릭합니다.

     의 실험적 빌드는 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 빈 테스트 파일이 포함 된 **디버깅** 솔루션을 엽니다.

3. **솔루션 탐색기**에서 테스트. trackingPropertyDsl 파일을 두 번 클릭 하 여 디자이너에서 열고 디자인 화면을 클릭 합니다.

     다이어그램에 대 한 **속성** 창에서 **기본 네임 스페이스** 속성은 **Defaultnamespace**이 고 **사용자 지정 요소** 속성은 **0/0**입니다.

4. **도구 상자** 에서 다이어그램 화면으로 **ExampleElement** 요소를 끌어 옵니다.

5. 요소에 대 한 **속성** 창에서 **요소 네임 스페이스** 속성을 선택 하 고 **defaultnamespace** 에서 **othernamespace**로 값을 변경 합니다.

     이제 **요소 네임 스페이스** 의 값이 굵게 표시 됩니다.

6. **속성** 창에서 **요소 네임 스페이스**를 마우스 오른쪽 단추로 클릭 한 다음 **다시 설정**을 클릭 합니다.

     속성의 값이 **Defaultnamespace**로 변경 되 고 값이 일반 글꼴로 표시 됩니다.

     **요소 네임 스페이스** 를 다시 마우스 오른쪽 단추로 클릭 합니다. 속성이 현재 추적 중 상태 이므로 **Reset** 명령을 이제 사용할 수 없습니다.

7. **도구 상자** 에서 다른 **ExampleElement** 를 다이어그램 화면으로 끌고 **요소 네임 스페이스** 를 **othernamespace**로 변경 합니다.

8. 디자인 화면을 클릭 합니다.

     다이어그램의 **속성** 창에서 **사용자 지정 요소의** 값은 이제 **1/2**입니다.

9. 다이어그램의 **기본 네임 스페이스** 를 **Defaultnamespace** 에서 **newnamespace**로 변경 합니다.

     첫 번째 요소의 **네임** 스페이스는 **기본 네임 스페이스** 속성을 추적 하는 반면 두 번째 요소의 **네임** 스페이스는 **othernamespace**의 사용자 업데이트 값을 유지 합니다.

10. 솔루션을 저장 하 고 실험적 빌드를 닫습니다.

## <a name="next-steps"></a>다음 단계
 둘 이상의 추적 속성을 사용 하거나 둘 이상의 DSL에서 추적 속성을 구현할 계획인 경우 텍스트 템플릿을 만들어 각 추적 속성을 지 원하는 공통 코드를 생성할 수 있습니다. 텍스트 템플릿에 대 한 자세한 내용은 [코드 생성 및 T4 텍스트 템플릿](../modeling/code-generation-and-t4-text-templates.md)을 참조 하세요.

## <a name="see-also"></a>관련 항목
 <xref:Microsoft.VisualStudio.Modeling.Design.TrackingPropertyDescriptor> <xref:Microsoft.VisualStudio.Modeling.Design.ElementTypeDescriptor>
 [도메인 특정 언어를 정의 하는 방법](../modeling/how-to-define-a-domain-specific-language.md) [방법: 도메인별 언어 솔루션 만들기](../modeling/how-to-create-a-domain-specific-language-solution.md) [연습: 도메인 특정 언어 정의 사용자 지정](../misc/walkthrough-customizing-the-domain-specific-language-definition.md)
