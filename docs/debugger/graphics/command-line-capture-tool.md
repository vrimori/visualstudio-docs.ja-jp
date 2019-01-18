---
title: コマンド ライン キャプチャ ツール |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: db75b3a7-80b2-4a74-91d2-fd6e0f73b45d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 12aa697bff0a60ce6ab9a24351514c96ce107d02
ms.sourcegitcommit: 5a65ca6688a2ebb36564657d2d73c4b4f2d15c34
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "53960655"
---
# <a name="command-line-capture-tool"></a>コマンド ライン キャプチャ ツール
DXCap.exe は、グラフィックス診断のキャプチャと再生に使用されるコマンド ライン ツールです。 すべての機能レベルで、Direct3D 10 から Direct3D 12 をサポートしています。  
  
## <a name="syntax"></a>構文  
  
```cmd  
DXCap.exe [-file filename] [-frame frames | -period periods | -manual] -c app [args...]  
DXCap.exe -p [filename] [-debug | -warp | -hw] [-config] [-rawmode]  
DXCap.exe -p [filename] -screenshot [-frame frames]  
DXCap.exe -p [filename] -toXML [xml_filename]  
DXCap.exe -v [-file filename] [-examine events] [-haltonfail | -exitonfail] [-showprogress]  
DXCap.exe -e [search_string]  
DXCap.exe -info  
```  
  
#### <a name="parameters"></a>パラメーター  
 `-file` `filename`  
 キャプチャ モード (`-c`)、`filename`にグラフィックス情報が記録されているグラフィックス ログ ファイルの名前を指定します。 場合`filename`が指定されていない、という名前のファイルにグラフィックス情報を記録`<appname>-<date>-<time>.vsglog`既定。  
  
 検証 (-v) モードの場合、`filename` には、検証するグラフィックス ログ ファイルの名前を指定します。 場合`filename`が指定されていない、最後に検証されたグラフィックス ログがもう一度使用されます。  
  
 `-frame` `frames`  
 キャプチャ モードの場合、`frames` には、キャプチャするフレームを指定します。 最初のフレームは 1 です。 コンマおよび範囲を使用して、複数のフレームを指定できます。 たとえば場合、`frames`は`2, 5, 7-9, 15`、フレーム`2`、 `5`、 `7`、 `8`、 `9`、および`15`がキャプチャされます。  

> [!TIP]
> 使用`-frame` `manual` Print Screen キーを押してフレームを手動でキャプチャはことを指定します。 フレームはアプリの起動時にキャプチャできます。フレームのキャプチャを停止するには、コマンド ライン インターフェイスに戻り、Enter キーを押します。  
  
 `-period` `periods`  
 キャプチャ モードの場合、`periods` には、フレームをキャプチャする時間の範囲を秒単位で指定します。 コンマおよび範囲を使用して、いくつかの期間を指定できます。 たとえば場合`periods`は`2.1-5, 7.0-9.3`、フレームがレンダリングされ`2.1`と`5`(秒単位)、および`7`と`9.3`秒がキャプチャされます。  
  
 `-c` `app` [`args...`]  
 キャプチャ モード。 キャプチャ モードの場合、`app` には、グラフィックス情報の取得元となるアプリの名前を指定します。`args...` には、そのアプリに対する追加のコマンド ライン パラメーターを指定します。  
  
 `-p` [`filename`]  
 再生モード (`-p`)。 再生モードの場合、`filename` には、再生するグラフィックス ログ ファイルの名前を指定します。 場合`filename`が指定されていない、グラフィックス ログが最後に再生をもう一度使用されます。  
  
 `-debug`  
 再生モードの場合は、`-debug`再生を有効になっている、Direct3D デバッグ レイヤーを再生するかを指定します。  
  
 `-warp`  
 再生モードの場合は、 `-warp` WARP ソフトウェア レンダラーを使用して、その再生を再生するかを指定します。  
  
 `-hw`  
 再生モードの場合は、 `-hw` GPU ハードウェアを使用して、再生を再生するかを指定します。  
  
 `-config`  
 再生モードの場合は、`-config`グラフィックス ログ ファイルのキャプチャに使用されたコンピューターに関する情報が表示されます。  
  
 `-rawmode`  
 再生モードの場合は、`-rawmode`記録されたイベントを変更しなくても、その再生を実行する必要がありますを指定します。 再生モードの通常の動作では、デバッグを単純化し、再生を高速化するために、再生に若干の変更が加えられる場合があります。 たとえば、スワップ チェーンのコマンドを実行する代わりに、スワップ チェーンの出力をシミュレートする場合があります。 通常この再生の問題はありません再生をに対してより忠実に記録されたイベントのある方法で実行する必要があります。 たとえば、全画面表示モードで実行中にキャプチャされたアプリを全画面レンダリング動作を復元するのに、このオプションを使用できます。  
  
 `-toXML` [`xml_filename`]  
 再生モードの場合、`xml_filename` には、再生の XML 表現の書き込み先となるファイルの名前を指定します。 `xml_filename` が指定されていない場合、XML 表現は、再生するファイルと同じ名前を持ち、`.xml` 拡張子が付けられたファイルに書き込まれます。  
  
 `-v`  
 検証モード。 検証モードの場合、キャプチャしたフレームはハードウェアと WARP の両方で再生され、イメージ比較関数によって、それらの結果が比較されます。 この機能を使用すると、レンダリングに影響を与えるドライバーの問題をすばやく識別できます。  
  
 `-examine` `events`  
 検証モードの場合、`events` には、直近の結果を比較する一連のグラフィックス イベントを指定します。 たとえば、`-examine present,draw,copy,clear`制限をカテゴリに属するイベントのみを比較します。  
  
