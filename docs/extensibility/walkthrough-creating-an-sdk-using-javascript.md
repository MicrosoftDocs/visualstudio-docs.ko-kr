---
title: '연습: JavaScript를 사용 하 여 SDK 만들기 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: a8c89d5d-5b78-4435-817f-c5f25ca6d715
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 29dac6cca7936dde8be2ebc57366f6370b8bcbc6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85904947"
---
# <a name="walkthrough-create-an-sdk-using-javascript"></a>연습: JavaScript를 사용 하 여 SDK 만들기
이 연습에서는 JavaScript를 사용 하 여 간단한 수학 SDK를 VSIX (Visual Studio Extension)로 만드는 방법을 배웁니다.  이 연습은 다음과 같은 부분으로 나눌 수 있습니다.

- [SimpleMathVSIX 확장 SDK 프로젝트를 만들려면](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSimpleMathVSIX)

- [SDK를 사용 하는 샘플 앱을 만들려면](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSampleApp)

  JavaScript의 경우 클래스 라이브러리 프로젝트 형식이 없습니다. 이 연습에서는 샘플 *arithmetic.js* 파일이 VSIX 프로젝트에 직접 생성 됩니다. 실제로 VSIX 프로젝트에 삽입 하기 전에 먼저 JavaScript 및 CSS 파일을 Windows 스토어 앱으로 빌드 및 테스트 하는 것이 좋습니다 (예: **빈 앱** 템플릿 사용).

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 수행하려면 Visual Studio SDK를 설치해야 합니다. 자세한 내용은 [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md)를 참조 하세요.

## <a name="to-create-the-simplemathvsix-extension-sdk-project"></a><a name="createSimpleMathVSIX"></a> SimpleMathVSIX 확장 SDK 프로젝트를 만들려면

1. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

2. 템플릿 범주 목록에서 **Visual c #** 아래에 있는 **확장성**을 선택한 다음 **VSIX 프로젝트** 템플릿을 선택 합니다.

3. **이름** 텍스트 상자에서를 지정 `SimpleMathVSIX` 하 고 **확인** 단추를 선택 합니다.

4. **Visual Studio 패키지 마법사** 가 표시 되 면 **시작** 페이지에서 **다음** 단추를 선택 하 고 **1의 7 페이지**에서 **마침** 단추를 선택 합니다.

     **매니페스트 디자이너** 를 열면 매니페스트 파일을 직접 수정 하 여이 연습을 간단 하 게 유지할 수 있습니다.

5. **솔루션 탐색기**에서 **source.extension.vsixmanifest** 파일에 대 한 바로 가기 메뉴를 열고 **코드 보기**를 선택 합니다. 이 코드를 사용 하 여 파일의 기존 내용을 바꿉니다.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
      <Metadata>
        <Identity Id="SimpleMathVSIX" Version="1.0" Language="en-US" Publisher="myname" />
        <DisplayName>Simple Math</DisplayName>
        <Description>Does basic arithmetic calculations.</Description>
      </Metadata>
      <Installation Scope="Global" AllUsers="true">
        <InstallationTarget Id="Microsoft.ExtensionSDK" TargetPlatformIdentifier="Windows" TargetPlatformVersion="v8.0" SdkName="SimpleMath" SdkVersion="1.0" />
      </Installation>
      <Dependencies>
        <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" d:Source="Manual" Version="4.5" />
      </Dependencies>
      <Assets>
        <Asset Type="Microsoft.ExtensionSDK" d:Source="File" Path="SDKManifest.xml" />
      </Assets>
    </PackageManifest>
    ```

6. **솔루션 탐색기**에서 **SimpleMathVSIX** 프로젝트에 대 한 바로 가기 메뉴를 열고 **Add**  >  **새 항목**추가를 선택 합니다.

7. **데이터** 범주에서 **XML 파일**을 선택 하 고 파일 이름을 `SDKManifest.xml` 로 선택한 다음 **추가** 단추를 선택 합니다.

8. **솔루션 탐색기**에서 **SDKManifest.xml** 파일에 대 한 바로 가기 메뉴를 열고 **열기** 를 선택 하 여 **XML 편집기**에 파일을 표시 합니다.

9. **SDKManifest.xml** 파일에 다음 코드를 추가 합니다.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <FileList
      DisplayName="Simple Math"
      MinVSVersion="14.0"
      AppliesTo="JavaScript+WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="https://msdn.microsoft.com/">

      <!-- JS -->
      <File Content="js\arithmetic.js" />
    </FileList>

    ```

