---
title: トランザクションを使用して UML モデルの更新をリンク |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML API, transactions
ms.assetid: a1df6c38-a3d1-4a3f-82bc-c8f363ab916e
caps.latest.revision: 18
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 99cbbb2a2c67ec077fec8554694cba58fc37bd59
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49844498"
---
# <a name="link-uml-model-updates-by-using-transactions"></a>トランザクションを使用して UML モデルの更新をリンクする
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio で UML デザイナー向けに拡張機能を定義するときと呼ばれる単一のトランザクションにいくつかの変更をグループ化することができます、*リンクされた undo コンテキスト*します。 UML モデルをサポートする Visual Studio のバージョンを確認するには、「 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)」を参照してください。  
  
 既定では、ユーザーは、コードによってモデルに加えられた変更を個別に元に戻すことができます。 たとえば、2 つの UML クラスの名前を入れ替えるメニュー コマンドを定義した場合に、ユーザーがそのコマンドを起動して、元に戻す操作を 1 回実行するとします。 この場合、1 つの名前に対する変更は元に戻されますが、もう 1 つの名前の変更は元に戻されず、モデルは意図されていない状態になります。  
  
 このような状況を回避するために、コードでトランザクション内の一連の変更を実行できます。 これにより、一連の変更がユーザーにとって単一の変更に見えます。 その後に元に戻すコマンドを実行すると、一連の操作が元に戻されます。  
  
 さらに、例外をスローするかまたはトランザクションを中止することで、部分的に完了した変更のセットをコードで元に戻すことができるという利点もあります。  
  
## <a name="to-group-changes-into-a-single-transaction"></a>一連の変更を単一のトランザクションにグループ化するには  
 プロジェクトの参照に次の .NET アセンブリが含まれていることを確認します。  
  
 **Microsoft.VisualStudio.Modeling.Sdk します。[バージョン] .dll**  
  
 クラス内で、<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ILinkedUndoContext> 型のインポート プロパティを宣言します。  
  
 `using Microsoft.VisualStudio.Modeling.ExtensionEnablement;`  
  
 `...`  
  
 `class … {`  
  
 `[Import]`  
  
 `public ILinkedUndoContext LinkedUndoContext { get; set; }`  
  
 モデルを変更するメソッドで、変更をトランザクションに含めます。  
  
 `using (ILinkedUndoTransaction transaction =`  
  
 `LinkedUndoContext.BeginTransaction("my updates"))`  
  
 `{`  
  
 `// code to update model elements or shapes goes here`  
  
 `transaction.Commit();`  
  
 `}`  
  
 次の点に注意してください。  
  
-   トランザクションの最後に必ず `Commit()` を含める必要があります。 トランザクションがコミットされることなく破棄されると、トランザクションはロールバックされます。 つまり、モデルは、トランザクションが開始された時点の状態に復元されます。  
  
-   トランザクション内でキャッチされない例外が発生すると、トランザクションはロールバックされます。 一般的なパターンとしては、トランザクションの `using` ブロックを `try…catch` ブロックで囲む方法があります。  
  
-   トランザクションは、入れ子にできます。  
  
-   `BeginTransaction()` には、任意の空白でない名前を付けることができます。  
  
-   これらのトランザクションの影響を受けるのは、UML モデル ストアのみです。 モデリング トランザクションは、変数、外部ストア (ファイルやデータベースなど)、レイヤー図、およびコード モデルに影響を及ぼしません。  
  
## <a name="example"></a>例  
  
```  
    using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
    using Microsoft.VisualStudio.Uml.Interfaces;  
    using Microsoft.VisualStudio.Uml.Classes;  
    using Microsoft.VisualStudio.Uml.Extensions;  
    using System.Linq;  
    using System.ComponentModel.Composition;  
 ...  
  [Import]  
  public ILinkedUndoContext LinkedUndoContext { get; set; }  
  
  /// <summary>  
  /// Swap the names of the currently selected elements.  
  /// </summary>  
  public void Execute(IMenuCommand command)  
  {  
    var selectedShapes =  
      Context.CurrentDiagram.GetSelectedShapes<IClassifier>();  
    if (selectedShapes.Count() < 2) return;  
    IClassifier firstElement = selectedShapes.First().Element;  
    IClassifier lastElement = selectedShapes.Last().Element;  
    string firstName = firstElement.Name;  
    // Perform changes inside a transaction so that undo  
    // works as a single change.  
    using (ILinkedUndoTransaction transaction =   
      LinkedUndoContext.BeginTransaction("Swap names"))  
    {  
        firstElement.Name = lastElement.Name;  
        lastElement.Name = firstName;  
        transaction.Commit();  
    }  
 }  
```  
  
## <a name="see-also"></a>関連項目  
 [UML API を使用したプログラミング](../modeling/programming-with-the-uml-api.md)   
 [モデリング図にメニュー コマンドを定義します。](../modeling/define-a-menu-command-on-a-modeling-diagram.md)   
 [UML モデルと図の拡張](../modeling/extend-uml-models-and-diagrams.md)



