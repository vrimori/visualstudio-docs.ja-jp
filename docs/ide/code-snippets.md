---
title: "コード スニペット | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.ExpansionManagerImport
- vs.codesnippetmanager
helpviewer_keywords:
- code snippets, replacement parameters
- code snippets, surround with
- replacement parameters
- code snippets, expansion
- surround with
- code snippets
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 999a4f6fb5c60b7d2708134706024a42d44b2611
ms.sourcegitcommit: ebe9fb5eda724936f7a059d35d987c29dffdb50d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/07/2017
---
# <a name="code-snippets"></a>コード スニペット

コードスニペットは、コンテキスト メニュー コマンドまたはホット キーの組み合わせを使用してコード ファイルに挿入できる、再利用可能なコードの小さなブロックです。 通常、スニペットには try-finally または if-else などよく使用されるコード ブロックが含まれていますが、スニペットを使用してクラス全体またはメソッド全体を挿入することもできます。

## <a name="expansion-snippets-and-surround-with-snippets"></a>拡張スニペットとブロックの挿入用スニペット

Visual Studio には、2 種類のコード スニペットがあります。1 つ目は、指定した挿入ポイントに追加され、スニペット ショートカットを置換できる拡張スニペットで、2 つ目は、選択したコード ブロックの周囲に追加される、ブロックの挿入用スニペット (C# および C++ のみ) です。

挿入スニペットの例: C# では、ショートカット tryf は try-finally ブロックの挿入に使用されます。

```csharp
try
{

}
finally
{

}
```

このスニペットを挿入するには、コード ウィンドウのコンテキスト メニューで **[スニペットの挿入]** をクリックしてから、**[Visual C#]** をクリックし、「`tryf`」と入力して、**Tab** キーを押します。または、「`tryf`」と入力して **Tab** キーを 2 回押します。

ブロックの挿入用スニペットの例: C++ では、ショートカット `if` は挿入スニペットまたはブロックの挿入用スニペットとして使用できます。 コード行 (例: `return FALSE;`) を選択し、**[ブロックの挿入]**、**[if]** をクリックすると、行の周りにスニペットが展開されます。

```cpp
if (true)
{
    return FALSE;
}
```

## <a name="snippet-replacement-parameters"></a>スニペットの置換パラメーター

スニペットには置換パラメーターを含めることができます。置換パラメーターとは、作成中の実際のコードに応じた置換を必要とするプレースホルダーです。 前の例で、`true` は置換パラメーターであり、適切な条件への置換が必要です。 置換を行うと、スニペット内の同じ置換パラメーターのすべてのインスタンスでもこれが繰り返されます。

たとえば、Visual Basic には、プロパティを挿入するコード スニペットがあります。 コード ウィンドウのコンテキスト メニューで **[スニペットの挿入]** をクリックし、**[コード パターン]**、**[プロパティ、プロシージャ、イベント]**、[プロパティの定義] の順にクリックします。 次のコードが挿入されます。

```vb
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

`newPropertyValue` を `m_property` に変更すると、`newPropertyValue` のすべてのインスタンスが変更されます。 プロパティ宣言の `String` を `Int` に変更すると、set メソッド内の値も `Int` に変更されます。

## <a name="code-snippet-manager"></a>コード スニペット マネージャー

現在インストールされているすべてのコード スニペットと、ディスク上でのそれらの場所を表示するには、**[ツール]**、**[コード スニペット マネージャー]** の順に選択します。 スニペットが言語別に表示されます。

**[コード スニペット マネージャー]** ダイアログの **[追加]** と **[削除]** ボタンを使用して、スニペット ディレクトリを追加および削除することができます。 個々のコード スニペットを追加するには、**[インポート]** ボタンを使用します。

## <a name="see-also"></a>関連項目

[チュートリアル: コード スニペットを作成する](../ide/walkthrough-creating-a-code-snippet.md)  
[方法: コード スニペットを配布する](../ide/how-to-distribute-code-snippets.md)  
[コード スニペットを使用するためのベスト プラクティス](../ide/best-practices-for-using-code-snippets.md)  
[スニペットのトラブルシューティング](../ide/troubleshooting-snippets.md)  
[Visual C# のコード スニペット](../ide/visual-csharp-code-snippets.md)  
[Visual C# のコード スニペット](../ide/visual-cpp-code-snippets.md)  
[コード スニペット スキーマ リファレンス](../ide/code-snippets-schema-reference.md)