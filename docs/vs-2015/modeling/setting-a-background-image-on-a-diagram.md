---
title: 図の背景イメージの設定 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e334a24c-8521-4072-b50f-e59158dde145
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: ea74561974db32a831b4123578bffb755a24cbc8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537423"
---
# <a name="setting-a-background-image-on-a-diagram"></a>ダイアグラムへの背景イメージの設定
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ダイアグラムに背景イメージの設定](https://docs.microsoft.com/visualstudio/modeling/setting-a-background-image-on-a-diagram)します。  
  
[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Visualization and Modeling SDK では、カスタム コードを使用して生成されるデザイナーの背景イメージを設定できます。  
  
## <a name="setting-the-background-image"></a>背景イメージの設定  
  
#### <a name="to-set-a-background-image-for-a-generated-designer"></a>生成されるデザイナーの背景イメージを設定するには  
  
1.  図の背景として使用するイメージ ファイルを、現在のプロジェクトの Dsl\Resources ディレクトリにコピーします。  
  
2.  **ソリューション エクスプ ローラー**、dsl \resources フォルダーを右クリックし、 をポイント**追加**、 をクリックし、**既存項目の**します。  
  
3.  **既存項目の追加** ダイアログ ボックスで dsl \resources フォルダーを参照します。  
  
4.  **ファイルの種類**一覧で、**イメージ ファイル**します。  
  
5.  ディレクトリにコピーしたイメージ ファイルをクリックし、クリックして**追加**します。  
  
6.  Dsl を右クリックし、をクリックして**プロパティ**Dsl プロジェクトのプロパティを開きます。  
  
7.  **リソース**] タブで [**このプロジェクトに既定のリソース ファイルが含まれていません。ここをクリックすると、1 つを作成します。**  
  
8.  イメージ ファイルをリソース ファイルから画像をドラッグして追加**ソリューション エクスプ ローラー**リソース ウィンドウにします。  
  
9. ［ファイル］ メニューを開き、プロジェクトのプロパティを保存するオプションをクリックします。  
  
10. ファイル Dsl\Properties\Resources.resx が存在しており、その下に Resources.Designer.cs ファイルがあることを確認します。  
  
11. Resources.Designer.cs が不足している場合は、Resources.resx ファイルをクリックします。 **ソリューション エクスプ ローラー**します。  
  
12. **プロパティ**ウィンドウで、設定、`Custom Tool`プロパティを`ResXFileCodeGenerator`します。  
  
13. **ソリューション エクスプ ローラー**、Dsl プロジェクトを右クリックし、 をポイント**追加**、 をクリック**新しいフォルダー**します。  
  
14. フォルダーの名前**カスタム**します。  
  
15. カスタム フォルダーを右クリックし、[**追加**、] をクリック**新しい項目の**します。  
  
16. **新しい項目の追加**] ダイアログ ボックスで、**テンプレート**一覧で、[**コード ファイル**します。  
  
17. **名前**ボックスに「 `BackgroundImage.cs`、 をクリック**追加**します。  
  
18. 次のコードを BackgroundImage.cs ファイルにコピーし、名前空間、図クラス名、およびイメージ ファイル リソース名を調整します。  
  
     "MyDiagramClass" を、Dsl\GeneratedCode\Diagrams.cs で定義されている図の部分クラスの名前に置き換えます。 Dsl\GeneratedCode\Diagrams.cs ファイルから正しい名前空間を取得することもできます。  
  
    ```  
    using System;  
    using Microsoft.VisualStudio.Modeling.Diagrams;  
  
    // Fix the namespace:  
    namespace Fabrikam.MyLanguage  
    {  
      // Fix the Diagram Class name - get it from GeneratedCode\Diagram.cs  
  
      public partial class Language29Diagram  
      {  
        protected override void InitializeInstanceResources()  
        {  
          // Fix the Resources namespace and the Image resource name:  
          ImageField backgroundField = new ImageField("background",  
              Fabrikam.MyLanguage.Properties.Resources.MyPicture);  
  
          backgroundField.DefaultFocusable = false;  
          backgroundField.DefaultSelectable = false;  
          backgroundField.DefaultVisibility = true;  
          backgroundField.DefaultUnscaled = false;  
  
          shapeFields.Add(backgroundField);  
  
          backgroundField.AnchoringBehavior  
            .SetTopAnchor(AnchoringBehavior.Edge.Top, 0.01);  
          backgroundField.AnchoringBehavior  
            .SetLeftAnchor(AnchoringBehavior.Edge.Left, 0.01);  
          backgroundField.AnchoringBehavior  
            .SetRightAnchor(AnchoringBehavior.Edge.Right, 0.01);  
          backgroundField.AnchoringBehavior  
            .SetBottomAnchor(AnchoringBehavior.Edge.Bottom, 0.01);  
  
          base.InitializeInstanceResources();  
        }  
      }  
    }  
    ```  
  
     プログラム コードでモデルをカスタマイズする方法の詳細については、次を参照してください。[を移動すると、プログラム コードでのモデルを更新する](../modeling/navigating-and-updating-a-model-in-program-code.md)します。  
  
## <a name="see-also"></a>関連項目  
 [シェイプとコネクタの定義](../modeling/defining-shapes-and-connectors.md)   
 [テキストおよびイメージ フィールドのカスタマイズ](../modeling/customizing-text-and-image-fields.md)   
 [移動して、プログラム コードでモデルを更新しています](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [ドメイン固有言語をカスタマイズするコードの記述](../modeling/writing-code-to-customise-a-domain-specific-language.md)



