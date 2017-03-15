---
title: "CA2109: 表示するイベント ハンドラーを確認します | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2109"
  - "ReviewVisibleEventHandlers"
helpviewer_keywords: 
  - "CA2109"
  - "ReviewVisibleEventHandlers"
ms.assetid: 8f8fa0ee-e94e-400e-b516-24d8727725d7
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA2109: 表示するイベント ハンドラーを確認します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReviewVisibleEventHandlers|  
|CheckId|CA2109|  
|分類|Microsoft.Security|  
|互換性に影響する変更点|あり|  
  
## 原因  
 パブリックまたはプロテクトのイベント ハンドラー メソッドが検出されました。  
  
## 規則の説明  
 外部から参照できるイベント ハンドラー メソッドにはセキュリティ上の問題があるため、再確認が必要です。  
  
 イベント ハンドラー メソッドは、絶対に必要な場合を除き公開しないでください。  公開されたメソッドを呼び出すイベント ハンドラー \(デリゲート型\) とイベントのシグネチャが一致していれば、そのイベント ハンドラーを任意のイベントに追加できます。  イベントはどのコードからでも発生する可能性があり、ボタンのクリックなどユーザー操作に応答して信頼性の高いシステム コードからイベントが呼び出されることがよくあります。  イベント ハンドラー メソッドにセキュリティ チェックを追加する方法では、メソッドを呼び出すイベント ハンドラーがコードに登録されることを防ぐことはできません。  
  
 確認要求では、イベント ハンドラーから呼び出されるメソッドを確実に保護できません。  セキュリティ確認要求によってコール スタックの呼び出し元を検査することで、信頼関係のない呼び出し元からコードを保護できます。  イベント ハンドラー メソッドが実行されているとき、イベント ハンドラーをイベントに追加するコードを、コール スタックに配置する必要はありません。  そのため、イベント ハンドラー メソッドが呼び出されたときに、コール スタックに信頼性の高い呼び出し元しかないことがあります。  これにより、イベント ハンドラー メソッドによって正常に確認要求が行われます。  また、要求されたアクセス許可は、メソッドが呼び出されたときにアサートされることがあります。  そのため、この規則違反を修正しない場合のリスクは、イベント ハンドラー メソッドを再確認した後にのみ評価できます。  コードを再確認するときに、次の問題を検討します。  
  
-   アクセス許可のアサートやアンマネージ コード アクセス許可の削除など、イベント ハンドラーで危険な操作やセキュリティ上の脆弱性がある操作を実行するか。  
  
-   コール スタック上の信頼性の高い呼び出し元のみを使用して任意のタイミングで実行できるために発生する、コードのセキュリティ上の脅威は何か。  
  
## 違反の修正方法  
 この規則違反を修正するには、メソッドを再確認し、次の項目を評価します。  
  
-   イベント ハンドラー メソッドを非パブリックにすることはできるか。  
  
-   イベント ハンドラーから、すべての危険な機能を外すことはできるか。  
  
-   セキュリティ確認要求が設定された場合、別の方法で実現できるか。  
  
## 警告を抑制する状況  
 必ず、コードにセキュリティ上の脅威がないようにセキュリティの再確認を慎重に行ってから、この規則による警告を抑制します。  
  
## 使用例  
 次のコードは、悪意のあるコードから不正使用される可能性のあるイベント ハンドラー メソッドの例です。  
  
 [!code-cs[FxCop.Security.EventSecLib#1](../code-quality/codesnippet/CSharp/ca2109-review-visible-event-handlers_1.cs)]  
  
## 参照  
 <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName>   
 <xref:System.EventArgs?displayProperty=fullName>   
 [Security Demands](http://msdn.microsoft.com/ja-jp/324c14f8-54ff-494d-9fd1-bfd20962c8ba)