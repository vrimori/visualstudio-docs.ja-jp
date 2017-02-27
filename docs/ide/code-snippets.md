---
title: "コード スニペット | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.ExpansionManagerImport"
  - "vs.codesnippetmanager"
helpviewer_keywords: 
  - "コード スニペット"
  - "コード スニペット, 展開"
  - "コード スニペット, 置換パラメーター"
  - "コード スニペット, ブロックの挿入"
  - "置換パラメーター"
  - "ブロックの挿入"
ms.assetid: 85976ad9-4c9a-4e7b-896e-66ec6f955199
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# コード スニペット
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

コードスニペットは、コンテキスト メニュー コマンドまたはホット キーの組み合わせを使用してコード ファイルに挿入できる、再利用可能なコードの小さなブロックです。  通常、スニペットには try\-finally または if\-else などよく使用されるコード ブロックが含まれていますが、スニペットを使用してクラス全体またはメソッド全体を挿入することもできます。  
  
## 拡張スニペットとブロックの挿入用スニペット  
 Visual Studio には、2 種類のコード スニペットがあります。1 つ目は、指定した挿入ポイントに追加され、スニペット ショートカットを置換できる拡張スニペットで、2 つ目は、選択したコード ブロックの周囲に追加される、ブロックの挿入用スニペット \(C\# および C\+\+ のみ\) です。  
  
 挿入スニペットの例: C\# では、ショートカット tryf は try\-finally ブロックの挿入に使用されます。  
  
```  
try  
{  
  
}  
finally  
{  
  
}  
  
```  
  
 このスニペットを挿入するには、コード ウィンドウのコンテキスト メニューで **\[スニペットの挿入\]** をクリックしてから、**\[Visual C\#\]** をクリックし、 `tryf` と入力して、Tab キーを押します。あるいは `tryf` と入力して Tab キーを押し、もう一度 Tab キーを押します。  
  
 ブロックの挿入用スニペットの例: C\+\+ では、ショートカット `if` は挿入スニペットまたはブロックの挿入用スニペットとして使用できます。  コード行 \(例: `return FALSE;`\) を選択し、**\[ブロックの挿入\]**、**\[if\]** をクリックすると、行の周りにスニペットが展開されます。  
  
```  
if (true)  
{  
    return FALSE;  
}  
  
```  
  
## スニペットの置換パラメーター  
 スニペットには置換パラメーターを含めることができます。置換パラメーターとは、作成中の実際のコードに応じた置換を必要とするプレースホルダーです。  前の例で、`true` は置換パラメーターであり、適切な条件への置換が必要です。  置換を行うと、スニペット内の同じ置換パラメーターのすべてのインスタンスでもこれが繰り返されます。  
  
 たとえば、Visual Basic には、プロパティを挿入するコード スニペットがあります。  コード ウィンドウのコンテキスト メニューで **\[スニペットの挿入\]** をクリックし、**\[コード パターン\]**、**\[プロパティ、プロシージャ、イベント\]**、\[プロパティの定義\] の順にクリックします。  次のコードが挿入されます。  
  
```  
Private newPropertyValue As String  
Public Property NewProperty() As String  
    Get  
        Return newPropertyValue  
    End Get  
    Set(ByVal value As String)  
        newPropertyValue = value  
    End Set  
End Property  
  
```  
  
 `newPropertyValue` を `m_property` に変更すると、`newPropertyValue` のすべてのインスタンスが変更されます。  プロパティ宣言の `String` を `Int` に変更すると、set メソッド内の値も `Int` に変更されます。  
  
## コード スニペット マネージャー  
 現在インストールされているコード スニペットと、ディスク上の場所に関する情報を表示するには、**\[ツール \/ コード スニペット マネージャー\]** をクリックします。  スニペットが言語別に表示されます。  
  
 **\[コード スニペット マネージャー\]** ダイアログの **\[追加\]** と **\[削除\]** ボタンを使用して、スニペット ディレクトリを追加および削除することができます。  個々のコード スニペットを追加するには、**\[インポート\]** ボタンを使用します。  
  
## 参照  
 [チュートリアル: コード スニペットを作成する](../ide/walkthrough-creating-a-code-snippet.md)   
 [方法: コード スニペットを配布する](../ide/how-to-distribute-code-snippets.md)   
 [コード スニペットを使用するためのベスト プラクティス](../ide/best-practices-for-using-code-snippets.md)   
 [スニペットのトラブルシューティング](../ide/troubleshooting-snippets.md)   
 [Visual C\# のコード スニペット](../ide/visual-csharp-code-snippets.md)   
 [Visual C\+\+ コード スニペット](../ide/visual-cpp-code-snippets.md)   
 [コード スニペット スキーマ リファレンス](../ide/code-snippets-schema-reference.md)