---
title: "DA0005: 頻繁な GC2 のコレクションです | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.DA0005"
  - "vs.performance.rules.DAManyGC2Collections"
  - "vs.performance.5"
  - "vs.performance.rules.DA0005"
ms.assetid: 8d3f267c-8a74-4cf4-91a5-0b06a76dc2bd
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# DA0005: 頻繁な GC2 のコレクションです
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|規則 ID|DA0005|  
|分類|.NET Framework の使用|  
|プロファイル方法|.NET メモリ|  
|メッセージ|オブジェクトの多くはジェネレーション 2 のガベージ コレクションで収集されています。|  
|メッセージの種類|警告|  
  
## 原因  
 多数の .NET メモリ オブジェクトが、ジェネレーション 2 のガベージ コレクションで再利用されています。  
  
## 規則の説明  
 Microsoft .NET 共通言語ランタイム \(CLR: Common Language Runtime\) は、自動メモリ管理メカニズムを備えています。このメカニズムは、ガベージ コレクターを使用して、アプリケーションで使用されなくなったオブジェクトのメモリを解放します。  ガベージ コレクターはジェネレーション指向です。これは、多くの割り当てが短時間で終了することを前提としています。  たとえば、ローカル変数の有効期間は短時間で終了します。  新しく作成されたオブジェクトはジェネレーション 0 \(gen 0\) から始まり、ガベージ コレクションの実行中に破棄されなければジェネレーション 1 に昇格します。その後もアプリケーションによって引き続き使用されていれば、最後はジェネレーション 2 に昇格します。  
  
 ジェネレーション 0 のオブジェクトの収集頻度は高く、通常は非常に効率的に収集されます。  ジェネレーション 1 のオブジェクトの収集頻度はそれよりも低くなり、収集効率も下がります。  有効期間の長いジェネレーション 2 のオブジェクトの場合、収集頻度はさらに低くなります。  また、ジェネレーション 2 のコレクション \(フル ガベージ コレクションの実行\) は、最も負荷のかかる操作になります。  
  
 この規則は、ジェネレーション 2 のガベージ コレクションの発生率が高くなりすぎた場合に適用されます。  多数の有効期間が比較的短いオブジェクトが、ジェネレーション 1 のコレクションでは収集されずにジェネレーション 2 のフル コレクションで収集されると、メモリ管理のコストが高くなる可能性があります。  詳細については、MSDN Web [中年の危機](http://go.microsoft.com/fwlink/?LinkId=177835) サイトの" Rico Mariani's Performance ティドビッツ ポストを参照します。  
  
## 警告の調査方法  
 [.NET メモリのデータ ビュー](../profiling/dotnet-memory-data-views.md) レポートを確認して、メモリ割り当てに関するアプリケーションのパターンを把握します。  [オブジェクトの有効期間ビュー](../profiling/object-lifetime-view.md) を使用して、ジェネレーション 2 に残っており、その後そこからクリアされる、プログラムのデータ オブジェクトを確認します。  [割り当てビュー](../profiling/dotnet-memory-allocations-view.md) を使用して、これらの割り当てが行われた実行パスを判断します。  
  
 ガベージ コレクションのパフォーマンスを向上する方法の詳細については、Microsoft Web サイトの [ガベージ コレクターの基本とパフォーマンスのヒント](http://go.microsoft.com/fwlink/?LinkId=148226) "参照してください。  自動ガベージ コレクションのオーバーヘッドについては、"参照してください [クロークを選択大きいオブジェクト ヒープ](http://go.microsoft.com/fwlink/?LinkId=177836)。