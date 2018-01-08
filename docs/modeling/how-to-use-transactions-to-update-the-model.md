---
title: "方法: トランザクションを使用してモデルを更新する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e24436a5-7f97-401b-bc83-20d188d10d5b
caps.latest.revision: "7"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: e117b6fad7a558d002bf0e8689c56dbc2947644f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-transactions-to-update-the-model"></a>方法: トランザクションを使用してモデルを更新する
トランザクションをストアに加えられた変更がグループとして扱われることを確認します。 グループ化されている変更をコミットまたは 1 つの単位としてロールバックできます。  
  
 ときに、プログラム コードを変更追加すると、またはストア内の任意の要素を削除[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Visualization and Modeling SDK では、トランザクションの内部ようにする必要があります。 アクティブなインスタンスである必要があります<xref:Microsoft.VisualStudio.Modeling.Transaction>変更が行われる場合、ストアに関連付けられています。 これは、すべてのモデル要素、リレーションシップ、図形、図、およびそのプロパティに適用されます。  
  
 トランザクション メカニズムを使用して、一貫性のない状態を回避できます。 トランザクション中にエラーが発生した、すべての変更はロールバックされます。 ユーザーは、元に戻すコマンドを実行する場合、最近使用した各トランザクションは、1 つのステップとして扱われます。 ユーザーは、個別のトランザクションに明示的に配置する場合を除き、最近の変更の部分を取り消すことはできません。  
  
## <a name="opening-a-transaction"></a>トランザクションを開く  
 トランザクションを管理するための最も便利な方法は、`using`ステートメントで囲む、`try...catch`ステートメント。  
  
```  
Store store; ...  
try  
{  
  using (Transaction transaction =  
    store.TransactionManager.BeginTransaction("update model"))  
    // Outermost transaction must always have a name.  
  {  
    // Make several changes in Store:  
    Person p = new Person(store);  
    p.FamilyTreeModel = familyTree;  
    p.Name = "Edward VI";  
    // end of changes to Store  
  
    transaction.Commit(); // Don't forget this!  
  } // transaction disposed here  
}  
catch (Exception ex)  
{  
  // If an exception occurs, the Store will be   
  // rolled back to its previous state.  
}  
```  
  
 場合により、最終的な例外`Commit()`ストアは以前の状態にリセットされます、変更中に発生します。 これにより、エラーが残されていないモデルを矛盾した状態になっていることを確認できます。  
  
 任意の数の 1 つのトランザクションの内部で変更を行うことができます。 アクティブなトランザクション内で新しいトランザクションを開くことができます。 入れ子になったトランザクションはコミットまたはを含むトランザクションが終了する前にロールバックする必要があります。 詳細については、例を参照してください、<xref:Microsoft.VisualStudio.Modeling.Transaction.TransactionDepth%2A>プロパティです。  
  
 変更を恒久的なようにするには`Commit`トランザクションが破棄される前にします。 トランザクション内でキャッチされない例外が発生した場合、ストアは、変更前に、の状態にリセットされます。  
  
## <a name="rolling-back-a-transaction"></a>トランザクションのロールバック  
 ストアに残っていることを確認をトランザクションの前に、の状態に戻りますするには、これらの方法のいずれかを使用できます。  
  
1.  トランザクションのスコープ内でキャッチされない例外が発生します。  
  
2.  明示的にトランザクションをロールバックします。  
  
    ```  
    this.Store.TransactionManager.CurrentTransaction.Rollback();  
    ```  
  
## <a name="transactions-do-not-affect-non-store-objects"></a>トランザクションは、ストア以外のオブジェクトには影響しません  
 トランザクションは、ストアの状態だけを制御します。 ファイル、データベース、または DSL 定義の外部の通常の型で宣言されているオブジェクトなどの外部のアイテムに加えられた変更の部分が元に戻すことはできません。  
  
 例外可能性がありますのままにしてこのような変更をストアと一貫性のない場合、は、例外ハンドラーでその可能性を処理する必要があります。 外部リソースのストア オブジェクトを同期を保つことを確認する方法の 1 つは、ストア内の要素へのイベント ハンドラーを使用して、各外部オブジェクトを結合するのにです。 詳細については、次を参照してください。[イベント ハンドラー反映されるまで変更 Outside the モデル](../modeling/event-handlers-propagate-changes-outside-the-model.md)です。  
  
## <a name="rules-fire-at-the-end-of-a-transaction"></a>トランザクションの最後にルールの起動  
 トランザクションの最後に、トランザクションが破棄される前に、ストア内の要素に適用される規則が発生しました。 各ルールは、変更されたモデル要素に適用される方法です。 たとえば、要素は、モデル要素が変更されたときに、図形の状態を更新する「を修正.」の規則があるし、モデル要素が作成されるときに図形を作成します。 指定された起動順序はありません。 ルールによって行われた変更は、別のルールを起動できます。  
  
 独自の規則を定義することができます。 ルールの詳細については、次を参照してください。[への応答と変更を反映する](../modeling/responding-to-and-propagating-changes.md)です。  
  
 ルールは、元に戻す、やり直し操作、またはロールバック コマンドの後に発生しません。  
  
## <a name="transaction-context"></a>トランザクションのコンテキスト  
 各トランザクションには情報を格納するディクショナリ。  
  
 `store.TransactionManager`  
  
 `.CurrentTransaction.TopLevelTransaction`  
  
 `.Context.Add(aKey, aValue);`  
  
 これは、ルール間で情報を転送する際に特に役立ちます。  
  
## <a name="transaction-state"></a>トランザクションの状態  
 避ける必要がありますには、元に戻すまたはやり直すと、トランザクションによって変更が発生した場合、変更を反映します。 これは、たとえば、ストア内の別の値を更新できるプロパティの値のハンドラーを記述する場合に発生します。 元に戻す操作では、以前の状態をストア内のすべての値がリセットされ、ために、更新された値を計算する必要はありません。 このコードを使用します。  
  
```  
if (!this.Store.InUndoRedoOrRollback) {...}  
```  
  
 ルールは、ストアが最初に、ファイルから読み込まれるときに発生します。 これらの変更に応答を避けるためには、次のコマンドを使用します。  
  
```  
if (!this.Store.InSerializationTransaction) {...}  
  
```