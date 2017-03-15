---
title: "Visual C# のコード スニペット | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "スニペット [C#]、既定のスニペット"
  - "スニペット[C#]、コード スニペット挿入機能"
  - "コード スニペット挿入機能 [J#]"
  - "コード スニペット挿入機能 [C#]"
  - "Visual C#、既定のスニペット"
ms.assetid: dbea3dd6-e650-4190-b874-c9f097d7de6e
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# <a name="visual-c-code-snippets"></a>Visual C# のコード スニペット
コード スニペットは、あらかじめ用意されているコードのスニペットで、コードにすぐに挿入できます。 たとえば、`for` コード スニペットは空の `for` ループを作成します。 一部のコード スニペットは surround-with コード スニペットであり、コード行を選んでから、選んだコード行を組み込むコード スニペットを選ぶことができます。 たとえば、コード行を選んでから `for` コード スニペットをアクティブにすると、選んだコード行がループ ブロックの中に含まれる `for` ループが作成されます。 コード スニペットを使うと、速く、容易に、信頼性の高いプログラム コードを作成できます。  
  
 カーソル位置にコード スニペットを挿入したり、現在選択されているコード ブロックを囲むように surround-with コード スニペットを挿入したりすることができます。 コード スニペット挿入機能は、**IntelliSense** メニューの **[コード スニペットの挿入]** または **[ブロックの挿入]** コマンドで、または Ctrl キーを押しながら T キー、X キーの順に押すか、Ctrl キーを押しながら K キー、S キーの順に押すことで、起動できます。  
  
 コード スニペット挿入機能では、すべての利用可能なコード スニペットのコード スニペット名が表示されます。 また、コード スニペット挿入機能には、コード スニペットの名前または名前の一部を入力できる入力ダイアログ ボックスもあります。 最も近いコード スニペット名が強調表示されます。 Tab キーを押すと、コード スニペット挿入機能が閉じて、現在選択されているコード スニペットが挿入されます。 Esc キーを押すか、コード エディターをマウスでクリックすると、コード スニペットを挿入することなくコード スニペット挿入機能が閉じます。  
  
## <a name="default-code-snippets"></a>既定のコード スニペット  
 既定では、Visual Studio には次のコード スニペットが含まれます。  
  
|名前 (またはショートカット)|説明|スニペットを挿入できる場所|  
|--------------------------|-----------------|---------------------------------------|  
|#if|[#if](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-if) ディレクティブと [#endif](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-endif) ディレクティブを作成します。|任意の場所。|  
|#region|[#region](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-region) ディレクティブと [#endregion](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-endregion) ディレクティブを作成します。|任意の場所。|  
|~|外側のクラスのデストラクターを作成します。|クラスの内部。|  
|attribute|<xref:System.Attribute> から派生するクラスの宣言を作成します。|名前空間 (グローバル名前空間を含む)、クラス、または構造体の内部。|  
|checked|[checked](/dotnet/csharp/language-reference/keywords/checked) ブロックを作成します。|メソッド、インデクサー、プロパティ アクセサー、またはイベント アクセサーの内部。|  
|class|クラスの宣言を作成します。|名前空間 (グローバル名前空間を含む)、クラス、または構造体の内部。|  
|ctor|外側のクラスのコンストラクターを作成します。|クラスの内部。|  
|cw|<xref:System.Console.WriteLine%2A> の呼び出しを作成します。|メソッド、インデクサー、プロパティ アクセサー、またはイベント アクセサーの内部。|  
|do|[do](/dotnet/csharp/language-reference/keywords/do)`while` ループを作成します。|メソッド、インデクサー、プロパティ アクセサー、またはイベント アクセサーの内部。|  
|else|[else](/dotnet/csharp/language-reference/keywords/if-else) ブロックを作成します。|メソッド、インデクサー、プロパティ アクセサー、またはイベント アクセサーの内部。|  
|enum|[enum](/dotnet/csharp/language-reference/keywords/enum) 宣言を作成します。|名前空間 (グローバル名前空間を含む)、クラス、または構造体の内部。|  
|equals|<xref:System.Object> クラスで定義されている <xref:System.Object.Equals%2A> メソッドをオーバーライドするメソッド宣言を作成します。|クラスまたは構造体の内部。|  
|exception|exception (既定では <xref:System.Exception>) から派生するクラスの宣言を作成します。|名前空間 (グローバル名前空間を含む)、クラス、または構造体の内部。|  
|for|[for](/dotnet/csharp/language-reference/keywords/for) ループを作成します。|メソッド、インデクサー、プロパティ アクセサー、またはイベント アクセサーの内部。|  
|foreach|[foreach](/dotnet/csharp/language-reference/keywords/foreach-in) ループを作成します。|メソッド、インデクサー、プロパティ アクセサー、またはイベント アクセサーの内部。|  
|forr|各イテレーションの後でループ変数をデクリメントする [for](/dotnet/csharp/language-reference/keywords/for) ループを作成します。|メソッド、インデクサー、プロパティ アクセサー、またはイベント アクセサーの内部。|  
|if|[if](/dotnet/csharp/language-reference/keywords/if-else) ブロックを作成します。|メソッド、インデクサー、プロパティ アクセサー、またはイベント アクセサーの内部。|  
|indexer|インデクサーの宣言を作成します。|クラスまたは構造体の内部。|  
|interface|[interface](/dotnet/csharp/language-reference/keywords/interface) 宣言を作成します。|名前空間 (グローバル名前空間を含む)、クラス、または構造体の内部。|  
|invoke|イベントを安全に呼び出すブロックを作成します。|メソッド、インデクサー、プロパティ アクセサー、またはイベント アクセサーの内部。|  
|iterator|反復子を作成します。|クラスまたは構造体の内部。|  
|iterindex|入れ子になったクラスを使って "名前付き" の反復子とインデクサーのペアを作成します。|クラスまたは構造体の内部。|  
|lock|[lock](/dotnet/csharp/language-reference/keywords/lock-statement) ブロックを作成します。|メソッド、インデクサー、プロパティ アクセサー、またはイベント アクセサーの内部。|  
|mbox|<xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> の呼び出しを作成します。 場合によっては、System.Windows.Forms.dll への参照を追加する必要があります。|メソッド、インデクサー、プロパティ アクセサー、またはイベント アクセサーの内部。|  
|namespace|[namespace](/dotnet/csharp/language-reference/keywords/namespace) 宣言を作成します。|名前空間 (グローバル名前空間を含む) の内部。|  
|prop|[自動実装プロパティ](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties)の宣言を作成します。|クラスまたは構造体の内部。|  
ropfull|get および set アクセサーを持つプロパティの宣言を作成します。|クラスまたは構造体の内部。|  
|propg|プライベートな "set" アクセサーを持つ読み取り専用の[自動実装プロパティ](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties)を作成します。|クラスまたは構造体の内部。|  
|sim|[static](/dotnet/csharp/language-reference/keywords/static) [int](/dotnet/csharp/language-reference/keywords/int) の Main メソッドの宣言を作成します。|クラスまたは構造体の内部。|  
|struct|[struct](/dotnet/csharp/language-reference/keywords/struct) 宣言を作成します。|名前空間 (グローバル名前空間を含む)、クラス、または構造体の内部。|  
|svm|[static](/dotnet/csharp/language-reference/keywords/static) [void](/dotnet/csharp/language-reference/keywords/void) の Main メソッドの宣言を作成します。|クラスまたは構造体の内部。|  
|switch|[switch](/dotnet/csharp/language-reference/keywords/switch) ブロックを作成します。|メソッド、インデクサー、プロパティ アクセサー、またはイベント アクセサーの内部。|  
|try|[try-catch](/dotnet/csharp/language-reference/keywords/try-catch) ブロックを作成します。|メソッド、インデクサー、プロパティ アクセサー、またはイベント アクセサーの内部。|  
|tryf|[try-finally](/dotnet/csharp/language-reference/keywords/try-finally) ブロックを作成します。|メソッド、インデクサー、プロパティ アクセサー、またはイベント アクセサーの内部。|  
|unchecked|[unchecked](/dotnet/csharp/language-reference/keywords/unchecked) ブロックを作成します。|メソッド、インデクサー、プロパティ アクセサー、またはイベント アクセサーの内部。|  
|unsafe|[unsafe](/dotnet/csharp/language-reference/keywords/unsafe) ブロックを作成します。|メソッド、インデクサー、プロパティ アクセサー、またはイベント アクセサーの内部。|  
|使用|[using](/dotnet/csharp/language-reference/keywords/using-directive) ディレクティブを作成します。|名前空間 (グローバル名前空間を含む) の内部。|  
|while|[while](/dotnet/csharp/language-reference/keywords/while) ループを作成します。|メソッド、インデクサー、プロパティ アクセサー、またはイベント アクセサーの内部。|  
  
## <a name="see-also"></a>関連項目  
 [コード スニペットの関数](../ide/code-snippet-functions.md)   
 [コード スニペット](../ide/code-snippets.md)   
 [方法 : 新規スニペットを置換で作成する](http://msdn.microsoft.com/en-us/8d56d43c-097a-475b-aa85-cae1554b6338)   
 [テンプレート パラメーター](../ide/template-parameters.md)   
 [方法 : surround-with コード スニペットを使用する](../ide/how-to-use-surround-with-code-snippets.md)   
 


<!--HONumber=Feb17_HO4-->