10. **솔루션 탐색기**의 **SDKManifest.xml** 파일에 대 한 바로 가기 메뉴에서 **속성**을 선택 합니다.

11. **속성** 창에서 **VSIX에 포함** 속성을 **True**로 설정 합니다.

12. **솔루션 탐색기**의 **SimpleMathVSIX** 프로젝트에 대 한 바로 가기 메뉴에서 **Add**  >  **새 폴더**추가를 선택한 다음 폴더 이름을로 설정 `Redist` 합니다.

13. Redist 아래에 하위 폴더를 추가 하 여이 폴더 구조를 만듭니다.

     *\Redist\CommonConfiguration\Neutral\SimpleMath\js\\*

14. ** \\ \Js** 폴더에 대 한 바로 가기 메뉴에서 **Add**  >  **새 항목**추가를 선택 합니다.

15. **Visual c # 항목**에서 **웹** 범주를 선택한 다음 **JavaScript 파일** 항목을 선택 합니다. 파일 이름을 `arithmetic.js` 로 지정한 다음 **추가** 단추를 선택 합니다.

16. *arithmetic.js*에 다음 코드를 삽입 합니다.

    ```csharp
    (function (global) {
        "use strict";
        global.Arithmetic = {
            add: function (firstNumber, secondNumber) {
                return firstNumber + secondNumber;
            },

            subtract: function (firstNumber, secondNumber) {
                return firstNumber - secondNumber;
            },

            multiply: function (firstNumber, secondNumber) {
                return firstNumber * secondNumber;
            },

            divide: function (firstNumber, secondNumber) {
                return firstNumber / secondNumber;
            }
        };
    })(this);

    ```

17. **솔루션 탐색기**의 **arithmetic.js** 파일에 대 한 바로 가기 메뉴에서 **속성**을 선택 합니다. 이러한 속성을 변경 합니다.

    - **VSIX에 포함** 속성을 **True**로 설정 합니다.

    - **출력 디렉터리로 복사** 속성을 **항상 복사**로 설정 합니다.

18. **솔루션 탐색기**의 **SimpleMathVSIX** 프로젝트에 대 한 바로 가기 메뉴에서 **빌드**를 선택 합니다.

19. 빌드가 성공적으로 완료 된 후 프로젝트에 대 한 바로 가기 메뉴에서 **파일 탐색기에서 폴더 열기**를 선택 합니다. **\Bin\debug \\ **로 이동 하 고를 실행 `SimpleMathVSIX.vsix` 하 여 설치 합니다.

20. **설치** 단추를 선택 하 고 설치가 완료 되도록 합니다.

21. Visual Studio를 다시 시작합니다.

## <a name="to-create-a-sample-app-that-uses-the-sdk"></a><a name="createSampleApp"></a> SDK를 사용 하는 샘플 앱을 만들려면

1. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

2. 템플릿 범주 목록에서 **JavaScript**아래에 있는 **Windows 스토어**를 선택 하 고 **비어 있는 앱** 템플릿을 선택 합니다.

3. **이름** 상자에를 지정 `ArithmeticUI` 합니다. **확인** 단추를 선택합니다.

4. **솔루션 탐색기**에서 **ArithmeticUI** 프로젝트에 대 한 바로 가기 메뉴를 열고 참조 **추가**를 선택  >  **Reference**합니다.

5. **Windows**에서 **확장**을 선택 하 고 **간단한 수학** 이 표시 되는지 확인 합니다.

6. **간단한 수학** 확인란을 선택 하 고 **확인** 단추를 선택 합니다.

7. **솔루션 탐색기**의 **참조**에서 **단순 수학** 참조가 표시 됩니다. 확장 하 고 **arithmetic.js**를 포함 하는 **\js \\ ** 폴더가 있는지 확인 합니다. **arithmetic.js** 를 열어 소스 코드가 설치 되어 있는지 확인할 수 있습니다.

