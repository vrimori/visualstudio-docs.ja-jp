---
title: "同時実行ビジュアライザー SDK | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.sdk.about"
ms.assetid: 4b22cdf9-59b1-4c88-a6d8-1644a4a11e08
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 同時実行ビジュアライザー SDK
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

同時実行ビジュアライザーの追加情報を表示するために、同時実行ビジュアライザー SDK を使用して、ソース・コードをインストルメントできます。  フェーズと追加コードやデータのイベントを関連付けることができます。  これらの追加の視覚化、*マーカー*と呼ばれます。入門編のチュートリアルでは、参照してください [同時実行ビジュアライザー SDK の概要](http://go.microsoft.com/fwlink/?LinkId=235405)。  
  
## プロパティ  
 フラグは、範囲とメッセージにそれぞれ 2 とおりのプロパティがあります: カテゴリと重要度です。  [詳細設定](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) ダイアログ ボックスで、表示するマーカーのセットをフィルター処理するためにこれらのプロパティを使用できます。  また、これらのプロパティは、マーカーのビジュアル表現に影響します。  重要度を表すには、たとえば、フラグのサイズが使用されます。  さらにカテゴリを示すために、色が使用されます。  
  
## 基本的な使用法  
 同時実行ビジュアライザーは、マーカーを生成するために使用できる既定のプロバイダーを公開します。  プロバイダーは、同時実行ビジュアライザーとともに登録され、マーカーを UI に表示されるように何も行う必要はありません。  
  
### C\# および Visual Basic  
 C\# では、Visual Basic などのマネージ コードが <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers>を呼び出すことにより、既定のプロバイダーを使用します。  これはマーカーを生成するための 4 種類の関数を公開します: <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteFlag%2A>、<xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.EnterSpan%2A>、<xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteMessage%2A>と <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteAlert%2A>。  プロパティに既定を使用するか、これらの関数に対する複数のオーバーロード\) です。最も単純なオーバーロードはイベントの説明を指定する文字列パラメーターを受け取ります。  説明は同時実行ビジュアライザー レポートに表示されます。  
  
##### C\# または Visual Basic で SDK のサポートを追加するには、  
  
1.  メニュー バーで、**\[同時実行ビジュアライザー\]**、**\[プロジェクトへの SDK の追加\]\[解析\]** をクリックします。  
  
2.  、SDK にアクセスし、**\[選択したプロジェクトに SDK を追加\]** をクリックするプロジェクトを選択します。  
  
3.  コードに Imports ステートメントまたは using ステートメントを追加します。  
  
    ```c#  
    using Microsoft.ConcurrencyVisualizer.Instrumentation;  
    ```  
  
    ```vb  
    Imports Microsoft.ConcurrencyVisualizer.Instrumentation  
    ```  
  
### C\+\+  
 C\+\+ では、[marker\_series クラス](../profiling/marker-series-class.md) オブジェクトを作成し、関数を呼び出すために使用します。`marker_series` クラスは、マーカー [marker\_series::write\_flag メソッド](../profiling/marker-series-write-flag-method.md)、[marker\_series::write\_message メソッド](../profiling/marker-series-write-message-method.md)と [marker\_series::write\_alert メソッド](../profiling/marker-series-write-alert-method.md)を生成するための 3 種類の機能を公開します。  
  
##### C \+\+.または C に SDK のサポートを追加するには、  
  
1.  メニュー バーで、**\[同時実行ビジュアライザー\]**、**\[プロジェクトへの SDK の追加\]\[解析\]** をクリックします。  
  
2.  、SDK にアクセスし、**\[選択したプロジェクトに SDK を追加\]** をクリックするプロジェクトを選択します。  
  
3.  C\+\+ では、`cvmarkersobj.h`を含めます。  C では、`cvmarkers.h`を含めます。  
  
4.  コードにステートメントを追加します。  
  
    ```  
    using namespace Concurrency::diagnostic;  
    ```  
  
5.  `marker_series` オブジェクトを作成し、`span` のコンストラクターに渡します。  
  
    ```cpp  
  
    marker_series mySeries;  
    span s(mySeries, _T("Span description"));  
  
    ```  
  
## カスタムの使用  
 高度なシナリオでは、同時実行ビジュアライザー SDK には、他のコントロールを公開します。2 種類の主要な機能は、より高度なシナリオに関連付けられています。: マーカーのプロバイダーおよびマーカーのシリーズ。  マーカーのプロバイダーは、ETW のプロバイダーです \(それぞれに異なる GUID が含まれます。  マーカーのシリーズは 1 個のプロバイダーによって生成されるイベントのシリアル チャネルです。  マーカーのプロバイダーによって生成されるイベントを整理することもできます。  
  
#### C\# または Visual Basic で新しいマーカーのプロバイダーを使用するには、  
  
1.  <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerWriter> オブジェクトを作成します。コンストラクターは、GUID を取得します。  
  
2.  プロバイダーを登録するには、同時実行ビジュアライザーを [詳細設定](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) ダイアログ ボックスを開きます。**\[マーカー\]** タブを選択し、**\[新しいプロバイダーの追加\]** ボタンをクリックします。  [詳細設定](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) ダイアログ ボックスで、プロバイダーのプロバイダーと説明を作成するために使用される GUID を入力します。  
  
#### C \+\+.または C で新しいマーカーのプロバイダーを使用するには、  
  
1.  PCV\_PROVIDER を初期化するために `CvInitProvider` 関数を使用します。コンストラクターは GUID\* と PCV\_PROVIDER\* を受け取ります。  
  
2.  プロバイダーを登録するには、[詳細設定](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) ダイアログ ボックスを開きます。**\[マーカー\]** タブを選択し、**\[新しいプロバイダーの追加\]** ボタンをクリックします。  このダイアログ ボックスでは、プロバイダーのプロバイダーと説明を作成するために使用される GUID を入力します。  
  
#### C\# または Visual Basic のマーカーのシリーズを使用するには、  
  
1.  新しい <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerSeries>を使用するには、最初に <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerWriter> オブジェクトを使用して作成し、新しいシリーズのマーカー イベントを直接生成します。  
  
    ```c#  
    MarkerSeries series1 = myMarkerWriter.CreateMarkerSeries(″Series 1″);  
    series1.WriteFlag(″My flag″);  
    ```  
  
    ```vb  
    Dim series1 As New myMarkerWriter.CreateMarkerSeries(″Series 1″)  
    series1.WriteFlag(″My flag″)  
    ```  
  
#### C\+\+ プロジェクトで.マーカーのシリーズを使用するには、  
  
1.  `marker_series` オブジェクトを作成します。この新しい一連のイベントを生成します。  
  
    ```scr  
    marker_series series;  
    series.write_flag(_T("Hello world!"));  
    ```  
  
#### C\+\+.でマーカーのシリーズを使用するには、  
  
1.  PCV\_MARKERSERIES の作成に `CvCreateMarkerSeries` 関数を使用します。  
  
    ```cpp  
    PCV_MARKERSERIES series;  
    CvCreatemarkerSeries(myProvider, _T("My Series"), &series);  
    CvWriteFlag(series, _T("Writing a flag"));  
    ```  
  
## 関連トピック  
  
|タイトル|説明|  
|----------|--------|  
|[C\+\+ ライブラリ リファレンス](../profiling/cpp-library-reference.md)|C\+\+ の同時実行ビジュアライザー API について説明します。|  
|[C ライブラリ リファレンス](../profiling/c-library-reference.md)|C.の同時実行ビジュアライザー API について説明します。|  
|<xref:Microsoft.ConcurrencyVisualizer.Instrumentation>|マネージ コードの同時実行ビジュアライザー API について説明します。|  
|[同時実行ビジュアライザー](../profiling/concurrency-visualizer.md)|同時実行方式を使用して生成され、スレッド実行データを含むプロファイル データ ファイルのビューとレポートに関するリファレンス情報。|