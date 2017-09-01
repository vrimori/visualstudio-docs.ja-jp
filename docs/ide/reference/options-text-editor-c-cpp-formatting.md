---
title: "[オプション]、[テキスト エディター]、[C/C++]、[書式設定] | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.C%2fC%2b%2b.Formatting.General
dev_langs:
- C++
helpviewer_keywords:
- Text Editor Options dialog box, formatting
ms.assetid: cb6f1cbb-5305-48da-a8e8-33fd70775d46
caps.latest.revision: 16
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
ms.openlocfilehash: 41cca3051eaf1bfdc90f6616900699b8996033b0
ms.contentlocale: ja-jp
ms.lasthandoff: 05/24/2017

---
# <a name="options-text-editor-cc-formatting"></a>[オプション]、[テキスト エディター]、[C/C++]、[書式設定]
このページでは、C または C++ でプログラムを記述する際のコード エディターの既定の動作を変更できます。  
  
 このページを表示するには、左ペインの [**オプション**] ダイアログ ボックスで、[**テキスト エディター**] フォルダー、[**C/C++**] を順に展開して、[**書式設定**] をクリックします。  
  
> [!NOTE]
>  次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。 これらの要素は、使用している Visual Studio のエディションや独自の設定によって決まります。 詳細については、「[Visual Studio IDE のカスタマイズ](../../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
## <a name="cc-options"></a>[C/C++ オプション]  
 [**自動クイック ヒントのツールヒントを有効にする**]  
 IntelliSense のクイック ヒント機能を有効または無効にします。  
  
## <a name="inactive-code"></a>[アクティブでないコード]  
 [**アクティブでないブロックの表示**]  
 `#ifdef` 宣言によって無効化されているコードが、識別しやすいように異なる色で表示されます。  
  
 [**アクティブでないコードの不透明度の無効化**]  
 アクティブでないコード ブロックを不透明にする代わりに色で識別できるようにします。  
  
 [**アクティブでないコードの不透明度**]  
 アクティブでないコード ブロックの不透明度の割合をカスタマイズできます。  
  
## <a name="indentation"></a>[インデント幅]  
 [**中かっこのインデント**]  
 関数、`for` ループなどのコード ブロックの開始後に Enter キーを押したときの中かっこの配置を構成できます。 中かっこは、コード ブロックの最初の文字位置に合わせて、またはインデント位置に合わせて配置されます。  
  
 [**自動インデントを有効にするタブ**]  
 Tab キーを押したときに現在のコード行で発生する動作を構成できます。 行がインデントされるか、またはタブが挿入されます。  
  
## <a name="miscellaneous"></a>その他  
 [**[タスク一覧] ウィンドウにコメントが列挙されます**]  
 開いているソース ファイルのコメント内に事前設定された語がないか、エディターでスキャンできます。 見つかったキーワードのエントリが [**タスク一覧**] ウィンドウに作成されます。  
  
 [**一致するトークンの強調表示**]  
 カーソルが中かっこの横に置かれたときに、その中かっこで囲まれているコードの内容を確認しやすいように、対応する中かっこが強調表示されます。  
  
## <a name="outlining"></a>アウトライン  
 [**ファイルが開かれたときにアウトライン モードを実行する**]  
 ファイルをテキスト エディターで開くときに、アウトライン表示機能を有効にできます。 詳細については、「[アウトライン](../../ide/outlining.md)」を参照してください。 このチェック ボックスをオンにすると、ファイルを開いたときにアウトライン表示機能が有効になります。  
  
 [**#pragma 領域ブロックを自動的に縮小する**]  
 このチェック ボックスをオンにすると、[プラグマ ディレクティブ](/cpp/preprocessor/pragma-directives-and-the-pragma-keyword)の自動アウトラインが有効になります。 これにより、アウトライン モードでプラグマ領域ブロックの展開と折りたたみを行うことができます。  
  
 [**ステートメント ブロックのアウトラインを自動的に実行する**]  
 このオプションを選択すると、次のステートメント構造で自動アウトラインが有効になります。  
  
-   [if-else](/dotnet/csharp/language-reference/keywords/if-else)  
  
-   [switch ステートメント (C++)](/cpp/cpp/switch-statement-cpp)  
  
-   [while ステートメント (C++)](/cpp/cpp/while-statement-cpp)  
  
## <a name="see-also"></a>関連項目  
 [[全般]、[環境]、[オプション] ダイアログ ボックス](../../ide/reference/general-environment-options-dialog-box.md)   
 [IntelliSense の使用](../../ide/using-intellisense.md)
