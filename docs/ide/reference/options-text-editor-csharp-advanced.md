---
title: "[オプション]、[テキスト エディター]、[C#]、[詳細] | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Advanced
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
helpviewer_keywords:
- XML comments
- XML documentation, generating
- outlining options [C#]
- outlining options [J#]
- XML documentation, creating
ms.assetid: 947f9d9a-b0f3-408d-9866-d82895bcee31
caps.latest.revision: 22
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 61a061b6a58b18451fc53c8d53f77889cc1ea253
ms.contentlocale: ja-jp
ms.lasthandoff: 05/24/2017

---
# <a name="options-text-editor-c-advanced"></a>[オプション]、[テキスト エディター]、[C#]、[詳細]
このダイアログ ボックスを使用して、Visual C# のエディターの書式設定、コードのリファクタリング、および XML ドキュメントのコメントの設定を変更します。 このダイアログ ボックスを表示するには、[**ツール**] メニューの [**オプション**] をクリックし、[**テキスト エディター**] フォルダー、[**C#**] を順に展開し、[**詳細設定**] をクリックします。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](../../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
## <a name="outlining"></a>アウトライン  
 ファイルが開かれたときにアウトライン モードを実行する  
 選択すると、コードの折りたたみ可能なブロックを作成するコード ファイルが自動的にアウトラインになります。 初めてファイルが開かれると、#regions ブロックとアクティブでないコード ブロックが折りたたまれます。  
  
## <a name="editor-help"></a>エディターのヘルプ  
 エディターでエラーに下線を引く  
 コードのビルド エラーを識別します。 このオプションを選択すると、色付きの波線が表示されます。色にはそれぞれ特定の意味があります。  
  
-   赤は解析エラーです。  
  
-   青はビルド エラーです。  
  
-   緑はビルドの警告です。  
  
-   紫は無効な[エディット コンティニュ](../../debugger/edit-and-continue.md)の編集内容です。  
  
 下線付きのコード セグメントの上にマウス ポインターを置いて、ヒントでエラーに関する情報を確認してください。  
  
 有効なセマンティック エラーを表示する  
 明示的なコンパイルのない特定のコンパイル エラー (たとえば、不明な型を宣言して使用したり、不明なプロパティを参照したりする) を特定します。  
  
 カーソルの下にあるシンボルへの参照をハイライトする  
 シンボル内にカーソルを置いたり、シンボルをクリックしたりすると、コード ファイル内のそのシンボルのすべてのインスタンスが強調表示されます。  
  
## <a name="refactoring"></a>リファクタリング  
 リファクタリングの結果を確認する  
 ビルド エラーを含むコードをリファクタリングする場合、またはリファクタリングによってコード参照が元のバインドとは別のものにバインドされる場合に、[**検証結果**] ダイアログ ボックスが表示されます。  
  
 メンバーにコンパイラが生成した参照が指定されているときに警告する  
 コンパイラによって生成された参照と同じ名前を持つメンバーをリファクタリングすると、警告ダイアログ ボックスが表示されます。  
  
## <a name="xml-documentation-comments"></a>XML ドキュメントのコメント  
 /// が入力されたとき、XML ドキュメントのコメントを生成する  
 選択すると、/// コメント イントロダクションを入力した後に、\<summary> start タグと end タグが XML ドキュメント コメントに自動的に挿入されます。 XML ドキュメントの詳細については、「[XML ドキュメント コメント](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)」を参照してください。  
  
## <a name="implement-interface"></a>インターフェイスの実装  
 生成されたコードを #region で囲む  
 [インターフェイスの実装] または [インターフェイスを明示的に実装] が使用されると、#region \<*interface name*> メンバーがメソッドの前後に挿入されます。  
  
## <a name="organize-usings"></a>using の整理  
 using を並べ替える際に、'System' ディレクティブを先頭に配置する  
 選択すると、`System` using ディレクティブが他の using ディレクティブより前に表示されます。 詳細については、[Visual C# IntelliSense](../../ide/visual-csharp-intellisense.md#automatic-code-generation) の「using の整理」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [XML ドキュメント コメント](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)   
 [言語固有のエディター オプションの設定](../../ide/reference/setting-language-specific-editor-options.md)   
 [Visual C# の IntelliSense](../../ide/visual-csharp-intellisense.md)
