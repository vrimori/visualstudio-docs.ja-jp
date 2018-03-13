---
title: "イメージと Visual Studio のアイコン |Microsoft ドキュメント"
ms.custom: 
ms.date: 04/26/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f410325e-9cf2-4f39-b6d7-b672121c2691
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 164a450ca346fe2bd7b267d951ce522d27f14160
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/13/2018
---
# <a name="images-and-icons-for-visual-studio"></a>イメージと Visual Studio のアイコン
##  <a name="BKMK_ImageUseInVisualStudio"></a> Visual Studio でのイメージの使用  
 アートワークを作成する前に考慮 1,000 + 内のイメージを使用して、 [Visual Studio Image Library](http://www.microsoft.com/en-my/download/details.aspx?id=35825)です。  
  
### <a name="types-of-images"></a>イメージの種類  
  
-   **アイコン**です。 コマンド、階層、テンプレート、およびように表示される小さいイメージ。 Visual Studio で使用される既定のアイコンのサイズは、16 x 16 PNG です。 イメージ サービスによって自動的に生成されるアイコンは、HDPI サポートについては XAML 形式を生成します。  
  
     **注:**すべてのコマンドのアイコンを作成しないでください] メニューの [システムのイメージが使用されますが、します。 参照してください[メニューと Visual Studio のコマンド](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)をコマンドがアイコンを取得するかどうかを確認します。  
  
-   **縮小表示します。** 新しいプロジェクトのダイアログなど、ダイアログ ボックスの [プレビュー] 領域で使用する画像。  
  
-   **ダイアログの画像。** ダイアログまたはウィザードでは、わかりやすいグラフィックまたはメッセージの評価指標としてに表示されるイメージです。 頻度の低いと困難な概念を示すため、ユーザーの注意 (アラート、警告) を取得したりするために必要な場合にのみを使用します。  
  
-   **アニメーション化されたイメージ。** 進行状況インジケーター、ステータス バー、および操作のダイアログ ボックスで使用されます。  
  
-   **カーソルです。** オブジェクトが破棄される可能性がありますには、マウスを使用して、操作を許可するかどうかを示すために使用されます。  
  
##  <a name="BKMK_IconDesign"></a> アイコンのデザイン  
  
### <a name="overview"></a>概要  
 Visual Studio では、クリーン geometry と 50/50 残高 (明/暗)、正または負の値があると理解できるものの直接の要素を使用して、モダン スタイル アイコンを使用します。 重要なアイコンのデザインは、わかりやすくするため、単純化、およびコンテキストを中心とを指します。  
  
-   **わかりやすくするため:**アイコンは、その意味と個性コア比喩に注目します。  
  
-   **単純化:**の中核的な意味にアイコンを減らす - 必要な要素だけとない余分な装飾間でテーマを取得します。  
  
-   **コンテキスト:**これは、どの要素を構成して、アイコンのコア比喩を決定するときに重要な概念の開発中に、アイコンのロールのすべての側面を検討してください。  
  
 アイコン、さまざまな設計ポイントを回避するのには。  
  
-   該当する場合を除く、UI 要素を示すアイコンを使用しないでください。 UI 要素は、一般的な明確でも一意より抽象的またはシンボリック アプローチを選択します。  
  
-   ドキュメント、フォルダー、矢印、拡大鏡などの共通の要素が禁物です。 アイコンの意味に不可欠な場合にのみ、このような要素を使用します。 たとえば、右向きの虫眼鏡がだけの検索を示す必要がありますを参照し、検索できます。  
  
-   一部のレガシ アイコン要素は、パースペクティブの使用を管理、作成しない新しいアイコン パースペクティブを持つ要素が指定されていない場合は、わかりやすくするためがない限り、します。  
  
-   アイコンに情報が多すぎるを詰め込もうしません。 簡単に認識または認識可能なシンボルとして学習できる単純なイメージが過度に複雑なイメージよりもはるかに便利です。 アイコンは、全体の状況を判断できません。  
  
### <a name="icon-creation"></a>アイコンの作成  
  
#### <a name="concept-development"></a>概念の開発  
 Visual Studio では、アイコンの種類のさまざまな UI 内がします。 開発時に、アイコンの種類を慎重に検討します。 アイコン要素の不明なまたは珍しいことで UI オブジェクトを使用しないでください。 スマート タグ アイコンをなどこのような場合は、シンボリック リンクの選択します。 左側のタグが抽象の意味が右側の UI ベース漠然としたバージョンよりもわかりやすいことに注意してください。  
  
|||  
|-|-|  
|**シンボリック画像の正しい使用方法**|**シンボリック画像の不適切な使用**|  
|![正しい [スマート タグ] アイコン](../../extensibility/ux-guidelines/media/0404-01_smarttagcorrect.png "0404 01_SmartTagCorrect")|![スマート タグ アイコンの正しくない](../../extensibility/ux-guidelines/media/0404-02_smarttagincorrect.png "0404 02_SmartTagIncorrect")|  
  
 標準、容易に認識できる UI 要素がうまくアイコンも用インスタンスが生じます。 ウィンドウは、このような 1 つの例を追加します。  
  
|||  
|-|-|  
|**アイコンの正しい UI 要素**|**アイコンの正しくない UI 要素**|  
|![正しい [ウィンドウの追加] アイコン](../../extensibility/ux-guidelines/media/0404-03_addwindowcorrect.png "0404 03_AddWindowCorrect")|![不適切なウィンドウの追加 アイコン](../../extensibility/ux-guidelines/media/0404-04_addwindowincorrect.png "0404 04_AddWindowIncorrect")|  
  
 アイコンの意味に不可欠である場合を除き、基本要素として、ドキュメントを使用しないでください。 ドキュメントなし (下記参照)、意味の文書に追加の要素は、更新でドキュメントの要素は意味を通信するために必要な一方、失われます。  
  
|||  
|-|-|  
|**ドキュメント アイコンの正しい使用方法**|**ドキュメント アイコンの不適切な使用**|  
|![正しい [ドキュメント] アイコン](../../extensibility/ux-guidelines/media/0404-05_documenticoncorrect.png "0404 05_DocumentIconCorrect")|![正しくないドキュメント アイコン](../../extensibility/ux-guidelines/media/0404-06_documenticonincorrect.png "0404 06_DocumentIconIncorrect")|  
  
 「表示」の概念は、最適な内容が表示されているなどと同様に、すべてのファイルを表示する例を示すアイコンで表示する必要があります。 レンズ比喩を使用してを"view"など、必要なリソース ビューの例を使用する場合の概念を示す可能性があります。  
  
|||  
|-|-|  
|**"Show"**|**"View"**|  
|![アイコンを表示する](../../extensibility/ux-guidelines/media/0404-07_show.png "0404 07_Show")|![表示アイコン](../../extensibility/ux-guidelines/media/0404-08_view.png "0404 08_View")|  
  
 右向きの表す・のみ検索ガラスのアイコンを拡大、検索、および参照します。 プラス記号またはマイナス記号を使用して、左向きのバリアントで唯一のズームを表す/ズーム アウトする必要があります。  
  
|||  
|-|-|  
|**"Search"**|**"Zoom"**|  
|![[検索] アイコン](../../extensibility/ux-guidelines/media/0404-09_search.png "0404 09_Search")|![ズーム アイコン](../../extensibility/ux-guidelines/media/0404-10_zoom.png "0404 10_Zoom")|  
  
 ツリー [フォルダー] アイコンと修飾子の両方、ビューは使わないでください。 利用可能であれば、修飾子のみを使用します。  
  
|||  
|-|-|  
|**正しい ツリー ビュー アイコン**|**正しくない ツリー ビュー アイコン**|  
|![正しい ツリー ビュー アイコン&#40;1&#41;](../../extensibility/ux-guidelines/media/0404-11_treeviewcorrect1.png "0404 11_TreeViewCorrect1") ![正しい ツリー ビュー アイコン&#40;2&#41;](../../extensibility/ux-guidelines/media/0404-12_treeviewcorrect2.png "0404 12_TreeViewCorrect2")|![正しくない ツリー ビュー アイコン&#40;1&#41;](../../extensibility/ux-guidelines/media/0404-13_treeviewincorrect1.png "0404 13_TreeViewIncorrect1") ![正しくない ツリー ビュー アイコン&#40;2&#41;](../../extensibility/ux-guidelines/media/0404-14_treeviewincorrect2.png "0404 14_TreeViewIncorrect2")|  
  
### <a name="style-details"></a>スタイルの詳細  
  
#### <a name="layout"></a>レイアウト  
 標準の 16 x 16 のアイコンのようには、要素をスタックにします。  
  
 ![16 x 16 のアイコンのレイアウト スタック](../../extensibility/ux-guidelines/media/0404-15_layoutstack.png "0404 15_LayoutStack")<br />16 x 16 のアイコンのレイアウト スタック
  
 状態通知の要素は、スタンドアロンのアイコンとして使用されています。 ただしを通知する必要がありますまとめられ、基本要素などのアイコンがタスクの完了コンテキストがあります。  
  
 ![Visual Studio でのスタンドアロン通知](../../extensibility/ux-guidelines/media/0404-16_standalonenotificationicons.png "0404 16_StandaloneNotificationIcons")<br />スタンドアロンの通知アイコン
  
 ![タスクの完了 アイコン](../../extensibility/ux-guidelines/media/0404-17_taskcomplete.png "0404 17_TaskComplete")<br />タスクの完了 アイコン
  
 プロジェクト アイコンは、通常、複数のサイズを含む .ico ファイルです。 ほとんどの 16 x 16 のアイコンでは、同じ要素が存在します。 32 x 32 のバージョンでは、詳細については、該当する場合、プロジェクトの種類を含むがあります。  
  
 ![Visual Studio でのアイコンをプロジェクト](../../extensibility/ux-guidelines/media/0404-18_iconprojectthreesizes.png "0404 18_IconProjectThreeSizes")<br />16 x 16、32 x 32 の VB Windows コントロール ライブラリ プロジェクト アイコン 
  
 ピクセル フレーム内のアイコンを中心にします。 可能でない場合、アイコン、ページのトップへ、またはフレームの右に揃えます。  
  
 ![ピクセル フレーム内で中央揃えアイコン](../../extensibility/ux-guidelines/media/0404-19_iconcentered.png "0404 19_IconCentered")<br />ピクセル フレーム内に中央揃えで配置されたアイコン
  
 ![配置されたアイコン ピクセル フレームの右の上位](../../extensibility/ux-guidelines/media/0404-20_icontopright.png "0404 20_IconTopRight")<br />一番上に配置されたアイコン、フレームの右
  
 ![アイコンが中央に配置し、ピクセル フレームの上部に揃えます](../../extensibility/ux-guidelines/media/0404-21_icontopalign.png "0404 21_IconTopAlign")<br />中央に配置され、フレームの上部に配置されたアイコン
  
 理想的なアラインメントと分散を実現するためにアクション グリフでアイコンの基本要素の障害を回避します。 基本要素の上部にある、グリフが左を置きます。 その他の要素を追加する場合は、アラインメントとアイコンの分散を検討してください。  
  
|||  
|-|-|  
|**適切なアラインメントと残高**|**配置が正しくないと残高**|  
|![アイコンの分散と配置を修正](../../extensibility/ux-guidelines/media/0404-22_alignbalancecorrect.png "0404 22_AlignBalanceCorrect")|![正しくないアイコンの分散と配置](../../extensibility/ux-guidelines/media/0404-23_alignbalanceincorrect.png "0404 23_AlignBalanceIncorrect")|  
  
 要素を共有し、セットで使用されるアイコンのサイズのパリティを確認します。 正しくない組み合わせで、円と矢印はサイズ超過に注意してくださいし、一致しません。  
  
|||  
|-|-|  
|**適切なサイズのパリティ**|**サイズが正しくパリティ**|  
|![アイコンのサイズとパリティ修正](../../extensibility/ux-guidelines/media/0404-24_sizeparitycorrect.png "0404 24_SizeParityCorrect")|![正しくないアイコンのサイズとパリティ](../../extensibility/ux-guidelines/media/0404-25_sizeparityincorrect.png "0404 25_SizeParityIncorrect")|  
  
 一貫性のある行とビジュアルの重みを使用します。 その他のアイコンをサイド バイ サイドの比較を使用して構築するアイコンの比較を評価します。 使用して、全体の 16 x 16 フレームが 15 x 15、または小さい方を使用しないでください。 負の値に正 (濃い光) 比率を 50/50 にする必要があります。  
  
|||  
|-|-|  
|**正しい負の値が正数比**|**正しくない負の値に正の値の比率**|  
|![アイコンの視覚的なウェイトを修正&#40;1&#41;](../../extensibility/ux-guidelines/media/0404-26_visualweightcorrect1.png "0404 26_VisualWeightCorrect1")<br /><br /> ![アイコンの視覚的なウェイトを修正&#40;2&#41;](../../extensibility/ux-guidelines/media/0404-27_visualweightcorrect2.png "0404 27_VisualWeightCorrect2")<br /><br /> ![アイコンの視覚的なウェイトを修正&#40;3&#41;](../../extensibility/ux-guidelines/media/0404-28_visualweightcorrect3.png "0404 28_VisualWeightCorrect3")|![アイコンの正しくない視覚的なウェイト](../../extensibility/ux-guidelines/media/0404-29_visualweightincorrect.png "0404 29_VisualWeightIncorrect")|  
  
 シンプルで同等の図形と補色角度を使用すると、要素の整合性を損なうことがなく、要素を構築できます。 可能な場合は、45 度または 90 度の角度を使用します。  
  
 ![アイコンの角度を修正](../../extensibility/ux-guidelines/media/0404-30_iconanglescorrect.png "0404 30_IconAnglesCorrect")  
  
#### <a name="perspective"></a>透視投影  
 明確でわかりやすいアイコンを保持します。 パースペクティブと光源必要な場合にのみ使用します。 パースペクティブを使用するアイコンの要素では避ける必要があります、いくつかの要素はなしで認識されていません。 このような場合は、定型パースペクティブは、要素のわかりやすくするためを通信します。  
  
 ![3 点透視投影](../../extensibility/ux-guidelines/media/0404-31_3pointperspective.png "0404 31_3PointPerspective")<br />3 点透視投影
  
 ![1 点透視投影](../../extensibility/ux-guidelines/media/0404-32_1pointperspective.png "0404 32_1PointPerspective")<br />1 点透視投影
  
 ほとんどの要素は、接続する必要があります。 または右に傾いた。  
  
 ![アイコンを右に傾いた](../../extensibility/ux-guidelines/media/0404-33_angledright.png "0404 33_AngledRight")  
  
 オブジェクトに必要なわかりやすくするためを追加する場合にのみ、光源を使用します。  
  
|||  
|-|-|  
|**正しい光源**|**正しくない光源**|  
|![アイコンの光源の解決](../../extensibility/ux-guidelines/media/0404-34_lightsourcescorrect.png "0404 34_LightSourcesCorrect")|![アイコンの正しくない光源](../../extensibility/ux-guidelines/media/0404-35_lightsourcesincorrect.png "0404 35_LightSourcesIncorrect")|  
  
 アウトラインを使用して、読みやすさを向上させる場合にのみ、または、比喩をより適切に伝達します。 負の値で、正 (濃い光) 残高を 50/50 にする必要があります。  
  
|||  
|-|-|  
|**アウトラインの正しい使用方法**|**アウトラインの不適切な使用**|  
|![アウトラインを修正](../../extensibility/ux-guidelines/media/0404-36_outlinescorrect.png "0404 36_OutlinesCorrect")|![正しくないアウトライン](../../extensibility/ux-guidelines/media/0404-37_outlinesincorrect.png "0404 37_OutlinesIncorrect")|  
  
#### <a name="icon-types"></a>アイコンの種類  
 **シェルおよびコマンド バー**個のうち 3 つ次の要素で構成されているアイコン: 基数が 1 つ、修飾子を 1 つ、1 つのアクション、または 1 つの状態。  
  
 ![シェルおよびコマンド バーのアイコンの例として](../../extensibility/ux-guidelines/media/0404-38_shellicons.png "0404 38_ShellIcons")<br />シェルとコマンド バーのアイコンの例
  
 **ツール ウィンドウ コマンド バー**個のうち 3 つ次の要素で構成されているアイコン: 基数が 1 つ、修飾子を 1 つ、1 つのアクション、または 1 つの状態。  
  
 ![ツール ウィンドウの例のコマンド バーのアイコン](../../extensibility/ux-guidelines/media/0404-39_toolwindowcommandbaricons.png "0404 39_ToolWindowCommandBarIcons")<br />ツール ウィンドウ コマンド バーのアイコンの例
  
 **ツリー ビューの曖昧性解消子**個のうち 3 つ次の要素で構成されているアイコン: 基数が 1 つ、修飾子を 1 つ、1 つのアクション、または 1 つの状態。  
  
 ![ツリーの例については曖昧性解消子のアイコンを表示する](../../extensibility/ux-guidelines/media/0404-40_treeviewicons.png "0404 40_TreeViewIcons")<br />ビューの曖昧性解消子のアイコンをツリーの例
  
 **値の状態に基づく分類**アイコンは、次の状態で存在: アクティブ、無効になっている、アクティブおよび非アクティブな無効になっています。  
  
 ![値の状態に基づく分類アイコンの例](../../extensibility/ux-guidelines/media/0404-41_statebasedtaxonomy.png "0404 41_StateBasedTaxonomy")<br />値の状態に基づく分類アイコンの例
  
 **IntelliSense**個のうち 3 つ次の要素で構成されているアイコン: 基数が 1 つ、修飾子を 1 つ、および 1 つの状態。  
  
 ![IntelliSense アイコンの例](../../extensibility/ux-guidelines/media/0404-42_intellisenseicons.png "0404 42_IntelliSenseIcons")<br />IntelliSense アイコンの例
  
 **小規模な (16 x 16) プロジェクト**アイコンには 2 つの要素を持つ必要があります。 1 つのベースと修飾子を 1 つです。  
  
 ![小 (16 x 16) の例はプロジェクト アイコン](../../extensibility/ux-guidelines/media/0404-43_16x16project1.png "0404 43_16x16Project1") ![16 x 16 プロジェクト アイコン&#40;2&#41;](../../extensibility/ux-guidelines/media/0404-44_16x16project2.png "0404 44_16x16Project2") ![16 x 16 プロジェクト アイコン&#40;3&#41;](../../extensibility/ux-guidelines/media/0404-45_16x16project3.png "0404 45_16x16Project3")<br />小規模 (16 x 16 プロジェクト アイコンの例
  
 **大規模な (32 x 32) プロジェクト**アイコンは、次の要素の 4 個ので構成されています: 基数が 1 つ、1 ~ 2 修飾子、および 1 つの言語をオーバーレイします。  
  
 ![大規模な (32 x 32) の例はプロジェクト アイコン](../../extensibility/ux-guidelines/media/0404-46_32x32project.png "0404 46_32x32Project")<br />大規模な (32 x 32) プロジェクト アイコンの例
  
### <a name="production-details"></a>運用環境の詳細  
 Windows Presentation Foundation (WPF) を使用してすべての新しい UI 要素を作成する必要があり、WPF のすべての新しいアイコンが 32 ビット PNG 形式でなければなりません。 24 ビット PNG は、レガシ形式の透過性をサポートしていませんし、そのため、アイコンの推奨されません。  
  
 96 DPI での解決を保存します。  
  
#### <a name="file-types"></a>ファイルの種類  
  
-   **32 ビット PNG:**アイコンの優先形式です。 (ピクセル) の単一のラスター イメージを格納できるロスレス データの圧縮ファイル形式。 32 ビットの PNG ファイルは、アルファ チャネルの透過性、ガンマ補正とインター レースをサポートします。  
  
-   **32 ビット BMP:**非 WPF コントロールのです。 呼ばれます XP、high color、32 ビット BMP は、RGB、イメージ形式、アルファ チャネルの透過性で true カラー イメージです。 アルファ チャネル レイヤーの透明度の追加 (4) として、ビットマップ内で保存するには Adobe Photoshop で指定されているはカラー チャネル。 黒の背景色深度に関するクイック視覚上の手掛かりを提供するすべての 32 ビット BMP ファイルへのアートワーク実稼動中に追加されます。 この黒の背景色は、ui をマスクする領域を表します。  
  
-   **32 ビット ICO:**のプロジェクト アイコンと項目の追加。 すべての ICO ファイルは、32 ビットの場合は true。 カラー透過性のアルファ チャネル (RGB/A)。 ICO ファイルは、複数のサイズと色深度を格納するため Vista アイコンは 16 x 16、32 x 32、48 x 48、および 256 x 256 イメージのサイズを含む ICO 形式で多くの場合です。 Windows エクスプ ローラーで適切に表示するために ICO ファイル必要がある保存ダウン イメージ サイズごとに 24 ビットと 8 ビット色深度をします。  
  
-   **XAML:**デザイン サーフェイスと Windows 装飾します。 XAML のアイコンは、拡大/縮小、回転、書類、および透明度をサポートするベクター ベースのイメージ ファイルです。 これらは、本日 Visual Studio では一般的ではありませんが、柔軟性のため普及しつつあります。  
  
-   **SVG**  
  
-   **24 ビット BMP:** Visual Studio のコマンド バーのです。 True 色の RGB イメージ形式、24 ビット BMP は、アウト透過性レイヤーの色キーとしてマゼンタ (R = 255, G = 0, B = 255) を使用してレイヤーの透明度を作成したアイコン規約です。 24 ビット BMP、背景色を使用してすべてマゼンタ画面が表示されます。  
  
-   **24 ビット GIF:** Visual Studio のコマンド バーのです。 透過性をサポートする true 色の RGB イメージ形式。 GIF ファイルは、ウィザードのアートワークおよび GIF アニメーションでよく使用されます。  
  
### <a name="icon-construction"></a>アイコンの構築  
 Visual Studio で最も小さいアイコンのサイズは、16 x 16 です。 最大共通の使用は 32 x 32 です。 アイコンをデザインするとき、全体の 16 x 16、24 x 24、または 32 x 32 のフレームがいっぱいにないことに注意してください。 読みやすい、一貫したアイコン コンストラクションは、ユーザーの認識に不可欠です。 アイコンを構築するときに、次の点に準拠します。  
  
-   アイコンは、クリア、理解できるもの、および一貫性にする必要があります。  
  
-   状態通知の要素を 1 つのアイコンとして使用してアイコンの基本要素の上に重ねることにしないことをお勧めします。 特定のコンテキストで、UI は、基本要素と組で使用する状態要素を必要があります。  
  
-   プロジェクト アイコンは、通常、.ico ファイルをいくつかのサイズを含むです。 16 x 16、24 x 24、および 32 x 32 アイコンのみを更新しています。 ほとんどの 16 x 16、24 x 24 アイコンは、同じ要素が含まれます。 32 x 32 のアイコンを含む詳細については、該当する場合は、プロジェクトの言語の種類を含むです。  
  
-   32 x 32 アイコンの基本要素は、2 ピクセル線の太さを一般にあります。 詳細要素を 1 または 2 ピクセル線の太さを使用できます。 特定するには適切な判断を使用します。  
  
-   16 x 16 の要素と 24 x 24 アイコンの間には、少なくとも 1 ピクセルのスペースがあります。 32 x 32 のアイコン、2 ピクセル間隔要素間および修飾子と基本要素を使用します。  
  
 ![16 x 16、24 x 24、および 32 x 32 アイコンのサイズの要素間のスペース](../../extensibility/ux-guidelines/media/0404-47_elementspacing.png "0404 47_ElementSpacing")<br />16 x 16、24 x 24、および 32 x 32 アイコンの要素間スペースのサイズ
  
#### <a name="color-and-accessibility"></a>色とアクセシビリティ  
 Visual Studio のコンプライアンス ガイドラインは、製品内のすべてのアイコンが色とコントラストのアクセシビリティの要件を満たしている必要があります。 これは、アイコンの逆転によって実現しをデザインするときに注意してください、製品にプログラムで反転されます。  
  
 Visual Studio のアイコンの色を使用する方法については、次を参照してください。[画像の色を使用して](../../extensibility/ux-guidelines/images-and-icons-for-visual-studio.md#BKMK_UsingColorInImages)です。  
  
##  <a name="BKMK_UsingColorInImages"></a> 画像の色を使用します。  
  
### <a name="overview"></a>概要  
 Visual Studio でのアイコンは、主にモノクロです。 色は特定の情報を伝えるために予約されていて、の装飾のことはありません。 色を使用します。  
  
-   アクションを示すために  
  
-   状態の通知をユーザーに警告するには  
  
-   言語への関連付けを指定するには  
  
-   IntelliSense 内のアイテムを区別するために  
  
### <a name="accessibility"></a>ユーザー補助  
 Visual Studio のコンプライアンス ガイドラインは、製品のパスにチェックインされたすべてのアイコンが、色とコントラストのアクセシビリティの要件を使用することが必要です。 ビジュアルな言語パレットの色がテストされ、これらの要件を満たしています。  
  
#### <a name="color-inversion-for-dark-themes"></a>ダーク テーマの色の反転  
 アイコンの正しいコントラスト比が Visual Studio ダーク テーマでの表示を行うためには、反転がプログラムで適用されます。 正しく反転するようにこのガイドの色が部分的に選択されています。 このパレットに色の使用が制限されるか、反転が適用されるときに予期しない結果が得られます。  
  
 ![逆に、それぞれの色を持っているアイコンの例](../../extensibility/ux-guidelines/media/0405-01_darkthemeinversion.png "0405 01_DarkThemeInversion")<br />逆に、それぞれの色を持っているアイコンの例
  
### <a name="base-palette"></a>基本パレット  
 すべての標準的なアイコンには、3 つの基本色が含まれています。 アイコンは、グラデーションを含んでいないか、ドロップ シャドウ、3 D ツール アイコンの 1 つまたは 2 つの例外を許可します。  
  
|使用法|name|値 (明るいテーマ)|見本|例|  
|-----------|----------|---------------------------|------------|-------------|  
|バック グラウンド/ダークグレー|VS BG|424242 / 66,66,66|![見本 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|![基本パレットの例](../../extensibility/ux-guidelines/media/0405-02_basepaletteexample.png "0405 02_BasePaletteExample")|  
|フォア グラウンド/低負荷|VS FG|F0EFF1 240,239,241/|![Swatch F0EFF1](../../extensibility/ux-guidelines/media/0405_f0eff1.png "0405_F0EFF1")||  
|アウトライン|VS アウト|F6F6F6 / 246,246,246|![Swatch F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")||  
  
 基本の色に加えて、各アイコンは拡張パレットから 1 つの追加の配色を含めることです。  
  
### <a name="extended-palette"></a>拡張パレット  
  
#### <a name="action-modifiers"></a>操作の修飾子  
 次の 4 つの色は、操作の修飾子で必要なアクションの種類を示します。  
  
|使用法|name|値 (すべてのテーマ)|見本|  
|-----------|----------|--------------------------|------------|  
|正|VS アクション緑|388A34 56,138,52/|![見本 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|  
|負|VS アクション赤|A1260D 161,38,13/|![見本 A1260D](../../extensibility/ux-guidelines/media/0405_a1260d.png "0405_A1260D")|  
|ニュートラル|VS アクション青|00539C / 0,83,156|![Swatch 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|  
|/新規作成|VS アクション オレンジ色|C27D1A / 194,156,26|![見本c27d1a](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|  
  
##### <a name="examples"></a>使用例  
 緑を「追加」のような正の値の操作の修飾子の使用が「実行」"、"と「検証します」。  
  
|||||  
|-|-|-|-|  
|![実行アイコン](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405 03_ActionModifierRun")<br />実行|![[クエリ] アイコンを実行](../../extensibility/ux-guidelines/media/0405-04_executequery.png "0405 04_ExecuteQuery")<br />クエリを実行します。|![すべての手順のアイコンを再生](../../extensibility/ux-guidelines/media/0405-05_playallsteps.png "0405 05_PlayAllSteps")<br />すべてのステップを再生します。|![コントロール アイコンを追加](../../extensibility/ux-guidelines/media/0405-06_addcontrol.png "0405 06_AddControl")<br />コントロールを追加します。|  
  
 赤の場合は負の値の操作の修飾子「の削除、」「停止」と同じようにため「キャンセル」と「閉じる」。  
  
|||||  
|-|-|-|-|  
|![リレーションシップのアイコンを削除](../../extensibility/ux-guidelines/media/0405-07_deleterelationship.png "0405 07_DeleteRelationship")<br />リレーションシップを削除します。|![[列] アイコンを削除](../../extensibility/ux-guidelines/media/0405-08_deletecolumn.png "0405 08_DeleteColumn")<br />列の削除|![停止クエリ アイコン](../../extensibility/ux-guidelines/media/0405-09_stopquery.png "0405 09_StopQuery")<br />クエリを停止します。|![接続 [オフライン] アイコン](../../extensibility/ux-guidelines/media/0405-10_connectionoffline.png "0405 10_ConnectionOffline")<br />オフラインの接続|  
  
 青は修飾子を最もよく「開くには、」「次に、」"Previous、"と同じように、矢印として表されます「インポート」、「エクスポート」ニュートラル アクションに適用します。  
  
|||||  
|-|-|-|-|  
|![フィールドのアイコンに移動して](../../extensibility/ux-guidelines/media/0405-11_gotofield.png "0405 11_GoToField")<br />フィールドに移動します。|![確認をバッチ処理&#45;アイコン](../../extensibility/ux-guidelines/media/0405-12_batchedcheckin.png "0405 12_BatchedCheckIn")<br />バッチ処理されたチェックイン|![[アドレス エディター] アイコン](../../extensibility/ux-guidelines/media/0405-13_addresseditor.png "0405 13_AddressEditor")<br />アドレス エディター|![[関連付けエディター] アイコン](../../extensibility/ux-guidelines/media/0405-14_associationeditor.png "0405 14_AssociationEditor")<br />関連付けエディター|  
  
 濃い gold は「新規」修飾子は、主に使用されます。  
  
|||||  
|-|-|-|-|  
|![New project icon](../../extensibility/ux-guidelines/media/0405-15_newproject.png "0405-15_NewProject")<br />新しいプロジェクト|![[新しいグラフ] アイコンを作成する](../../extensibility/ux-guidelines/media/0405-16_createnewgraph.png "0405 16_CreateNewGraph")<br />新しいグラフを作成します。|![新しい単体テスト アイコン](../../extensibility/ux-guidelines/media/0405-17_newunittest.png "0405 17_NewUnitTest")<br />新しい単体テスト|![新しいリスト項目のアイコン](../../extensibility/ux-guidelines/media/0405-18_newlistitem.png "0405 18_NewListItem")<br />新しいリスト アイテム|  
  
#### <a name="special-cases"></a>特殊なケース  
 特殊な場合は、色分けされたアクション修飾子可能性があります単独で使用スタンドアロン アイコンとして。 アイコンに使用される色は、アイコンが関連付けられているアクションを反映します。 この使用も含め、アイコンの小さなサブセットに制限されています。  
  
||||||  
|-|-|-|-|-|  
|![実行アイコン](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405 03_ActionModifierRun")<br />実行|![停止アイコン](../../extensibility/ux-guidelines/media/0405-19_stop.png "0405 19_Stop")<br />停止|![削除アイコン](../../extensibility/ux-guidelines/media/0405-20_delete.png "0405 20_Delete")<br />削除|![[保存] アイコン](../../extensibility/ux-guidelines/media/0405-21_save.png "0405 21_Save")<br />保存|![戻る アイコンを移動](../../extensibility/ux-guidelines/media/0405-22_navigateback.png "0405 22_NavigateBack")<br />前に移動します。|  
  
### <a name="code-hierarchy-palette"></a>コード階層パレット  
  
#### <a name="folder"></a>フォルダー  
  
|使用法|name|値 (すべてのテーマ)|見本|例|  
|-----------|----------|--------------------------|------------|-------------|  
|フォルダー|フォルダー|DCB67A / 220,182,122|![見本 DCB67A](../../extensibility/ux-guidelines/media/0405_dcb67a.png "0405_DCB67A")|![フォルダーの色のアイコン](../../extensibility/ux-guidelines/media/0405-23_foldercolor.png "0405 23_FolderColor")|  
  
#### <a name="visual-studio-languages"></a>Visual Studio の言語  
 一般的な言語または Visual Studio で使用可能なプラットフォームには、関連付けられている色があります。 [基本] アイコンまたは複合アイコンの右上隅に表示される言語修飾子で、これらの色が使用されます。  
  
|使用法|name|値 (すべてのテーマ)|見本|  
|-----------|----------|--------------------------|------------|  
|ASP では、HTML、WPF|ASP HTML WPF 青|0095D7 / 0,149,215|![Swatch 0095D7](../../extensibility/ux-guidelines/media/0405_0096d7.png "0405_0096D7")|  
|C++|CPP 紫|9B4F96 / 155,79,150|![Swatch 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|  
|C#|CS 緑 (VS アクション緑)|388A34 56,138,52/|![見本 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|  
|CSS|CSS 赤|BD1E2D 189,30,45/|![Swatch BD1E2D](../../extensibility/ux-guidelines/media/0405_bd1e2d.png "0405_BD1E2D")|  
|F#|FS 紫|672878 / 103,40,120|![見本 672878](../../extensibility/ux-guidelines/media/0405_672878.png "0405_672878")|  
|JavaScript|JS オレンジ色|F 16421 241,100,33/|![見本 f 16421](../../extensibility/ux-guidelines/media/0405_f16421.png "0405_F16421")|  
|VB|VB 青 (VS アクション青)|00539C / 0,83,156|![Swatch 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|  
|TypeScript|TS オレンジ色|E04C06 224,76,6/|![見本e04c06](../../extensibility/ux-guidelines/media/0405_e04c06.png "0405_E04C06")|  
|Python|PY 緑|879636 / 135,150,54|![Swatch 879636](../../extensibility/ux-guidelines/media/0405_879636.png "0405_879636")|  
  
##### <a name="examples-of-icons-with-language-modifiers"></a>Language 修飾子のアイコンの例  
  
|||||||  
|-|-|-|-|-|-|  
|![Visual Basic アイコン](../../extensibility/ux-guidelines/media/0405-25_vb.png "0405 25_VB")<br />VB|![C&#35;アイコン](../../extensibility/ux-guidelines/media/0405-26_csharp.png "0405 26_CSharp")<br />C#|![C&#43; &#43;アイコン](../../extensibility/ux-guidelines/media/0405-27_cplusplus.png "0405 27_CPlusPlus")<br />C++|![F&#35;アイコン](../../extensibility/ux-guidelines/media/0405-28_fsharp.png "0405 28_FSharp")<br />F#|![JavaScript アイコン](../../extensibility/ux-guidelines/media/0405-29_javascript.png "0405 29_JavaScript")<br />JavaScript|![Python アイコン](../../extensibility/ux-guidelines/media/0405-30_python.png "0405 30_Python")<br />Python|  
|![HTML アイコン](../../extensibility/ux-guidelines/media/0405-31_html.png "0405 31_HTML")<br />HTML|![WPF アイコン](../../extensibility/ux-guidelines/media/0405-32_wpf.png "0405 32_WPF")<br />WPF|![ASP icon](../../extensibility/ux-guidelines/media/0405-33_asp.png "0405-33_ASP")<br />ASP|![CSS アイコン](../../extensibility/ux-guidelines/media/0405-34_css.png "0405 34_CSS")<br />CSS|![TypeScript アイコン](../../extensibility/ux-guidelines/media/0405-35_typescript.png "0405 35_TypeScript")<br />TypeScript||  
  
#### <a name="intellisense"></a>IntelliSense  
 IntelliSense アイコンは、排他的なカラー パレットを使用します。 これらの色は、IntelliSense のポップアップ リスト内の別の項目の間で簡単に見分けるやすくために使用されます。  
  
|使用法|name|値 (すべてのテーマ)|見本|  
|-----------|----------|--------------------------|------------|  
|イベント クラス|VS アクション オレンジ色|C27D1A / 194,125,26|![見本c27d1a](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|  
|拡張メソッド、メソッド、モジュール、デリゲート|VS アクション紫|652D90 / 101,45,144|![見本 652d90](../../extensibility/ux-guidelines/media/0405_652d90.png "0405_652D90")|  
|インターフェイスのフィールド、列挙型項目、マクロ、構造体、共用体の値の型、演算子、|VS アクション青|00539C / 0,83,156|![Swatch 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|  
|Object|VS アクション緑|388A34 56,138,52/|![見本 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|  
|定数、例外、列挙型項目、マップ、マップ項目、Namespace、テンプレート、種類の定義|バック グラウンド (VS BG)|424242 / 66,66,66|![見本 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|  
  
##### <a name="examples-of-intellisense-icons"></a>IntelliSense アイコンの例  
  
||||||  
|-|-|-|-|-|  
|![IntelliSense クラスのアイコン](../../extensibility/ux-guidelines/media/0405-36_intellisenseclass.png "0405 36_IntelliSenseClass")<br />クラス|![IntelliSense プライベート イベント アイコン](../../extensibility/ux-guidelines/media/0405-37_intellisenseprivateevent.png "0405 37_IntelliSensePrivateEvent")<br />プライベート イベント|![IntelliSense デリゲートのアイコン](../../extensibility/ux-guidelines/media/0405-38_intellisensedelegate.png "0405 38_IntelliSenseDelegate")<br />Delegate|![IntelliSense メソッド フレンドのアイコン](../../extensibility/ux-guidelines/media/0405-39_intellisensemethodfriend.png "0405 39_IntelliSenseMethodFriend")<br />メソッドのフレンド|![フィールド アイコン](../../extensibility/ux-guidelines/media/0405-40_field.png "0405 40_Field")<br />フィールド|  
|![IntelliSense には、列挙型項目のアイコンが保護されている](../../extensibility/ux-guidelines/media/0405-41_intellisenseprotectedenumitem.png "0405 41_IntelliSenseProtectedEnumItem")<br />保護された列挙型項目|![IntelliSense オブジェクト アイコン](../../extensibility/ux-guidelines/media/0405-42_intellisenseobject.png "0405 42_IntelliSenseObject")<br />Object|![IntelliSense テンプレートのアイコン](../../extensibility/ux-guidelines/media/0405-43_intellisensetemplate.png "0405 43_IntelliSenseTemplate")<br />テンプレート|![IntelliSense の例外のショートカット アイコン](../../extensibility/ux-guidelines/media/0405-44_intellisenseexceptionshortcut.png "0405 44_IntelliSenseExceptionShortcut")<br />例外のショートカット||  
  
### <a name="notifications"></a>通知  
 Visual Studio での通知は、ステータスを示すために使用されます。 通知パレットは、次の 4 つの色と黒と白の前景の塗りつぶしのオプションを使用して、次の状態レベルでの通知を定義します。  
  
|使用法|name|値 (すべてのテーマ)|見本|  
|-----------|----------|--------------------------|------------|  
|状態: ニュートラル|通知の青 (VS 青)|1BA1E2 / 27,161,226|![見本 1BA1E2](../../extensibility/ux-guidelines/media/0405_1ba1e2.png "0405_1BA1E2")|  
|状態: 正の値|通知の緑 (VS 緑)|339933 / 51,153,51|![見本 339933](../../extensibility/ux-guidelines/media/0405_339933.png "0405_339933")|  
|状態: 負の値|通知の赤 (VS 赤)|E 51400 229,20,0/|![Swatch E51400](../../extensibility/ux-guidelines/media/0405_e51400.png "0405_E51400")|  
|状態: 警告|通知黄色 (VS オレンジ色)|FFCC00 255,204,0/|![見本 FFCC00](../../extensibility/ux-guidelines/media/0405_ffcc00.png "0405_FFCC00")|  
|前景の塗りつぶし|通知黒 (黒)|000000 / 0,0,0|![見本&#35;000000](../../extensibility/ux-guidelines/media/0405_000000.png "0405_000000")|  
|前景の塗りつぶし|通知の空白 (空白)|FFFFFF / 255,255,255|![Swatch FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
  
#### <a name="examples-of-notification-icons"></a>通知アイコンの例  
  
|||||  
|-|-|-|-|  
|![警告アイコン](../../extensibility/ux-guidelines/media/0405-45_alert.png "0405 45_Alert")<br />警告|![警告アイコン](../../extensibility/ux-guidelines/media/0405-48_warning.png "0405 48_Warning")<br />警告|![[完了] アイコン](../../extensibility/ux-guidelines/media/0405-46_complete.png "0405 46_Complete")<br />完了|![停止アイコン](../../extensibility/ux-guidelines/media/0405-47_stop.png "0405 47_Stop")<br />停止|  
  
### <a name="visual-studio-online"></a>Visual Studio Online  
 一般に、Visual Studio Online の機能で構成ブラウザーでホストします。 色は、さまざまな環境で異なりますが、スタイルは変わりません。  
  
|グループ化|使用法|name|値 (すべてのテーマ)|見本|  
|-----------|-----------|----------|--------------------------|------------|  
|TFS|背景|TFSO BG|656565/ 101, 101, 101|![Swatch 656565](../../extensibility/ux-guidelines/media/0405_656565.png "0405_656565")|  
|TFS|アウトライン|TFSO OUT|FFFFFF/255, 255, 255|![Swatch FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|Napa|背景|白|FFFFFF/255, 255, 255|![Swatch FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|モナコ|背景|白|FFFFFF/255, 255, 255|![Swatch FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|F12|背景|白|FFFFFF/255, 255, 255|![Swatch FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|F12|標準|F12 Grey_Primary|555555 / 85, 85, 85|![Swatch 555555](../../extensibility/ux-guidelines/media/0405_555555.png "0405_555555")|  
|F12|ホバー|F12 Blue_Hover|2279BF / 34,121,191|![Swatch 2279BF](../../extensibility/ux-guidelines/media/0405_2279bf.png "0405_2279BF")|  
|F12|無効|F12 LtGrey_Disabled|ABABAC / 171,171,172|![見本 ABABAC](../../extensibility/ux-guidelines/media/0405_ababac.png "0405_ABABAC")|  
|F12|ホバー時の背景|Bg のマウス ポインターを移動します。|D9EBF7 / 217,235,247|![Swatch D9EBF7](../../extensibility/ux-guidelines/media/0405_d9ebf7.png "0405_D9EBF7")|  
|F12|押されているバック グラウンド|押された bg|B2D7F0 178,215,240/|![見本b2d7f0](../../extensibility/ux-guidelines/media/0405_b2d7f0.png "0405_B2D7F0")|  
|F12|アウトライン|VS OUT|F6F6F6 / 246,246,246|![Swatch F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")|  
|F12|情報|情報|00BCF2 / 0,188,242|![Swatch 00BCF2](../../extensibility/ux-guidelines/media/0405_00bcf2.png "0405_00BCF2")|  
|F12|警告|警告|F28300 / 242,131,0|![見本 f 28300](../../extensibility/ux-guidelines/media/0405_f28300.png "0405_F28300")|  
|F12|エラー/負の値|Error_Negative|E 81123 232,17,35/|![Swatch E81123](../../extensibility/ux-guidelines/media/0405_e81123.png "0405_E81123")|  
|F12|開始/正の値|Start_Positive|009E49 / 0,158,73|![Swatch 009E49](../../extensibility/ux-guidelines/media/0405_009e49.png "0405_009E49")|  
|F12|中断の種類|中断の種類|9B4F96 / 155,79,150|![Swatch 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|  
|F12|イベントのマーク|イベントのマーク|A51F00 165,31,0/|![見本 A51F00](../../extensibility/ux-guidelines/media/0405_a51f00.png "0405_A51F00")|  
|F12|ユーザー マーク|ユーザー マーク|F 16220 241,98,32/|![見本 f 16220](../../extensibility/ux-guidelines/media/0405_f16220.png "0405_F16220")|  
  
#### <a name="examples-of-visual-studio-online-icons"></a>Visual Studio Online のアイコンの例  
  
|TFS オンライン||||  
|----------------|-|-|-|  
|![TFS オンライン チームのアイコン](../../extensibility/ux-guidelines/media/0405-49_tfsonlineteam.png "0405 49_TFSOnlineTeam")<br />オンラインのチーム|![TFS 情報アイコン](../../extensibility/ux-guidelines/media/0405-50_tfsinformation.png "0405 50_TFSInformation")<br />情報|![TFS history icon](../../extensibility/ux-guidelines/media/0405-51_tfshistory.png "0405-51_TFSHistory")<br />履歴|![TFS 分岐アイコン](../../extensibility/ux-guidelines/media/0405-52_tfsbranch.png "0405 52_TFSBranch")<br />分岐|  
  
|Napa||||  
|----------|-|-|-|  
|![Napa コンテンツ アイコン](../../extensibility/ux-guidelines/media/0405-53_napacontent.png "0405 53_NapaContent")<br />Content|![Napa office メール アイコン](../../extensibility/ux-guidelines/media/0405-54_napaofficemail.png "0405 54_NapaOfficeMail")<br />Office メール|![Napa SharePoint アイコン](../../extensibility/ux-guidelines/media/0405-55_napasharepoint.png "0405 55_NapaSharePoint")<br />SharePoint|![Napa タスク ペイン アイコン](../../extensibility/ux-guidelines/media/0405-56_napataskpane.png "0405 56_NapaTaskPane")<br />作業ウィンドウ|  
  
|モナコ||||  
|------------|-|-|-|  
|![モナコ ファイル アイコン](../../extensibility/ux-guidelines/media/0405-57_monacofiles.png "0405 57_MonacoFiles")<br />ファイル|![モナコ Git アイコン](../../extensibility/ux-guidelines/media/0405-58_monacogit.png "0405 58_MonacoGit")<br />Git|![モナコの検索アイコン](../../extensibility/ux-guidelines/media/0405-59_monacosearch.png "0405 59_MonacoSearch")<br />検索|![モナコのテキスト アイコン](../../extensibility/ux-guidelines/media/0405-60_monacotext.png "0405 60_MonacoText")<br />テキスト|  
  
|F12|||  
|---------|-|-|  
|![F12 再フォーマット コード アイコン](../../extensibility/ux-guidelines/media/0405-61_f12prettycode.png "0405 61_F12PrettyCode")<br />再フォーマット コード|![F12 警告アイコン](../../extensibility/ux-guidelines/media/0405-62_f12warning.png "0405 62_F12Warning")<br />警告|![F12 エミュレート アイコン](../../extensibility/ux-guidelines/media/0405-63_f12emulate.png "0405 63_F12Emulate")<br />エミュレート|