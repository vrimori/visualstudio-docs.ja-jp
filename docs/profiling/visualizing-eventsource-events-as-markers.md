---
title: "マーカーとしての EventSource イベントの視覚化 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a10022a-5c37-48b1-a833-dd35902176b6
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 24a7ce6857830b056a9a17f5f551c443d76e2b4d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="visualizing-eventsource-events-as-markers"></a>マーカーとしての EventSource イベントの視覚化
同時実行ビジュアライザーは、マーカーとして EventSource イベントを表示でき、マーカーの表示方法を制御できます。 EventSource マーカーを表示するには、[[詳細設定]](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) ダイアログ ボックスを使用して ETW プロバイダー GUID を登録します。 同時実行ビジュアライザーには、[フラグ マーカー](../profiling/flag-markers.md)、[スパン マーカー](../profiling/span-markers.md)、[メッセージ マーカー](../profiling/message-markers.md)として EventSource イベントを表す既定の規約があります。 イベントにカスタム フィールドを追加することで、EventSource イベントの表示方法をカスタマイズできます。 マーカーに関する詳細については、「[同時実行ビジュアライザー マーカー](../profiling/concurrency-visualizer-markers.md)」を参照してください。 EventSource イベントの詳細については、「<xref:System.Diagnostics.Tracing>」を参照してください。  
  
## <a name="default-visualization-of-eventsource-events"></a>EventSource イベントの既定の視覚化  
 既定では、同時実行ビジュアライザーは EventSource イベントを表すために次の規約を使用します。  
  
### <a name="marker-type"></a>マーカーの種類  
  
1.  [オペコード](http://msdn.microsoft.com/en-us/d97953df-669b-4c55-b1a8-925022b339b7) win:Start または win:Stop を持つイベントは、それぞれスパンの開始と終了として扱われます。  入れ子になっているスパンまたは重複するスパンは表示できません。 あるスレッドで開始し、別のスレッドで終了するイベント ペアは表示できません。  
  
2.  オペコードが win:Start でも win:Stop でもないイベントは、その[レベル](http://msdn.microsoft.com/en-us/dfa4e0a9-4d89-4f50-aef9-1dae0dc11726) (EVENT_RECORD.EVENT_HEADER.EVENT_DESCRIPTOR のフィールド) が win:Verbose 以上でない限り、マーカー フラグとして扱われます。  
  
3.  それ以外の場合はすべて、イベントはメッセージとして扱われます。  
  
### <a name="importance"></a>重要度  
 次の表にイベント レベルとマーカーの重要度の対応関係を定義します。  
  
|ETW レベル|同時実行ビジュアライザーの重要度|  
|---------------|---------------------------------------|  
|win:LogAlways|標準|  
|win:Critical|重大|  
|win:Error|重大|  
|win:Warning|High|  
|win:Informational|標準|  
|win:Verbose|Low|  
|win:verbose より大きい|Low|  
  
### <a name="series-name"></a>系列の名前  
 イベントのタスク名は系列名に使用されます。 イベントにタスクが定義されていない場合、系列名は空です。  
  
### <a name="category"></a>カテゴリ  
 レベルが win:Critical または win:Error の場合、カテゴリはアラート (-1) です。 それ以外の場合は、カテゴリは既定 (0) です。  
  
### <a name="text"></a>テキスト  
 printf 型の書式設定されたテキスト メッセージがイベントに対して定義されている場合、マーカーの説明として表示されます。 それ以外の場合は、説明はイベントの名前と各ペイロード フィールドの値です。  
  
## <a name="customizing-visualization-of-eventsource-events"></a>EventSource イベントの視覚化のカスタマイズ  
 次のセクションで説明されているように、イベントに適切なフィールドを追加すれば、EventSource イベントの表示方法をカスタマイズできます。  
  
### <a name="marker-type"></a>マーカーの種類  
 `cvType` フィールド (バイト) を使用して、イベントを表すために使用するマーカーの種類を制御します。 cvType に使用できる値は次のとおりです。  
  
|cvType 値|結果として得られるマーカーの種類|  
|------------------|---------------------------|  
|0|メッセージ|  
|1|スパンの開始|  
|2|スパンの終了|  
|3|フラグ|  
|その他のすべての値|メッセージ|  
  
### <a name="importance"></a>重要度  
 `cvImportance` フィールド (バイト) を使用して、EventSource イベントの重要度の設定を制御できます。 しかし、表示されるイベントの重要度はレベルを使用して制御することをお勧めします。  
  
|cvImportance 値|同時実行ビジュアライザーの重要度|  
|------------------------|---------------------------------------|  
|0|標準|  
|1|重大|  
|2|High|  
|3|High|  
|4|標準|  
|5|Low|  
|その他のすべての値|Low|  
  
### <a name="series-name"></a>系列の名前  
 `cvSeries` イベント フィールド (文字列) を使用して、同時実行ビジュアライザーが EventSource イベントに指定する系列名を制御できます。  
  
### <a name="category"></a>カテゴリ  
 `cvCategory` フィールド (バイト) を使用して、同時実行ビジュアライザーが EventSource イベントに指定するカテゴリを制御できます。  
  
### <a name="text"></a>テキスト  
 `cvTextW` フィールド (文字列) を使用して、同時実行ビジュアライザーが EventSource イベントに指定する説明を制御できます。  
  
### <a name="spanid"></a>SpanID  
 cvSpanId フィールド (int) を使用して、イベントのペアを照合します。 スパンを表す開始/終了イベントの各ペアの値は一意である必要があります。 そのために、同時実行コードの場合は特に、<xref:System.Threading.Interlocked.Exchange%2A> などの同期プリミティブを使用して、キー (CvSpanID に使用される値) が正しいことを確認する必要があります。  
  
> [!NOTE]
>  SpanID を使用してスパンを入れ子にすること、同じスレッドで部分的に重複させること、または開始と終了のスレッドを別にすることはサポートされていません。  
  
## <a name="see-also"></a>参照  
 [同時実行ビジュアライザー マーカー](../profiling/concurrency-visualizer-markers.md)