---
title: '方法: トランザクションを使用してモデルを更新します |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e24436a5-7f97-401b-bc83-20d188d10d5b
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 50f9d491ed52098edb8a8ccd1a7b2f9c8834447e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49236861"
---
# <a name="how-to-use-transactions-to-update-the-model"></a>方法: トランザクションを使用してモデルを更新する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

トランザクションをストアに加えられた変更がグループとして扱われることを確認します。 グループ化されている変更をコミットまたは 1 つの単位としてロールバックできます。  
  
 たびに、プログラム コードを変更しますの追加、または、ストア内の任意の要素を削除します[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Visualization and Modeling SDK では、トランザクション内で行う必要があります。 アクティブなインスタンスが必要がある<xref:Microsoft.VisualStudio.Modeling.Transaction>変更が発生したときに、ストアに関連付けられています。 これは、すべてのモデル要素、リレーションシップ、図形、図、およびそのプロパティに適用されます。  
  
 トランザクションのメカニズムを使用して、一貫性のない状態を回避できます。 トランザクション中にエラーが発生したすべての変更はロールバックされます。 ユーザーは、元に戻すコマンドを実行する場合は、最近使用した各トランザクションが 1 つのステップとして扱われます。 個別のトランザクションに明示的に配置する場合を除き、ユーザーは、直近の変更の部分を取り消すことはできません。  
  
## <a name="opening-a-transaction"></a>トランザクションを開く  
 トランザクションの管理の最も便利な方法は、`using`ステートメントで囲む、`try...catch`ステートメント。  
  
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
  
 場合、例外が、最終的な`Commit()`ストアは、以前の状態にリセットされます、変更するときに発生します。 これにより、エラー、モデルに置かないでが不整合な状態かどうかを確認できます。  
  
 任意の数の 1 つのトランザクションの内部で変更を行うことができます。 アクティブなトランザクション内で新しいトランザクションを開くことができます。 入れ子になったトランザクションはコミットまたは含んでいるトランザクションが終了する前にロールバックする必要があります。 詳細については、の例を参照してください、<xref:Microsoft.VisualStudio.Modeling.Transaction.TransactionDepth%2A>プロパティ。  
  
 変更を永続的なようにするにする必要があります`Commit`破棄される前に、トランザクション。 トランザクション内でキャッチされない例外が発生した場合、ストアが、変更前に、の状態にリセットされます。  
  
## <a name="rolling-back-a-transaction"></a>トランザクションのロールバック  
 ストアに残っていることを確認、トランザクションの前に、の状態に戻りするには、これらの戦術のいずれかを使用できます。  
  
1.  トランザクションのスコープ内でキャッチされない例外を発生させます。  
  
2.  明示的にトランザクションをロールバックします。  
  
    ```  
    this.Store.TransactionManager.CurrentTransaction.Rollback();  
    ```  
  
## <a name="transactions-do-not-affect-non-store-objects"></a>トランザクションは、Store 以外のオブジェクトには影響しません  
 トランザクションには、ストアの状態のみによって制御されます。 ファイル、データベース、または DSL 定義の外部の通常の型で宣言されているオブジェクトなどの外部のアイテムに対する部分の変更が元に戻すことはできません。  
  
 場合は、例外がこのような変更をストアと一貫性のないは、例外ハンドラーでその可能性を処理する必要があります。 外部リソースが、オブジェクトの保存と同期を保つことを確認する方法の 1 つでは、ストア内の要素にイベント ハンドラーを使用して各外部オブジェクトを結合します。 詳細については、次を参照してください。[イベント ハンドラー反映されるまで変更 Outside the モデル](../modeling/event-handlers-propagate-changes-outside-the-model.md)します。  
  
## <a name="rules-fire-at-the-end-of-a-transaction"></a>トランザクションの最後にルールの起動  
 トランザクションの最後に、トランザクションが破棄される前に、ストア内の要素に適用される規則が発生します。 各ルールは、変更されたモデル要素に適用される方法です。 たとえば、「修正」のモデル要素が変更されたときに、図形の状態を更新する規則があるし、モデル要素が作成されるときに図形を作成します。 指定された起動順序はありません。 ルールによって行われた変更は、別のルールを起動できます。  
  
 独自のルールを定義することができます。 ルールの詳細については、次を参照してください。[への対応および変更の反映](../modeling/responding-to-and-propagating-changes.md)します。  
  
 ルールは、元に戻す、やり直し操作、または rollback コマンドの後に起動されません。  
  
## <a name="transaction-context"></a>トランザクションのコンテキスト  
 各トランザクションでは、情報を格納するディクショナリには。  
  
 `store.TransactionManager`  
  
 `.CurrentTransaction.TopLevelTransaction`  
  
 `.Context.Add(aKey, aValue);`  
  
 これは、ルール間で情報を転送する場合に特に役立ちます。  
  
## <a name="transaction-state"></a>トランザクションの状態  
 避ける必要があります、変更が元に戻すか、トランザクションを再実行によって発生した場合、変更の伝達。 これは、たとえば、ストア内の別の値を更新できるプロパティの値のハンドラーを記述する場合に発生します。 元に戻す操作では、前の状態ストア内のすべての値がリセットされ、ために、更新された値を計算する必要はありません。 このコードを使用します。  
  
```  
if (!this.Store.InUndoRedoOrRollback) {...}  
```  
  
 ルールは、ストアは、最初に、ファイルから読み込まれるときに起動できます。 これらの変更に応答を避けるためには、次のコマンドを使用します。  
  
```  
if (!this.Store.InSerializationTransaction) {...}  
  
```



