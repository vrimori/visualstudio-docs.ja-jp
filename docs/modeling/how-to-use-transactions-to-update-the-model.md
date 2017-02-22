---
title: "方法: トランザクションを使用してモデルを更新する | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e24436a5-7f97-401b-bc83-20d188d10d5b
caps.latest.revision: 7
caps.handback.revision: 7
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# 方法: トランザクションを使用してモデルを更新する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

トランザクションはストアに加えられた変更をグループとして扱うようになります。  変更する一つの単位としてコミットまたはロールバックできるグループ化します。  
  
 プログラム コードが [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の視覚化ストアの要素とモデリング SDK 変更追加または削除した場合は必ずトランザクション内で実行する必要があります。  変更が発生したストアに関連する <xref:Microsoft.VisualStudio.Modeling.Transaction> のアクティブなインスタンスが必要です。  これはすべてのモデル要素関係図形ダイアグラムおよびプロパティに適用されます。  
  
 トランザクション機能が矛盾した状態を回避できます。  トランザクション中にエラーが発生した場合すべての変更がロールバックされます。  ユーザーが元に戻すコマンドを実行するとそれぞれの最新のトランザクションは一つの手順として扱われます。  ユーザーは別のトランザクションに明示的に配置する最新の変更の一部を元に戻すことはできません。  
  
## トランザクションの開始  
 トランザクションを管理する最も簡単な方法は `try...catch` のステートメントで囲まれた `using` のステートメントです :  
  
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
  
 最終的な `Commit()` を防ぐ変更時に例外が発生した場合ストアは前の状態にリセットされます。  これはエラーが矛盾した状態にモデルを継続することを確認できます。  
  
 1 回のトランザクション内の変更の数を設定できます。  アクティブなトランザクション内で新しいトランザクションを開くことができます。  含むトランザクションが終了する前に入れ子になったトランザクションをコミットまたはロールバック。  詳細については<xref:Microsoft.VisualStudio.Modeling.Transaction.TransactionDepth%2A> のプロパティの例を参照してください。  
  
 破棄される前にすべての変更を永続化するには`Commit` トランザクション必要があります。  トランザクション内でキャッチされない例外が発生した場合ストアは変更前の状態にリセットされます。  
  
## トランザクションをロールバックできます。  
 の値がである場合またはにトランザクション前の状態に戻すことを確認するには次のいずれかを使用できます :  
  
1.  トランザクションのスコープ内でキャッチされない例外を生成します。  
  
2.  明示的にトランザクションをロールバックするには :  
  
    ```  
    this.Store.TransactionManager.CurrentTransaction.Rollback();  
    ```  
  
## トランザクションはストア内のオブジェクトには影響しません  
 トランザクションがストアの状態のみを管理します。  これらのファイルはDSL 定義の外部の通常の型で宣言したデータベースまたはオブジェクトなどの外部項目に加えられた部分的な変更を元に戻すことはできません。  
  
 例外がストアのこのような変更が競合する場合にその例外ハンドラーの可能性を処理する必要があります。  外部リソースがストアのオブジェクトと同期して維持する 1 つがイベント ハンドラーを使用して内部ストアの要素に対する各オブジェクトを外部結合。  詳細については、「[イベント ハンドラーによって変更内容がモデル外に反映される](../modeling/event-handlers-propagate-changes-outside-the-model.md)」を参照してください。  
  
## 規則はトランザクションの最後に発生します。  
 トランザクションが終了するとトランザクションが破棄される前にストア内の要素にアタッチされている規則が適用されます。  各規則が変更されたモデル要素に適用されるメソッドです。  たとえば「固定」モデル要素の作成時にモデル要素が変更されている場合図形を作成する図形の状態を更新する場合があります。  指定点火順序はありません。  規則で行った変更は別の規則を適用できます。  
  
 独自の規則を定義できます。  詳細については、「[変更内容への対応および変更内容の反映](../modeling/responding-to-and-propagating-changes.md)」を参照してください。  
  
 規則は後に実行またはロールバック コマンド発生しません。  
  
## コンテキスト トランザクション  
 各トランザクションに必要な情報を格納できるディクショナリがあります :  
  
 `store.TransactionManager`  
  
 `.CurrentTransaction.TopLevelTransaction`  
  
 `.Context.Add(aKey, aValue);`  
  
 これは規則間で情報を転送する場合に特に便利です。  
  
## トランザクションの状態  
 場合によっては変更がトランザクションを元に戻すまたはやり直すことが原因の変更を反映させることは避ける必要があります。  これにはストア内の別の値を更新できるプロパティ値ハンドラーを作成する場合などに発生します。  元に戻す操作は以前の状態に格納されたすべての値にリセットされるため更新された値を計算する必要はありません。  このコードを使用する :  
  
```  
if (!this.Store.InUndoRedoOrRollback) {...}  
```  
  
 規則はストアがファイルの先頭に読み込まれている場合に発生します。  これらの変更に応答することを回避するには使用 :  
  
```  
if (!this.Store.InSerializationTransaction) {...}  
  
```