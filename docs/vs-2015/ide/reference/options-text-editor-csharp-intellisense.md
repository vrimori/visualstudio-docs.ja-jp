---
title: '[オプション]、[テキスト エディター]、[C#]、[IntelliSense] | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
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
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 31c9909e5ea9364e806fdd2d7a39903bf1468abb
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49262172"
---
# <a name="options-text-editor-c-intellisense"></a>[オプション]、[テキスト エディター]、[C#]、[IntelliSense]
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Visual C# での IntelliSense の動作設定を変更するには、**[IntelliSense]** プロパティ ページを使用します。 **[IntelliSense]** プロパティ ページにアクセスするには、**[ツール]** メニューの **[オプション]** をクリックして、**[テキスト エディター]** フォルダーで **[C#]** をクリックし、**[IntelliSense]** をクリックします。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
 **[IntelliSense]** プロパティ ページには、以下のプロパティがあります。  
  
## <a name="completion-lists"></a>入力候補一覧  
 **文字が入力された後に入力候補一覧を表示する**  
 このオプションを選択すると、入力を開始したときに IntelliSense によって入力候補一覧が自動的に表示されます。 このオプションを選択しない場合でも、IntelliSense の入力候補は **[IntelliSense]** メニューから、または CTRL キーを押しながら SPACE キーを押して使用できます。  
  
 **入力候補一覧にキーワードを配置する**  
 このオプションを選択すると、IntelliSense によって C# キーワード ([class](http://msdn.microsoft.com/library/b95d8815-de18-4c3f-a8cc-a0a53bdf8690) など) が入力候補一覧に追加されます。  
  
 **入力候補一覧にコード スニペットを配置する**  
 このオプションを選択すると、IntelliSense によって C# コード スニペットのエイリアスが入力候補一覧に追加されます。 コード スニペットのエイリアスがキーワードと同じ場合 ([class](http://msdn.microsoft.com/library/b95d8815-de18-4c3f-a8cc-a0a53bdf8690) など)、キーワードは、ショートカットで置き換えられます。 詳細については、「[Visual C# のコード スニペット](../../ide/visual-csharp-code-snippets.md)」を参照してください。  
  
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
 このオプションを選択すると、統合開発環境 (IDE) での現在のセッション中に、オブジェクト名の自動補完のために、ポップアップ メンバーの一覧ボックスで最近選択したメンバーが IntelliSense によってあらかじめ選択されます。 最近使用したメンバーの履歴は、IDE の各セッションの間に消去されます。 詳細については、「[最近使用されたメンバーに対する IntelliSense](../../misc/intellisense-for-most-recently-used-members.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [[全般]、[環境]、[オプション] ダイアログ ボックス](../../ide/reference/general-environment-options-dialog-box.md)   
 [XML ドキュメント コメント](http://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199)   
 [IntelliSense の使用](../../ide/using-intellisense.md)



