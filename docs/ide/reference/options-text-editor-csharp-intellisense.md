---
title: "[オプション]、[テキスト エディター]、[C#]、[IntelliSense] | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Intellisense
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Intellisense
helpviewer_keywords:
- IntelliSense [J#], options
- underlines, wavy
- IntelliSense [C#], options
- IntelliSense [C#], wavy underlines
- wavy underlines
- Text Editor Options dialog box, IntelliSense
ms.assetid: 3466dedb-e5f4-424c-8dd8-e4941b2f4fc2
caps.latest.revision: 25
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
ms.openlocfilehash: b34b280b3558003c5c3ad92515d773bc7d45fdda
ms.contentlocale: ja-jp
ms.lasthandoff: 05/24/2017

---
# <a name="options-text-editor-c-intellisense"></a>[オプション]、[テキスト エディター]、[C#]、[IntelliSense]
Visual C# での IntelliSense の動作設定を変更するには、[**IntelliSense**] プロパティ ページを使用します。 [**IntelliSense**] プロパティ ページにアクセスするには、[**ツール**] メニューの [**オプション**] をクリックして、[**テキスト エディター**] フォルダーで [**C#**] をクリックし、[**IntelliSense**] をクリックします。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](../../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
 **[IntelliSense]** プロパティ ページには、以下のプロパティがあります。  
  
## <a name="completion-lists"></a>入力候補一覧  
 **文字が入力された後に入力候補一覧を表示する**  
 このオプションを選択すると、入力を開始したときに IntelliSense によって入力候補一覧が自動的に表示されます。 このオプションを選択しない場合でも、IntelliSense の入力候補は [**IntelliSense**] メニューから、または CTRL キーを押しながら SPACE キーを押して使用できます。  
  
 **入力候補一覧にキーワードを配置する**  
 このオプションを選択すると、IntelliSense によって C# キーワード ([class](/dotnet/csharp/language-reference/keywords/class) など) が入力候補一覧に追加されます。  
  
 **入力候補一覧にコード スニペットを配置する**  
 このオプションを選択すると、IntelliSense によって C# コード スニペットのエイリアスが入力候補一覧に追加されます。 コード スニペットのエイリアスがキーワードと同じ場合 ([class](/dotnet/csharp/language-reference/keywords/class) など)、キーワードは、ショートカットで置き換えられます。 詳細については、「[Visual C# のコード スニペット](../../ide/visual-csharp-code-snippets.md)」を参照してください。  
  
## <a name="selection-in-completion-lists"></a>入力候補一覧からの選択  
 **次の文字の入力によって確定する**  
 入力すると、入力候補一覧内の選択した項目に対して IntelliSense のオート コンプリートを実行するすべての文字を指定します。  
  
 **スペース バーを押すことによって確定する**  
 入力候補一覧内の選択した項目に対して IntelliSense のオート コンプリートを実行するために、スペース バーを押すアクションを含めることを指定します。  
  
 **単語を完全に入力した後 Enter キーで新しい行を追加する**  
 入力候補一覧内のエントリのすべての文字を入力して ENTER キーを押すと、新しい行が自動的に作成され、新しい行にカーソルが移動することを指定します。  
  
 たとえば、`else` を入力し、ENTER キーを押すと、エディターには次のように表示されます。  
  
 `else`  
  
 `|` (カーソルの位置)  
  
 ただし、`el` のみを入力して ENTER キーを押すと、エディターには次のように表示されます。  
  
 `else|` (カーソルの位置)  
  
## <a name="intellisense-member-selection"></a>IntelliSense メンバーの選択  
 **最近使用されたメンバーをあらかじめ選択する**  
 このオプションを選択すると、統合開発環境 (IDE) での現在のセッション中に、オブジェクト名の自動補完のために、ポップアップ メンバーの一覧ボックスで最近選択したメンバーが IntelliSense によってあらかじめ選択されます。 最近使用したメンバーの履歴は、IDE の各セッションの間に消去されます。 詳細については、「[最近使用されたメンバーに対する IntelliSense](../../ide/visual-csharp-intellisense.md#most-recently-used-members)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [[全般]、[環境]、[オプション] ダイアログ ボックス](../../ide/reference/general-environment-options-dialog-box.md)   
 [XML ドキュメント コメント](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)   
 [IntelliSense の使用](../../ide/using-intellisense.md)