> [!TIP]
>  始まることをお勧めします。`-examine present,draw,copy,clear`これはほとんどの問題を表示がより広範な一連のイベントよりも大幅に少ない時間がかかるためです。 必要に応じて、より多くの、または異なる一連のイベントを指定して、それらのイベントを検証し、その他の種類の問題を明らかにすることもできます。  
  
 `-haltonfail`  
 検証モードの場合は、`-haltonfail`ハードウェア レンダラーと WARP レンダラーの違いが検出されたときに、検証を停止します。 検証は、キーが押された後に再開されます。  
  
 `-exitonfail`  
 検証モードの場合は、`-exitonfail`ハードウェア レンダラーと WARP レンダラーの違いが検出されたときにすぐに、検証を終了します。 この方法で、プログラムが終了すると、それを返します`0`; 環境に返します`1`します。  
  
 `-showprogress`  
 検証モードの場合は、`-showprogress`検証セッション情報の進行状況が表示されます。 WARP の進行状況が左側に表示され、ハードウェアの進行状況が右側に表示されます。  
  
 `-e` `search_string`  
 インストールされている UWP アプリを列挙します。 この情報を使用して、UWP アプリでコマンド ライン キャプチャを実行することができます。  
  
 `-info`  
 コンピューターとキャプチャの DLL に関する情報を表示します。  
  
