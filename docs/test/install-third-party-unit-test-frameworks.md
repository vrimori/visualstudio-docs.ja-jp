---
title: "サードパーティ製の単体テスト フレームワークをインストールする | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 47893b70-46f8-49dc-84bd-ec820178f683
caps.latest.revision: 10
ms.author: douge
manager: douge
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
translationtype: Human Translation
ms.sourcegitcommit: 5ab78b6b8eaa8156ed2c8a807b1d8a80e75afa84
ms.openlocfilehash: 1c0cf482a2a5862ea8e34d20e3e75f005dbc0f17
ms.lasthandoff: 04/04/2017

---
# <a name="install-third-party-unit-test-frameworks"></a>サードパーティ製の単体テスト フレームワークをインストールする
Visual Studio テスト エクスプ ローラーは、エクスプ ローラーのアダプター インターフェイスを開発した単体テスト フレームワークを実行できます。 フレームワークのインストール プログラムは、バイナリをインストールし、サポートする言語の Visual Studio プロジェクト テンプレートを追加します。 テンプレートを使用してプロジェクトを作成する際、フレームワークはテスト エクスプ ローラーに登録されます。 Visual Studio ソリューションには異なるフレームワークを使用する単体テスト プロジェクトと、異なる言語を対象とした単体テスト プロジェクトを含めることができます。 テスト エクスプ ローラーはそれらすべてを実行します。  
  
 **Requirements**  
  
-   Visual Studio Enterprise、Visual Studio Professional  
  
## <a name="acquiring-third-party-frameworks"></a>サード パーティ製フレームワークの取得  
 Visual Studio 拡張機能マネージャーを使用して、または MSDN Web サイトの Visual Studio ギャラリーから、多くのサードパーティ製の単体テスト フレームワークをダウンロードしてインストールすることができます。 フレームワークは、フレームワークの Web サイトなどの他のサイトからダウンロードすることもできます。  
  
### <a name="installing-from-visual-studio"></a>Visual Studio からのインストール  
  
1.  [標準] メニューで **[ツール]** をクリックしてから、**[拡張機能と更新プログラム]** をクリックします。  
  
2.  **[オンライン]**、**[Visual Studio ギャラリー]**、**[ツール]** の順に展開します。 **[テスト]** をクリックします。  
  
3.  一覧を参照してフレームワークを検索します。  
  
4.  フレームワークを選択し、**[ダウンロード]** をクリックします。  
  
 詳細については、「[Visual Studio 拡張機能の検索と使用](../ide/finding-and-using-visual-studio-extensions.md)」を参照してください。  
  
### <a name="installing-from-the-web"></a>Web からのインストール  
 関心のあるフレームワークが分かっている場合は、  
  
1.  MSDN Web サイトの [Visual Studio ギャラリー](http://go.microsoft.com/fwlink/?LinkId=236267)を開きます。  
  
2.  **[検索]** ボックスに、フレームワーク名を入力します。  
  
3.  結果の一覧でフレームワークを選択してから、ツールの Visual Studio ギャラリー ページに移動します。  
  
 フレームワークの一覧とともにその他のテスト ツールを参照するには、  
  
1.  MSDN Web サイトの [Visual Studio ギャラリー](http://go.microsoft.com/fwlink/?LinkId=236267)を開きます。  
  
2.  **[参照]** をクリックします。  
  
3.  **[カテゴリ]** の一覧で、**[ツール]** ノードを展開してから、**[テスト]** をクリックします。  
  
4.  結果の一覧でフレームワークを選択してから、ツールの Visual Studio ギャラリー ページに移動します。  
  
## <a name="see-also"></a>関連項目  
 [コードの単体テスト](../test/unit-test-your-code.md)

