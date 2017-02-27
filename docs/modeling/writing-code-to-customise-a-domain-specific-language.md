---
title: "ドメイン固有言語をカスタマイズするコードの記述 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ドメイン固有言語のプログラミング"
ms.assetid: a4a17f5b-9c97-4575-b2d1-3182c1896b72
caps.latest.revision: 29
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 29
---
# ドメイン固有言語をカスタマイズするコードの記述
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ここではドメイン固有言語モデルにアクセスしたり変更または作成するカスタム コードを使用する方法を示します。  
  
 DSL を使用するコードを作成できる複数のコンテキストがあります :  
  
-   **カスタム コマンド。**ユーザーが図上で右クリックして呼び出すことができるモデルを変更できます。コマンドを作成できます。  詳細については、「[方法: ショートカット メニューにコマンドを追加する](../Topic/How%20to:%20Add%20a%20Command%20to%20the%20Shortcut%20Menu.md)」を参照してください。  
  
-   **検証。**モデルは正しい状態であることを検証するコードを記述できます。  詳細については、「[ドメイン固有言語における検証](../modeling/validation-in-a-domain-specific-language.md)」を参照してください。  
  
-   **既定の動作をオーバーライドします。**DslDefinition.dsl から生成されたコードのさまざまな側面を変更できます。  詳細については、「[生成済みクラスのオーバーライドおよび拡張](../modeling/overriding-and-extending-the-generated-classes.md)」を参照してください。  
  
-   **テキスト変換します。**プログラム コードを生成するにはたとえばモデルにアクセスしテキスト ファイルを生成するコードを含むテキスト テンプレートを作成できます。  詳細については、「[ドメイン固有言語からのコード生成](../modeling/generating-code-from-a-domain-specific-language.md)」を参照してください。  
  
-   **他の Visual Studio 拡張機能。**モデルを読み取って変更する別の VSIX 拡張機能を作成できます。  詳細については、「[方法: プログラム コード内のファイルからモデルを開く](../modeling/how-to-open-a-model-from-file-in-program-code.md)」を参照してください。  
  
 DslDefinition.dsl で定義したクラスのインスタンスはメモリ  *ストア \(IMS\)*またはストアと呼ばれるデータ構造に格納されます *。* でDSL を定義するクラスは引数としてコンストラクターにストアを常に書き込みます。  たとえばDSL が Example という名前のクラスを定義する場合 :  
  
 `Example element = new Example (theStore);`  
  
 ストアにはオブジェクトを保持すること \(ではなく通常のオブジェクト\) いくつかの利点があります。  
  
-   **トランザクション** 。  トランザクションに関連する一連の変更をグループ化できます :  
  
     `using (Transaction t = store.TransactionManager.BeginTransaction("updates"))`  
  
     `{`  
  
     `// make several changes to Store elements here`  
  
     `t.Commit();`  
  
     `}`  
  
     例外が変更中に発生すると最後のコミット \(\) が実行されないようにストアは前の状態にリセットされます。  これはエラーが矛盾した状態にモデルを継続することを確認できます。  詳細については、「[プログラム コードにおけるモデル内の移動およびモデルの更新](../modeling/navigating-and-updating-a-model-in-program-code.md)」を参照してください。  
  
-   **バイナリ関係** 。  2 個のクラス間の関係を定義する場合は両端のインスタンスに他の末尾に移動するプロパティがあります。  2 種類の末尾は常に同期されます。  たとえばParents とその子という名前のロールの親子関係の関係を定義して記述できます。:  
  
     `John.Children.Add(Mary)`  
  
     次の式の両方で同様です :  
  
     `John.Children.Contains(Mary)`  
  
     `Mary.Parents.Contains(John)`  
  
     また記述して同じ効果を実現できます :  
  
     `Mary.Parents.Add(John)`  
  
     詳細については、「[プログラム コードにおけるモデル内の移動およびモデルの更新](../modeling/navigating-and-updating-a-model-in-program-code.md)」を参照してください。  
  
-   **イベントと規則** 。  指定した変更が発生するたびに発生する規則を定義できます。  規則はダイアグラムの図形を最新表示してモデル要素として使用されます。  詳細については、「[変更内容への対応および変更内容の反映](../modeling/responding-to-and-propagating-changes.md)」を参照してください。  
  
-   **シリアル化** 。  ストアはファイルに含めるオブジェクトをシリアル化する標準的な方法を提供します。  シリアル化および逆シリアル化する規則をカスタマイズできます。  詳細については、「[ファイル格納処理および XML シリアル化処理のカスタマイズ](../modeling/customizing-file-storage-and-xml-serialization.md)」を参照してください。  
  
## 参照  
 [ドメイン固有言語のカスタマイズおよび拡張](../modeling/customizing-and-extending-a-domain-specific-language.md)