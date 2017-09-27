---
title: "[オプション]、[テキスト エディター]、[C/C++]、[実験用] | Microsoft Docs"
ms.custom: 
ms.date: 08/02/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Experimental
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Experimental
- VS.ToolsOptionsPages.Text_Editor.C\C++.Experimental
ms.assetid: b9e9dda2-350c-460d-b368-37d6c5342eee
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.technology:
- vs-ide-general
ms.translationtype: HT
ms.sourcegitcommit: ea1e787c1d509123a650cf2bd20e5fa8bffd5b4e
ms.openlocfilehash: faa37f88995f232f1198d3738ac5fba99d2970bd
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="options-text-editor-cc-experimental"></a>[オプション]、[テキスト エディター]、[C/C++]、[実験用]
これらのオプションを変更することによって、C または C++ でプログラミングを行うときに、IntelliSense に関連する動作と参照データベースを変更できます。 これらの機能は完全に実験用であり、Visual Studio の将来のリリースでは変更または削除される可能性があります。 このトピックでは、Visual Studio 2017 のオプションについて説明します。 Visual Studio 2015 の詳細については、「[[オプション]、[テキスト エディター]、[C/C++]、[実験用]](https://msdn.microsoft.com/library/mt591979.aspx)」を参照してください。 
  
 このプロパティ ページにアクセスするには、**Control + Q** キーを押し、`Quick Launch` をアクティブ化してから「実験用」と入力します。 クイック起動では、最初の数文字に一致するページが検索されます。 **[ツール] - [オプション]** を選択して **[テキスト エディター]** を展開し、**[C/C++]**、**[実験用]** の順に選択してアクセスすることもできます。  

 これらの機能は、Visual Studio 2017 のインストールで使用できます。  
  
> [!NOTE]
>  次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。 これらの要素は、使用している Visual Studio のエディションや独自の設定によって決まります。 「[Visual Studio IDE のカスタマイズ](../../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
## <a name="enable-predictive-intellisense"></a>予測 IntelliSense を有効にする
予測 IntelliSense は、コンテキストに関連のある結果のみが表示されるように、IntelliSense ドロップダウン リストに表示される結果の数を制限します。 たとえば、「<code>int x =</code>」と入力して IntelliSense ドロップダウン リストを呼び出すと、整数または整数を返す関数のみが表示されます。 予測 IntelliSense は既定ではオフになっています。

## <a name="enable-faster-project-load"></a>プロジェクトの高速読み込みを有効にする 
**Visual Studio 2017 バージョン 15.3 およびそれ以降**: この機能は現在、**プロジェクトのキャッシュを有効にする**と呼ばれており、[[VC++ プロジェクトの設定]](vcpp-project-settings-projects-and-solutions-options-dialog-box.md) プロパティ ページに移動しました。
このオプションでは、Visual Studio がプロジェクト データをキャッシュすることで、次にプロジェクトを開いたときにプロジェクト ファイルから再計算せずにキャッシュされたデータを読み込めるようになります。 キャッシュされたデータを使用すると、プロジェクトの読み込み時間を大幅に短縮できます。  

## <a name="additional-features-in-the-visual-studio-gallery"></a>Visual Studio ギャラリーで追加された機能
Visual Studio ギャラリーのその他のテキスト エディター機能については、[こちら](http://go.microsoft.com/fwlink/?LinkId=692016)の一覧をご覧ください。 例として、 [C++ Quick Fixes](https://visualstudiogallery.msdn.microsoft.com/be91feef-8dc3-4f7a-ac9f-f34e7ca5918f)があります。これは、次をサポートします。  
  
-   **不足している #include の追加** -コード内の不明なシンボルについて関連する #include を提案します  
  
-   **名前空間/完全修飾シンボルの使用を追加** - 前の項目と同様ですが、名前空間に機能します。  
  
-   **不足しているセミコロンの追加**  
  
-   **MSDN ヘルプ** - MSDN を検索して、エラー メッセージを調べます  
  
 波線の上にカーソルを合わせて電球マークを表示させるか、Ctrl キーを押しながらドットを押すだけです (Ctrl+.、既定のキーボード ショートカット)。 キーボード ショートカットでは、キャレットを特定のエラーやトークンの位置に置く必要はありません。エラーが出た同じ行にカーソルがあれば、行の上の何らかのものに対して解決策が提示されます。  
  
## <a name="see-also"></a>関連項目  
 [言語固有のエディター オプションの設定](../../ide/reference/setting-language-specific-editor-options.md)   
 [C++ でのリファクタリング (VC のブログ)](http://blogs.msdn.com/b/vcblog/archive/2014/11/14/all-about-c-refactoring-in-visual-studio-2015-preview.aspx)

