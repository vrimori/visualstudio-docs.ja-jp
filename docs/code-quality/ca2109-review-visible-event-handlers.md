---
title: 'Ca 2109: 表示するイベント ハンドラーを確認する |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2109
- ReviewVisibleEventHandlers
helpviewer_keywords:
- ReviewVisibleEventHandlers
- CA2109
ms.assetid: 8f8fa0ee-e94e-400e-b516-24d8727725d7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7949c7f0b1bfa535fea2c30fd3a473f5fe82fc37
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="ca2109-review-visible-event-handlers"></a>CA2109: 表示するイベント ハンドラーをレビューします
|||  
|-|-|  
|TypeName|ReviewVisibleEventHandlers|  
|CheckId|CA2109|  
|カテゴリ|Microsoft.Security|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 パブリックまたはプロテクトのイベント ハンドラー メソッドが検出されました。  
  
## <a name="rule-description"></a>規則の説明  
 外部から参照可能なイベント処理メソッドは、レビューを必要とするセキュリティの問題を表示します。  
  
 イベント ハンドラー メソッドは、絶対に必要な場合を除き公開しないでください。 イベントのシグネチャと一致する限り、任意のイベントにイベント ハンドラーで公開されているメソッドを呼び出すデリゲート型を追加できます。 イベントは、可能性のあるすべてのコードによって発生する可能性し、ボタンのクリックしてなどのユーザー アクションへの応答で信頼性の高いシステム コードによって頻繁に発生します。 イベント処理メソッドにセキュリティ チェックを追加することは防止しませんコード メソッドを呼び出すイベント ハンドラーを登録します。  
  
 要求では、イベント ハンドラーによって呼び出されるメソッドを確実に保護できません。 セキュリティ確認要求コール スタックに呼び出し元を確認するには、信頼されていない呼び出し元からコードを保護します。 イベント ハンドラー メソッドが実行時に、イベントにイベント ハンドラーを追加するコードは、コール スタックに配置する必要ではありません。 そのため、コール スタック可能性がありますが信頼性の高いしか呼び出し元イベント ハンドラー メソッドが呼び出されるとします。 これにより、要求が成功するイベント ハンドラー メソッドで行われます。 また、メソッドが呼び出されたときに、要求されたアクセス許可をアサートする可能性があります。 これらの理由から、この規則違反を修正しない場合のリスクをイベント処理メソッドを確認した後評価のみできます。 コードを再確認する場合は、次の問題を考慮します。  
  
-   イベント ハンドラーは危険なやアクセス許可をアサートすると、アンマネージ コード アクセス許可など、悪用される操作を実行しますか。  
  
-   スタックに呼び出し元を信頼する高だけでいつでも実行できるため、コードとの間は、セキュリティ上の脅威とは?  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、メソッドを確認し、次を評価します。  
  
-   ことができます、イベント処理メソッド パブリックでないですか。  
  
-   イベント ハンドラー外のすべての危険性のある機能を移動することができますか。  
  
-   セキュリティの要求が適用されると場合、こので実行できる他の方法ですか。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 セキュリティを慎重確認した後のみ、コードにセキュリティ上の脅威がないかどうかを確認するこの規則による警告は抑制します。  
  
## <a name="example"></a>例  
 次のコードでは、悪意のあるコードが誤用されるイベント処理メソッドを示します。  
  
 [!code-csharp[FxCop.Security.EventSecLib#1](../code-quality/codesnippet/CSharp/ca2109-review-visible-event-handlers_1.cs)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName>   
 <xref:System.EventArgs?displayProperty=fullName>   
 