---
title: サードパーティ製の単体テスト フレームワークをインストールする | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 47893b70-46f8-49dc-84bd-ec820178f683
caps.latest.revision: 12
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0901c16d4e467869768b3863a194ea524b5f9472
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54787882"
---
# <a name="install-third-party-unit-test-frameworks"></a>サードパーティ製の単体テスト フレームワークをインストールする
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio テスト エクスプ ローラーは、エクスプ ローラーのアダプター インターフェイスを開発した単体テスト フレームワークを実行できます。 フレームワークのインストール プログラムは、バイナリをインストールし、サポートする言語の Visual Studio プロジェクト テンプレートを追加します。 テンプレートを使用してプロジェクトを作成する際、フレームワークはテスト エクスプ ローラーに登録されます。 Visual Studio ソリューションには異なるフレームワークを使用する単体テスト プロジェクトと、異なる言語を対象とした単体テスト プロジェクトを含めることができます。 テスト エクスプ ローラーはそれらすべてを実行します。  
  
 **必要条件**  
  
-   Visual Studio Enterprise、Visual Studio Professional  
  
## <a name="acquiring-third-party-frameworks"></a>サード パーティ製フレームワークの取得  
 Visual Studio 拡張機能マネージャーを使用して、または MSDN Web サイトの Visual Studio ギャラリーから、多くのサードパーティ製の単体テスト フレームワークをダウンロードしてインストールすることができます。 フレームワークは、フレームワークの Web サイトなどの他のサイトからダウンロードすることもできます。  
  
### <a name="installing-from-visual-studio"></a>Visual Studio からのインストール  
  
1. [標準] メニューで **[ツール]** をクリックしてから、**[拡張機能と更新プログラム]** をクリックします。  
  
2. **[オンライン]**、**[Visual Studio ギャラリー]**、**[ツール]** の順に展開します。 **[テスト]** をクリックします。  
  
3. 一覧を参照してフレームワークを検索します。  
  
4. フレームワークを選択し、**[ダウンロード]** をクリックします。  
  
   詳細については、「[Visual Studio 拡張機能の検索と使用](../ide/finding-and-using-visual-studio-extensions.md)」を参照してください。  
  
### <a name="installing-from-the-web"></a>Web からのインストール  
 関心のあるフレームワークが分かっている場合は、  
  
1. MSDN Web サイトの [Visual Studio ギャラリー](http://go.microsoft.com/fwlink/?LinkId=236267)を開きます。  
  
2. **[検索]** ボックスに、フレームワーク名を入力します。  
  
3. 結果の一覧でフレームワークを選択してから、ツールの Visual Studio ギャラリー ページに移動します。  
  
   フレームワークの一覧とともにその他のテスト ツールを参照するには、  
  
4. MSDN Web サイトの [Visual Studio ギャラリー](http://go.microsoft.com/fwlink/?LinkId=236267)を開きます。  
  
5. **[参照]** をクリックします。  
  
6. **[カテゴリ]** の一覧で、**[ツール]** ノードを展開してから、**[テスト]** をクリックします。  
  
7. 結果の一覧でフレームワークを選択してから、ツールの Visual Studio ギャラリー ページに移動します。  
  
## <a name="see-also"></a>「  
 [コードの単体テスト](../test/unit-test-your-code.md)
