---
title: "DA0012: リフレクションが頻繁に実行されています | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.rules.DAReflection
- vs.performance.12
- vs.performance.rules.DA0012
- vs.performance.DA0011
ms.assetid: c92a1d76-21fa-426e-8b1b-a3c08e9bcbca
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: e09aa099a362182ff46ce0de998f0117100b162c

---
# <a name="da0012-significant-amount-of-reflection"></a>DA0012: リフレクションが頻繁に実行されています
|||  
|-|-|  
|規則 ID|DA0012|  
|カテゴリ|.NET Framework の使用|  
|プロファイル方法|サンプリング|  
|メッセージ|リフレクションを使いすぎている可能性があります。 これは負荷が高い操作です。|  
|規則の種類|警告|  
  
## <a name="cause"></a>原因  
 InvokeMember および GetMember などの System.Reflection メソッドまたは MemberInvoke などの Type メソッドへの呼び出しが、プロファイリング データの大きな割合を占めています。 可能な場合は、事前バインディングを使用するこれらのメソッドを、依存アセンブリのメソッドに置き換えることを検討してください。  
  
## <a name="rule-description"></a>規則の説明  
 リフレクションは、.NET Framework の柔軟な機能です。この機能は、依存ランタイム アセンブリに対してアプリケーションの遅延バインディングを実行したり、実行時に新しい型を作成して動的に実行する場合に使用できます。 ただし、この手法は頻繁に使用したり短いループで呼び出したりすると、パフォーマンスが低下する可能性があります。  
  
 詳細については、MSDN の Microsoft Patterns and Practices (マイクロソフトのパターンと手法) ライブラリの「.NET アプリケーションのパフォーマンスとスケーラビリティの向上」の第 5 章「マネージ コード パフォーマンスの向上」の「[リフレクションと遅延バインディング](http://go.microsoft.com/fwlink/?LinkId=177826)」を参照してください。  
  
## <a name="how-to-investigate-a-warning"></a>警告の調査方法  
 [エラー一覧] ウィンドウに表示されたメッセージをダブルクリックして、プロファイル データの[関数の詳細ビュー](../profiling/function-details-view.md)に移動します。 System.Type メソッドまたは System.Reflection メソッドの呼び出し関数を調べ、.NET リフレクション API を最も頻繁に使用するプログラムのセクションを見つけます。 メタデータを返すメソッドは使用しないでください。 アプリケーションのパフォーマンスが重大である場合、状況によっては遅延バインディングの使用と、実行時の動的な型の作成を行わないようにする必要があります。


<!--HONumber=Feb17_HO4-->