8. 다음 코드를 사용 하 여 *default.htm*내용을 바꿉니다.

   ```html
   <!DOCTYPE html>
   <html>
   <head>
       <meta charset="utf-8" />
       <title>ArithmeticUI</title>

       <!-- WinJS references -->
       <link href="//Microsoft.WinJS.1.0/css/ui-dark.css" rel="stylesheet" />
       <script src="//Microsoft.WinJS.1.0/js/base.js"></script>
       <script src="//Microsoft.WinJS.1.0/js/ui.js"></script>

       <!-- ArithmeticUI references -->
       <link href="/css/default.css" rel="stylesheet" />
       <script src="/js/default.js"></script>
       <script src="/SimpleMath/js/arithmetic.js"></script>
   </head>
   <body>
       <form>
       <div id="calculator" class="ms-grid">
           <input name="firstNumber" id="firstNumber" type="number" step="any">
           <div id="operators">
               <button class="operator" type="button">+</button>
               <button class="operator" type="button">-</button>
               <button class="operator" type="button">*</button>
               <button class="operator" type="button">/</button>
           </div>
           <input id="secondNumber" type="number">
           <button class="calculate" type="button">=</button>
           <input id="result" type="number" name="result" disabled="" readonly="">
       </div>
       </form>
   </body>
   </html>
   ```

9. 다음 코드를 사용 하 여 *\js\default.js*내용을 바꿉니다.

    ```csharp
    (function () {
        "use strict";

        var app = WinJS.Application;
        var operation = null;

        function calculateResult() {
            var firstNumber = parseFloat(document.querySelector("#firstNumber").value),
                secondNumber = parseFloat(document.querySelector("#secondNumber").value),
                result = 0;

            if (isNaN(firstNumber) || isNaN(secondNumber)) {
                result = 0;
            }
            else {
                switch (operation) {
                    case "+":
                        result = Arithmetic.add(firstNumber, secondNumber);
                        break;
                    case "-":
                        result = Arithmetic.subtract(firstNumber, secondNumber);
                        break;
                    case "*":
                        result = Arithmetic.multiply(firstNumber, secondNumber);
                        break;
                    case "/":
                        result = Arithmetic.divide(firstNumber, secondNumber);
                        break;
                    default:
                }
            }
            document.querySelector("#result").value = result.toString();
        }

        app.onactivated = function (args) {
            document.querySelector("#calculator").addEventListener("click", function (event) {
                if (event.target.tagName.toLowerCase() === "button") {
                    switch (event.target.className) {
                        case "operator":
                            operation = event.target.innerText;
                            break;
                        case "calculate":
                            calculateResult();
                            break;
                        default:
                            break;
                    }
                }
            });
        };

        app.start();
    })();
    ```

10. *\Css\default.css* 의 내용을 다음 코드로 바꿉니다.

    ```xml
    form {
        display: -ms-grid;
        -ms-grid-rows: 1fr auto 1fr;
        -ms-grid-columns: 1fr auto 1fr;
        height: 100%;
        width: 100%;
    }

    button, input[type=number] {
        margin-right: 5px;
        -ms-grid-row-align: center;
    }

    #calculator {
        -ms-grid-column: 2;
        -ms-grid-row: 2;
        display: -ms-grid;
        -ms-grid-rows: 1fr;
        -ms-grid-columns: auto min-content auto auto auto;
    }

    .ms-grid input {
        width: 5em;
    }

    #firstNumber {
        -ms-grid-column: 1;
        -ms-grid-row-align: center;
    }

    #operators {
        -ms-grid-column: 2;
        -ms-grid-row-align: center;
    }

        #operators button.operator {
            margin-bottom: 5px;
            height: 40px;
        }

    #secondNumber {
        -ms-grid-column: 3;
    }

    button.calculate {
        -ms-grid-column: 4;
        -ms-grid-row-align: center;
        height: 40px;
    }

    #result {
        -ms-grid-column: 5;
    }

    ```

11. **F5** 키를 선택 하 여 앱을 빌드하고 실행 합니다.

12. 앱 UI에서 두 숫자를 입력 하 고 작업을 선택한 다음 단추를 선택 **=** 합니다. 올바른 결과가 나타납니다.

## <a name="see-also"></a>추가 정보
- [소프트웨어 개발 키트 만들기](../extensibility/creating-a-software-development-kit.md)
