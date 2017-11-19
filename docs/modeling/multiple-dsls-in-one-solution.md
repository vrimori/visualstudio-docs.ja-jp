---
title: "1 つのソリューションに複数の Dsl |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e668620-6217-4e87-aea7-e9036776c8e4
caps.latest.revision: "3"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: b55d1d5ec8e84c8d16681ffd0ac738291e1bc39d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="multiple-dsls-in-one-solution"></a>1 つのソリューション内の複数の DSL
いくつかの DSL を単一ソリューションの一部としてパッケージ化し、同時にインストールすることができます。  
  
 複数の DSL を統合するためにいくつかの手法を使用できます。 詳細については、次を参照してください。 [Visual Studio Modelbus を使用してモデルを統合する](../modeling/integrating-models-by-using-visual-studio-modelbus.md)と[する方法: ドラッグ アンド ドロップのハンドラーを追加](../modeling/how-to-add-a-drag-and-drop-handler.md)と[コピー動作のカスタマイズ](../modeling/customizing-copy-behavior.md)です。  
  
### <a name="to-build-more-than-one-dsl-in-the-same-solution"></a>複数の DSL を同じソリューションの中にビルドするには  
  
1.  2 つ以上の DSL ソリューションと 1 つの VSIX プロジェクトを作成し、すべてのプロジェクトを単一のソリューションに追加します。  
  
    -   新しい VSIX プロジェクトを作成する: で、**新しいプロジェクト**ダイアログで、 **Visual c#**、 **Extensibility**、 **VSIX プロジェクト**です。  
  
    -   VSIX ソリューション ディレクトリ内に 2 つ以上の DSL ソリューションを作成します。  
  
         各 DSL について、Visual Studio の新しいインスタンスを開きます。 新しい DSL を作成し、同じソリューション フォルダとして VSIX ソリューションを指定します。  
  
         各 DSL は異なるファイル拡張子名を付けて作成します。  
  
    -   名前を変更、 **Dsl**と**DslPackage**プロジェクトは、すべて異なるようにします。 たとえば、`Dsl1`、`DslPackage1`、`Dsl2`、`DslPackage2` のようになります。  
  
    -   各**DslPackage\*\source.extension.tt**、正しい Dsl プロジェクト名に次の行を更新します。  
  
         `string dslProjectName = "Dsl2";`  
  
    -   VSIX ソリューションに追加、Dsl * と DslPackage\*プロジェクト。  
  
         各ペアを独自のソリューション フォルダーに配置することを推奨します。  
  
2.  以下のように DSL の VSIX マニフェストを結合します。  
  
    1.  開いている*YourVsixProject***\source.extension.manifest**です。  
  
    2.  各 DSL 選択**コンテンツの追加**追加。  
  
        -   `Dsl*`プロジェクトとして、 **MEF コンポーネント**  
  
        -   `DslPackage*`プロジェクトとして、 **MEF コンポーネント**  
  
        -   `DslPackage*`プロジェクトとして、 **VS パッケージ**  
  
3.  ソリューションをビルドします。  
  
 この結果の VSIX では両方の DSL がインストールされます。 F5 キーを使用してそれらをテストまたは配置することができます*YourVsixProject***\bin\Debug\\\*.vsix**です。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio Modelbus を使用してモデルを統合します。](../modeling/integrating-models-by-using-visual-studio-modelbus.md)   
 [方法: ドラッグ アンド ドロップのハンドラーを追加](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [コピー動作のカスタマイズ](../modeling/customizing-copy-behavior.md)