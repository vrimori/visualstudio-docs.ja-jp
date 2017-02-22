---
title: "マーカーとしての EventSource イベントの視覚化 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3a10022a-5c37-48b1-a833-dd35902176b6
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# マーカーとしての EventSource イベントの視覚化
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

同時実行ビジュアライザーは、マーカーとして EventSource イベントを表示マーカーの表示方法を制御できます。  EventSource にマーカーを表示するには、[詳細設定](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) ダイアログ ボックスを使用して ETW プロバイダーの GUID を登録します。  同時実行ビジュアライザーでは、[フラグ マーカー](../profiling/flag-markers.md)[スパン マーカー](../profiling/span-markers.md)と [メッセージ マーカー](../profiling/message-markers.md)として EventSource イベントを表す既定の規則があります。  EventSource イベントがイベントにカスタム フィールドを追加して、どのように表示する方法をカスタマイズできます。  マーカーに関する詳細については、「[同時実行ビジュアライザー マーカー](../profiling/concurrency-visualizer-markers.md)」を参照してください。  EventSource イベントに関する詳細については、「<xref:System.Diagnostics.Tracing>」を参照してください。  
  
## EventSource イベントの既定の視覚化  
 既定では、同時実行ビジュアライザー EventSource イベントを表すには、次の規則を使用します。  
  
### マーカーの種類  
  
1.  [オペコード](http://msdn.microsoft.com/ja-jp/d97953df-669b-4c55-b1a8-925022b339b7) の優先のイベント: 開始または優先: 扱われます範囲の先頭または末尾に、個別に停止します。入れ子になっていないか、重複する範囲を表示できません。  別の 1 種類のスレッドと末尾で始まるイベントのペアを表示できません。  
  
2.  オペコードを win:Start や win:Stop でないイベントはマーカー フラグとして [レベル](http://msdn.microsoft.com/ja-jp/dfa4e0a9-4d89-4f50-aef9-1dae0dc11726) \(EVENT\_RECORD.EVENT\_HEADER.EVENT\_DESCRIPTOR のフィールド\) が優先である処理: 冗長以上。  
  
3.  それ以外の場合、イベントはメッセージとして扱われます。  
  
### 重要度  
 次の表にマーカーの重要性にイベント レベル マップ定義されています。  
  
|ETW レベル|同時実行ビジュアライザーの重要性|  
|-------------|----------------------|  
|win:LogAlways|Normal|  
|win:Critical|Critical|  
|win:Error|Critical|  
|win:Warning|High|  
|win:Informational|Normal|  
|win:Verbose|Low|  
|win:verboseより大きい|Low|  
  
### ファミリ名  
 イベントのタスク名はファミリ名として使用されます。  ファミリ名がタスクのイベントに対して定義されていない場合は空です。  
  
### 分類  
 レベルを win:Critical または win:Errorの場合、カテゴリは通知です \(\- 1\)。  それ以外の場合、カテゴリが既定 \(0\) です。  
  
### テキスト  
 printf 型の書式設定されたテキスト メッセージがイベントに対して定義されている場合、マーカーの説明として表示されます。  それには、各フィールドのペイロード イベントと値の名前です。  
  
## EventSource イベントの視覚化のカスタマイズ  
 次のセクションで説明されているように EventSource イベントがイベントに適切なフィールドを追加することで、どのように表示する方法をカスタマイズできます。  
  
### マーカーの種類  
 イベントを表すために使用されるマーカーの種類を制御するために `cvType` フィールド、バイトを使用します。  cvType に使用できる値は次のとおりです。:  
  
|cvType 値|結果のマーカーの種類|  
|--------------|----------------|  
|0|メッセージ|  
|1|範囲の開始|  
|2|範囲の終了|  
|3|フラグ|  
|その他すべての値|メッセージ|  
  
### 重要度  
 EventSource イベントに設定する重要性を制御するために `cvImportance` フィールド、バイトを使用できます。  ただし、レベルでイベントが表示される重要度を制御することをお勧めします。  
  
|cvImportance 値|同時実行ビジュアライザーの重要性|  
|--------------------|----------------------|  
|0|Normal|  
|1|Critical|  
|2|High|  
|3|High|  
|4|Normal|  
|5|Low|  
|その他すべての値|Low|  
  
### ファミリ名  
 同時実行ビジュアライザーが EventSource イベントに与えるファミリ名を制御するために `cvSeries` イベント フィールド、文字列を使用します。  
  
### 分類  
 同時実行ビジュアライザーが EventSource イベントに提供するカテゴリを制御するために `cvCategory` フィールド、バイトを使用します。  
  
### テキスト  
 同時実行ビジュアライザーが EventSource のイベントに対する説明を制御するために `cvTextW` フィールド、文字列を使用します。  
  
### SpanID  
 イベントのペアに cvSpanId フィールド、int を使用します。  範囲を表す開始\/停止イベントの各ペアの値は一意である必要があります。  通常、並列コードの場合、これは <xref:System.Threading.Interlocked.Exchange%2A> などの同期プリミティブを使用 CvSpanID で使用されるキー \(値\) が正しいことを確認する必要があります。  
  
> [!NOTE]
>  SpanID の使用は範囲にある、部分的に同じスレッドで重複するようにしたり、1 種類のスレッドで開始されるようにし、別の終了することはできません。  
  
## 参照  
 [同時実行ビジュアライザー マーカー](../profiling/concurrency-visualizer-markers.md)