---
title: オプション、テキスト エディターでは、C、C++、実験用 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Experimental
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Experimental
- VS.ToolsOptionsPages.Text_Editor.C\C++.Experimental
ms.assetid: b9e9dda2-350c-460d-b368-37d6c5342eee
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6b07bdc7ab114619629ab4ef360ded3bf6655e6e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49285117"
---
# <a name="options-text-editor-cc-experimental"></a>[オプション]、[テキスト エディター]、[C/C++]、[実験用]
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
これらのオプションを変更することによって、C または C++ でプログラミングを行うときに、IntelliSense に関連する動作と参照データベースを変更できます。  
  
 このページを表示するには、左ウィンドウの **[オプション]** ダイアログ ボックスで、 **[テキスト エディター]**、 **[C/C++]** を順に展開して、 **[実験用]** を選びます。  
  
 これらの機能は、Visual Studio 2015 更新プログラム 1 RC のインストールで入手できます。  
  
> [!NOTE]
>  次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。 これらの要素は、使用している Visual Studio のエディションや独自の設定によって決まります。 「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## <a name="browsingnavigation"></a>参照/ナビゲーション  
 **新しいデータベース エンジンの有効化**  
 これにより、データベースへのデータ追加が自動的にスピードアップし、 **[定義へ移動]** や **[すべての参照の検索]** など、すべてのデータベース操作が (精度を落とすことなく) 速くなります。 (変更を適用するにはソリューションを閉じてもう一度開くだけです。Visual Studio を再起動する必要はありません。)  
  
## <a name="intellisense"></a>IntelliSense  
 **メンバー リストをドットから矢印へ**  
 メンバー リストに該当する場合に、ドット ('.') を矢印 ('->') に置換します。  
  
## <a name="refactoring"></a>リファクタリング  
 **Extract 関数の有効化**  
 選んだコードを抽出して独自の関数にし、コードを新しい関数への呼び出しに置き換えます。 この機能にアクセスするには、選んだコードを右クリックして **[クイック アクション]** を選ぶか、単に Ctrl キーを押しながらドット キーを押すだけです (Ctrl+.、既定のショートカット)。  
  
 **署名の変更を有効化**  
 関数のパラメーターを、追加、並べ替え、削除して、その変更をすべての呼び出しサイトに反映します。 この機能にアクセスするには、関数の任意の使用法を右クリックして **[クイック アクション]** を選ぶか、Ctrl キーを押しながらドット キーを押すだけです (Ctrl+.、既定のショートカット)。  
  
## <a name="text-editor"></a>[テキスト エディター]  
 **スコープの展開を有効にする**  
 有効にすると、テキスト エディターに '{' を入力すれば選んだテキストが中かっこで囲まれます。  
  
 **優先順位の展開を有効にする**  
 有効にすると、テキスト エディターに '(' を入力すれば選んだテキストがかっこで囲まれます。  
  
 Visual Studio ギャラリーのその他のテキスト エディター機能については、 [ここ](http://go.microsoft.com/fwlink/?LinkId=692016)の一覧をご覧ください。 例として、 [C++ Quick Fixes](https://visualstudiogallery.msdn.microsoft.com/be91feef-8dc3-4f7a-ac9f-f34e7ca5918f)があります。これは、次をサポートします。  
  
-   **不足している #include の追加** -コード内の不明なシンボルについて関連する #include を提案します  
  
-   **名前空間/完全修飾シンボルの使用を追加** - 前の項目と同様ですが、名前空間に機能します。  
  
-   **不足しているセミコロンの追加**  
  
-   **MSDN ヘルプ** - MSDN を検索して、エラー メッセージを調べます  
  
 波線の上にカーソルを合わせて電球マークを表示させるか、Ctrl キーを押しながらドットを押すだけです (Ctrl+.、既定のキーボード ショートカット)。 キーボード ショートカットでは、キャレットを特定のエラーやトークンの位置に置く必要はありません。エラーが出た同じ行にカーソルがあれば、行の上の何らかのものに対して解決策が提示されます。  
  
## <a name="see-also"></a>関連項目  
 [言語固有のエディター オプションの設定](../../ide/reference/setting-language-specific-editor-options.md)   
 [C++ でのリファクタリング (VC のブログ)](http://blogs.msdn.com/b/vcblog/archive/2014/11/14/all-about-c-refactoring-in-visual-studio-2015-preview.aspx)



