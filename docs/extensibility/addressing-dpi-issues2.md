---
title: "DPI Issues2 をアドレス指定 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# DPI の問題の対応
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

「高解像度」モニターにデバイス数が増加も付属します。 これらの画面には、通常、200 を超えるピクセル\/インチ \(ppi\) があります。 これらのコンピューター上のアプリケーションの操作は、コンテンツをデバイスに通常表示する距離にあるコンテンツを表示するためのニーズに合わせてスケール アップする必要があります。 2014 年時点では、高密度ディスプレイの主要なターゲットはモバイル コンピューティング デバイス \(タブレットやクラムシェル ラップトップ、携帯電話\) です。  
  
 Windows 8.1 以降では、表示と、マシンが高密度の両方に接続され、同時に標準密度が表示されます。 環境を操作するこれらのマシンを有効にするいくつかの機能が含まれています。  
  
-   Windows を"のテキストおよびその他の項目拡大または縮小する"を使用してデバイスにコンテンツを拡大縮小をできるようにすることができます \(Windows XP 以降で使用可能\) を設定します。  
  
-   Windows 8.1 以降を異なるピクセル密度の表示の間を移動すると一貫性を維持するほとんどのアプリケーション コンテンツを自動的にスケールできます。 プライマリ ディスプレイが高密度が \(200% のスケーリング\) とセカンダリ ディスプレイは、標準の密度 \(100%\)、Windows を自動的にスケール アプリケーション ウィンドウの内容セカンダリ ディスプレイ \(1 ピクセルのアプリケーションで表示されたすべての 4 ピクセルが表示されます\) にします。  
  
-   Windows は、ピクセル密度のスケーリングと表示 \(Windows 7 以降では OEM が構成可能な\) の距離を表示する右に設定されます。  
  
