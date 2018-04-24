---
title: 同時実行ビジュアライザー SDK | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.sdk.about
ms.assetid: 4b22cdf9-59b1-4c88-a6d8-1644a4a11e08
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7268e786c7d68d642778f0c0dca31de170b424b4
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="concurrency-visualizer-sdk"></a>同時実行ビジュアライザー SDK
同時実行ビジュアライザー SDK を使用してソース コードをインストルメント化し、同時実行ビジュアライザーに追加情報を表示することができます。 コードでフェーズとイベントに追加データを関連付けることができます。 このような追加の視覚化機能のことを*マーカー*と呼びます。  入門用のチュートリアルについては、「[Introducing the Concurrency Visualizer SDK](http://go.microsoft.com/fwlink/?LinkId=235405)」 (同時実行ビジュアライザー SDK の概要) を参照してください。  
  
## <a name="properties"></a>プロパティ  
 フラグ、スパン、およびメッセージにはそれぞれ、カテゴリおよび重要度という 2 つのプロパティがあります。 [[詳細設定]](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) ダイアログ ボックスで、これらのプロパティを使用して、表示されるマーカーのセットをフィルター処理することができます。 また、これらのプロパティはマーカーの視覚表示に影響します。 たとえば、フラグのサイズを使用して重要度を表します。 また、色を使用してカテゴリを示します。  
  
## <a name="basic-usage"></a>基本的な使用方法  
 同時実行ビジュアライザーは、マーカーの生成に使用できる既定のプロバイダーを示します。 プロバイダーは同時実行ビジュアライザーと共に既に登録されており、UI にマーカーを表示するためにユーザー側で行う必要がある操作はありません。  
  
### <a name="c-and-visual-basic"></a>C# および Visual Basic  
 C#、Visual Basic、および他のマネージ コードでは、<xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers> を呼び出して既定のプロバイダーを使います。 マーカー生成用の 4 つの関数、<xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteFlag%2A>、<xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.EnterSpan%2A>、<xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteMessage%2A>、<xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteAlert%2A> が公開されます。 プロパティで既定を使用するかどうかに応じて、これらの関数には複数のオーバーロードがあります。  最も単純なオーバーロードは、イベントの説明を指定する文字列パラメーターのみを受け取ります。 説明は同時実行ビジュアライザーのレポートに表示されます。  
  
##### <a name="to-add-sdk-support-to-a-c-or-visual-basic-project"></a>C# または Visual Basic のプロジェクトに SDK のサポートを追加するには  
  
1.  メニュー バーで、**[分析]**、**[同時実行ビジュアライザー]**、**[プロジェクトへの SDK の追加]** の順に選択します。  
  
2.  SDK にアクセスするプロジェクトを選択し、**[選択したプロジェクトに SDK を追加]** ボタンを選択します。  
  
3.  imports ステートメントまたは using ステートメントをコードに追加します。  
  
    ```csharp  
    using Microsoft.ConcurrencyVisualizer.Instrumentation;  
    ```  
  
    ```VB  
    Imports Microsoft.ConcurrencyVisualizer.Instrumentation  
    ```  
  
### <a name="c"></a>C++  
 C++ では、[marker_series クラス](../profiling/marker-series-class.md) オブジェクトを作成し、それを使用して関数を呼び出します。  `marker_series` クラスは、マーカーを生成するための 3 つの関数 ([marker_series::write_flag メソッド](../profiling/marker-series-write-flag-method.md)、[marker_series::write_message メソッド](../profiling/marker-series-write-message-method.md)、および [marker_series::write_alert メソッド](../profiling/marker-series-write-alert-method.md)) を示します。  
  
##### <a name="to-add-sdk-support-to-a-c-or-c-project"></a>C++ または C のプロジェクトに SDK のサポートを追加するには  
  
1.  メニュー バーで、**[分析]**、**[同時実行ビジュアライザー]**、**[プロジェクトへの SDK の追加]** の順に選択します。  
  
2.  SDK にアクセスするプロジェクトを選択し、**[選択したプロジェクトに SDK を追加]** ボタンを選択します。  
  
3.  C++ の場合は、`cvmarkersobj.h` を含めます。 C の場合は、`cvmarkers.h` を含めます。  
  
4.  using ステートメントをコードに追加します。  
  
    ```  
    using namespace Concurrency::diagnostic;  
    ```  
  
5.  `marker_series` オブジェクトを作成し、それを `span` コンストラクターに渡します。  
  
    ```C++  
  
    marker_series mySeries;  
    span s(mySeries, _T("Span description"));  
  
    ```  
  
## <a name="custom-usage"></a>カスタムの使用方法  
 高度なシナリオの場合、同時実行ビジュアライザー SDK はより詳細に制御します。  より高度なシナリオには、2 つの主な概念 (マーカー プロバイダーとマーカー シリーズ) が関連付けられています。 マーカー プロバイダーはさまざまな ETW プロバイダー (それぞれ異なる GUID を持つ) です。 マーカー シリーズは、1 つのプロバイダーによって生成されるイベントのシリアル チャネルです。 マーカー プロバイダーによって生成されるイベントを整理する場合に使用できます。  
  
#### <a name="to-use-a-new-marker-provider-in-a-c-or-visual-basic-project"></a>C# または Visual Basic プロジェクトで新しいマーカー プロバイダーを使用するには  
  
1.  <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerWriter> オブジェクトを作成します。  コンストラクターは GUID を受け取ります。  
  
2.  プロバイダーを登録するには、同時実行ビジュアライザーの [[詳細設定]](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) ダイアログ ボックスを開きます。  **[マーカー]** タブを選択してから、**[新しいプロバイダーを追加します]** ボタンを選択します。 [[詳細設定]](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) ダイアログ ボックスで、プロバイダーの作成に使用された GUID と、プロバイダーの説明を入力します。  
  
#### <a name="to-use-a-new-marker-provider-in-a-c-or-c-project"></a>C# または C プロジェクトで新しいマーカー プロバイダーを使用するには  
  
1.  `CvInitProvider` 関数を使用して、PCV_PROVIDER を初期化します。  コンストラクターは GUID* と PCV_PROVIDER\* を受け取ります。  
  
2.  プロバイダーを登録するには、[[詳細設定]](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) ダイアログ ボックスを開きます。  **[マーカー]** タブを選択してから、**[新しいプロバイダーを追加します]** ボタンを選択します。 ダイアログ ボックスに、プロバイダーの作成に使用された GUID と、プロバイダーの説明を入力します。  
  
#### <a name="to-use-a-marker-series-in-a-c-or-visual-basic-project"></a>C# または Visual Basic プロジェクトでマーカー シリーズを使用するには  
  
1.  新しい <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerSeries> を使うには、最初に <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerWriter> オブジェクトを使って作成した後、新しいシリーズから直接マーカー イベントを生成します。  
  
    ```csharp  
    MarkerSeries series1 = myMarkerWriter.CreateMarkerSeries("Series 1");  
    series1.WriteFlag("My flag");  
    ```  
  
    ```VB  
    Dim series1 As New myMarkerWriter.CreateMarkerSeries("Series 1")  
    series1.WriteFlag("My flag")  
    ```  
  
#### <a name="to-use-a-marker-series-in-a-c-project"></a>C++ プロジェクトでマーカー シリーズを使用するには  
  
1.  `marker_series` オブジェクトを作成します。  この新しいシリーズからイベントを生成することができます。  
  
    ```scr  
    marker_series series;  
    series.write_flag(_T("Hello world!"));  
    ```  
  
#### <a name="to-use-a-marker-series-in-a-c-project"></a>C プロジェクトでマーカー シリーズを使用するには  
  
1.  `CvCreateMarkerSeries` 関数を使用して、PCV_MARKERSERIES を作成します。  
  
    ```C++  
    PCV_MARKERSERIES series;  
    CvCreatemarkerSeries(myProvider, _T("My Series"), &series);  
    CvWriteFlag(series, _T("Writing a flag"));  
    ```  
  
## <a name="related-topics"></a>関連トピック  
  
|Title|説明|  
|-----------|-----------------|  
|[C++ ライブラリ リファレンス](../profiling/cpp-library-reference.md)|C++ の同時実行ビジュアライザー API について説明します。|  
|[C ライブラリ リファレンス](../profiling/c-library-reference.md)|C の同時実行ビジュアライザー API について説明します。|  
|<xref:Microsoft.ConcurrencyVisualizer.Instrumentation>|マネージ コードの同時実行ビジュアライザー API について説明します。|  
|[同時実行ビジュアライザー](../profiling/concurrency-visualizer.md)|同時実行メソッドを使用して生成され、スレッド実行データを含む、プロファイル データ ファイルのビューとレポートに関するリファレンス情報。|