---
title: Xamarin.ios를 사용 하 여 앱 빌드 기본 사항 알아보기
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: d22b5186-9e03-4e85-afc9-7cbe28522a6d
caps.latest.revision: 14
ms.author: crdun
manager: crdun
ms.openlocfilehash: 09da3bd59163cbef8b33b1d5ece732330e32eac7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75918925"
---
# <a name="learn-app-building-basics-with-xamarinforms-in-visual-studio"></a>Visual Studio에서 Xamarin.Forms를 사용한 앱 빌드 기본 사항 알아보기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[Setup and install](../cross-platform/setup-and-install.md) 및 [Verify your Xamarin environment](../cross-platform/verify-your-xamarin-environment.md)의 단계를 완료했으면 이 연습 과정을 통해 Xamarin.Forms로 기본 앱을 구축하는 방법을 확인합니다(아래 참조). Xamarin.Forms를 사용하여 모든 UI 코드를 PCL(이식 가능한 클래스 라이브러리)로 한꺼번에 작성합니다. 그러면 Xamarin은 iOS, Android 및 Windows 플랫폼에 대한 네이티브 UI 컨트롤을 자동으로 렌더링합니다. PCL 옵션은 모든 대상 플랫폼에서 지원되는 .NET API만 사용하는 경우를 가장 잘 지원하고 Xamarin.Forms는 플랫폼 간 UI 코드 공유를 가능하게 하므로 이 접근 방법이 권장됩니다.

 ![Android, iOS 및 Windows Phone의 날씨 앱 샘플](../cross-platform/media/crossplat-xamarin-formsguide-1.png "CrossPlat Xamarin 양식 가이드 1")

 앱을 빌드하려면 다음 작업을 수행합니다.