-   Windows は 280 ppi \(現在、Windows 8.1 S14\) を超える新しいデバイスによっては 250% にコンテンツを自動的にスケールできます。  
  
 Windows には、増加のピクセル数を活用するためにスケール アップ UI を扱う方法があります。 アプリケーションには、指定のこのシステム自体「システム DPI 対応にする」を宣言します。 これを変更しないアプリケーションは、システムによってスケール アップをしました。 これにより、全体のアプリケーションが一様に分布ピクセル引き伸ばされる「あいまい」ユーザー エクスペリエンス。 例:  
  
 ![DPI 問題 &#40;ファジー&#41;](../extensibility/media/dpi-issues-fuzzy.png "DPI Issues Fuzzy")  
  
 Visual Studio は、拡大\/縮小対応、DPI の中にオプトインを指定し、そのため、「仮想化されません」  
  
 Windows \(および Visual Studio\) は、スケーリング、システムによって設定される要素の処理のさまざまな方法があるいくつかの UI テクノロジを活用します。 例:  
  
-   WPF では、単位 \(ピクセル単位ではありません\) は、デバイスに依存しない方法でコントロールを測定します。 WPF の UI は、現在の DPI に自動的に拡張できます。  
  
-   UI フレームワークに関係なくすべてのテキストのサイズは、ポイント単位表され、DPI に依存しないと、システムによって扱わためです。 Win32、WinForms、および WPF 内のテキストは既に、正しくスケーリングしてディスプレイ デバイスに描画した場合。  
  
-   Win32\/WinForms ダイアログおよびウィンドウ レイアウトのサイズを変更テキスト – たとえば、グリッド、フロー、およびテーブル レイアウト パネルを有効にするための手段があります。 これらには、フォント サイズを増やすときに調整されないピクセルをハード コーディングされた場所の回避が有効にします。  
  
-   システムによって提供されるアイコンやシステムのメトリック \(たとえば、SM\_CXICON および SM\_CXSMICON\) に基づいて、リソースは既にスケール アップします。  
  
## 古い Win32 \(GDI、GDI \+\) と Winform ベースの UI  
 WPF の高 DPI 対応中、Win32 GDI ベース コードの多くいないで書き込まれて DPI 対応に注意します。 Windows は、Api の DPI スケールを提供しています。 Win32 問題の修正には、製品全体にわたる一貫してこれらを使用する必要があります。 Visual Studio を提供するヘルパー クラス ライブラリの機能を複製して、製品全体にわたる一貫性を保つことを回避します。  
  
## 高解像度の画像  
 このセクションでは、主に Visual Studio 2013 を拡張する開発者向けです。 Visual Studio 2015、Visual Studio に組み込まれたイメージのサービスを使用します。 多くのバージョンの Visual Studio のサポート\/ターゲットする必要があるあり、したがって 2015年の \[イメージのサービスを使用してオプションではありません、以前のバージョンでは存在しないのでこともあります。 このセクションではまた、なります。  
  
## イメージが小さすぎることを拡大\/縮小  
 イメージが小さすぎることを「スケール アップ」と GDI といくつかの一般的な方法を使用して WPF で描画します。 マネージ DPI ヘルパー クラスは、内部および外部の Visual Studio インテグレーター アイコン、ビットマップ、imagestrips、および imagelists をスケーリングするアドレスを使用できます。 Win32 ベースのネイティブ C と c\+\+ のヘルパーを HICON、HBITMAP、HIMAGELIST、および VsUI::GdiplusImage を拡張するために利用できます。 通常、ビットマップのスケーリングでは、ヘルパー ライブラリへの参照を含めた後で 1 行の変更のみが必要です。 例:  
  
```cpp  
(Unmanaged)  VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
```  
  
```c#  
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);  
```  
  
 Imagelist を拡大\/縮小は、イメージ リストが、読み込み時に完了またはが実行時に追加されるかどうかによって異なります。 読み込み時に完了すると場合、は、ビットマップのと同様に、イメージ リストを LogicalToDeviceUnits\(\) を呼び出します。 コードは、イメージ リストを作成する前に個々 のビットマップを読み込む必要があるとき、は、イメージ リストのイメージ サイズを調整することを確認してください。  
  
```c#  
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);  
```  
  
 ネイティブ コードは、次のように、イメージ リストを作成するときに、ディメンションを拡張できます。  
  
```cpp  
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);  
```  
  
 サイズ変更のアルゴリズムを指定することは、ライブラリ内の関数をします。 Imagelists に格納されるイメージをスケーリングは透過性、使用されている背景色を指定することを確認または NearestNeighbor スケーリング \(これは、125% と 150% でゆがみが発生\) を使用します。  
  
 参照してください、 <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> MSDN のドキュメントです。  
  
 次の表では、スケール係数を使用して対応する DPI のイメージのスケーリング方法の例を示します。 緑色でイメージを表す \(100 ~ 200 %dpi のスケール\) Visual Studio 2013 の時点でベスト プラクティス。  
  
 ![DPI 問題 &#40;スケーリング&#41;](../extensibility/media/dpi-issues-scaling.png "DPI Issues Scaling")  
  
## レイアウトの問題  
 絶対位置 \(具体的には、ピクセル単位\) を使用せずに、拡大\/縮小、UI には相互に関連したは、ポイントを保持することで、主に、一般的なレイアウトに問題を回避できます。 例:  
  
-   レイアウト\]、\[テキストの位置は、スケール アップ イメージのアカウントを調整する必要があります。  
  
-   グリッドの列には、スケール アップ テキストに合わせて調整幅が必要です。  
  
-   ハードコーディングのサイズまたは要素間の領域は、スケール アップする必要があります。 テキストの寸法にのみ基づいたサイズは、フォントは自動的にスケール アップしたために通常問題ありません。  
  
 ヘルパー関数は、 <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> X と Y 軸上の拡張を許可するクラス。  
  
-   LogicalToDeviceUnitsX\/LogicalToDeviceUnitsY \(X 上の拡張関数を使用すると Y 軸\)  
  
-   int 領域 \= DpiHelper.LogicalToDeviceUnitsX \(10\)。  
  
-   int 高さ \= VsUI::DpiHelper::LogicalToDeviceUnitsY\(5\) です。  
  
 Rect、ポイント、およびサイズなどのオブジェクトの規模を設定する LogicalToDeviceUnits オーバー ロードがあります。  
  
## スケール イメージ、レイアウトへ DPIHelper ライブラリ\/クラスを使用します。  
 Visual Studio DPI ヘルパー ライブラリでは、ネイティブおよびマネージ フォームで使用され、他のアプリケーションで、Visual Studio shell の外部で使用できます。  
  
 ライブラリを使用するには、 [Visual Studio VSSDK 拡張のサンプル](https://github.com/Microsoft/VSSDK-Extensibility-Samples) 高 DPI\_Images\_Icons サンプルの複製を作成します。  
  
 ソース ファイルで VsUIDpiHelper.h および VsUI::DpiHelper クラスの静的関数を呼び出します。  
  
```cpp  
#include "VsUIDpiHelper.h"  
  
int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);  
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
  
```  
  
> [!NOTE]
>  モジュール レベルまたはクラス レベルの静的変数には、ヘルパー関数を使用しません。 ライブラリがスレッドの同期化も静的変数を使用し、注文の初期化の問題が発生する可能性があります。 非静的メンバー変数をこれらの静的変数を変換するか、\(そのため、このクラスは構築最初のアクセス\) に、それらを関数にラップします。  
  
 Visual Studio 環境内で実行されるマネージ コードから DPI ヘルパー関数にアクセスします。  
  
-   利用するプロジェクトでは、シェル MPF の最新バージョンを参照する必要があります。 例:  
  
    ```c#  
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />  
    ```  
  
-   プロジェクトで参照していることを確認 **System.Windows.Forms**, 、**PresentationCore**, 、および **PresentationUI**します。  
  
-   コードを使用して、 **Microsoft.VisualStudio.PlatformUI** DpiHelper クラスの名前空間と呼び出しの静的関数です。 \(ポイント、サイズ、四角形、およびなど\) のサポートされる種類については、拡張機能を返す新しい関数オブジェクトを拡大\/縮小いますがあります。 例:  
  
    ```c#  
    using Microsoft.VisualStudio.PlatformUI;  
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);  
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();  
    DpiHelper.LogicalToDeviceUnits(ref bitmap);  
  
    ```  
  
## ズーム可能な UI での WPF のイメージの許容量を処理します。  
 WPF は、ビットマップは、画像や大規模なスクリーン ショットに適しては、見かけ上の許容量が導入されているために、メニュー項目のアイコンに適した高品質双三次アルゴリズム \(既定値\) を使用して現在の DPI のズーム レベルに、WPF によって自動的に変更されます。  
  
 推奨事項:  
  
-   ロゴ イメージとリボン アートワーク、既定値の <xref:System.Windows.Media.BitmapScalingMode> モードをサイズ変更を使用できます。  
  
-   メニュー項目とアイコンの画像、 <xref:System.Windows.Media.BitmapScalingMode> が原因で他の歪みアイテム \(200% から 300%\) での許容量を排除するときに使用する必要があります。  
  
-   •	あいまい色あせたの UI は、大規模なズーム レベルを 100% \(たとえば、250% または 350%\) の倍数ではない、の結果双三次アイコン イメージをスケーリングします。 最初の 100% \(200% または 300% など\) の最大の倍数に NearestNeighbor でイメージを拡大\/縮小とそこから双三次によるスケール変更してより良い結果が取得されます。 特殊なケースを参照してください。 詳細情報のレベルの大規模な DPI の WPF のイメージを prescaling します。  
  
 Microsoft.VisualStudio.PlatformUI 名前空間に DpiHelper クラスには、メンバーが用意されています <xref:System.Windows.Media.BitmapScalingMode> バインドに使用することができます。 Visual Studio シェル スケール モード製品全体にわたる一様に、DPI のスケール ファクターによってビットマップを制御することができます。  
  
 これを使用する XAML で次のように追加します。  
  
```xaml  
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
  
<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />  
  
```  
  
 既に、Visual Studio シェルは、最上位ウィンドウとダイアログ ボックスのこのプロパティを設定します。 Visual Studio で実行されている WPF ベースの UI がそれを既に継承されます。 設定は、特定の UI に反映しない場合、は、XAML と WPF の UI のルート要素で設定されることができます。 場所で行いますがポップアップ、Win32 の親を持つ要素を含めるし、Blend などのデザイナー ウィンドウの実行を処理します。  
  
 一部の UI は、Visual Studio テキスト エディター \(WPF\) ベースのデザイナー \(WPF デスクトップと Windows ストア\) など、システム設定の DPI ズーム レベルとは無関係に拡張できます。 このような場合は、DpiHelper.BitmapScalingMode を使用しない必要があります。 エディターでこの問題を解決するには、カスタム プロパティを作成する IDE チーム タイトル RenderOptions.BitmapScalingMode になります。 システムと、UI の結合されたズーム レベルに応じて HighQuality または NearestNeighbor にそのプロパティ値を設定します。  
  
## 特殊なケース: prescaling WPF イメージの大規模な DPI レベル  
 100% \(たとえば、および 250%、350%\) の倍数ではない非常に大規模なズーム レベルの場合は、あいまい色あせたの UI で双三次結果とアイコン イメージを拡大\/縮小します。 これらのイメージの鮮明なテキストの横の印象が錯覚のようにはほぼです。 目に、テキストとの関連のフォーカスが近い位置に、画像が表示されます。 拡大されたこのサイズのスケーリングの結果は、最初の 100% \(200% または 300% など\) の最大の倍数に NearestNeighbor でイメージを拡大\/縮小と双三次残りの部分 \(さらに 50%\) を使用したスケールによって向上させることができます。  
  
 次は、結果の違いの例の最初のイメージが拡大\/縮小 200% と 100%\-\> 強化倍スケーリング アルゴリズムを使用\] は、\[の 250% とだけ双三次 100% で 2 つ目が 250%\-\> です。  
  
 ![DPI Issues Double Scaling Example](../extensibility/media/dpi-issues-double-scaling-example.png "DPI Issues Double Scaling Example")  
  
 各イメージ要素を表示するため、この倍拡大\/縮小、XAML マークアップを使用する UI を有効にするには、変更する必要があります。 次の例では、DpiHelper ライブラリと Shell.12\/14 を使用して Visual Studio で WPF 内の二重スケーリングを使用する方法を示します。  
  
 手順 1: は 300%、200% にイメージを Prescale し、NearestNeighbor を使用するようにします。  
  
 バインディング、または XAML マークアップ拡張機能で適用コンバーターを使用してイメージを prescale します。 例:  
  
```xaml  
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />  
  
<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
  
<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />  
  
```  
  
 イメージをテーマを付ける必要がある場合、ほとんどすべてではないか、マークアップは、イメージと、事前のスケーリングのテーマを最初に行うさまざまなコンバーターを使用できます。 マークアップは、いずれかを使用して <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter> または <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter>, に必要な変換出力に依存します。  
  
```xaml  
<vsui:DpiPrescaleThemedImageSourceConverter x:Key="DpiPrescaleThemedImageSourceConverter" />  
  
<Image Width="16" Height="16">  
  <Image.Source>  
    <MultiBinding Converter="{StaticResource DpiPrescaleThemedImageSourceConverter}">  
      <Binding Path="Icon" />  
      <Binding Path="(vsui:ImageThemingUtilities.ImageBackgroundColor)"    
               RelativeSource="{RelativeSource Self}" />  
      <Binding Source="{x:Static vsui:Boxes.BooleanTrue}" />  
    </MultiBinding>  
  </Image.Source>  
</Image>  
```  
  
 手順 2: は、最終的なサイズが現在の DPI の正しいことを確認します。  
  
 WPF は、UIElement に設定する BitmapScalingMode プロパティを使用して、現在 DPI の UI を拡張、ため 2、3 倍よりも大きくなりますが、ソースになります prescaled イメージを使用してイメージ コントロール必要があります。 この特殊効果のカウンターの値にはいくつかの方法を次に示します。  
  
-   100% で、元のイメージのディメンションがわかっている場合は、イメージ コントロールの正確なサイズを指定できます。 スケーリングする前に、UI のサイズが適用されるこれらのサイズが反映されます。  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
    ```  
  
-   元のイメージのサイズが不明の場合は、スケール ダウン、最終的なイメージ オブジェクトに、LayoutTransform を使用できます。 例:  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" >  
        <Image.LayoutTransform>  
         <ScaleTransform  
             ScaleX="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}"  
             ScaleY="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}" />  
        </Image.LayoutTransform>  
    </Image>  
    ```  
  
## では、WebOC に HDPI サポートの有効化  
 既定では、WebOC コントロール \(WPF、または IWebBrowser2 インターフェイスで WebBrowser コントロール\) などは HDPI 検出とサポートを有効にしません。 結果を表示する内容が高解像度のディスプレイには小さすぎると、埋め込みのコントロールとなります。 次に、特定の web WebOC インスタンスでの高解像度のサポートを有効にする方法について説明します。  
  
 IDocHostUIHandler インターフェイスを実装する \(について、MSDN の記事を参照してください、 [IDocHostUIHandler](http://msdn.microsoft.com/library/aa753260.aspx) インターフェイス\)。  
  
```idl  
[ComImport, InterfaceType(ComInterfaceType.InterfaceIsIUnknown),  
 Guid("BD3F23C0-D43E-11CF-893B-00AA00BDCE1A")]  
public interface IDocHostUIHandler  
{  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int ShowContextMenu(  
        [In, MarshalAs(UnmanagedType.U4)] int dwID,  
        [In] POINT pt,  
        [In, MarshalAs(UnmanagedType.Interface)] object pcmdtReserved,  
        [In, MarshalAs(UnmanagedType.IDispatch)] object pdispReserved);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetHostInfo([In, Out] DOCHOSTUIINFO info);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int ShowUI(  
        [In, MarshalAs(UnmanagedType.I4)] int dwID,  
        [In, MarshalAs(UnmanagedType.Interface)] object activeObject,  
        [In, MarshalAs(UnmanagedType.Interface)] object commandTarget,  
        [In, MarshalAs(UnmanagedType.Interface)] object frame,  
        [In, MarshalAs(UnmanagedType.Interface)] object doc);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int HideUI();  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int UpdateUI();  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int EnableModeless([In, MarshalAs(UnmanagedType.Bool)] bool fEnable);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int OnDocWindowActivate([In, MarshalAs(UnmanagedType.Bool)] bool fActivate);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int OnFrameWindowActivate([In, MarshalAs(UnmanagedType.Bool)] bool fActivate);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int ResizeBorder(  
        [In] COMRECT rect,  
        [In, MarshalAs(UnmanagedType.Interface)] object doc,  
        bool fFrameWindow);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int TranslateAccelerator(  
        [In] ref MSG msg,  
        [In] ref Guid group,  
        [In, MarshalAs(UnmanagedType.I4)] int nCmdID);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetOptionKeyPath(  
        [Out, MarshalAs(UnmanagedType.LPArray)] string[] pbstrKey,  
        [In, MarshalAs(UnmanagedType.U4)] int dw);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetDropTarget(  
        [In, MarshalAs(UnmanagedType.Interface)] IOleDropTarget pDropTarget,  
        [MarshalAs(UnmanagedType.Interface)] out IOleDropTarget ppDropTarget);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetExternal([MarshalAs(UnmanagedType.IDispatch)] out object ppDispatch);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int TranslateUrl(  
        [In, MarshalAs(UnmanagedType.U4)] int dwTranslate,  
        [In, MarshalAs(UnmanagedType.LPWStr)] string strURLIn,  
        [MarshalAs(UnmanagedType.LPWStr)] out string pstrURLOut);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int FilterDataObject(  
        IDataObject pDO,  
        out IDataObject ppDORet);  
    }   
```  
  
 必要に応じて、ICustomDoc インターフェイスを実装 \(について、MSDN の記事を参照してください、 [ICustomDoc](http://msdn.microsoft.com/library/aa753272.aspx) インターフェイス\)。  
  
```idl  
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),  
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]  
public interface ICustomDoc  
{  
    void SetUIHandler(IDocHostUIHandler pUIHandler);  
}   
```  
  
 WebOC のドキュメントを含む IDocHostUIHandler を実装するクラスを関連付けます。 上記の ICustomDoc インターフェイスを実装した場合 WebOC のドキュメント プロパティは、使用するとすぐに、ICustomDoc にキャストし、IDocHostUIHandler を実装するクラスを渡して SetUIHandler メソッドを呼び出します。  
  
```c#  
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface  
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;  
customDoc.SetUIHandler(this);  
  
```  
  
 ICustomDoc インターフェイスを実装しなかった場合、WebOC のドキュメント プロパティは、使用するとすぐにする必要がありますへ、キャストし、IDocHostUIHandler を実装するクラスで渡して SetClientSite メソッドを呼び出します。 GetHostInfo メソッドの呼び出しに渡される受け取るで DOCHOSTUIFLAG\_DPI\_AWARE フラグを設定します。  
  
```c#  
public int GetHostInfo(DOCHOSTUIINFO info)  
{  
    // This is what the default site provides.  
    info.dwFlags = (DOCHOSTUIFLAG)0x5a74012;  
    // Add the DPI flag to the defaults  
    info.dwFlags |=.DOCHOSTUIFLAG.DOCHOSTUIFLAG_DPI_AWARE;  
    return S_OK;  
}  
```  
  
 すべての HPDI をサポートするために、WebOC コントロールを取得する必要があるはずです。  
  
## ヒント  
  
1.  WebOC コントロールのドキュメント プロパティが変更された場合は、IDocHostUIHandler クラスを使用して、ドキュメントを再関連付けする必要があります。  
  
2.  上記が機能しない場合は、DPI フラグへの変更を取得していない WebOC の既知の問題。 この問題の修正の最も信頼性の高い方法は、WebOC、ズームの割合 \(%\) の 2 つの異なる値を持つ 2 つの呼び出しを意味の光学ズームを切り替えるにです。 さらに、この回避策が必要な場合、移動の呼び出しごとに実行するために必要な場合があります。  
  
    ```c#  
    // browser2 is a SHDocVw.IWebBrowser2 in this case  
    // EX: Call the Exec twice with DPI%-1 and then DPI% as the zoomPercent values  
    IOleCommandTarget cmdTarget = browser2.Document as IOleCommandTarget;  
    if (cmdTarget != null)  
    {  
        object commandInput = zoomPercent;  
        cmdTarget.Exec(IntPtr.Zero,  
                       OLECMDID_OPTICAL_ZOOM,  
                       OLECMDEXECOPT_DONTPROMPTUSER,  
                       ref commandInput,  
                       ref commandOutput);  
    }  
    ```