## <a name="remarks"></a>コメント  
 DXCap.exe は 3 つのモードで動作します。  
  
 キャプチャ モード (-c)  
 実行中のアプリからグラフィックス情報をキャプチャし、その情報をグラフィックス ログ ファイルに記録します。 キャプチャ機能とファイル形式は、Visual Studio と同じです。  
  
 再生モード (-p)  
 再生は、以前既存のグラフィックス ログ ファイルからのグラフィックス イベントをキャプチャします。 既定では、グラフィックス ログ ファイルが全画面アプリからキャプチャされた場合でも、再生はウィンドウ内で実行されます。 ファイルが全画面アプリからキャプチャされた、グラフィックス ログの場合にのみ、全画面表示で再生が発生したと`-rawmode`を指定します。  
  
 検証モード (`-v`)  
 キャプチャしたフレームをハードウェアと WARP の両方で再生してレンダリング動作を検証した後、イメージ比較関数を使用して、結果を比較します。 この機能を使用すると、レンダリングに影響を与えるドライバーの問題をすばやく識別できます。  
  
 これらのモードに加えて、dxcap.exe は、グラフィックス情報のキャプチャや再生を実行しない、他の 2 つの機能を実行します。  
  
 列挙関数 (`-e`)  
 コンピューターにインストールされている UWP アプリの詳細を表示します。 これらの詳細には、UWP アプリで実行可能ファイルを識別する appid とパッケージの名前が含まれます。 DXCap.exe を使用して、Windows ストア アプリからグラフィックス情報をキャプチャするには、デスクトップ アプリをキャプチャするときに使用する実行可能ファイルの名前ではなく、このパッケージ名とアプリ ID を使用します。  
  
 情報関数 (`-info)`  
 コンピューターとキャプチャの DLL の詳細を表示します。  
  
## <a name="examples"></a>使用例  
  
### <a name="capture-graphics-information-from-a-desktop-app"></a>デスクトップ アプリからのグラフィックス情報のキャプチャ  
 使用`-c`グラフィックス情報をキャプチャするアプリを指定します。  
  
```cmd  
DXCap.exe -c BasicHLSL11.exe  
```  
  
 既定では、グラフィックス情報はという名前のファイルに記録`<appname>-<date>-<time>.vsglog`します。 使用`-file`を記録する別のファイルを指定します。  
  
```cmd  
DXCap.exe -file regression_test_12.vsglog -c BasicHLSL11.exe  
```  
  
 キャプチャ元のアプリに対する追加のコマンド ライン パラメーターを、そのアプリのファイル名の後に含めることによって指定します。  
  
```cmd  
DXCap.exe -c "C:\Program Files\Internet Explorer\iexplorer.exe" "www.fishgl.com"  
```  
  
 上記の例のコマンドでは、WebGL API を使用して 3-D コンテンツをレンダリングする、www.fishgl.com にある Web ページの表示中に、Internet Explorer のデスクトップ バージョンからグラフィックス情報をキャプチャします。  
  
> [!NOTE]
>  アプリの後に指定したコマンド ライン引数はアプリに渡されるため、`-c` オプションを使用する前に、DXCap.exe の引数を指定する必要があります。  
  
### <a name="capture-graphics-information-from-a-uwp-app"></a>UWP アプリからグラフィックス情報をキャプチャします。  
 UWP アプリからグラフィックス情報をキャプチャすることができます。  
  
```cmd  
DXCap.exe -c Microsof.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe,AppexMaps  
```  
  
 DXCap.exe を使用して UWP アプリからキャプチャするは、Windows デスクトップ アプリからキャプチャするために使用すると似ていますが、代わりに、パッケージ名と名前で UWP アプリを識別するために、ファイル名でデスクトップ アプリを識別する、またはするパッケージを実行可能ファイル内の ID キャプチャします。 コンピューターにインストールされている UWP アプリを識別する方法を見つけやすくする、使用、`-e`それらを列挙するために、DXCap.exe のオプション。  
  
```cmd  
DXCap.exe -e  
```  
  
 オプションの検索文字列を指定して、探しているアプリの検索に役立てることもできます。 検索文字列を指定した場合、DXCap.exe は、パッケージ名、アプリの名前またはアプリ Id を持つ検索文字列に一致する UWP アプリを列挙します。 検索では、大文字と小文字を区別しません。  
  
```cmd  
DXCap.exe -e map  
```  
  
 上記のコマンドは、"map"; に一致する UWP アプリを列挙します。出力を次に示します。  
  
 **パッケージ "Microsoft.BingMaps":**  
 **検出:C:\Program Files\WindowsApps\Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe**  
 **FullNameMicrosoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe**  
 **UserSID:S-1-5-21-2127521184-1604012920-1887927527-5603533**  
 **名前(&N):Microsoft.BingMaps**  
 **発行元CN = Microsoft Corporation, O = Microsoft Corporation, L = Redmond, S = Washington, C = u. s.**  
 **バージョン          : 2.1.2914.1734**  
 **起動可能なアプリケーション:**   
 **IDAppexMaps**  
 **Exe:C:\Program Files\WindowsApps\Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe\Map.exe**  
 **IsWWA:いいえ**  
 **(起動) を AppSpec:DXCap.exe の-c Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe,AppexMaps**列挙された各アプリの出力の最後の行からグラフィックス情報をキャプチャする際のコマンドを表示します。  
  
### <a name="capture-specific-frames-or-frames-between-specific-times"></a>特定のフレームまたは特定の期間のフレームのキャプチャ  
 使用`-frame`コンマおよび範囲を使用してキャプチャするフレームを指定します。  
  
```cmd  
DXCap.exe -frame 2,5,7-9,15 -c SimpleBezier11.exe  
```  
  
 または、使用して`-period`フレームをキャプチャする時間範囲のセットを指定します。 時間の範囲は秒単位で指定し、複数の範囲を指定することもできます。  
  
```cmd  
DXCap.exe -period 2.1-5, 7.0-9.3 -c SimpleBezier11.exe  
```  
  
### <a name="capture-frames-interactively"></a>フレームの対話的なキャプチャ  
 使用`-manual`フレームを対話的にキャプチャします。 Enter キーを押してキャプチャを開始し、もう一度 Enter キーを押して停止します。  
  
```cmd  
DXCap.exe -manual -c SimpleBezier11.exe  
```  
  
### <a name="play-back-a-graphic-log-file"></a>グラフィックス ログ ファイルを再生します。  
 使用`-p`以前にキャプチャしたグラフィックス ログ ファイルを再生します。  
  
```cmd  
DXCap.exe -p regression_test_12.vsglog  
```  
  
 最後にキャプチャされたグラフィックス ログを再生する場合は、ファイル名を指定しません。  
  
```cmd  
DXCap.exe -p  
```  
  
### <a name="play-back-in-raw-mode"></a>Raw モードでの再生  
 使用`-rawmode`発生したとおりには、キャプチャしたコマンドを再生します。 通常の再生では、特定のコマンドがエミュレートされます。たとえば、全画面アプリからキャプチャされたグラフィックス ログ ファイルは、ウィンドウ内で再生されます。Raw モードが有効になっている場合は、同じファイルの再生が全画面で試行されます。  
  
```cmd  
DXCap.exe -p regression_test_12.vsglog -rawmode  
```  
  
### <a name="play-back-using-warp-or-a-hardware-device"></a>WARP またはハードウェア デバイスの使用の再生  
 ハードウェア デバイス上でキャプチャしたグラフィックス ログ ファイルの再生で、WARP を強制的に使用したり、WARP 上でキャプチャされたログの再生で、強制的にハードウェア デバイスを使用したりできます。 使用`-warp`WARP を使用して再生します。  
  
```cmd  
DXCap.exe -p regression_test_12.vsglog -warp  
```  
  
 使用`-hw`ハードウェアを使用して再生します。  
  
```cmd  
DXCap.exe -p regression_test_12.vsglog -hw  
```  
  
### <a name="validate-a-graphics-log-file-against-warp"></a>WARP に対するグラフィックス ログ ファイルの検証  
 検証モードの場合、グラフィックス ログ ファイルはハードウェアと WARP の両方で再生され、その結果が比較されます。 これは、ドライバーが原因で発生するレンダリング エラーを識別するのに役立ちます。 -v を使用すると、WARP に対してグラフィックス ハードウェアが正しく動作するかどうかを検証できます。  
  
```cmd  
DXCap.exe -v regression_test_12.vsglog  
```  
  
 比較の量を減らすために、比較する検証用コマンドのサブセットを指定できます。この場合、他のコマンドは無視されます。 結果を比較するコマンドを指定するには、-examine を使用します。  
  
```cmd  
DXCap.exe -v regression_test_12.vsglog -examine present,draw,copy,clear  
```  
  
### <a name="convert-a-graphics-log-file-to-pngs"></a>PNG へのグラフィックス ログ ファイルの変換  
 グラフィックス ログ ファイルのフレームを表示または分析するために、DXCap.exe は、キャプチャしたフレームを .png (ポータブル ネットワーク グラフィックス) イメージ ファイルとして保存できます。 使用`-screenshot`に再生モードの出力をキャプチャしたフレームを .png ファイルとして。  
  
```cmd  
DXCap.exe -p BasicHLSL11.vsglog -screenshot  
```  
  
 使用`-frame`で`-screenshot`を出力するフレームを指定します。  
  
```cmd  
DXCap.exe -p BasicHLSL11.vsglog -screenshot -frame 5, 7-9  
```  
  
### <a name="convert-a-graphics-log-file-to-xml"></a>XML へのグラフィックス ログ ファイルの変換  
 FindStr や XSLT などの使い慣れたツールを使用して、グラフィックス ログを処理および分析するために、DXCap.exe はグラフィックス ログ ファイルを XML に変換できます。 使用`-toXML`再生モードの再生ではなく、ログを XML に変換するバックアップを作成します。  
  
```cmd  
DXCap.exe -p regression_test_12.vsglog -toXML  
```  
  
 既定では、XML 出力は、グラフィックス ログと同じ名前を持ち、.xml 拡張子が付けられたファイルに書き込まれます。 上記の例では、XML ファイルの名前は**regression_test_12.xml**します。 XML ファイルに別の名前を付けるには、指定した後、`-toXML`します。  
  
```cmd  
DXCap.exe -p regression_test_12.vsglog -toXML temp.xml  
```  
  
 結果のファイルには、次のような XML が格納されます。  
  
```xml  
<Moment value="67"/>  
<Method name="CreateDXGIFactory1" >  
    <Return type="HRESULT" value="S_OK" />  
    <Parameter name="riid" type="IID" value="770AAE78-F26F-4DBA-A829-253C83D1B387" />  
    <Parameter name="ppFactory" type="void" handle="1" isOutput="true" />  
</Method>  
  
<Moment value="167"/>  
<Method name="D3D11CreateDevice" >  
    <Return type="HRESULT" value="S_OK" />  
    <Parameter name="pAdapter" type="IDXGIAdapter" handle="34" />  
    <Parameter name="DriverType" type="D3D_DRIVER_TYPE" value="D3D_DRIVER_TYPE_UNKNOWN" />  
    <Parameter name="Software" type="HMODULE" value="pointer" />  
    <Parameter name="Flags" type="UINT" value="0" />  
    <Parameter name="pFeatureLevels" type="D3D_FEATURE_LEVEL" arrSize="1" >  
        <Element value="D3D_FEATURE_LEVEL_11_0" />  
    </Parameter>  
    <Parameter name="FeatureLevels" type="UINT" value="1" />  
    <Parameter name="SDKVersion" type="UINT" value="7" />  
    <Parameter name="ppDevice" type="ID3D11Device" handle="35" isOutput="true" />  
    <Parameter name="pFeatureLevel" type="D3D_FEATURE_LEVEL" value="D3D_FEATURE_LEVEL_11_0" isOutput="true" />  
    <Parameter name="ppImmediateContext" type="ID3D11DeviceContext" value="nullptr" isOutput="true" />  
</Method>  
```  
  
## <a name="requirements"></a>要件