- [솔루션 설정](#solution)

- [공유 데이터 서비스 코드 작성](#dataservice)

- [공유 UI 코드 작성 시작](#uicode)

- [Android 용 Visual Studio 에뮬레이터를 사용 하 여 앱 테스트](#test)

- [플랫폼 간에 네이티브 모양 및 느낌을 사용 하 여 UI 완료](#finish)

> [!TIP]
> [GitHub의 xamarin-forms-samples 리포지토리](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather)에서 이 프로젝트에 대한 전체 소스 코드를 찾을 수 있습니다.

## <a name="set-up-your-solution"></a><a name="solution"></a> 솔루션 설정
 다음 단계에서는 공유 코드에 대한 PCL과 두 개의 추가 NuGet 패키지를 포함하는 Xamarin.Forms 솔루션을 만듭니다.

1. Visual Studio에서 새 **비어 있는 앱(Xamarin.Forms 이식 가능)** 솔루션을 만들고 **WeatherApp**으로 이름을 지정합니다. 검색 필드에 **Xamarin.Forms** 를 입력하면 이 템플릿을 가장 쉽게 찾을 수 있습니다.

     없는 경우 Xamarin을 설치 하거나 Visual Studio 2015 기능을 사용 하도록 설정 해야 할 수 있습니다. [설치 및 설치](../cross-platform/setup-and-install.md)를 참조 하세요.

     ![Xamarin.ios 휴대용&#41; 프로젝트 &#40;새 빈 앱 만들기](../cross-platform/media/crossplat-xamarin-formsguide-2.png "CrossPlat Xamarin 양식 가이드 2")

2. 확인을 클릭하여 솔루션을 만든 후에는 몇 개의 개별 프로젝트가 만들어집니다.

    - **WeatherApp(이식 가능)**: 일반적인 비즈니스 논리 및 Xamarin.Forms를 사용하는 UI 코드를 포함하여 플랫폼 간에 공유되는 코드를 작성하는 PCL입니다.

    - **WeatherApp.Droid**: 네이티브 Android 코드를 포함하는 프로젝트. 이 프로젝트가 기본 시작 프로젝트로 설정됩니다.

    - **WeatherApp.iOS**: 네이티브 iOS 코드를 포함하는 프로젝트

    - **WeatherApp.UWP**: Windows 10 UWP 코드를 포함하는 프로젝트

    - **WeatherApp.Windows(Windows 8.1)**: 네이티브 Windows 8.1 코드를 포함하는 프로젝트

    - **WeatherApp.WinPhone(Windows Phone 8.1)**: 네이티브 Windows Phone 코드를 포함하는 프로젝트

    > [!NOTE]
    > 대상으로 하지 플랫폼에 대한 프로젝트는 삭제할 수 있습니다. 이 연습에서는 Android, iOS 및 Windows Phone 8.1 프로젝트를 참조합니다. UWP 및 Windows 8.1 프로젝트 작업은 Windows Phone 8.1 프로젝트 작업과 아주 유사합니다.

     각 네이티브 프로젝트 내에서 해당 플랫폼에 대한 네이티브 디자이너에 액세스하여 플랫폼 특정 화면 및 기능을 필요에 따라 구현할 수 있습니다.

3. 다음과 같이 솔루션의 Xamarin.Forms NuGet 패키지를 안정적인 최신 버전으로 업그레이드합니다. 새 Xamarin 솔루션을 만들 때마다 다음 작업을 수행하는 것이 좋습니다.

    - **도구 > NuGet 패키지 관리자 > 솔루션용 NuGet 패키지 관리**를 선택합니다.

    - **업데이트** 탭 아래에서 **Xamarin.Forms** 업데이트를 선택하고 솔루션의 모든 프로젝트를 업데이트하도록 선택합니다. (참고: Xamarin.Android.Support에 대한 모든 업데이트는 선택되지 않은 상태로 둡니다.)

    - **버전** 필드를 사용 가능한 **안정적인 최신** 버전으로 업데이트합니다.

    - **업데이트**를 클릭합니다.

         ![Xamarin Forms NuGet 패키지를 업데이트 하는 중](../cross-platform/media/crossplat-xamarin-formsguide-4.png "CrossPlat Xamarin 양식 가이드 4")

4. **Newtonsoft.Json** 및 NuGet 패키지를 PCL 프로젝트에 추가합니다. 이 프로젝트는 날씨 데이터 서비스에서 검색된 정보를 처리하는 데 사용됩니다.

    - NuGet 패키지 관리자(3단계부터 열려 있음)에서 **찾아보기** 탭을 선택하고 **Newtonsoft**를 검색합니다.

    - **Newtonsoft.Json**을 선택합니다.

    - **WeatherApp** 프로젝트를 선택합니다(패키지를 설치하는 데는 이 프로젝트만 필요함).

    - **버전** 필드가 **안정적인 최신 버전** 으로 설정되어 있는지 확인합니다.

    - **Install**을 클릭합니다.

    - ![NuGet 패키지에 대 한 Newtonsoft.Js찾기 및 설치](../cross-platform/media/crossplat-xamarin-formsguide-5.png "CrossPlat Xamarin 양식 가이드 5")

5. 4단계를 반복하여 **Microsoft.Net.Http** 패키지를 찾아서 설치합니다.

6. 솔루션을 빌드하고 빌드 오류가 없는지 확인합니다.

## <a name="write-shared-data-service-code"></a><a name="dataservice"></a> 공유 데이터 서비스 코드 작성
 **WeatherApp(이식 가능)** 프로젝트는 모든 플랫폼에서 공유되는 PCL(이식 가능한 클래스 라이브러리)에 대한 코드를 작성하는 프로젝트입니다. PCL는 iOS, Android, Windows Phone 프로젝트에서 빌드된 앱 패키지에 자동으로 포함됩니다.

 이 샘플을 실행 하려면 먼저에서 무료 API 키에 등록 해야 합니다 [http://openweathermap.org/appid](https://openweathermap.org/appid) .

 다음 단계에서는 날씨 서비스의 데이터를 액세스하고 저장하기 위한 코드를 PCL에 추가합니다.

1. **WeatherApp** 프로젝트를 마우스 오른쪽 단추로 클릭하고 **추가 > 클래스...** 를 선택합니다. **새 항목 추가** 대화 상자에서 파일 이름을 **Weather.cs**로 지정합니다. 이 클래스는 날씨 데이터 서비스의 데이터를 저장하는 데 사용합니다.

2. **Weather.cs** 의 전체 내용을 다음으로 바꿉니다.

    ```csharp
    namespace WeatherApp
    {
        public class Weather
        {
            public string Title { get; set; }
            public string Temperature { get; set; }
            public string Wind { get; set; }
            public string Humidity { get; set; }
            public string Visibility { get; set; }
            public string Sunrise { get; set; }
            public string Sunset { get; set; }

            public Weather()
            {
                //Because labels bind to these values, set them to an empty string to
                //ensure that the label appears on all platforms by default.
                this.Title = " ";
                this.Temperature = " ";
                this.Wind = " ";
                this.Humidity = " ";
                this.Visibility = " ";
                this.Sunrise = " ";
                this.Sunset = " ";
            }
        }
    }
    ```

3. **DataService.cs** 라는 PCL 프로젝트에 다른 클래스를 추가합니다. 이 프로젝트는 날씨 데이터 서비스의 JSON 데이터를 처리하는 데 사용됩니다.

4. **DataService.cs** 의 전체 내용을 다음 코드로 바꿉니다.

    ```csharp
    using System.Threading.Tasks;
    using Newtonsoft.Json;
    using System.Net.Http;

    namespace WeatherApp
    {
        public class DataService
        {
            public static async Task<dynamic> getDataFromService(string queryString)
            {
                HttpClient client = new HttpClient();
                var response = await client.GetAsync(queryString);

                dynamic data = null;
                if (response != null)
                {
                    string json = response.Content.ReadAsStringAsync().Result;
                    data = JsonConvert.DeserializeObject(json);
                }

                return data;
            }
        }
    }
    ```

5. **Core** 라는 PCL에 세 번째 클래스를 추가합니다. 여기서는 우편 번호를 사용하여 쿼리 문자열을 구성하고, 날씨 데이터 서비스를 호출한 다음 **Weather** 클래스의 인스턴스를 채우는 논리와 같은 공유 비즈니스 논리를 추가하게 됩니다.

6. 그런 후 **Core.cs** 의 내용을 다음으로 바꿉니다.

    ```csharp
    using System;
    using System.Threading.Tasks;

    namespace WeatherApp
    {
        public class Core
        {
            public static async Task<Weather> GetWeather(string zipCode)
            {
                //Sign up for a free API key at http://openweathermap.org/appid
                string key = "YOUR KEY HERE";
                string queryString = "http://api.openweathermap.org/data/2.5/weather?zip="
                    + zipCode + ",us&appid=" + key + "&units=imperial";

                dynamic results = await DataService.getDataFromService(queryString).ConfigureAwait(false);

                if (results["weather"] != null)
                {
                    Weather weather = new Weather();
                    weather.Title = (string)results["name"];
                    weather.Temperature = (string)results["main"]["temp"] + " F";
                    weather.Wind = (string)results["wind"]["speed"] + " mph";
                    weather.Humidity = (string)results["main"]["humidity"] + " %";
                    weather.Visibility = (string)results["weather"][0]["main"];

                    DateTime time = new System.DateTime(1970, 1, 1, 0, 0, 0, 0);
                    DateTime sunrise = time.AddSeconds((double)results["sys"]["sunrise"]);
                    DateTime sunset = time.AddSeconds((double)results["sys"]["sunset"]);
                    weather.Sunrise = sunrise.ToString() + " UTC";
                    weather.Sunset = sunset.ToString() + " UTC";
                    return weather;
                }
                else
                {
                    return null;
                }
            }
        }
    }
    ```

7. **WeatherApp** PCL 프로젝트를 빌드하여 코드가 올바른지 확인합니다.

## <a name="begin-writing-shared-ui-code"></a><a name="uicode"></a> 공유 UI 코드 작성 시작
 Xamarin.Forms를 사용하여 PCL에서 공유 UI 코드를 구현할 수 있습니다. 이 단계에서는 이전 섹션에서 추가한 코드를 날씨 데이터 서비스 코드에 의해 반환된 데이터로 해당 텍스트를 업데이트하는 단추가 있는 화면을 PCL에 추가합니다.

1. **WeatherApp** 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **> 새 항목 추가**...를 선택 하 여 **WeatherPage.cs** 이라는 **Forms Xaml 페이지** 를 추가 합니다. **새 항목 추가** 대화 상자에서 "양식", **Forms Xaml 선택 페이지**를 검색 하 고 이름을 **WeatherPage.cs**로 설정 합니다.

     Xamarin.Forms는 XAML 기반이므로 이 단계에서는 중첩된 코드 숨김 파일 **WeatherPage.xaml.cs** 와 함께 **WeatherPage.xaml**파일을 만듭니다. 이 방법을 사용하면 XAML 또는 코드를 통해 UI를 생성할 수 있습니다. 이 연습에서는 둘 중 일부 작업을 수행합니다.

     ![새 Xamarin Forms XAML 페이지 추가](../cross-platform/media/crossplat-xamarin-formsguide-6.png "CrossPlat Xamarin 양식 가이드 6")

2. WeatherPage 화면에 단추를 추가하려면 WeatherPage.xaml의 내용을 다음 코드로 바꿉니다.

    ```xaml
    <?xml version="1.0" encoding="utf-8" ?>
    <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
           xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
           x:Class="WeatherApp.WeatherPage">
      <Button x:Name="getWeatherBtn" Text="Get Weather"/>
    </ContentPage>
    ```

     코드 숨김 파일 내에서 이름으로 이 단추를 참조할 수 있도록 단추 이름은 **x:Name** 특성을 사용하여 정의해야 합니다.

3. 단추의 **Clicked** 이벤트에 대한 이벤트 처리기를 추가하여 단추 텍스트를 업데이트하려면 **WeatherPage.xaml.cs** 의 내용을 아래 코드로 바꿉니다. ("60601"을 다른 우편 번호로 변경해도 됩니다.)

    ```csharp
    using System;
    using Xamarin.Forms;

    namespace WeatherApp
    {
        public partial class WeatherPage: ContentPage
        {
            public WeatherPage()
            {
                InitializeComponent();
                this.Title = "Sample Weather App";
                getWeatherBtn.Clicked += GetWeatherBtn_Clicked;

                //Set the default binding to a default object for now
                this.BindingContext = new Weather();
            }

            private async void GetWeatherBtn_Clicked(object sender, EventArgs e)
            {
                Weather weather = await Core.GetWeather("60601");
                getWeatherBtn.Text = weather.Title;
            }
        }
    }
    ```

4. 앱이 시작될 때 첫 번째 화면으로 **WeatherPage** 를 열려면 **App.cs** 의 기본 생성자를 다음 코드로 바꿉니다.

    ```csharp
    public App()
    {
        MainPage = new NavigationPage(new WeatherPage());
    }
    ```

5. WeatherApp PCL 프로젝트를 빌드하여 코드가 올바른지 확인합니다.

## <a name="test-your-app-using-the-visual-studio-emulator-for-android"></a><a name="test"></a> Android용 Visual Studio 에뮬레이터를 사용하여 앱 테스트
 이제 앱을 실행할 준비가 되었습니다. 지금은 앱이 날씨 서비스의 데이터를 가져오는지를 Android 버전에서만 확인해 보겠습니다. iOS 및 Windows Phone 버전은 다른 UI 요소를 추가한 후에 실행해 보겠습니다. (참고: Windows 7에서 Visual Studio를 실행하는 경우 동일한 단계를 수행하지만 대신 Xamarin Player를 사용합니다.)

1. **WeatherApp.Droid** 프로젝트를 마우스 오른쪽 단추로 클릭하고 **시작 프로젝트로 설정**을 선택하여 해당 프로젝트를 시작 프로젝트로 설정합니다.

2. Visual Studio 도구 모음에서 **WeatherApp.Droid** 가 대상 프로젝트로 표시됩니다. 디버깅을 위해 Android 에뮬레이터 중 하나를 선택하고 **F5**키를 누릅니다. Android 옵션용 Visual Studio 에뮬레이터에서 앱을 실행하는 **VS 에뮬레이터** 옵션 중 하나를 사용하는 것이 좋습니다.

     ![VS 에뮬레이터 디버그 대상 선택](../cross-platform/media/crossplat-xamarin-formsguide-7.png "CrossPlat Xamarin 양식 가이드 7")

3. 에뮬레이터에서 앱이 시작되면 **날씨 검색** 단추를 클릭합니다. 단추 텍스트가 **Chicago, IL**로 업데이트되어 표시되며, 이것은 날씨 서비스에서 가져온 데이터의 *Title* 속성입니다.

     ![단추를 누르기 전과 후의 날씨 앱](../cross-platform/media/crossplat-xamarin-formsguide-8.png "CrossPlat Xamarin 양식 가이드 8")

## <a name="finish-the-ui-with-a-native-look-and-feel-across-platforms"></a><a name="finish"></a> 플랫폼 간에 네이티브 모양 및 느낌을 지정하여 UI 완료
 Xamarin.Forms는 앱이 자동으로 네이티브 모양 및 느낌을 갖도록 각 플랫폼에 대해 네이티브 UI 컨트롤을 렌더링합니다. 이를 보다 명확히 이해하기 위해 우편 번호 입력 필드로 UI를 완료한 다음 서비스에서 반환되는 날씨 데이터를 표시해 보겠습니다.

1. **WeatherPage.xaml** 의 내용을 아래 코드로 바꿉니다. 코드에서 요소를 참조할 수 있도록 모든 요소는 앞서 설명된 대로 **X:name** 특성을 사용하여 명명됩니다. 또한 Xamarin.Forms는 다양한 [레이아웃 옵션](/xamarin/xamarin-forms/user-interface/controls/layouts) (xamarin.com)을 제공합니다. 여기서 WeatherPage는 [StackLayout](/dotnet/api/Xamarin.Forms.StackLayout?view=xamarin-forms) (xamarin.com)을 사용합니다.

   ```xaml
   <?xml version="1.0" encoding="utf-8" ?>
   <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
          xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
          x:Class="WeatherApp.WeatherPage">

     <ContentPage.Resources>
       <ResourceDictionary>
         <Style x:Key="labelStyle" TargetType="Label">
           <Setter Property="TextColor" Value="#a8a8a8" />
           <Setter Property="FontSize" Value="Small" />
         </Style>
         <Style x:Key="fieldStyle" TargetType="Label">
           <Setter Property="TextColor">
             <OnPlatform x:TypeArguments="Color" iOS="Black" Android="White" WinPhone="White" />
           </Setter>
           <Setter Property="FontSize" Value="Medium" />
         </Style>
         <Style x:Key="fieldView" TargetType="ContentView">
           <Setter Property="Padding" Value="10,0,0,0" />
         </Style>
       </ResourceDictionary>
     </ContentPage.Resources>

     <ContentPage.Content>
       <ScrollView>
         <StackLayout>
           <StackLayout Orientation="Horizontal" HorizontalOptions="FillAndExpand"
                 BackgroundColor="#545454">
             <StackLayout Padding="10,10,10,10" HorizontalOptions="Start">
               <Label Text="Search by Zip Code" TextColor="White" FontAttributes="Bold"
                   FontSize="Medium" />
               <Label x:Name="zipCodeLabel" Text="Zip Code" Style="{StaticResource labelStyle}" />
               <Entry x:Name="zipCodeEntry" />
             </StackLayout>
             <StackLayout Padding="0,0,0,10" VerticalOptions="End">
               <Button x:Name="getWeatherBtn" Text="Get Weather" WidthRequest="185" BorderWidth="1" >
                 <!-- Set iOS colors; use defaults on other platforms -->
                 <Button.TextColor>
                   <OnPlatform x:TypeArguments="Color" iOS="White"/>
                 </Button.TextColor>
                 <Button.BorderColor>
                   <OnPlatform x:TypeArguments="Color" iOS="White"/>
                 </Button.BorderColor>
               </Button>
             </StackLayout>
           </StackLayout>
           <StackLayout Padding="10,10,10,10" HorizontalOptions="Start">
             <Label Text="Location" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label Text="{Binding Title}" Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Temperature" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="tempLabel" Text="{Binding Temperature}"
                   Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Wind Speed" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="windLabel" Text="{Binding Wind}" Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Humidity" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="humidityLabel" Text="{Binding Humidity}"
                   Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Visibility" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="visibilitylabel" Text="{Binding Visibility}"
                   Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Time of Sunrise" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="sunriseLabel" Text="{Binding Sunrise}"
                   Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Time of Sunset" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="sunsetLabel" Text="{Binding Sunset}"
                   Style="{StaticResource fieldStyle}" />
             </ContentView>
           </StackLayout>
         </StackLayout>
       </ScrollView>
     </ContentPage.Content>
   </ContentPage>
   ```

    Xamarin.Forms의 **OnPlatform** 태그 사용에 유의합니다. **OnPlatform** 은 앱을 실행 중인 현재 플랫폼에 해당하는 속성 값을 선택합니다( [외부 XAML 구문](/xamarin/xamarin-forms/xaml/xaml-basics/essential-xaml-syntax) 참조)(xamarin.com). 여기서는 데이터 필드에 대해 다른 텍스트 색을 설정하는 데 사용합니다. 즉, Android 및 Windows Phone에서는 흰색, iOS에서 검은색을 설정합니다. 어떤 속성 및 데이터 형식에도 **OnPlatform** 을 사용하여 XAML에서 플랫폼별 조정을 수행할 수 있습니다. 코드 숨김 파일에서는 같은 용도로 [Device.OnPlatform API](/xamarin/xamarin-forms/platform/device) 를 사용할 수 있습니다.

2. **WeatherPage.xaml.cs**에서 **GetWeatherBtn_Clicked** 이벤트 처리기를 아래 코드로 바꿉니다. 이 코드는 입력 필드에 우편 번호가 있는지 확인하고, 해당 우편 번호에 대한 데이터를 검색하고, 전체 화면 바인딩 컨텍스트를 결과 Weather 인스턴스로 설정한 다음 단추 텍스트를 "다시 검색"으로 설정합니다. UI의 각 레이블은 Weather 클래스의 속성에 바인딩되므로 화면의 바인딩 컨텍스트를 **Weather** 인스턴스로 설정하면 해당 레이블이 자동으로 업데이트됩니다.

   ```csharp
   private async void GetWeatherBtn_Clicked(object sender, EventArgs e)
   {
       if (!String.IsNullOrEmpty(zipCodeEntry.Text))
       {
           Weather weather = await Core.GetWeather(zipCodeEntry.Text);
           this.BindingContext = weather;
           getWeatherBtn.Text = "Search Again";
       }
   }
   ```

3. 해당 프로젝트를 마우스 오른쪽 단추로 클릭하고 시작 프로젝트로 설정을 선택한 후 디바이스 또는 에뮬레이터나 시뮬레이터에서 앱을 시작하여 세 플랫폼(Android, iOS 및 Windows Phone) 모두에서 앱을 실행합니다. 아래와 같이 유효한 미국 우편 번호(예: 60601)를 입력하고 날씨 검색 단추를 눌러 해당 지역의 날씨 데이터를 표시합니다. 물론 iOS 프로젝트의 경우 네트워크의 Mac OS X 컴퓨터에 Visual Studio가 연결되어 있어야 합니다.

    ![Android, iOS 및 Windows Phone의 날씨 앱 샘플](../cross-platform/media/crossplat-xamarin-formsguide-1.png "CrossPlat Xamarin 양식 가이드 1")

   이 프로젝트에 대한 전체 소스 코드는 [GitHub의 xamarin-forms-samples 리포지토리](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather)에 있습니다.
